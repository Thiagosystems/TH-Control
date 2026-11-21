<p align="center">
  <img src="docs/logo.png" alt="TH Control" width="220">
</p>

<h1 align="center">TH Control</h1>

<p align="center">
  Monitor de hardware, perfis de ventoinha e energia, e otimizador de internet para jogos, num só painel.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Windows-10%20%7C%2011-0078D6?logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/.NET-8-512BD4?logo=dotnet" alt=".NET 8">
  <img src="https://img.shields.io/badge/licen%C3%A7a-MIT-green" alt="Licença MIT">
</p>

<p align="center"><a href="README.md">🇺🇸 Read in English</a></p>

---

## ✨ Recursos

### 📊 Monitor de hardware
- **Painel** com CPU (temperatura, uso, clock, potência), GPU (temperatura, hot spot, uso, clock, potência, VRAM), RAM, ventoinhas e discos
- **Gráfico** das temperaturas da CPU e da GPU nos últimos 2 minutos
- **Saúde dos SSDs e HDs**: vida útil restante, temperatura, total escrito e espaço ocupado
- **Todos os sensores** (estilo HWMonitor) agrupados por dispositivo, com valor atual, mínimo e máximo
- Filtro, zerar mínimos/máximos e exportar para CSV ou TXT
- °C ou °F e intervalo de atualização configurável

### 🌀 Ventoinhas e energia
- Perfis **Silencioso**, **Equilibrado** e **Desempenho** (mais "Padrão do sistema")
- Cada perfil ajusta o plano de energia do Windows, o limite da CPU, a política de resfriamento e a curva das ventoinhas
- O Desempenho usa o plano "Desempenho Máximo" quando ele existe no PC
- **Curva automática**: a velocidade das ventoinhas acompanha a temperatura; acima de 90 °C vai a 100% por segurança
- Cada ventoinha pode seguir o perfil, ficar em velocidade manual (0–100%) ou voltar ao controle da BIOS
- Ao fechar, o controle volta para a BIOS (opcional)
- Troca de perfil pelo ícone da bandeja

### 🌐 Internet para jogos
- **Ping ao vivo** com gráfico, média, mínimo, máximo, jitter e perda de pacotes
- **Troca de DNS** em um clique: Cloudflare, Google, Quad9, OpenDNS, AdGuard ou automático
- **Teste de velocidade dos DNS** para descobrir o mais rápido para você
- **Otimizações**:
  - desativar o algoritmo de Nagle (pacotes do jogo saem na hora)
  - desligar a limitação de rede do Windows
  - prioridade de rede (QoS) para os jogos que você escolher
- Velocidade de download/upload em tempo real e dados da conexão
- Limpar cache DNS e redefinir a rede do Windows

### 🎨 Personalização
- Temas escuro, preto e claro, 8 combinações de cores ou cores próprias, cor da logo ajustável
- Inicia com o Windows e fica na bandeja

## ⚠️ Limitações importantes

- A temperatura da CPU, os sensores da placa-mãe e o controle de ventoinhas precisam do driver **PawnIO**. O TH Control avisa quando ele falta e instala pelo winget (`winget install PawnIO`).
- **Controle de ventoinhas** só funciona em placas-mãe e placas de vídeo que permitem isso. Em notebooks e em muitas placas o controle fica travado na BIOS ou no app do fabricante; nesse caso os perfis mudam só a energia.
- As otimizações de rede **não aumentam a velocidade do seu plano**. A prioridade QoS depende de o roteador respeitar a marcação.

## 📥 Download

Baixe a versão mais recente em [**Releases**](https://github.com/Thiagosystems/THControl/releases).

> Requer o [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0) (x64) e permissão de **administrador**.

## 🛠️ Compilar

Pré-requisito: [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)

```bat
git clone https://github.com/Thiagosystems/THControl.git
cd THControl
build.bat
```

O executável fica em `publish\THControl.exe`.

## 📁 Estrutura

| Arquivo | Função |
|---|---|
| `HardwareService.cs` | Leitura dos sensores (LibreHardwareMonitor) |
| `FanAndPower.cs` | Perfis de energia e controle das ventoinhas |
| `NetworkTools.cs` | DNS, teste de DNS, otimizações e QoS |
| `Util.cs` | Comandos, PawnIO e início com o Windows |
| `ThemeManager.cs` | Temas e cores |
| `Settings.cs` | Configurações (`%AppData%\THControl\settings.json`) |
| `MainWindow.xaml` | Interface |

## 📄 Licença

Distribuído sob a licença MIT. Veja [LICENSE](LICENSE).

Usa a biblioteca [LibreHardwareMonitor](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor) (MPL-2.0) e o driver [PawnIO](https://github.com/namazso/PawnIO.Setup). Veja [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
