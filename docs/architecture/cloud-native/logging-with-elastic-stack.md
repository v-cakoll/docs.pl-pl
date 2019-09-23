---
title: Rejestrowanie przy użyciu elastycznego stosu
description: Rejestrowanie przy użyciu Elastic Stack, logstash i Kibana
ms.date: 09/23/2019
ms.openlocfilehash: b3fd3ea30f46914e6513be79f7d949499142b381
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182833"
---
# <a name="logging-with-elastic-stack"></a>Rejestrowanie przy użyciu elastycznego stosu 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Istnieje wiele dobrych narzędzi do rejestrowania, które różnią się kosztami od bezpłatnych, dostępnych narzędzi "open source" do bardziej kosztownych opcji. W wielu przypadkach bezpłatne narzędzia są tak dobre, jak w przypadku płatnych ofert. Jedno z tych narzędzi jest kombinacją trzech składników typu "open source": Wyszukiwanie elastyczne, logstash i Kibana. Zbiorowo te narzędzia są nazywane stosem elastycznym lub stosem ELK.

## <a name="what-are-the-advantages-of-elastic-stack"></a>Jakie są zalety elastycznego stosu?

Elastyczny stos umożliwia scentralizowane rejestrowanie w niedrogim, skalowalnym, przyjaznym dla chmury. Interfejs użytkownika usprawnia analizę danych, dzięki czemu można poświęcać czas na zastosują wglądu w dane na podstawie danych, zamiast zwalczać interfejs clunky. Obsługuje szeroką gamę danych wejściowych, dlatego w przypadku, gdy aplikacja rozproszona obejmuje więcej i różne rodzaje usług, można oczekiwać, że dane dziennika i metryk są dostępne w systemie. Elastyczny stos obsługuje również szybkie wyszukiwania nawet w dużych zestawach danych, dzięki czemu możliwe jest, że nawet duże aplikacje mogą rejestrować szczegółowe dane i nadal mieć możliwość wglądu w nie w sposób w pełni.

## <a name="logstash"></a>Logstash

Pierwszy składnik to [logstash](https://www.elastic.co/products/logstash). To narzędzie służy do zbierania informacji o dziennikach z wielu różnych źródeł. Na przykład logstash może odczytywać dzienniki z dysku, a także odbierać komunikaty z bibliotek rejestrowania, takich jak [Serilog](https://serilog.net/). Logstash może wykonywać pewne podstawowe filtrowanie i rozszerzanie dzienników w miarę ich odbierania. Na przykład, Jeśli dzienniki zawierają adresy IP, logstash może być skonfigurowany do przeszukiwania geograficznego i uzyskania kraju lub nawet miejscowości pochodzenia dla tego komunikatu. 

Serilog to biblioteka rejestrowania dla języków .NET, która umożliwia rejestrowanie sparametryzowane. Zamiast generowania komunikatu dziennika tekstowego, który osadza pola, parametry są przechowywane oddzielnie. Pozwala to na bardziej inteligentne filtrowanie i wyszukiwanie. Przykładowa konfiguracja Serilog do zapisu do logstash pojawia się na rysunku 7-2.

```csharp
var log = new LoggerConfiguration()   
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

**Rysunek 7-2** Serilog konfiguracja do zapisywania informacji dziennika bezpośrednio do logstash za pośrednictwem protokołu HTTP

Logstash użyje konfiguracji podobnej do przedstawionej na rysunku 7-3. 

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

**Rysunek 7-3** — konfiguracja logstash do konsumowania dzienników z Serilog

W przypadku scenariuszy, w których nie jest wymagana obszerne manipulowanie dziennikiem, istnieje alternatywa dla logstash znany jako [uderzeń](https://www.elastic.co/products/beats). Uderzeń to rodzina narzędzi, która umożliwia gromadzenie różnorodnych danych z dzienników do danych sieciowych i informacji o przestoju. Wiele aplikacji będzie używać zarówno logstash, jak i uderzeń.

Po zebraniu dzienników przez logstash należy je umieścić w miejscu. Choć logstash obsługuje wiele różnych danych wyjściowych, jedno z bardziej atrakcyjnych jest wyszukiwaniem elastycznym.

## <a name="elastic-search"></a>Wyszukiwanie elastyczne

Wyszukiwanie elastyczne to zaawansowany aparat wyszukiwania, który umożliwia indeksowanie dzienników w miarę ich odbierania. Umożliwia szybkie wykonywanie zapytań dotyczących dzienników. Wyszukiwanie elastyczne może obsługiwać duże ilości dzienników i w skrajnych przypadkach może być skalowane w wielu węzłach. 

Komunikaty dziennika, które zostały spreparowane w celu zawierają parametry lub które zostały poddane podzielenia między nimi za pośrednictwem przetwarzania logstash, można zbadać bezpośrednio, ponieważ Elasticsearch zachowuje te informacje.

Zapytanie, które wyszukuje 10 najważniejszych stron odwiedzonych przez `jill@example.com`, pojawia się na rysunku 7-4.

```
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

**Rysunek 7-4** . zapytanie Elasticsearch do znajdowania 10 najważniejszych stron odwiedzonych przez użytkownika

## <a name="visualizing-information-with-kibana-web-dashboards"></a>Wizualizacja informacji przy użyciu pulpitów nawigacyjnych sieci Web Kibana

Końcowym składnikiem stosu jest Kibana. To narzędzie służy do udostępniania interaktywnych wizualizacji na pulpicie nawigacyjnym sieci Web. Pulpity nawigacyjne mogą być przygotowane nawet przez użytkowników, którzy nie są techniczne. Większość danych znajdujących się w indeksie Elasticsearch można dołączać do pulpitów nawigacyjnych Kibana. Indywidualni użytkownicy mogą korzystać z różnych pulpitów nawigacyjnych i Kibana umożliwia to dostosowanie przez umożliwienie pulpitów nawigacyjnych specyficznych dla użytkownika. 

## <a name="installing-elastic-stack-on-azure"></a>Instalowanie elastycznego stosu na platformie Azure

Stos elastyczny można zainstalować na platformie Azure na wiele sposobów. Jak zawsze, możliwe jest [udostępnienie maszyn wirtualnych i bezpośrednie zainstalowanie na nich elastycznego stosu](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch). Ta opcja jest preferowana przez niektórych doświadczonych użytkowników, ponieważ oferuje ona najwyższy stopień szerszym. Wdrożenie w ramach infrastruktury jako usługi wprowadza znaczące narzuty związane z zarządzaniem wymuszające, że ta ścieżka przejęcie na własność wszystkich zadań związanych z infrastrukturą jako usługą, takich jak Zabezpieczanie maszyn i aktualizowanie ich przy użyciu poprawek. 

Opcja o mniejszej obciążeniu polega na użyciu jednego z wielu kontenerów platformy Docker, na którym został już skonfigurowany Stos elastyczny. Te kontenery można porzucić w istniejącym klastrze Kubernetes i uruchamiać wraz z kodem aplikacji. Kontener [sebp/Elk](https://elk-docker.readthedocs.io/) to dobrze udokumentowany i przetestowany kontener stosu elastycznego.

Kolejną opcją jest [niedawna ogłoszona oferta Elk jako usługa](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).

## <a name="references"></a>Odwołania

- [Instalowanie elastycznego stosu na platformie Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
>[Poprzedni](observability-patterns.md)
>[Następny](monitoring-azure-kubernetes.md)
