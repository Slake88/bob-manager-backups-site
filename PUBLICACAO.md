# Preparação e publicação — BOB Manager Backups

Estado em 11-11-2026: MINUTA. Não publicar nem utilizar no OAuth antes de completar as confirmações.
Repositório autorizado: Slake88/bob-manager-backups-site. Base: main.
Sem alterações ao BOB Manager, BOB TESTE, BOB REAL, Supabase ou outros repositórios.

## Conteúdo e limites
- Site estático em docs/: início, privacidade e termos; CSS local; sem dependências de compilação.
- Sem JavaScript, fontes remotas, formulários, autenticação, cookies definidos pelo código ou análise de tráfego.
- Textos pendentes visíveis; noindex é apenas uma indicação para motores de pesquisa, não controlo de acesso.
- O ramo e os ficheiros são públicos porque o repositório é público. Não colocar dados privados em minutas.
- Não foram incluídos segredos, tokens, backups, identificadores de projetos ou contas de Drive.
- Não foi criado CNAME nem workflow de publicação automática. A ausência é deliberada.

## Confirmações que bloqueiam a publicação
1. Entidade responsável e contacto público de privacidade/apoio.
2. Dados pessoais e técnicos incluídos nos backups e recebidos das APIs Google.
3. Destinos de armazenamento (Drive e outros), acessos e destinatários/prestadores.
4. Retenção, rotação, versões/lixo, eliminação e tratamento após revogação.
5. Local e proteção dos tokens e dos registos técnicos (descrever sem divulgar valores).
6. Âmbitos pedidos efetivamente pelo código: apenas drive.file foi confirmado como escolhido na consola.
7. Finalidade, fundamento aplicável, direitos, transferências e práticas Google/Limited Use.
8. Termos operacionais e apoio. Não inventar garantias, inexistência de partilha ou cumprimento já verificado.
Completar privacidade e termos e rever coerência com o funcionamento real antes de retirar avisos e noindex.
Não usar o email do autor do commit como contacto público sem confirmação.

## Exigências Google verificadas
- A política OAuth exige uma página inicial pública em domínio verificado, descrição da aplicação e ligações de privacidade e termos. Manter as três páginas solicitadas.
- A política de privacidade deve estar acessível, no mesmo domínio da página inicial e representar os tratamentos reais.
- drive.file é não sensível e limita o acesso a ficheiros criados pela app ou explicitamente abertos/partilhados com ela; não significa só escrita nem só backups.
- O âmbito escolhido na consola deve corresponder ao pedido no código. A classificação não dispensa obrigações de privacidade nem resolve automaticamente a verificação de marca.
- “Uso interno” descreve a utilização; não confirma elegibilidade para o tipo de público OAuth Internal. O histórico refere External/Testing; não foi alterado.
- A Google exige projetos separados para testes e produção; BOB TESTE e BOB REAL separados não demonstram que os projetos/clientes OAuth também estão separados. Confirmar antes da produção.
- A verificação Search Console de blueonblack.pt é informação fornecida pelo utilizador; confirmar a conta proprietária/editora associada ao projeto Google. Não alterar TXT.
- Este site informativo não deve ser usado como callback OAuth. Não criar URLs de redirecionamento fictícias.

## Pages — ativar apenas após conclusão editorial
1. Rever os ficheiros e integrar o ramo de preparação em main.
2. Em Settings > Pages > Build and deployment escolher Deploy from a branch, main, /docs. Guardar.
3. Esta opção é adequada a HTML estático e dispensa workflow personalizado e credenciais de deploy.
4. Confirmar o primeiro deploy na secção Actions/Pages. URL inicial esperada: https://slake88.github.io/bob-manager-backups-site/ (não usar como Branding definitivo).
5. Em Pages > Custom domain, guardar backups.blueonblack.pt ANTES da alteração DNS. Para publicação por ramo, o GitHub cria docs/CNAME com apenas backups.blueonblack.pt.
6. A verificação de domínio no GitHub é distinta da Search Console. O GitHub recomenda-a contra apropriação indevida. Como existe proibição de alterar TXT, qualquer verificação que exija novo TXT fica fora desta execução e requer decisão específica.
7. Só depois da associação em Pages, consultar o registo exato de backups. Se já existir e tiver outra função, não substituir sem esclarecer.
8. Criar apenas o registo DNS abaixo no fornecedor que efetivamente gere a zona. Não assumir que o alojamento Amen é o fornecedor DNS.

| Tipo | Nome | Destino |
| --- | --- | --- |
| CNAME | backups | Slake88.github.io |

Sem https://, sem nome do repositório e sem caminho no destino. TTL: manter o padrão do fornecedor.
Não alterar blueonblack.pt, www, MX, TXT, CNAME bobmanager/teste ou qualquer outro registo.
Não criar wildcard, A/AAAA no domínio principal ou redirecionamentos.
O CNAME backups está autorizado apenas quando a associação do domínio em Pages estiver confirmada.
As ferramentas GitHub conectadas usadas na preparação não oferecem administração de Pages ou DNS; não considerar configurado por existir esta documentação.

## HTTPS — obrigatório antes de Branding
- Aguardar validação DNS e emissão do certificado GitHub Pages. A propagação pode demorar até 24 horas.
- Ativar Enforce HTTPS quando disponível.
- Verificar certificado válido para backups.blueonblack.pt, cadeia de confiança e validade, sem ignorar erros TLS.
- Abrir as três URLs finais e confirmar resposta 200, conteúdo correto e navegação sem autenticação.
- Confirmar que HTTP redireciona para HTTPS e que não há recursos HTTP/conteúdo misto.
- Registar evidências abaixo. Se o certificado falhar, parar; não preencher Branding.
- Diagnosticar apenas o subdomínio autorizado. Se um bloqueio exigir outros registos (por exemplo CAA), apresentar o bloqueio sem os alterar.

| Verificação | Evidência |
| --- | --- |
| Data/hora Europe/Lisbon | Pendente |
| Commit publicado / deploy | Pendente |
| CNAME DNS backups | Pendente |
| Custom domain associado em Pages | Pendente |
| Certificado e HTTPS forçado | Pendente |
| / → 200 | Pendente |
| /privacidade/ → 200 | Pendente |
| /termos/ → 200 | Pendente |
| HTTP → HTTPS | Pendente |
| Conteúdo final e contacto aprovados | Pendente |

## Só depois: Google Auth Platform > Branding
Página inicial: https://backups.blueonblack.pt/
Política de Privacidade: https://backups.blueonblack.pt/privacidade/
Termos de Serviço: https://backups.blueonblack.pt/termos/
Domínio autorizado: blueonblack.pt
Confirmar contacto de suporte e contactos de desenvolvimento. Guardar/rever a marca conforme o estado mostrado pela Google; não confundir publicação da marca com publicação do público-alvo.
Não mudar público, clientes, escopos ou tokens por efeito desta publicação.

## Fontes oficiais consultadas em 11-11-2026
- https://developers.google.com/identity/protocols/oauth2/policies
- https://developers.google.com/identity/protocols/oauth2/production-readiness/policy-compliance
- https://developers.google.com/identity/protocols/oauth2/production-readiness/brand-verification
- https://developers.google.com/workspace/drive/api/guides/api-specific-auth
- https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https
