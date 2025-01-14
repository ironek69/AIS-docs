---
title: Obsługa urządznia z przeglądarki
sidebar_label: Obsługa urządznia z przeglądarki
---

## Wprowadzenie

> <svg style="width:24px;height:24px" viewBox="0 0 24 24">
    <path fill="#000000" d="M13,9H11V7H13M13,17H11V11H13M12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0,0 22,12A10,10 0 0,0 12,2Z" />
</svg> Jeśli jesteś posiadaczem bramki IoT AIS dom i chcesz podłączyć do niej urządzenie AIS dom, to możesz pominąć ten opis i przejść do **[Obsługa urządzenia z bramki AIS dom](/AIS-docs/docs/en/next/ais_iot_gate.html) gdzie opisaliśmy jak dodać urządzenie za pomocą prostego kreatora.** 


Urządzenie z oprogramowaniem **AIS dom** jest autonomiczne i do podstawowych funkcjonalności nie potrzebuje żadnego dodatkowego komponentu, takiego jak lokalna bramka czy zdalny serwer (chmura). Poniżej przedstawiamy w jaki sposób urządzenie może być sterowane za pomocą dowolnej przeglądarki internetowej.

## Konfiguracja Wi-Fi
Urządzenia AIS dom zapewniają bezprzewodowy punkt dostępu do łatwej konfiguracji Wi-Fi.

Podłącz urządzenie do źródła zasilania, następnie wprowadź je w tryb konfiguracj (bezprzewodowego punktu dostępu) wciskając szybko 4 razy przycisk na urządzeniu, tak jak to pokazano na animacji poniżej
<img src="/AIS-docs/img/en/iot/ais_s20_2.gif" align="center"> </img>


<img src="/AIS-docs/img/en/iot/iot_ais_dom_wifi_step1.png" width="300px" align="left" style="margin:20px;"> </img>
 Teraz na smartfonie (komputerze, tablecie, laptopie albo innym urządzeniu obsługującym sieć i Wi-Fi) wyszukaj punkt dostępu Wi-Fi o nazwie **dom_xxx_yyyyyy_zzzz** (gdzie xxx_yyyyyy_zzzz jest nazwą modelu i unikalnym identyfikatorem urządzenia) i połącz się z nim. W tym przykładzie punkt dostępu Wi-Fi ma nazwę dom_s20_3EB39C_5020.

>Bezprzewodowy punkt dostepu na urządzeniu jest **aktywny tylko przez 3 minuty**. Jeśli przegapisz to okno czasowe, może być konieczne ponowne wprowadzenie go w tryb parowania.

<img src="/AIS-docs/img/en/iot/iot_ais_dom_wifi_step2.png" width="300px" align="right" style="margin:20px;"> </img>
Po połączeniu się z Wi-Fi na urządzeniu otwórz http://192.168.4.1 w przeglądarce internetowej. Niektóre urządzenia mogą wyświetlić powiadomienie o potrzebie zalogowania się do sieci Wi-Fi, wybranie tej opcji powinno otworzyć powyższy adres automatycznie.


Na tej stronie (http://192.168.4.1) możesz przeskanować dostępne sieci Wi-Fi, następnie z listy wykrytych sieci wybrać swoją sieć Wi-Fi, do której chcesz podłączyć urządzenie.
<img src="/AIS-docs/img/en/iot/iot_ais_dom_wifi_step3.png" width="300px" align="left" style="margin:20px;"> </img>

Podaj następujące informacje:
- **SSID** - nazwa sieci Wi-Fi, do której podłączasz urządzenie.
> **Uwaga** w Identyfikatorze SSID ważna jest wielkość liter
- **Hasło** - hasło do sieci Wi-Fi, do której podłączasz urządzenie.
> **Uwaga** Hasło Wi-Fi musi mieć mniej niż 32 znaki i nie może zawierać znaków specjalnych (np. gwiazdki) lub białych znaków

Sprawdź, czy podałeś poprawne dane do sieci i kliknij **Zapisz**, aby zastosować ustawienia. Urządzenie uruchomi się ponownie i połączy się z siecią domową.
<img src="/AIS-docs/img/en/iot/iot_ais_dom_wifi_step4.png" width="300px" align="center" style="margin:20px;"> </img>


## Adres IP urządzenia

Sprawdź adres IP nowo podłączonego urządzenia w Twojej sieci.

Możesz to zrobić na swoim routerze, wystarczy, że sprawdzisz jakie IP ma nowo podłączone urządzenie o tej samej nazwie, co miał punkt dostępu Wi-Fi na urządzeniu (w tym przykładzie było to dom_s20_3EB39C_5020).

Jeśli nie masz dostępu do routera, możesz znaleźć swoje nowe urządzenie za pomocą skanera IP, np:

* [Fing](https://www.fing.com/products/) - na Androida lub iOS
* [Angry IP Scanner](https://angryip.org/) - open source dla systemów Linux, Windows i Mac (wymagana Java)
* [Super Scan](https://sectools.org/tool/superscan/) - darmowe narzędzie dostępne tylko w systemie Windows

Gdy ustalisz jaki adres IP ma urządzenie to otwórz ten adres IP za pomocą przeglądarki internetowej i **masz pełny dostęp do urządzenia w swojej lokalnej sieci**.

![MQTT aktywacja](/AIS-docs/img/en/iot/iot_web_app.png)