# Site Dra. Camila Ananias Pedron: dados para hospedagem na Vercel

## 1. O que é
- Site de uma página (home), feito em **HTML e CSS puros**.
- **Não tem JavaScript**, WordPress, framework, plugin nem banco de dados.
- **Não precisa compilar** (não há build, npm install nem dependências).
- Substitui a home atual de camilapedronadvocacia.com.br. A página antiga não deve ficar no ar, nem em outra URL.

## 2. Estrutura de arquivos (raiz do projeto)
```
index.html          página inteira (HTML + CSS dentro do arquivo)
vercel.json         configuração da Vercel (cabeçalhos, cache, sem build)
package.json        metadados (sem dependências)
favicon.svg         ícone da aba
robots.txt          permite indexação e aponta o sitemap
sitemap.xml         lista a home
.vercelignore       ignora este arquivo de informações no deploy
assets/
  hero.webp / hero.png      foto do topo (WebP com PNG de reserva)
  sobre.webp / sobre.jpg    foto da seção "Quem vai analisar" (WebP com JPG de reserva)
  og.jpg                    imagem de pré-visualização (WhatsApp, redes, Google), 1200x630
```
Peso total: cerca de 870 KB. No celular carregam só os arquivos WebP (cerca de 130 KB de imagens).

## 3. Configuração na Vercel
| Campo | Valor |
|---|---|
| Framework Preset | **Other** |
| Build Command | vazio (deixar desligado) |
| Install Command | vazio |
| Output Directory | `.` (raiz) |
| Root Directory | raiz da pasta enviada |
| Node.js | indiferente (não é usado) |
| Variáveis de ambiente | nenhuma |

O `vercel.json` já traz essas opções. Não é preciso mexer.

## 4. Como publicar (escolher um caminho)
**A. Arrastar a pasta (mais simples)**
1. Instalar: `npm i -g vercel`
2. Dentro da pasta: `vercel` (primeira vez, responder às perguntas) e depois `vercel --prod`.

**B. Pelo GitHub (recomendado para o Pablo manter)**
1. Criar repositório e enviar estes arquivos na raiz.
2. Na Vercel: Add New > Project > importar o repositório > Framework "Other" > Deploy.
3. A cada alteração enviada ao GitHub, o site atualiza sozinho.

## 5. Domínio camilapedronadvocacia.com.br
1. Vercel > Project > Settings > Domains > adicionar `camilapedronadvocacia.com.br` e `www.camilapedronadvocacia.com.br`.
2. No local onde o domínio está registrado, ajustar o DNS conforme a Vercel indicar. Os valores aparecem na tela de Domains; em geral:
   - registro **A** do domínio raiz para o IP informado pela Vercel;
   - registro **CNAME** de `www` para o endereço informado pela Vercel.
3. Escolher um endereço principal (com ou sem www) e redirecionar o outro.
4. O certificado HTTPS é emitido automaticamente.
5. Só trocar o DNS quando o Pablo confirmar que a página nova está funcionando na URL provisória `*.vercel.app`. Se o e-mail do domínio usa registros MX, **não apagar** esses registros.

## 6. Dados que estão no código (conferir antes de publicar)
- **WhatsApp:** (14) 99748-5486, link `https://wa.me/5514997485486`. Há 4 botões, cada um com mensagem própria:
  1. Dívida da empresa (botão principal)
  2. Recuperação de tributos no Simples Nacional
  3. Isenção de imposto de renda
  4. Planejamento tributário
- **OAB:** OAB/SP 545.089
- **Cidade:** Ourinhos/SP, atendimento online em todo o Brasil
- **Instagram:** @camilapedron_tributario
- **Domínio usado em canonical, sitemap e imagem de compartilhamento:** https://camilapedronadvocacia.com.br/ (se o domínio principal for outro, trocar em `index.html`, `robots.txt` e `sitemap.xml`)
- **Fontes:** Cormorant Garamond e Raleway, carregadas do Google Fonts (precisa de internet no visitante; há fontes de reserva se falharem)
- **Cores:** vinho `#4a1410`, marfim `#f7f2e8`, areia `#efe6d6`, cobre `#b97a4a` (decorativo), cobre escuro `#7a4a26` (texto), tinta `#2a1210`

## 7. O que a página NÃO tem (incluir se a campanha exigir)
- Pixel da Meta, Google Tag, Google Analytics ou eventos de clique no WhatsApp. Se o site atual usa algum, copiar o código para o `<head>` do `index.html` e manter os parâmetros de campanha (UTM).
- Formulário de contato (todo contato é pelo WhatsApp).
- Política de privacidade. Se for ligar anúncios ou pixel, criar a página e linkar no rodapé (LGPD).

## 8. Conformidade OAB (Provimento 205/2021)
A página não contém: número de clientes, anos de experiência, valores recuperados, depoimentos, promessa de resultado, "consulta gratuita", "sigilo garantido" nem "menos impostos".
Depois de publicar, conferir que **nenhum** destes textos da versão antiga sobrou em outras páginas, menu, rodapé, SEO ou cache: "+500 clientes atendidos", "R$ 10M+ recuperados", "98% de satisfação", "8+ anos de experiência", depoimentos, "Membro da Comissão de Direito Tributário da OAB", "Pós-graduação", "Menos impostos", "Sigilo absoluto garantido", "Consulta gratuita".

## 9. Checklist de teste após publicar
- [ ] Abre em https://camilapedronadvocacia.com.br sem aviso de segurança
- [ ] Os 4 botões abrem o WhatsApp com a mensagem pronta (testar no celular)
- [ ] Sem rolagem lateral no celular (360 e 390 px)
- [ ] Fotos aparecem (topo e seção "Quem vai analisar")
- [ ] A versão antiga não abre em nenhuma outra URL
- [ ] Link colado no WhatsApp mostra título, descrição e imagem
- [ ] Rastreamento existente (se houver) está disparando
