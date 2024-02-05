# EconomiaEnergia
Este Repositório tem dicas de redução de Consumo de Energia em NAS e Home Server

# Como você pode apoiar o meu trabalho

[Seja membro no Yotube](https://www.youtube.com/@LeandroPinheiroTI/membership)
[Mande uma Gorjeta no PIX](https://livepix.gg/leandropinheiroti)

# Meus vídeos sobre o tema

[![OpenMediaVault Como Reduzir Consumo de Energia?](prints/OpenMeidaVault_Como_Reduzir_Consumo_de_Energia.png)](https://youtu.be/DvxArzs84t0)

# Menos é mais
Tudo que você pluga no servidor consome energia

O Servidor normalmente é headless (sem vídeo), se a sua placa mãe suporta boot sem placa de vídeo é melhor remover, se a placa mãe/CPU tem iGPU, prefira usar a iGPU, as intel tem aceleração de codificação/decodificação desde a 5ª Geração dos Core.

* Jellyfin [HWA Tutorial On Intel GPU](https://jellyfin.org/docs/general/administration/hardware-acceleration/intel/)
* Wikipedia [Broadwell Micro Architecture](https://pt.wikipedia.org/wiki/Broadwell_(microarquitetura))

Sempre que possivel remova:
* Módulos de memória
* Teclado e mouse
* monitor
* Placa de Vídeo

# Escolha Componentes Corretamente

Prefira usar:
* Modulos de memória LDDR (consomem menos)
* SSD SATA ao invés de NVME (consome menos)
* HDD 5400 vs 7200 (consome menos)
* HDD Notebook vs Desktop (consome menos)
* Placa Mãe ITX geralmente consome menos, por ter menos componentes

# Linux Tem Recursos extras de Conservação de Energia

Alguns recursos encontrados em distribuições Linux, os exemplos aqui são do PROXMOX que é baseado em Debian, então provavelmente vai funcionar qualquer distribuição baseada em Debian, exemplos: OMV, Ubuntu, Proxmox, etc.

Para outras distribuições deve funcionar também, mas você tem que pesquisar qual o nome dos pacotes e como instalar os mesmos.

# POWERTOP

É uma ferramente para monitorar o consumo de energia, também serve para calibrar baterias de notebooks, e habilitar funcionalidades de conservação de energia em qualquer computador.

>[!WARNING]
>  *** ATENÇÃO ALGUM HARDWARE PODE SER INCOMPATIVEL COM AS ALTERAÇÕES DO POWERTOP, ANTES DE APLICAR DEFINITIVAMENTE TESTE, SE DER ALGUM PROBLEMA DE TRAVAMENTO, OU DISCOS QUE DESCONECTAM, REINICIE E NÃO USE ***

>[!TIP]
>  *** AQUI EU TENHO DUAS CONTROLADORAS DE DISCO, UMA SATA E OUTRA SAS, AMBAS EU TIVE QUE ATUALIZAR O FIRMWARE PARA PARAR DE DAR PROBLEMA COM O POWERTOP, O FIRMWARE QUE VEIO DO FABRICANTE CHINES ERA MUITO ANTIGO E NÃO FUNCIONAVA DIREITO ***

## Instalar o Powertop

```
apt install powertop
```

Se você não está logado como root

```
sudo apt install powertop
```

## Testar o Powertop

```
powertop --auto-tune
```

Se você não está logado como root

```
sudo powertop --auto-tune
```

![exemplo de uso do powertop interativamente](prints/powertop.png)

## Fazendo o Powertop aplicar no boot

Caso você não tenha nenhum problema utilizando o **powertop** no modo interativo, que tal tornar automatico o auto tune?

Edite o arquivo Cron utilizando o utilitário crontab como **root**.

```
crontab -e
```

Se você não está logado como root

```
sudo crontab -e
```

Adicione a seguinte linha no arquivo:

```
@reboot /bin/sleep 60 && /sbin/powertop --auto-tune -q > /dev/null
```

Feche e salve o editor.

