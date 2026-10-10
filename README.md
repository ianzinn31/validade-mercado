# Rasga Preço Mercado — App de Controle de Validades (Android Nativo)

Aplicativo Android nativo desenvolvido em **Kotlin + Jetpack Compose (Material 3)** para controle rápido e visual de validade de produtos no chão de loja do **Mercado Rasga Preço**.

---

## 🎨 Identidade Visual e Régua de Cores

- **Cores Oficiais:** Verde Floresta (`#136437`) e Laranja Coral (`#E85835`) baseados no logo oficial do Rasga Preço.
- **Régua de Status:**
  - 🟣 **Vencido (≤ 0 dias restantes):** Indicação de produto expirado para recolhimento imediato e baixa por perda.
  - 🔴 **Crítico (1 a 5 dias restantes):** Alerta urgente para remarcação de preço ou queima rápida de estoque.
  - 🟡 **Atenção (6 a 10 dias restantes):** Monitoramento ativo de gôndola.
  - 🟠 **Planejar (11 a 15 dias restantes):** Planejamento antecipado de reposição e giro.
  - 🟢 **Normal (> 15 dias restantes):** Produto regular no prazo.

---

## 📱 Funcionalidades Principais

1. **Cadastro em < 15 segundos:**
   - Fotografa o produto diretamente pela câmera (com compressão inteligente para economia de memória).
   - Atalhos rápidos de validade (+3d, +5d, +7d, +10d, +15d, +30d) ou calendário com toque único.
   - Seleção do setor em carrossel (Laticínios, Padaria, Frios, Mercearia, Bebidas, etc.).
   - Seletor de quantidade com botões gigantes de `+` e `−`.

2. **Painel Geral de Leitura Rápida:**
   - Contadores rápidos no topo com o total de itens em cada status.
   - Cards visuais grandes projetados para leitura à distância no corredor do mercado.
   - Filtros instantâneos por cor/urgência e por setor.

3. **Área da Gerência (Protegida por PIN):**
   - Teclado numérico grande para entrada do PIN (padrão inicial: `1234`).
   - Permissão exclusiva para **dar baixa** nos produtos (*Vendido Totalmente* ou *Descarte por Perda*).
   - Histórico completo de baixas para conferência de perdas.
   - Configuração de conexão com o banco Supabase e troca do PIN.

4. **Operação 100% Offline-First:**
   - O aplicativo funciona e cadastra mesmo sem sinal de internet no fundo da loja. Os dados e fotos ficam salvos localmente e são sincronizados quando houver conexão.

---

## 🚀 Como Testar / Instalar

O APK de teste já está gerado na pasta:
```
validade-mercado/app/build/outputs/apk/debug/app-debug.apk
```

Você pode transferir este arquivo `.apk` diretamente para qualquer celular Android via USB, WhatsApp ou Google Drive e instalar.

---

## 🗄️ Configuração do Supabase (Banco de Dados e Fotos)

1. Crie um projeto gratuito em [supabase.com](https://supabase.com).
2. Vá em **SQL Editor** e cole todo o conteúdo do arquivo [`supabase_schema.sql`](./supabase_schema.sql).
3. Clique em **Run**. O script criará:
   - O bucket de fotos `produtos` com políticas de acesso.
   - A tabela `setores` com os setores do mercado.
   - A tabela `lotes` com índices otimizados.
   - A view `vw_lotes_painel` que calcula a cor e os dias restantes automaticamente.
   - A tabela `configuracoes` para o PIN do gerente.
4. No app, entre na **Área do Gerente** > **Configurações** e salve a URL e a Anon Key do seu projeto Supabase.
