---
title: "Dostęp do konsoli bramki po SSH"
sidebar_label: SSH
---

Asystent domowy dostarcza połączenie SSH za pośrednictwem bardzo popularnego pakietu openssh.

Środowisko Linux dostępne na bramce jest systemem dla pojedynczego użytkownika, dlatego niezależnie od podanej nazwy użytkownika zalogujesz się jako jedyny dostępny użytkownik systemu Asystent domowy.


## Dostęp do konsoli z aplikacji

Istnieje możliwość dostępu bezpośrednio z naszej aplikacji (działającej w dowolnej przeglądarce) do konsoli systemowej "Asystenta domowego"

> ***Ta opcja dostępna jest tylko w lokalnej sieci.*** Obecnie nie tunelujemy portu, na którym działa serwer SSH i gdy będziesz łączył się z bramką z Internetu, to konsola nie będzie dostępna.

![SSH z aplikacji](/AIS-docs/img/en/bramka/ssh_from_app.png)


## Dostęp do konsoli z zewnętrznych klientów


### Autentykacja za pomocą hasła

Jeśli chcesz, możesz łączyć się za pomocą hasła, w tym celu należy ustalić hasło komendą passwd (tak jak we wszystkich systemach Linux)

```bash
$ passwd
``` 

![Pobranie klucza SSH](/AIS-docs/img/en/bramka/ssh_passwd.png)



### Autentykacja za pomocą autoryzowanego klucza

> W Asystencie domowym obsługujemy logowanie po SSH za pomocą autoryzowanego klucza. Wygenerowany i autoryzowany klucz dostępny jest w lokalnej instancji systemu Asystent domowy pod adresem: [https://ais-dom.local:8123/local/id_rsa_ais](https://ais-dom.local:8123/local/id_rsa_ais)

Można też go pobrać wybierając z menu **Przydatne linki**

![Pobranie klucza SSH](/AIS-docs/img/en/bramka/ssh_download_key.png)


### Połączenie z konsolą bramki za pomocą hasła

Wystarczy uruchomić klienta ssh, podając nazwę hosta bramki (lub IP) oraz port 8022

```bash
$ ssh ais-dom.local -p 8022
```

następnie podajemy hasło, które wcześniej ustaliliśmy komendą passwd.


### Połączenie z konsolą bramki za pomocą autoryzowanego klucza

#### połączenie z konsolą bramki z systemu Linux i Apple

Po pobraniu autoryzowanego klucza ssh możemy połączyć się z konsolą bramki, w tym celu w swojej konsoli wystarczy:

- zmienić uprawnienia dla pobranego klucza

```bash
$ chmod 400 id_rsa_ais
```

- uruchomić ssh z odpowiednim portem i ścieżką do klucza ssh

```bash
$ ssh ais-dom.local -p 8022 -i id_rsa_ais
```

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_console.png)


#### połączenie z konsolą bramki z systemu Windows

Zalecamy użycie darmowego programu [PuTTY](https://www.putty.org/)


Po zainstalowaniu programu należy:

##### Przegenerować klucz dostępu pobrany z bramki do formatu PuTTY

PuTTY używa własnego formatu do przechowywania kluczy. W celu skonwertowania klucza na format PuTTY zastosujemy program PuTTY Key Generator instalowany domyślnie razem z PuTTY.
W  PuTTY Key Generator naciskamy przycisk "Load":

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_putty_1.png)

wczytujemy/importujemy pobrany z bramki klucz dostępu, plik: **id_rsa_ais**

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_putty_2.png)

po udanym imporcie

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_putty_3.png)

zapisujemy plik jako prywaais_bramka_remote_sshtny klucz w formacie PuTTY jako prywatny klucz **id_rsa_ais.ppk**

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_putty_4.png)

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_putty_5.png)

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_putty_6.png)


##### Łaczenie po SSH z bramką z programu PuTTY

Uruchamiamy program PuTTY i definiujemy nowe połączenie SSH z bramką:

- podajemy IP naszej bramki
- podajemy port **8022**
- wybieramy typ połączenia **SSH**

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_putty_7.png)

Następnie podajemy ścieżkę do prywatnego klucza **id_rsa_ais.ppk**, który skonwertowaliśmy programem PuTTY Key Generator

![Połączenie SSH](/AIS-docs/img/en/bramka/ssh_putty_8.png)

Nadajemy nazwę dla połączenia i zapisujemy ją, żeby kolejnym razem można było łączyć się bez konieczności przeprowadzania powyższej konfiguracji.
