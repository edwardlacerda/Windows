# 🛠️ Script de Manutenção Completa do Windows

Este script automatiza diversas tarefas de manutenção e limpeza no Windows, como atualizações de programas, verificação de integridade do sistema, reparos de imagem e limpeza de disco.

---

## ✅ Funcionalidades Incluídas

### 🔄 Atualização de Softwares
- Atualiza todos os programas instalados via **winget** (`winget upgrade --all`)

### 🧰 Verificações e Reparos do Sistema
- Verifica e repara arquivos corrompidos do sistema com `sfc /scannow`
- Repara a imagem do sistema com `DISM /Online /Cleanup-Image /RestoreHealth`

### 🌐 Rede
- Limpa o cache de DNS com `ipconfig /flushdns`

### 🧹 Limpeza
- Executa limpeza de disco com `cleanmgr /sagerun:1` (modo silencioso)
- Agenda uma verificação de disco com `chkdsk /F /R /X` (executada no próximo reinício)

---

## 📄 Código do Script (.bat)

Salve o conteúdo abaixo como um arquivo chamado `manutencao.bat` e execute como **Administrador**.

```bat
@echo off
title Manutenção Completa do Windows
color 0A

echo ========= MANUTENÇÃO INICIADA =========
echo.

:: 1. Atualizar todos os programas com winget
echo Atualizando programas via winget...
winget upgrade --all

:: 2. Verificar e reparar arquivos do sistema
echo Verificando arquivos do sistema...
sfc /scannow

:: 3. Reparar imagem do sistema
echo Reparo avançado da imagem do Windows...
DISM /Online /Cleanup-Image /RestoreHealth

:: 4. Limpar cache de DNS
echo Limpando cache de DNS...
ipconfig /flushdns

:: 5. Limpeza de disco (modo silencioso - limpeza básica)
echo Limpando arquivos temporários...
cleanmgr /sagerun:1

:: 6. Verificação do disco (será executado no próximo reinício)
echo Agendando verificação de disco para o próximo boot...
chkdsk C: /F /R /X

:: 7. Finalização
echo.
echo ========= MANUTENÇÃO CONCLUÍDA =========
pause
