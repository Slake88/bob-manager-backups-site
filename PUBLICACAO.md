# Preparação e publicação — BOB Manager Backups

Estado em 11-11-2026: EM REVISÃO. A entidade, o contacto público e a finalidade institucional foram confirmados; não publicar nem utilizar no OAuth antes de completar as confirmações operacionais e jurídicas abaixo.
Repositório autorizado: Slake88/bob-manager-backups-site. Base: main.
Sem alterações ao BOB Manager, BOB TESTE, BOB REAL, Supabase ou outros repositórios.

## Conteúdo e limites
- Site estático em docs/: início, privacidade e termos; CSS local; sem dependências de compilação.
- Sem JavaScript, fontes remotas, formulários, autenticação, cookies definidos pelo código ou análise de tráfego.
- Textos pendentes visíveis; noindex é apenas uma indicação para motores de pesquisa, não controlo de acesso.
- O ramo e os ficheiros são públicos porque o repositório é público. Não colocar dados privados em minutas.
- Não foram incluídos segredos, tokens, backups, identificadores de projetos ou contas de Drive.
- Não foi criado CNAME nem workflow de publicação automática. A ausência é deliberada.

## Informação confirmada
- Responsável institucional indicada: BOBLEGACY – Associação Motociclista de Ação Solidária e Cultura Biker.
- Contacto público confirmado: geral@blueonblack.pt.
- Finalidade: cópias de segurança internas do BOB Manager para Google Drive, apenas no contexto dos Blue On Black.
- Domínio previsto: backups.blueonblack.pt. Ainda não está associado nem publicado.

## Confirmações que bloqueiam a publicação definitiva
1. Categorias de dados pessoais e técnicos que entrarão efetivamente nos backups, e dados recebidos das APIs Google.
2. Conta/pasta Drive de destino, quem terá acesso, partilhas, destinatários e prestadores envolvidos.
3. Fundamento jurídico aplicável e processo para exercício de direitos; confirmar morada institucional e necessidade de contacto de DPO/representante.
4. Retenção, rotação, versões/lixo, eliminação e tratamento após revogação.
5. Proteção, localização e ciclo de vida dos tokens e dos registos técnicos, sem divulgar valores.
6. Confirmar os escopos efetivamente configurados e concedidos no cliente OAuth. O código consultado pede drive.file; o preflight apenas confirma que esse escopo aparece na resposta se o campo scope estiver presente, não prova exclusividade de escopos.
7. Confirmar transferências, salvaguardas e práticas Google/Limited Use aplicáveis.
8. Aprovar os termos operacionais e o canal de apoio. Não afirmar garantias, ausência de partilha ou controlos que não foram verificados.

Os documentos permanecem em revisão e com noindex até estas confirmações e a correspondência com a operação real. O endereço de contacto foi fornecido expressamente para publicação; não foi inferido do autor do commit.

## Implementação observada no código consultado
- `tools/bob_real_drive_preflight.py` obtém um token através de refresh token Google, consulta metadados de uma pasta Drive de nome fixo e, se não a encontrar, pode criar uma pasta vazia.
- O script não envia, descarrega, cifra, retém nem recupera cópias de segurança. Não foi encontrada chamada a esse script nos workflows examinados; a sua configuração e execução operacional não foram confirmadas.
- Backups automáticos, cifragem, retenção e recuperação continuam previstos/não validados operacionalmente. Não descrever como funcionalidades disponíveis.

## Exigências Google verificadas
- A política OAuth exige uma página inicial pública em domínio verificado, descrição da aplicação e ligações de privacidade e termos. Manter as três páginas solicitadas.
- A política de privacidade deve estar acessível, no mesmo domínio da página inicial e representar os tratamentos reais.
- drive.file permite à aplicação criar ficheiros e aceder a ficheiros que criou ou que o utilizador abriu/partilhou com ela; não equivale a acesso geral ao Drive nem se limita a escrita. A descrição oficial não deve ser interpretada como prova da configuração efetiva deste cliente.
- O âmbito configurado na consola e o consentimento efetivamente concedido têm de ser conferidos com o pedido no código. A classificação do âmbito não dispensa obrigações de privacidade nem resolve automaticamente a verificação de marca.
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
- https://eur-lex.europa.eu/eli/reg/2016/679/oj/eng/
