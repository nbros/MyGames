# Mes Jeux

https://nbros.github.io/MyGames/

## GOG

Synchroniser avec toutes les extensions.

## Export CSV

- installer Python3 (WSL2 ou à partir du Windows Store)
- récupérer https://github.com/AB1908/GOG-Galaxy-Export-Script/archive/refs/heads/master.zip
- extraire dans C:\Games\MyGames\GOG-Galaxy-Export-Script-master
- récupérer https://github.com/Varstahl/GOG-Galaxy-HTML5-exporter/archive/refs/heads/master.zip
- extraire dans C:\Games\MyGames\GOG-Galaxy-HTML5-exporter-master
```
cd C:\Games\MyGames\GOG-Galaxy-Export-Script-master
python galaxy_library_export.py -a # exporte la librairie GOG vers gameDB.csv
```
- remonter gameDB.csv dans C:\Games\MyGames
```
cd C:\Games\MyGames\GOG-Galaxy-HTML5-exporter-master
python -m pip install unidecode
python csv_parser.py --image-list -i ..\gameDB.csv
```
- remplacer les fins de ligne Windows par Linux dans "C:\Games\MyGames\GOG-Galaxy-HTML5-exporter-master\imagelist.txt"
```
wsl
wget -nc -P images -i "imagelist.txt"
exit # revenir sous Windows
Get-ChildItem | % { Rename-Item $_ ($_ -replace "namespace=gamesdb",'') } # retirer les suffixes d'URL
python csv_parser.py --html5 -i ..\gameDB.csv
```
