# Instalowanie Grafany, Prometheusa i Node Exportera

## Skorzystanie z skryptów

```bash
    git clone https://github.com/Talandar99/shellfish
```

## Instalacja i konfiguracja Grafany (tylko maste

```bash
   docker pull grafana/grafana-oss # ściągniecie najnowszego obrazka
    
```


## Testowanie Prometheusa

Aby uruchomić Graphane w przeglądarce należy wpisać w przeglądarce adres:

<http://ip_maszyny:9090>

## Ustawienie Graphany

Aby uruchomić Graphane w przeglądarce należy wpisać w przeglądarce adres:

<http://ip_maszyny_mastera:3000>

Domyślne login i hasło to admin/admin, ale po zalogowaniu od razu musimy zmienić hasło

Wtedy wybieramy opcję Add your first data source

Z listy wybieramy Prometheus

W polu URL w kategorii HTTP wpisujemy adres maszyny z której chcemy zczytywać dane (pod warunkiem, że na tej maszynie działa Prometheus i Node Exporter) z portem 9090 (np. <http://127.0.0.1:9090>)

Zjeżdzamy na dół strony i klikamy Save and Test. Jeżeli otrzymamy komunikat "Data source is working" to znaczy, że wszystko działa prawidłowo.

Wracamy na samą górę, przechodzimy do zakładiiki Dashboards i importujemy wszystkie 3.

Wracamy do zakładki Settings, zjeżdzamy na dół strony i klikamy Save and Test.

Wciskamy strzałkę rozwijającą lwey pasek ekranu i wybieramy Dashboards -> Browse.

Sprawdzamy po kolei każdy z wykresów czy i jak działają
