Visualizar Logs compactados


zcat para cat, para visualizar o arquivo compactado
zgrep para grep, para pesquisar dentro do arquivo compactado
zless para less, zmore para more, para visualizar o arquivo nas páginas
zdiff para diff, para ver a diferença entre dois arquivos compactados



Lendo arquivos compactados com zless e zmore
Da mesma forma que less e more, você pode usar zless e zmore para ler o conteúdo dos arquivos compactados sem descompactá-los. Todos os atalhos de teclado do less e more funcionam da mesma forma.

zless logfile.gz

zmore logfile.gz

Pesquisa dentro de arquivos compactados com zgrep
Grep é um comando poderoso e acho um dos comandos mais usados do Linux. zgrep é a contraparte Z de grep que permite pesquisar dentro de arquivos compactados com gzip sem extraí-los.

Você pode usá-lo com todas as opções regulares de grep. Por exemplo:
zgrep -i keyword_search logfile.gz

Comparando arquivos compactados com zdiff
Embora isso possa não ser tão útil em arquivos de log enormes, você pode usar o zdiff para ver a diferença entre os arquivos compactados, da mesma forma que usa o comando diff.


zdiff logfile1.gz logfile2.gz
