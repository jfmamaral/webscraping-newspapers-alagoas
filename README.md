# webscraping-newspapers-alagoas
Funções para raspagem de dados de três dos maiores jornais alagoanos (Gazeta de Alagoas, Tribuna Hoje e Jornal Extra de Alagoas).
Coletam títulos, links e data e autorias das páginas de resultados de busca por palavras-chave nos sites. Armazenam os dados coletados em um dicionário e criam um pandas dataframe a partir dele. Em seguida exportam o dataframe em um arquivo excel no diretório especificado.

As funções são construídas em notebooks separados. Apesar da semelhança do processo de raspagem, as especificidades de cada website tornaram mais simples a produção de uma função para cada jornal.

# Como funciona
As funções realizem requests para os sites inserindo as palavras-chave indicadas pelo usuário e o número da página de resultados. Ao conseguirem acesso, criam uma variável contendo o conteúdo html com BeautifulSoup e identificam padrões html de cada site que identificam os elementos que se referem aos cards de notícias resultantes da busca.
Salvam os conteúdos identificados em uma variável e iteram sobre eles identificando padrões html de cada site que identificam títulos, datas e autorias e links.

Os dados coletados são armazenados em listas que têm suas lengths testadas para garantir a sincronia dos dados. 
Listas desiguais retornam um erro. Listas de tamanhos iguais são definidas como values de keys de um dicionário que armazena todos os dados.

Um dataframe é criado a partir do dicionário e exportado para o diretório indicado como um arquivo .xlsx.
O dataframe é retornado como resultado da função e armazenado em uma variável.



As funções recebem como parâmetros:
#### keywords (str)
String com uma ou mais palavras-chave. Sistemas de busca diferentes entre os sites possuem funcionamentos diferentes em relação ao uso de múltiplas palavras-chave, gerando respostas diferentes. Verifique o site que deseja realizar a raspagem para compreender as formas mais eficientes de busca.

#### max_page (int)
Indica o número máximo de páginas de resultado que se deseja raspar dados. Caso os resultados cessem antes do número máximo de páginas indicado, o script conclui o processo de coleta com o número de páginas encontradas.

#### save_path (str)
Indica o diretório em que deve ser exportado o dataframe em excel. O path para salvar o arquivo deve ser escrito com barras invertidas duplas "\\". (Ex: 'C:\\\Users\\\João\\\Desktop')
