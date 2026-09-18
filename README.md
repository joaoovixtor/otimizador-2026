# Otimizador 2026 V3

O Otimizador 2026 V3 é um script em lote (Batch) desenvolvido para automação do processo de manutenção, reparo de integridade e otimização do sistema operacional Windows.

---

## Recursos e Funcionalidades

* **Elevação de Privilégios**: Verificação e solicitação automática de permissões de Administrador via UAC.
* **Sistema de Logs**: Registro detalhado de cada execução no diretório `Logs` com marcação de data/hora.
* **Reparo de Integridade**: Diagnóstico e reparo da imagem do Windows (DISM) e verificação de arquivos de sistema (SFC).
* **Verificação de Disco**: Verificação de consistência e erros no disco do sistema (`chkdsk`).
* **Gerenciamento de Atualizações**: Busca e instalação de atualizações do Windows Update (via módulo `PSWindowsUpdate`) e pacotes do sistema (via `winget`).
* **Otimização de Rede**: Limpeza do cache DNS (`flushdns`) e redefinição dos componentes TCP/IP e Winsock.
* **Limpeza de Sistema**: Remoção de arquivos temporários do usuário, diretório de sistema, cache do Prefetch, downloads antigos do Windows Update e relatórios de erro (WER).
* **Otimização de Armazenamento**: Execução de TRIM em unidades SSD / desfragmentação em HDs (`Optimize-Volume`) e limpeza avançada da pasta WinSxS (`/ResetBase`).

---

## Requisitos do Sistema

* **Sistema Operacional**: Windows 10 ou Windows 11.
* **Privilégios**: Acesso de Conta de Administrador.
* **PowerShell**: PowerShell 5.1 ou superior (nativo no Windows 10/11).

---

## Como Utilizar

1. Faça o download e extraia o arquivo `Otimizador 2026 V3.bat`.
2. Clique com o botão direito sobre o arquivo `.bat` e selecione **Executar como Administrador**.
3. Confirme a solicitação de Controle de Conta de Usuário (UAC), se exibida.
4. O script iniciará a execução sequencial das 14 etapas. Etapas de longa duração possuem um tempo limite de 10 segundos antes da confirmação automática.
5. Ao término da execução, consulte o resumo na tela ou verifique o arquivo de log gerado no diretório `Logs`.
6. Reinicie o computador para aplicar todas as alterações pendentes.

---

## Etapas da Execução

1. Atualização do Provedor de Pacotes NuGet e protocolo TLS 1.2.
2. Atualização das fontes do Windows Package Manager (winget).
3. Atualização automática dos aplicativos instalados.
4. Verificação e instalação de atualizações de segurança do Windows Update.
5. Diagnóstico da imagem do sistema (`DISM /ScanHealth`).
6. Reparo da imagem do sistema (`DISM /RestoreHealth`).
7. Verificação e reparo da integridade dos arquivos de sistema (`sfc /scannow`).
8. Verificação de superfície do disco local (`chkdsk C: /scan`).
9. Atualização das definições do Microsoft Defender e escaneamento rápido.
10. Limpeza de arquivos temporários, Prefetch e relatórios de erros.
11. Redefinição das configurações de rede e limpeza de cache DNS.
12. Otimização de volume e aplicação de comando TRIM/Defrag no disco.
13. Limpeza profunda e compactação da pasta de componentes (`WinSxS`).
14. Esvaziamento da Lixeira do sistema.

---

## Aviso de Isenção de Responsabilidade

Este script realiza alterações administrativas em serviços, configurações de rede e arquivos de sistema do Windows. Recomenda-se criar um Ponto de Restauração do Sistema antes da primeira execução.
