# 🐍 Guia: Snake Animation no GitHub Profile

Este arquivo contém instruções para adicionar a animação de cobra (snake) no seu perfil do GitHub.

## 📋 Pré-requisitos

1. **Repositório do perfil criado**: Você precisa ter um repositório chamado `antonioduarte07` (igual ao seu username)
2. **README.md no perfil**: Já deve ter o README.md no repositório do perfil

## 🚀 Como Adicionar a Snake Animation

### Passo 1: Criar a estrutura de diretórios

No repositório `antonioduarte07`:

1. Clique em "Add file" → "Create new file"
2. Crie o arquivo: `.github/workflows/snake.yml`
   - ⚠️ **Importante**: O ponto (.) no início é necessário!

### Passo 2: Copiar o conteúdo

1. Abra o arquivo `.github/workflows/snake.yml` que está neste projeto
2. Copie TODO o conteúdo
3. Cole no arquivo `.github/workflows/snake.yml` do repositório do perfil
4. Faça commit com a mensagem: "Add snake animation workflow"

### Passo 3: Executar o workflow manualmente (primeira vez)

1. Vá para a aba "Actions" no seu repositório do perfil
2. Clique em "generate animation" no menu lateral
3. Clique em "Run workflow" → "Run workflow"
4. Aguarde alguns minutos para o workflow executar

### Passo 4: Verificar se funcionou

Após alguns minutos:

1. O workflow criará uma branch chamada `output`
2. Nesta branch, haverá o arquivo `github-contribution-grid-snake.svg`
3. O README.md do seu perfil já deve estar configurado para mostrar esta animação!

## ✅ Resultado Esperado

A animação da cobra aparecerá no final do seu README do perfil, mostrando um gráfico animado das suas contribuições no GitHub!

## 🔄 Atualização Automática

O workflow é executado automaticamente a cada 12 horas, então a animação será atualizada regularmente.

## 📝 Observações

- O workflow usa o username `antonioduarte07` (já configurado)
- Você pode executar manualmente quando quiser pela aba "Actions"
- A animação funciona melhor com muitos commits/contribuições

---

**Dica**: Se a animação não aparecer imediatamente, aguarde alguns minutos ou execute o workflow manualmente pela aba "Actions".
