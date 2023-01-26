# Instalowanie Grafany, Prometheusa i Node Exportera

## Instalacja i konfiguracja Grafany (tylko maste

```bash
   docker pull grafana/grafana-oss # ściągniecie najnowszego obrazka
```
## Instalacja i konfiguracja Prometeusza
```bash
 mkdir prometheus
 cd ./prometheus
 nano Dockerfile
```
```Dockerfile
FROM prom/prometheus
COPY prometheus.yml /etc/prometheus/
CMD [ "--config.file=/etc/prometheus/prometheus.yml", "--storage.tsdb.path=/prometheus" ]
```
```bash
nano docker-compose.yml
```
```yaml
scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['192.168.56.102:9090']
  - job_name: 'node'
    static_configs:
      - targets: ['192.168.56.102:3000']
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['192.168.56.102:9100']
```

## Testowanie Prometheusa

Aby uruchomić Graphane w przeglądarce należy w```bashkkpisać w przeglądarce adres:

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
