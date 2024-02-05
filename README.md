# EconomiaEnergia
Este Repositório tem dicas de redução de Consumo de Energia em NAS e Home Server

# Menos é mais
Tudo que você pluga no servidor consome energia

O Servidor normalmente é headless (sem vídeo), se a sua placa mãe suporta boot sem placa de vídeo é melhor remover, se a placa mãe/CPU tem iGPU, prefira usar a iGPU, as intel tem aceleração de codificação/decodificação desde a 5ª Geração dos Core.

* https://jellyfin.org/docs/general/administration/hardware-acceleration/intel/
* https://pt.wikipedia.org/wiki/Broadwell_(microarquitetura)

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

