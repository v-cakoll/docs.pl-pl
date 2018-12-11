---
title: Definiowanie aplikacji z wieloma kontenerami za pomocą platformy docker-compose.yml
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Jak zmiennoprzecinkową mikrousług kompozycji wieloma kontenerami w celu aplikacji za pomocą platformy docker-compose.yml.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: dc9149cb1a17e3af66abd995fd2a2196109e0e05
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145257"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definiowanie aplikacji z wieloma kontenerami za pomocą platformy docker-compose.yml 

W tym przewodniku [docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku została wprowadzona w sekcji [krok 4. Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania aplikacji platformy Docker z wieloma kontenerami](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application). Istnieją dodatkowe sposoby korzystania z plików docker-compose, które jest wart poznania bardziej szczegółowo.

Na przykład można jawnie opisano, jak chcesz wdrożyć aplikację obsługującą wiele kontenerów w pliku docker-compose.yml. Opcjonalnie można opisać, jak zamierzasz skompilować niestandardowe obrazy usługi Docker. (Niestandardowe obrazy platformy Docker może być także kompilowane przy użyciu interfejsu wiersza polecenia platformy Docker).

Zasadniczo należy zdefiniować wszystkich kontenerów, do których chcesz wdrożyć, a także niektórych parametrów dla każdego wdrożenia kontenera. Po utworzeniu pliku opisu wdrożenia z wieloma kontenerami, można wdrożyć całego rozwiązania w ramach jednej akcji dzięki [narzędzia docker compose się](https://docs.docker.com/compose/overview/) interfejsu wiersza polecenia, albo wdrożyć go sposób niewidoczny dla użytkownika w programie Visual Studio. W przeciwnym razie będziesz potrzebować na potrzeby wdrażania kontenerów przez kontener kilku kroków za pomocą interfejsu wiersza polecenia Docker `docker run` polecenie w wierszu polecenia. W związku z tym każda usługa zdefiniowane w docker-compose.yml należy określić dokładnie jeden obraz lub kompilacji. Inne klucze są opcjonalne i są analogiczne do ich `docker run` odpowiedniki wiersza polecenia.

Poniższego kodu YAML jest definicja możliwe globalnych, ale pojedynczego pliku docker-compose.yml dla przykładu w ramach aplikacji eShopOnContainers. To nie jest plikiem docker-compose rzeczywistych, w ramach aplikacji eShopOnContainers. Zamiast tego jest to wersja uproszczony i skonsolidowane w jednym pliku, który nie jest najlepszy sposób pracy z plików docker-compose, ponieważ zostaną wyjaśnione później.

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

Klucz główny, w tym pliku jest usług. W ramach tego klucza, należy zdefiniować usług, należy wdrożyć i uruchomić podczas wykonywania `docker-compose up` polecenia lub podczas wdrażania w programie Visual Studio przy użyciu tego pliku docker-compose.yml. W takim przypadku plik docker-compose.yml ma wiele usług zdefiniowane, zgodnie z opisem w poniższej tabeli.

| Nazwa usługi | Opis |
|--------------|-------------|
| webmvc       | Kontener, w tym aplikacji ASP.NET Core MVC, korzystanie z mikrousług from C po stronie serwera\#|
| Catalog.API  | Kontener, w tym mikrousług katalogu ASP.NET Core Web API |
| Ordering.API | Kontenera w tym mikrousług porządkowanie Core Web API platformy ASP.NET |
| SQL.Data     | Działanie programu SQL Server dla systemu Linux, zawierający bazy danych mikrousług kontenera |
| basket.API   | Kontener z mikrousług koszyka ASP.NET Core Web API |
| basket.Data  | Usługi za pomocą bazy danych koszyka jako pamięci podręcznej REDIS w pamięci podręcznej kontenera z systemem usługi REDIS |

### <a name="a-simple-web-service-api-container"></a>Prosty kontener interfejsu API usługi sieci Web

Koncentrujących się na jednym kontenerze, catalog.api container mikrousług ma proste definicji:

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

Ta usługa konteneryzowanych ma podstawowe następującą konfigurację:

-   Jest ona oparta na obrazie eshop/catalog.api niestandardowych. Dla sake dla uproszczenia nie istnieje żadne kompilacji: ustawienia w pliku klucza. Oznacza to, że obraz muszą wcześniej utworzone (z kompilacji platformy docker) lub zostały pobrane (za pomocą polecenie docker pull) z dowolnego rejestru platformy Docker.

-   Definiuje zmienną środowiskową o nazwie ConnectionString przy użyciu parametrów połączenia używany przez program Entity Framework do dostępu do wystąpienia programu SQL Server, który zawiera model danych wykazu. W takim przypadku ten sam kontener programu SQL Server zawiera wiele baz danych. W związku z tym potrzebujesz mniejszej ilości pamięci w komputerze deweloperskim dla platformy Docker. Jednak możesz również wdrożyć jeden kontener programu SQL Server dla każdej bazy danych z mikrousług.

-   Nazwa programu SQL Server jest sql.data, który ma taką samą nazwę, używany do kontenera, w którym jest uruchomione wystąpienie programu SQL Server dla systemu Linux. Jest to wygodne; możliwości używania to rozpoznawanie nazw (wewnętrzne hosta platformy Docker) zostanie rozwiązany adresu sieciowego, dzięki czemu nie trzeba znać wewnętrznego adresu IP dla kontenerów, do których uzyskujesz dostęp do innych kontenerów.

Ponieważ ciąg połączenia jest zdefiniowana przez zmienną środowiskową, można ustawić tę zmienną za pomocą innego mechanizmu, a w innym czasie. Na przykład można ustawić parametrów połączenia różnych podczas wdrażania do produkcji w ostatnim hostów lub wykonując z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure lub preferowanego systemu metodyki DevOps.

-   Udostępnia ona port 80 dla wewnętrznego dostęp do usługi catalog.api w ramach hosta platformy Docker. Host jest obecnie Maszynę wirtualną systemu Linux, ponieważ jest ona oparta na obrazie platformy Docker dla systemu Linux, ale można skonfigurować kontenera dla obrazu Windows należy zamiast tego uruchomić.

-   Przekazuje narażonych port 80 w kontenerze do portu 5101 na maszynie hosta platformy Docker (maszyny Wirtualnej systemu Linux).

-   Łączy on usługę sieci web w usłudze sql.data (wystąpienie programu SQL Server dla bazy danych systemu Linux uruchomiony w kontenerze). Po określeniu tej zależności, kontener catalog.api nie uruchomi kontener sql.data został już uruchomiony; jest to ważne, ponieważ catalog.api musi mieć bazy danych programu SQL Server i uruchamianie najpierw. Jednak tego rodzaju zależności kontenera nie jest wystarczające w wielu przypadkach, ponieważ Docker testy tylko na poziomie kontenera. Czasami usługi (w tym przypadku SQL Server) może być nadal nie będzie gotowe, więc zaleca się, aby zaimplementować logikę ponawiania próby z wykorzystaniem wykładniczego wycofywania w mikrousługi klienta. Dzięki temu, jeśli kontener zależność nie jest gotowy, przez krótki czas aplikacji nadal będą odporne na błędy.

-   Jest skonfigurowana, aby zezwolić na dostęp do zewnętrznych serwerów: nadmiarowe\_hostów ustawienie umożliwia dostęp do zewnętrznych serwerach lub maszynach poza hosta platformy Docker (czyli poza domyślne maszyny Wirtualnej systemu Linux, czyli programowania Docker hosta), takie jak lokalna baza SQL Wystąpienie serwera na komputerze.

Istnieją także inne, bardziej zaawansowane ustawienia docker-compose.yml, które omówimy w kolejnych sekcjach.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Przy użyciu plików docker-compose pod kątem wielu środowisk

Pliki docker-compose.yml są plikami definicji i mogą być używane przez wiele infrastruktury, które zrozumieć tego formatu. To najprostszy narzędzia docker-compose polecenia.

W związku z tym, za pomocą platformy docker-compose polecenia można wskazać następujące główne scenariusze.

#### <a name="development-environments"></a>Środowiska deweloperskie

Podczas tworzenia aplikacji jest ważne, aby można było uruchomić aplikację w środowisku izolowanym rozwoju. Możesz użyć narzędzia docker-compose polecenia interfejsu wiersza polecenia do tworzenia tego środowiska, lub użyć programu Visual Studio, która używa aparatu docker-compose dzieje się w tle.

Plik docker-compose.yml pozwala na konfigurowanie i udokumentować wszystkie usługi zależności aplikacji (inne usługi, pamięci podręcznej, baz danych, kolejki itd.). Przy użyciu interfejsu wiersza polecenia platformy docker-compose, możesz utworzyć i uruchomić co najmniej jeden kontener dla poszczególnych zależności za pomocą jednego polecenia (docker-compose się).

Pliki docker-compose.yml znajdują się pliki konfiguracyjne interpretowane przez aparat platformy Docker, ale także służyć jako pliki dokumentacji wygodne temat układu aplikacji z wieloma kontenerami.

#### <a name="testing-environments"></a>Środowisk testowych

Ważnym dowolnego ciągłe wdrażanie (CD) lub procesu ciągłej integracji (CI) są testy jednostkowe i testy integracji. Tych zautomatyzowanych testów wymagają izolowanym środowisku, więc one nie ma wpływ na użytkowników lub innych zmian w danych aplikacji.

Przy użyciu narzędzia Docker Compose możesz tworzyć i niszczyć tego środowiska izolowanego w bardzo prosty sposób za pomocą kilku poleceń z wiersza polecenia lub skryptów, takich jak następujące polecenia:

```
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>Wdrożenia produkcyjne

Umożliwia także tworzenia do wdrażania na zdalny aparat platformy Docker. Typowy przypadek jest wdrożenie w ramach pojedynczego wystąpienia hosta platformy Docker (produkcyjna maszyna wirtualna lub udostępniane z serwera, takie jak [maszyny platformy Docker](https://docs.docker.com/machine/overview/)).

Jeśli używasz innych orchestrator (z usługi Azure Service Fabric, Kubernetes itp.), może być konieczne dodać ustawienia konfiguracji instalacji i metadanych, podobnie jak w docker-compose.yml, ale w formacie wymaganym przez program orchestrator.

W każdym przypadku docker-compose jest wygodne narzędzie i metadanych formatu dla przepływów pracy programowania, testowania i produkcji, mimo że przepływ pracy produkcji mogą się różnić na programu orchestrator, którego używasz.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Przy użyciu wielu plików docker-compose do obsługi wielu środowisk

Gdy przeznaczonych dla różnych środowisk, należy użyć wielu tworzą pliki. Dzięki temu można tworzyć wiele wariantów konfiguracji, w zależności od środowiska.

#### <a name="overriding-the-base-docker-compose-file"></a>Zastępowanie pliku podstawowego docker-compose

Można użyć pliku docker-compose.yml w jednym, jak uproszczone przykłady zamieszczone w poprzednich sekcjach. Nie jest, jednak zalecane w przypadku większości aplikacji.

Domyślnie Compose odczytuje dwa pliki docker-compose.yml i plik docker-compose.override.yml opcjonalne. Jak pokazano w rysunek 6-11, gdy używasz programu Visual Studio i włączenia obsługi programu Docker, Visual Studio tworzy również plik dodatkowe compose.vs.debug.g.yml platformy docker do debugowania aplikacji, możesz zapoznaj się z tego pliku w folderze obj.\\platformy Docker \\ w folderze głównym rozwiązania.

![Struktura plików projektów docker-compose: .dockerignore do ignorowania plików. docker-compose.yml do redagowania mikrousług; docker-compose.override.yml, aby skonfigurować środowisko mikrousług.](./media/image12.png)

**Rysunek 6-11**. docker-compose plików w programie Visual Studio 2017

Możesz edytować pliki docker-compose w dowolnym edytorze, np. Visual Studio Code lub Sublime i uruchomić aplikację za pomocą platformy docker-compose up polecenia.

Zgodnie z Konwencją pliku docker-compose.yml zawiera podstawowej konfiguracji i inne statyczne ustawienia. Czy oznacza to, że konfiguracja usługi nie należy zmieniać w zależności od środowiska wdrażania przeznaczonych do pracy.

Pliku docker-compose.override.yml sugeruje nazwa, zawiera ustawienia konfiguracji, które zastępują konfiguracji podstawowej, takie jak konfiguracja, który zależy od środowiska wdrażania. Również może mieć wiele plików przesłonięcie pod różnymi nazwami. Pliki zastąpienie zwykle zawierają dodatkowe informacje wymagane przez aplikację, ale określonego środowiska lub do wdrożenia.

#### <a name="targeting-multiple-environments"></a>Przeznaczone dla wielu środowisk

Typowym przypadkiem użycia jest podczas definiowania wielu tworzą pliki tak możliwe jest Określanie wielu środowisk, takich jak środowiska produkcyjnego, przemieszczania, ciągłej integracji i programowania. Aby obsługiwać te różnice, możesz podzielić konfigurację Compose na wiele plików, jak pokazano w rysunek 6-i 12.

![Można połączyć wiele plików compose*.fml platformy docker do obsługi różnych środowisk.](./media/image13.png)

**Rysunek 6-i 12**. Wiele plików docker-compose zastępowanie wartości z pliku docker-compose.yml podstawowy

Możesz uruchomić za pomocą pliku docker-compose.yml podstawowej. Ten plik podstawowy musi zawierają ustawienia konfiguracji bazowej lub statycznych, które nie zmieniają się w zależności od środowiska. Na przykład ramach aplikacji eShopOnContainers ma następujący plik docker-compose.yml (uproszczone dzięki mniej usługi) jako pliku podstawowego.

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile    
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis
      
  rabbitmq:
    image: rabbitmq:3-management

```

Wartości w pliku docker-compose.yml podstawowego nie należy zmieniać ze względu na inną docelową wdrożenia środowiska.

Jeśli możesz skoncentrować się na webmvc definicji usługi, na przykład widać jak te informacje są bardzo podobne do niezależnie od tego, jakiego środowiska mogą być przeznaczone dla. Masz następujące informacje:

-   Nazwa usługi: webmvc.

-   Niestandardowy obraz kontenera: eshop/webmvc.

-   Polecenie do tworzenia niestandardowego obrazu platformy Docker, wskazującą, które pliku Dockerfile do użycia.

-   W zależności od innych usług, dzięki czemu ten kontener nie uruchamia się, dopóki nie uruchomiono innych kontenerów zależności.

Masz dodatkowe czynności konfiguracyjne, ale istotną kwestią jest, że w pliku docker-compose.yml podstawowego, po prostu chcesz ustawić informacje, które są wspólne w środowiskach. Następnie w docker-compose.override.yml lub podobnych plików do produkcyjnego lub tymczasowego, należy umieścić konfiguracji, które są specyficzne dla każdego środowiska.

Zazwyczaj docker-compose.override.yml jest używany dla swojego środowiska programowania, jak w poniższym przykładzie w ramach aplikacji eShopOnContainers:

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services: 
# Simplified number of services here: 
      
  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}      
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}   
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}         
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}          
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"      
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

W tym przykładzie rozwoju zastępczą konfigurację ujawnia Niektóre porty do hosta, definiuje zmiennych środowiskowych poleceniem przekierowania adresów URL i określa parametry połączenia dla środowiska programistycznego. Te ustawienia dotyczą wszystkich tylko w środowisku deweloperskim.

Po uruchomieniu `docker-compose up` (lub uruchomić go w programie Visual Studio), polecenie odczytuje automatycznie zastąpienia, tak jakby były scalania, oba pliki.

Załóżmy, że ma inny plik Compose w środowisku produkcyjnym, przy użyciu wartości różnych konfiguracji, portów lub parametry połączenia. Możesz utworzyć inny plik zastąpienie, np. plik o nazwie `docker-compose.prod.yml` z różnymi ustawieniami i zmiennych środowiskowych.  Ten plik, mogą być przechowywane w różnych repozytorium Git lub zarządzane i chronione przez inny zespół.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Jak wdrożyć za pomocą pliku określone zastąpienia

Aby korzystać z wielu plików zastąpienia lub zastąpienie pliku o innej nazwie, można użyć opcji -f, przy użyciu narzędzia docker-compose polecenia i określić pliki. Tworzenie plików scalenia w kolejności, w której są one określone w wierszu polecenia. Poniższy przykład pokazuje, jak wdrożyć zastąpienie plików.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Korzystanie ze zmiennych środowiskowych w plików docker-compose

Jest to wygodne, szczególnie w środowiskach produkcyjnych, aby można było pobrać informacji o konfiguracji ze zmiennych środowiskowych, jak firma Microsoft ma w poprzednich przykładach. Zmienna środowiskowa można się odwoływać w docker-compose plików przy użyciu składni ${MY\_VAR}. Następujący wiersz z pliku docker-compose.prod.yml pokazuje, jak odwoływać się do wartości zmiennej środowiskowej.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Zmienne środowiskowe są tworzone i inicjowane na różne sposoby, w zależności od środowiska hosta (Linux, Windows, klaster Cloud itp.). Jednak wygodne podejściem jest użycie pliku env. Obsługa plików docker-compose deklarowanie domyślną zmiennych środowiskowych w pliku env. Wartości domyślne są to wartości zmiennych środowiskowych. Jednak mogą być zastąpione przez wartości, które może być zdefiniowane we wszystkich środowiskach (system operacyjny hosta lub zmiennych środowiskowych z klastra). Umieść ten plik ENV w folderze gdzie narzędzia docker compose polecenie jest wykonywane.

W poniższym przykładzie pokazano plik ENV, takich jak [ENV](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pliku dla aplikacji w ramach aplikacji eShopOnContainers.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Narzędzia docker compose oczekuje, że każdy wiersz w pliku ENV, aby być w formacie \<zmiennej\>=\<wartość\>.

Należy pamiętać, że wartości ustawione w środowisku uruchomieniowym zawsze zastąpić wartości zdefiniowanych w pliku env. W podobny sposób wartości przekazane za pośrednictwem argumentów wiersza polecenia Zastąp wartości domyślne ustawione w pliku env.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Przegląd platformy Docker Compose** <br/>
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Wiele pliki narzędzia Compose** <br/>
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Tworzenie zoptymalizowanych obrazów platformy Docker programu ASP.NET Core

Jeśli platforma Docker i platformy .NET Core analizujesz źródeł w Internecie, można znaleźć plików Dockerfile, które przedstawiają uproszczenia tworzenia obrazu platformy Docker, kopiując źródła w kontenerze. Te przykłady sugeruje, że za pomocą prostej konfiguracji, masz obraz platformy Docker ze środowiskiem spakować z aplikacją. Poniższy przykład pokazuje prosty plik Dockerfile, w tym względzie.

```
FROM microsoft/dotnet
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Plik Dockerfile, takich jak to będzie działać. Można jednak znacznie zoptymalizować obrazów, szczególnie obrazów produkcyjnych.

W modelu mikrousług i kontenerów, są stale uruchamianie kontenerów. Typowy sposób korzystania z kontenerów nie jest ponownie uruchamiany kontener uśpiony, ponieważ kontener jest możliwe do likwidacji. Koordynatorów (takich jak Kubernetes i usługi Azure Service Fabric) jest po prostu utworzyć nowe wystąpienia obrazów. Oznacza to, że będziesz potrzebować Optymalizowanie wstępnej kompilacji aplikacji, podczas tworzenia procesu tworzenia wystąpienia będą szybciej. Po uruchomieniu kontenera, powinno być gotowe do uruchomienia. Nie powinny przywracania i skompilować wykonywania użycie `dotnet restore` i `dotnet build` poleceń z wiersz polecenia dotnet tym, jak widać w wielu wpisów w blogu o platformy .NET Core i Docker.

Zespołem platformy .NET ma zostały wykonywania pracy zapewnienie platformy .NET Core i ASP.NET Core platforma zoptymalizowane pod kątem kontenera. Nie tylko to platformy .NET Core uproszczone środowisko z zużycie pamięci; zespół koncentruje się na zoptymalizowane obrazy platformy Docker dla trzech głównych scenariuszy i opublikowane je w rejestrze usługi Docker Hub w <span class="underline">microsoft/dotnet</span>, zaczynające się od wersji 2.1:

1.  **Programowanie**: Których priorytet jest możliwość szybkiego interate i debugowania zmian i rozmiaru to dodatkowa baza danych.

2.  **Tworzenie**: Priorytet jest Kompilowanie aplikacji i zawiera pliki binarne i inne zależności, aby zoptymalizować pliki binarne.

3.  **Produkcji**: Gdy fokus jest szybkie wdrażanie i uruchamianie kontenerów, dzięki czemu te obrazy są ograniczone do plików binarnych i nedded zawartości, aby uruchomić aplikację.

Aby to osiągnąć, zespół .NET dostarcza trzy podstawowe warianty w [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (w usłudze Docker Hub):

1.  **zestaw SDK**: dla scenariuszy projektowania i kompilowania.
2.  **środowisko uruchomieniowe**: w scenariuszu produkcji i
3.  **środowisko uruchomieniowe deps**: w scenariuszu produkcyjnym z [aplikacje samodzielne](https://docs.microsoft.com/dotnet/core/deploying/index#self-contained-deployments-scd).

Środowisko uruchomieniowe obrazów zapewnia również automatyczne ustawienie aspnetcore\_adresy URL do portu 80 i wstępnie ngend pamięci podręcznej zestawów; aby ułatwić wprowadzenie szybsze uruchamianie.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Tworzenie zoptymalizowane pod kątem obrazów platformy Docker z platformą ASP.NET Core** <br/>
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

-   **Tworzenie obrazów platformy Docker dla aplikacji .NET Core** <br/>
    [*https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images)

>[!div class="step-by-step"]
>[Poprzednie](data-driven-crud-microservice.md)
>[dalej](database-server-container.md)