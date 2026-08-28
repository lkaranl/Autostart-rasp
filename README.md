# Autostart Raspberry Pi (Modo Kiosk)

Guia rápido e direto para configurar a inicialização automática do **Firefox em modo Kiosk** (tela cheia) e ocultar o cursor do mouse no Raspberry Pi OS.

---

## 📋 Pré-requisitos

Instale os pacotes necessários:

```bash
sudo apt update
sudo apt install -y firefox unclutter
```

> **Nota:** O `unclutter` é responsável por esconder o cursor do mouse após alguns segundos de inatividade.

---

## 🚀 Instalação e Configuração

### 1. Criar a pasta de autostart
Caso o diretório de inicialização automática do usuário ainda não exista, crie-o:

```bash
mkdir -p ~/.config/autostart
```

### 2. Copiar os arquivos de configuração
Copie os arquivos `.desktop` deste repositório para o diretório de autostart:

```bash
cp *.desktop ~/.config/autostart/
```

*(Opcional)* Garanta as permissões de execução:

```bash
chmod +x ~/.config/autostart/*.desktop
```

---

## ⚙️ Personalização

Para alterar a URL ou o tempo de espera antes de abrir a página, edite o arquivo `firefox_kiosk.desktop`:

```bash
nano ~/.config/autostart/firefox_kiosk.desktop
```

Altere a linha `Exec` com a sua URL:

```ini
Exec=sh -c "sleep 10 && firefox --kiosk https://sua-url-aqui.com"
```

---

## 🔄 Testar

Reinicie o Raspberry Pi para validar a inicialização automática:

```bash
sudo reboot
```

---

## 📁 Estrutura dos Arquivos

| Arquivo | Descrição |
| :--- | :--- |
| [`firefox_kiosk.desktop`](firefox_kiosk.desktop) | Inicia o Firefox em modo `--kiosk` após 10s de boot. |
| [`unclutter.desktop`](unclutter.desktop) | Oculta o cursor do mouse após 2 segundos inativo. |