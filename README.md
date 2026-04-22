# 🛡️ Eliseu Silva - Portfolio Profissional TST

## 📋 Visão Geral

Portfolio profissional de Eliseu Silva, Técnico de Segurança do Trabalho especializado em assessoria e consultoria SST para empresas de construção civil e indústria de alto risco em Portugal.

**Website:** https://www.eliseusilvasts.com  
**Versão:** 2.0  
**Última Actualização:** 19/01/2026

---

## ✨ Características Principais

### 🎯 **Funcionalidades**
- ✅ Design responsivo (mobile-first)
- ✅ PWA (Progressive Web App) preparado
- ✅ Performance otimizada
- ✅ SEO avançado com Schema.org
- ✅ Acessibilidade WCAG 2.1 AA
- ✅ Animações suaves e profissionais
- ✅ Formulário de contacto com validação avançada
- ✅ Integração WhatsApp e Email direto
- ✅ Galeria de projetos interativa
- ✅ Métricas animadas de impacto

### 🚀 **Tecnologias Utilizadas**
- **HTML5** - Estrutura semântica
- **Tailwind CSS 3.x** - Framework CSS utility-first
- **JavaScript ES6+** - Interatividade e validações
- **Schema.org** - Structured Data para SEO
- **PWA Manifest** - Instalação como app
- **Lazy Loading** - Carregamento otimizado de imagens

---

## 📁 Estrutura de Ficheiros

```
Safety_Technician/
├── index.html              # Página principal
├── manifest.json           # PWA manifest
├── robots.txt              # SEO robots
├── sitemap.xml             # Sitemap para motores de busca
├── .htaccess               # Configurações Apache (segurança + performance)
├── MELHORIAS_IMPLEMENTADAS.md  # Documentação de melhorias
├── README.md               # Este ficheiro
└── img/                    # Directório de imagens
    ├── EliseuPerfilProfissional.jpg
    ├── EliseuPerfil6.png
    ├── CapaAtual3.png
    ├── favicon.png
    ├── icon-192.png        # (criar) - Ícone PWA 192x192
    ├── icon-512.png        # (criar) - Ícone PWA 512x512
    └── [outras imagens dos projetos]
```

---

## 🔧 Configuração e Deployment

### **1. Requisitos do Servidor**

#### Mínimos:
- Apache 2.4+ ou Nginx
- PHP 7.4+ (opcional, para funcionalidades futuras)
- SSL/TLS certificado (Let's Encrypt recomendado)
- 100 MB espaço em disco
- 1 GB RAM

#### Recomendados:
- Apache 2.4+ com mod_rewrite, mod_deflate, mod_expires, mod_headers
- PHP 8.1+
- MariaDB/MySQL 10.5+ (para formulário backend futuro)
- 500 MB espaço em disco
- 2 GB RAM
- CDN (Cloudflare recomendado)

---

### **2. Instalação**

#### **Opção A: Hospedagem Partilhada (cPanel)**

1. **Upload dos ficheiros:**
   ```bash
   # Via FTP ou File Manager do cPanel
   # Fazer upload de todos os ficheiros para /public_html/
   ```

2. **Verificar .htaccess:**
   ```bash
   # Garantir que o .htaccess foi transferido
   # (pode estar oculto no File Manager)
   ```

3. **Configurar DNS:**
   - Apontar domínio para o servidor
   - Configurar SSL no cPanel (Let's Encrypt)

4. **Testar:**
   - Aceder: https://www.eliseusilvasts.com
   - Verificar: robots.txt, sitemap.xml, manifest.json

#### **Opção B: VPS/Servidor Dedicado (Ubuntu/Debian)**

```bash
# 1. Actualizar sistema
sudo apt update && sudo apt upgrade -y

# 2. Instalar Apache
sudo apt install apache2 -y

# 3. Habilitar módulos necessários
sudo a2enmod rewrite deflate expires headers ssl

# 4. Configurar Virtual Host
sudo nano /etc/apache2/sites-available/eliseusilvasts.conf
```

**Conteúdo do Virtual Host:**
```apache
<VirtualHost *:80>
    ServerName eliseusilvasts.com
    ServerAlias www.eliseusilvasts.com
    DocumentRoot /var/www/eliseusilvasts
    
    <Directory /var/www/eliseusilvasts>
        Options -Indexes +FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    
    ErrorLog ${APACHE_LOG_DIR}/eliseusilvasts_error.log
    CustomLog ${APACHE_LOG_DIR}/eliseusilvasts_access.log combined
</VirtualHost>
```

```bash
# 5. Copiar ficheiros
sudo mkdir -p /var/www/eliseusilvasts
sudo cp -r * /var/www/eliseusilvasts/

# 6. Definir permissões
sudo chown -R www-data:www-data /var/www/eliseusilvasts
sudo chmod -R 755 /var/www/eliseusilvasts

# 7. Habilitar site
sudo a2ensite eliseusilvasts.conf
sudo systemctl reload apache2

# 8. Instalar Certbot (SSL)
sudo apt install certbot python3-certbot-apache -y
sudo certbot --apache -d eliseusilvasts.com -d www.eliseusilvasts.com
```

#### **Opção C: Netlify / Vercel (Deploy Automático)**

1. **Via Git:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/Dusampley/Safety_Technician.git
   git push -u origin main
   ```

2. **Conectar a Netlify/Vercel:**
   - Importar repositório GitHub
   - Deploy automático configurado
   - SSL automático incluído

---

### **3. Configurações Pós-Deploy**

#### **A. Activar HTTPS (se não automático)**
```bash
# No .htaccess, descomentar linhas 60-62:
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

#### **B. Google Analytics (opcional)**
```html
<!-- No index.html, linhas ~110-116, substituir GA_MEASUREMENT_ID -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

#### **C. Criar Ícones PWA**
```bash
# Criar ícones a partir do logo:
# - icon-192.png (192x192 pixels)
# - icon-512.png (512x512 pixels)
# Colocar em /img/
```

#### **D. Google Search Console**
1. Ir a: https://search.google.com/search-console
2. Adicionar propriedade: eliseusilvasts.com
3. Verificar propriedade (via meta tag ou ficheiro HTML)
4. Submeter sitemap: https://www.eliseusilvasts.com/sitemap.xml

#### **E. Configurar Email do Formulário**
```javascript
// index.html, linha ~4000+
// Substituir simulação por envio real via backend/API
// Opções: EmailJS, Formspree, SendGrid, ou backend PHP
```

---

## 🔍 SEO e Performance

### **Checklist de Optimização**

#### ✅ **SEO Básico**
- [x] Meta tags completas (title, description, keywords)
- [x] Schema.org structured data
- [x] Open Graph tags (Facebook)
- [x] Twitter Cards
- [x] Sitemap.xml
- [x] Robots.txt
- [x] URLs semânticas
- [x] Alt text em todas as imagens

#### ✅ **Performance**
- [x] Compressão GZIP/Brotli
- [x] Cache de recursos (1 ano para estáticos)
- [x] Lazy loading de imagens
- [x] Preload de recursos críticos
- [x] Minificação CSS/JS (Tailwind CDN já otimizado)
- [x] Imagens otimizadas (recomendado: WebP)

#### ✅ **Acessibilidade**
- [x] ARIA labels
- [x] Navegação por teclado
- [x] Contraste de cores WCAG AA
- [x] Formulário com validação acessível
- [x] Skip links
- [x] Screen reader friendly

#### ✅ **Segurança**
- [x] HTTPS obrigatório
- [x] CSP (Content Security Policy)
- [x] X-Frame-Options
- [x] X-Content-Type-Options
- [x] Referrer-Policy
- [x] Proteção contra clickjacking

---

## 📊 Métricas de Performance

### **Targets (Lighthouse)**
- **Performance:** ≥ 90
- **Accessibility:** ≥ 95
- **Best Practices:** ≥ 90
- **SEO:** 100

### **Testar Performance:**
```bash
# Google PageSpeed Insights
https://pagespeed.web.dev/

# GTmetrix
https://gtmetrix.com/

# WebPageTest
https://www.webpagetest.org/
```

---

## 🐛 Troubleshooting

### **Problema: .htaccess não funciona**
```bash
# Verificar se mod_rewrite está activo
sudo a2enmod rewrite
sudo systemctl restart apache2

# Verificar AllowOverride no Apache config
# Deve estar "AllowOverride All"
```

### **Problema: Imagens não carregam**
```bash
# Verificar permissões
sudo chmod -R 755 /caminho/para/img/

# Verificar paths no HTML (devem ser relativos)
```

### **Problema: Formulário não envia**
```javascript
// Verificar console do browser (F12)
// Implementar backend real (actualmente é simulação)
```

### **Problema: PWA não instala**
```bash
# Verificar:
# 1. HTTPS activo
# 2. manifest.json acessível
# 3. Ícones existem em /img/
# 4. Service worker (opcional, não implementado ainda)
```

---

## 📝 Próximos Passos Recomendados

### **Curto Prazo (1-2 semanas)**
1. ✅ Substituir imagens placeholder por reais
2. ✅ Criar ícones PWA (192x192 e 512x512)
3. ✅ Configurar Google Analytics
4. ✅ Submeter sitemap ao Google Search Console
5. ✅ Testar em todos os dispositivos/browsers

### **Médio Prazo (1-2 meses)**
1. ⏳ Implementar backend para formulário (PHP/Node.js)
2. ⏳ Adicionar Service Worker para offline
3. ⏳ Criar blog/artigos sobre SST
4. ⏳ Implementar sistema de newsletter
5. ⏳ Adicionar galeria de certificações visual

### **Longo Prazo (3-6 meses)**
1. ⏳ Integrar CMS (WordPress headless ou Strapi)
2. ⏳ Criar área de cliente (login/dashboard)
3. ⏳ Sistema de agendamento online
4. ⏳ Chat ao vivo ou chatbot
5. ⏳ Multi-idioma (EN/ES)

---

## 📞 Contacto e Suporte

**Eliseu Silva**  
📧 silva.eliseu.qsms@gmail.com  
📱 WhatsApp: +351 927 945 959  
🔗 LinkedIn: [linkedin.com/in/eliseubs-tsst](https://www.linkedin.com/in/eliseubs-tsst/)

---

## 📜 Licença

© 2026 Eliseu Silva. Todos os direitos reservados.

Este portfolio é propriedade exclusiva de Eliseu Silva. O código-fonte pode ser utilizado como referência para fins educacionais, mas não deve ser copiado ou redistribuído sem autorização prévia.

---

## 🙏 Agradecimentos

- **Tailwind CSS** - Framework CSS
- **Google Fonts** - Tipografia (Inter)
- **GitHub Copilot** - Assistência no desenvolvimento
- **Constante Primar** - Parceria estratégica futura

---

**Desenvolvido com 💜 e foco em Segurança**
