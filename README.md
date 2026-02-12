# Sistema de Cadastro de Produtos

## 📋 Descripción

Aplicação web para cadastro e gerenciamento de produtos com integração a Azure Blob Storage e SQL Server.

## 🚀 Como Executar

### 1. Instalar Dependências

```bash
pip install -r requirements.txt
```

### 2. Configurar Variáveis de Ambiente

Crie um arquivo `.env` na raiz do projeto com as seguintes variáveis:

```env
# Azure Blob Storage
BLOB_CONNECTION_STRING=sua_connection_string_aqui
BLOB_CONTAINER_NAME=seu_container_aqui
BLOB_ACCOUNT_NAME=sua_conta_aqui

# SQL Server
SQL_SERVER=seu_servidor_sql
SQL_DATABASE=seu_banco_dados
SQL_USER=seu_usuario
SQL_PASSWORD=sua_senha
```

### 3. Executar o Servidor Flask

```bash
python app.py
```

O servidor iniciará em `http://localhost:5000`

## 📁 Estrutura do Projeto

```
Lab/
├── app.py                    # Servidor Flask principal
├── main.py                   # (Legacy) Versão anterior com Streamlit
├── requirements.txt          # Dependências do projeto
├── .env                      # Variáveis de ambiente (não fazerpush para git)
├── templates/
│   └── index.html           # Template HTML principal
├── static/
│   ├── styles.css           # Estilos CSS
│   ├── app.js               # JavaScript da aplicação
│   └── uploads/             # Pasta para imagens locais
└── front.js                  # (Legado) JavaScript anterior
```

## 🎨 Recursos

- ✨ Interface moderna com cores vibrantes
- 📱 Design responsivo (funciona em desktop e mobile)
- 🖼️ Upload de imagens com preview
- 🎯 Drag and drop para upload
- 💾 Integração com Azure Blob Storage
- 🗄️ Integração com SQL Server
- ⚡ Validação de formulários em tempo real
- 🔄 Carregamento dinâmico de produtos

## 📡 Endpoints da API

### POST /api/products
Cadastra um novo produto

**Request:**
```javascript
FormData {
  product_name: "string",
  product_price: "number",
  product_description: "string",
  product_image: File
}
```

**Response:**
```json
{
  "success": true,
  "message": "Produto cadastrado com sucesso!",
  "product": {
    "name": "string",
    "price": "number",
    "description": "string",
    "image_url": "string"
  }
}
```

### GET /api/products
Lista todos os produtos cadastrados

**Response:**
```json
{
  "success": true,
  "products": [
    {
      "id": "number",
      "nome": "string",
      "preco": "number",
      "descricao": "string",
      "imagem_url": "string"
    }
  ],
  "total": "number"
}
```

## 🔧 Configurações

### Limites de Arquivo
- Tamanho máximo: 16MB
- Formatos aceitos: JPG, JPEG, PNG, GIF, WebP

### Extensões Permitidas
```python
ALLOWED_EXTENSIONS = {'jpg', 'jpeg', 'png', 'gif', 'webp'}
```

## ⚠️ Notas Importantes

1. **Variáveis de Ambiente**: O arquivo `.env` é essencial para conectar ao Azure e SQL Server
2. **Modo de Desenvolvimento**: O servidor roda em modo debug por padrão
3. **Fallback Local**: Se Azure não estiver configurado, as imagens são salvas localmente em `/static/uploads/`

## 🛠️ Desenvolvimento

Para modo de produção, atualize em `app.py`:

```python
if __name__ == '__main__':
    app.run(debug=False, host='0.0.0.0', port=5000)
```

## 📦 Dependências Principais

- **Flask** 3.0.0 - Framework web
- **Flask-CORS** 4.0.0 - Suporte CORS
- **azure-storage-blob** 12.28.0 - Azure Blob Storage
- **pymssql** 2.3.0 - Conexão SQL Server
- **python-dotenv** 1.0.0 - Gerenciamento de variáveis


