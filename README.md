# ipscanner

`ipscanner` is a small LAN scanner for people who want useful answers quickly: who is on the network, what each device probably is, and which manufacturer is behind the MAC address.

It keeps the fast, practical side of `arp-scan` and `avahi-browse`, but adds a local vendor database built from the official IEEE registries. That makes manufacturer names much more consistent than relying on whatever happens to come back from a single scan.

Current release: `v0.9.1`

Source for vendor data:
- IEEE Registration Authority: https://standards.ieee.org/products-programs/regauth/
- MA-L: https://standards-oui.ieee.org/oui/oui.csv
- MA-M: https://standards-oui.ieee.org/oui28/mam.csv
- MA-S: https://standards-oui.ieee.org/oui36/oui36.csv

## Portugues

### O que ele faz

O `ipscanner` foi feito para ser simples de usar e agradavel de ler no terminal. Ele mostra os dispositivos da sua LAN com IP, MAC, fabricante, nome mDNS/DNS quando existir e alguns servicos descobertos via Bonjour.

Em vez de depender apenas do texto devolvido pelo `arp-scan`, ele consulta uma base local da IEEE. Na pratica, isso melhora bastante a qualidade do campo de fabricante. Para MACs privados e aleatorios, que sao comuns em aparelhos modernos, ele tenta ser honesto: se nao der para ter certeza, ele marca como "provavel" em vez de fingir precisao.

### Requisitos

- Python 3
- `arp-scan`
- `avahi-browse`
- permissao para executar `sudo arp-scan`

No Debian ou Ubuntu:

```bash
sudo apt update
sudo apt install -y python3 arp-scan avahi-utils
```

### Uso rapido

```bash
chmod +x ipscanner ipscanner-update-db
./ipscanner-update-db
./ipscanner
```

Ver a versao:

```bash
./ipscanner --version
```

Ver informacoes da base local:

```bash
./ipscanner --db-info
```

Atualizar a base de fabricantes:

```bash
./ipscanner-update-db
```

### O que mudou no v0.9.1

- lookup local de fabricantes com base oficial da IEEE
- suporte a MA-L, MA-M e MA-S
- deduplicacao de entradas repetidas do `arp-scan`
- heuristica cautelosa para MAC privado aleatorio
- comando separado para atualizar a base local

## English

### What it does

`ipscanner` is meant to feel practical, not academic. You run it, and it gives you a readable picture of your LAN: IP addresses, MAC addresses, likely manufacturers, Bonjour/mDNS names, and a short list of visible services.

The main improvement in `v0.9.1` is vendor detection. Instead of trusting only the raw `arp-scan` output, the tool now uses a local database compiled from the official IEEE registries. That makes manufacturer names more reliable and easier to maintain. For randomized private MAC addresses, it stays conservative and labels guesses as probable rather than pretending certainty.

### Requirements

- Python 3
- `arp-scan`
- `avahi-browse`
- permission to run `sudo arp-scan`

On Debian or Ubuntu:

```bash
sudo apt update
sudo apt install -y python3 arp-scan avahi-utils
```

### Quick start

```bash
chmod +x ipscanner ipscanner-update-db
./ipscanner-update-db
./ipscanner
```

Check the version:

```bash
./ipscanner --version
```

Inspect the local vendor database:

```bash
./ipscanner --db-info
```

Refresh vendor data:

```bash
./ipscanner-update-db
```

### Highlights in v0.9.1

- local vendor lookup based on the official IEEE registries
- support for MA-L, MA-M, and MA-S allocations
- duplicate entry cleanup for noisy `arp-scan` results
- cautious heuristics for randomized private MAC addresses
- dedicated updater for the local vendor database

## Francais

### Ce que fait le projet

`ipscanner` a ete pense pour le terminal du quotidien. L'idee n'est pas de produire un rapport complique, mais de montrer rapidement quels appareils sont presents sur le reseau local, avec une sortie lisible et utile.

La vraie difference de la version `v0.9.1`, c'est la detection des fabricants. Au lieu de faire confiance uniquement au texte renvoye par `arp-scan`, le projet utilise maintenant une base locale construite a partir des registres officiels de l'IEEE. Le resultat est plus propre, plus stable et plus credible. Quand une adresse MAC privee et aleatoire empeche une identification certaine, l'outil reste prudent et affiche une estimation probable.

### Prerequis

- Python 3
- `arp-scan`
- `avahi-browse`
- autorisation d'executer `sudo arp-scan`

Sur Debian ou Ubuntu :

```bash
sudo apt update
sudo apt install -y python3 arp-scan avahi-utils
```

### Demarrage rapide

```bash
chmod +x ipscanner ipscanner-update-db
./ipscanner-update-db
./ipscanner
```

Afficher la version :

```bash
./ipscanner --version
```

Afficher les informations de la base locale :

```bash
./ipscanner --db-info
```

Mettre a jour la base des fabricants :

```bash
./ipscanner-update-db
```

### Points importants de la v0.9.1

- resolution locale des fabricants a partir des registres officiels IEEE
- prise en charge de MA-L, MA-M et MA-S
- suppression des doublons issus de `arp-scan`
- heuristiques prudentes pour les MAC privees aleatoires
- script dedie pour mettre a jour la base locale
