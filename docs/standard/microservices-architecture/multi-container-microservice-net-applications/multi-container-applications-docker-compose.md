---
title: Definiowanie aplikacji z wieloma kontenerami za pomocą platformy docker-compose.yml
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Definiowanie aplikacji z wieloma kontenerami za pomocą platformy docker-compose.yml
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: 0c4eda54fbb1f48095d52fa798ea839eb509a636
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42754732"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definiowanie aplikacji z wieloma kontenerami za pomocą platformy docker-compose.yml 

W tym przewodniku [docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku została wprowadzona w sekcji [krok 4. Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania aplikacji platformy Docker z wieloma kontenerami](#step4_define_svcs_in_docker_compose_yml). Istnieją dodatkowe sposoby korzystania z plików docker-compose, które jest wart poznania bardziej szczegółowo.

Na przykład można jawnie opisano, jak chcesz wdrożyć aplikację obsługującą wiele kontenerów w pliku docker-compose.yml. Opcjonalnie można opisać, jak zamierzasz skompilować niestandardowe obrazy usługi Docker. (Niestandardowe obrazy platformy Docker może być także kompilowane przy użyciu interfejsu wiersza polecenia platformy Docker).

Zasadniczo należy zdefiniować wszystkich kontenerów, do których chcesz wdrożyć, a także niektórych parametrów dla każdego wdrożenia kontenera. Po utworzeniu pliku opisu wdrożenia z wieloma kontenerami, można wdrożyć całego rozwiązania w ramach jednej akcji dzięki [narzędzia docker compose się](https://docs.docker.com/compose/overview/) interfejsu wiersza polecenia, albo wdrożyć go sposób niewidoczny dla użytkownika w programie Visual Studio. W przeciwnym razie należy użyć interfejsu wiersza polecenia platformy Docker do wdrożenia kontenera przez kontener kilku kroków przy użyciu platformy docker, uruchom polecenie w wierszu polecenia. W związku z tym każda usługa zdefiniowane w docker-compose.yml należy określić dokładnie jeden obraz lub kompilacji. Inne klucze są opcjonalne i są analogiczne do ich platformy docker, uruchom odpowiedniki wiersza polecenia.

Poniższego kodu YAML jest definicja możliwe globalnych, ale pojedynczego pliku docker-compose.yml dla przykładu w ramach aplikacji eShopOnContainers. To nie jest plikiem docker-compose rzeczywistych, w ramach aplikacji eShopOnContainers. Zamiast tego jest to wersja uproszczony i skonsolidowane w jednym pliku, który nie jest najlepszy sposób pracy z plików docker-compose, ponieważ zostaną wyjaśnione później.

```yml
version: '2'

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

Klucz główny, w tym pliku jest usług. W ramach tego klucza, należy zdefiniować usług, należy wdrożyć i uruchomić podczas wykonywania narzędzia docker compose polecenia lub podczas wdrażania w programie Visual Studio przy użyciu tego pliku docker-compose.yml. W takim przypadku plik docker-compose.yml ma wiele usług zdefiniowane, zgodnie z opisem w poniższej liście.

-   webmvc kontenera w tym aplikacji ASP.NET Core MVC, korzystanie z mikrousług from C po stronie serwera\#

-   Catalog.API kontenera w tym mikrousług katalogu ASP.NET Core Web API

-   Ordering.API kontenera w tym mikrousług porządkowanie Core Web API platformy ASP.NET

-   SQL.Data kontenera z programem SQL Server dla systemu Linux, zawierający bazy danych mikrousług

-   basket.API kontenera przy użyciu mikrousług koszyka ASP.NET Core Web API

-   basket.Data kontenera z systemem usługi REDIS cache service z bazą danych koszyka jako pamięci podręcznej REDIS

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

Ponieważ ciąg połączenia jest zdefiniowana przez zmienną środowiskową, można ustawić tę zmienną za pomocą innego mechanizmu, a w innym czasie. Na przykład można ustawić parametrów połączenia różnych podczas wdrażania do produkcji w ostatnim hostów lub wykonując z potoków ciągłej integracji/ciągłego wdrażania w usłudze VSTS lub preferowanego systemu metodyki DevOps.

-   Udostępnia ona port 80 dla wewnętrznego dostęp do usługi catalog.api w ramach hosta platformy Docker. Host jest obecnie Maszynę wirtualną systemu Linux, ponieważ jest ona oparta na obrazie platformy Docker dla systemu Linux, ale można skonfigurować kontenera dla obrazu Windows należy zamiast tego uruchomić.

-   Przekazuje narażonych port 80 w kontenerze do portu 5101 na maszynie hosta platformy Docker (maszyny Wirtualnej systemu Linux).

-   Łączy on usługę sieci web w usłudze sql.data (wystąpienie programu SQL Server dla bazy danych systemu Linux uruchomiony w kontenerze). Po określeniu tej zależności, kontener catalog.api nie uruchomi kontener sql.data został już uruchomiony; jest to ważne, ponieważ catalog.api musi mieć bazy danych programu SQL Server i uruchamianie najpierw. Jednak tego rodzaju zależności kontenera nie jest wystarczające w wielu przypadkach, ponieważ Docker testy tylko na poziomie kontenera. Czasami usługi (w tym przypadku SQL Server) może być nadal nie będzie gotowe, więc zaleca się, aby zaimplementować logikę ponawiania próby z wykorzystaniem wykładniczego wycofywania w mikrousługi klienta. Dzięki temu, jeśli kontener zależność nie jest gotowy, przez krótki czas aplikacji nadal będą odporne na błędy.

-   Jest skonfigurowana, aby zezwolić na dostęp do zewnętrznych serwerów: nadmiarowe\_hostów ustawienie umożliwia dostęp do zewnętrznych serwerach lub maszynach poza hosta platformy Docker (czyli poza domyślne maszyny Wirtualnej systemu Linux, czyli programowania Docker hosta), takie jak lokalna baza SQL Wystąpienie serwera na komputerze.

Istnieją także inne, bardziej zaawansowane ustawienia docker-compose.yml, które omówimy w kolejnych sekcjach.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Przy użyciu plików docker-compose pod kątem wielu środowisk

Pliki docker-compose.yml są plikami definicji i mogą być używane przez wiele infrastruktury, które zrozumieć tego formatu. Narzędzie to najprostszy jest platformy docker-compose polecenia, ale innych narzędzi, takich jak koordynatorów (na przykład, Docker Swarm) również zrozumienie tego pliku.

W związku z tym, za pomocą platformy docker-compose polecenia można wskazać następujące główne scenariusze.

#### <a name="development-environments"></a>Środowiska deweloperskie

Podczas tworzenia aplikacji jest ważne, aby można było uruchomić aplikację w środowisku izolowanym rozwoju. Możesz użyć narzędzia docker-compose polecenia interfejsu wiersza polecenia do tworzenia tego środowiska, lub użyć programu Visual Studio, która używa aparatu docker-compose dzieje się w tle.

Plik docker-compose.yml pozwala na konfigurowanie i udokumentować wszystkie usługi zależności aplikacji (inne usługi, pamięci podręcznej, baz danych, kolejki itd.). Przy użyciu interfejsu wiersza polecenia platformy docker-compose, możesz utworzyć i uruchomić co najmniej jeden kontener dla poszczególnych zależności za pomocą jednego polecenia (docker-compose się).

Pliki docker-compose.yml znajdują się pliki konfiguracyjne interpretowane przez aparat platformy Docker, ale także służyć jako pliki dokumentacji wygodne temat układu aplikacji z wieloma kontenerami.

#### <a name="testing-environments"></a>Środowisk testowych

Ważnym dowolnego ciągłe wdrażanie (CD) lub procesu ciągłej integracji (CI) są testy jednostkowe i testy integracji. Tych zautomatyzowanych testów wymagają izolowanym środowisku, więc one nie ma wpływ na użytkowników lub innych zmian w danych aplikacji.

Przy użyciu narzędzia Docker Compose możesz tworzyć i niszczyć tego środowiska izolowanego w bardzo prosty sposób za pomocą kilku poleceń z wiersza polecenia lub skryptów, takich jak następujące polecenia:

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Wdrożenia produkcyjne

Umożliwia także tworzenia do wdrażania na zdalny aparat platformy Docker. Typowy przypadek jest wdrożenie w ramach pojedynczego wystąpienia hosta platformy Docker (produkcyjna maszyna wirtualna lub udostępniane z serwera, takie jak [maszyny platformy Docker](https://docs.docker.com/machine/overview/)). Jednak może być również cały [Docker Swarm](https://docs.docker.com/swarm/overview/) klastra, ponieważ klastry są również zgodne z pliki docker-compose.yml.

Jeśli używasz innych orchestrator (usługi Azure Service Fabric, Mesos DC/OS, Kubernetes itp.), może być konieczne dodać ustawienia konfiguracji instalacji i metadanych, podobnie jak w docker-compose.yml, ale w formacie wymaganym przez program orchestrator.

W każdym przypadku docker-compose jest wygodne narzędzie i metadanych formatu dla przepływów pracy programowania, testowania i produkcji, mimo że przepływ pracy produkcji mogą się różnić na programu orchestrator, którego używasz.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Przy użyciu wielu plików docker-compose do obsługi wielu środowisk

Gdy przeznaczonych dla różnych środowisk, należy użyć wielu tworzą pliki. Dzięki temu można tworzyć wiele wariantów konfiguracji, w zależności od środowiska.

#### <a name="overriding-the-base-docker-compose-file"></a>Zastępowanie pliku podstawowego docker-compose

Można użyć pliku docker-compose.yml w jednym, jak uproszczone przykłady zamieszczone w poprzednich sekcjach. Nie jest, jednak zalecane w przypadku większości aplikacji.

Domyślnie Compose odczytuje dwa pliki docker-compose.yml i plik docker-compose.override.yml opcjonalne. Jak pokazano w rysunek 8-11, gdy są przy użyciu programu Visual Studio i włączenie również obsługę platformy Docker, Visual Studio tworzy plik dodatkowe compose.ci.build,yml platformy docker do użycia z potoków ciągłej integracji/ciągłego Dostarczania, takich jak w usłudze VSTS.

![](./media/image12.png)

**Rysunek 8-11**. docker-compose plików w programie Visual Studio 2017

Możesz edytować pliki docker-compose w dowolnym edytorze, np. Visual Studio Code lub Sublime i uruchomić aplikację za pomocą platformy docker-compose up polecenia.

Zgodnie z Konwencją pliku docker-compose.yml zawiera podstawowej konfiguracji i inne statyczne ustawienia. Czy oznacza to, że konfiguracja usługi nie należy zmieniać w zależności od środowiska wdrażania przeznaczonych do pracy.

Pliku docker-compose.override.yml sugeruje nazwa, zawiera ustawienia konfiguracji, które zastępują konfiguracji podstawowej, takie jak konfiguracja, który zależy od środowiska wdrażania. Również może mieć wiele plików przesłonięcie pod różnymi nazwami. Pliki zastąpienie zwykle zawierają dodatkowe informacje wymagane przez aplikację, ale określonego środowiska lub do wdrożenia.

#### <a name="targeting-multiple-environments"></a>Przeznaczone dla wielu środowisk

Typowym przypadkiem użycia jest podczas definiowania wielu tworzą pliki tak możliwe jest Określanie wielu środowisk, takich jak środowiska produkcyjnego, przemieszczania, ciągłej integracji i programowania. Aby obsługiwać te różnice, możesz podzielić konfigurację Compose na wiele plików, jak pokazano na rysunku 8-12.

![](./media/image13.png)

**Rysunek 8-12**. Wiele plików docker-compose zastępowanie wartości z pliku docker-compose.yml podstawowy

Możesz uruchomić za pomocą pliku docker-compose.yml podstawowej. Ten plik podstawowy musi zawierają ustawienia konfiguracji bazowej lub statycznych, które nie zmieniają się w zależności od środowiska. Na przykład ramach aplikacji eShopOnContainers ma następujący plik docker-compose.yml jako pliku podstawowego.

```yml
#docker-compose.yml (Base)
version: '3'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: ./src/Services/Basket/Basket.API
      dockerfile: Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: ./src/Services/Catalog/Catalog.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: ./src/Services/Marketing/Marketing.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: ./src/Web/WebMVC
      dockerfile: Dockerfile    
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
version: '3'

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
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5101/api/v1/catalog/items/[0]/pic/}   
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
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
      - LocationsUrl=http://locations.api
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://marketing.api                                                    
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc     
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
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

Po uruchomieniu `docker-compose up` (lub uruchomić go w programie Visual Studio), polecenie odczytuje automatycznie zastąpienia, tak jakby były scalania, oba pliki.

Załóżmy, że ma inny plik Compose w środowisku produkcyjnym, przy użyciu wartości różnych konfiguracji, portów lub parametry połączenia. Możesz utworzyć inny plik zastąpienie, np. plik o nazwie `docker-compose.prod.yml` z różnymi ustawieniami i zmiennych środowiskowych.  Ten plik, mogą być przechowywane w różnych repozytorium Git lub zarządzane i chronione przez inny zespół.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Jak wdrożyć za pomocą pliku określone zastąpienia

Aby korzystać z wielu plików zastąpienia lub zastąpienie pliku o innej nazwie, można użyć opcji -f, przy użyciu narzędzia docker-compose polecenia i określić pliki. Tworzenie plików scalenia w kolejności, w której są one określone w wierszu polecenia. Poniższy przykład pokazuje, jak wdrożyć zastąpienie plików.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Korzystanie ze zmiennych środowiskowych w plików docker-compose

Jest to wygodne, szczególnie w środowiskach produkcyjnych, aby można było pobrać informacji o konfiguracji ze zmiennych środowiskowych, jak firma Microsoft ma w poprzednich przykładach. Odwołania zmiennej środowiskowej w plikach docker-compose przy użyciu składni \${MY\_VAR}. Następujący wiersz z pliku docker-compose.prod.yml pokazuje, jak odwoływać się do wartości zmiennej środowiskowej.

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

Narzędzia docker compose oczekuje, że każdy wiersz w pliku ENV, aby być w formacie &lt;zmiennej&gt;=&lt;wartość&gt;.

Należy pamiętać, że wartości ustawione w środowisku uruchomieniowym zawsze zastąpić wartości zdefiniowanych w pliku env. W podobny sposób wartości przekazane za pośrednictwem argumentów wiersza polecenia Zastąp wartości domyślne ustawione w pliku env.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Przegląd platformy Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Wiele pliki narzędzia Compose**
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

W modelu mikrousług i kontenerów, są stale uruchamianie kontenerów. Typowy sposób korzystania z kontenerów nie jest ponownie uruchamiany kontener uśpiony, ponieważ kontener jest możliwe do likwidacji. Koordynatorów (np. rozwiązania Docker Swarm, Kubernetes, DCOS lub Azure Service Fabric) jest po prostu utworzyć nowe wystąpienia obrazów. Oznacza to, że będziesz potrzebować Optymalizowanie wstępnej kompilacji aplikacji, podczas tworzenia procesu tworzenia wystąpienia będą szybciej. Po uruchomieniu kontenera, powinno być gotowe do uruchomienia. Nie należy przywrócić i kompilacji w czasie wykonywania, za pomocą polecenia dotnet restore dotnet kompilacji i poleceń interfejsu wiersza polecenia platformy dotnet, jak widać w wielu wpisów w blogu o platformy .NET Core i Docker.

Zespołem platformy .NET ma zostały wykonywania pracy zapewnienie platformy .NET Core i ASP.NET Core platforma zoptymalizowane pod kątem kontenera. Nie tylko to platformy .NET Core uproszczone środowisko z zużycie pamięci; zespół koncentruje się na wydajności uruchamiania i generowane niektóre zoptymalizowane obrazy platformy Docker, takie jak [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obraz dostępne pod adresem [usługi Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), w porównaniu ze zwykłych [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) lub [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) obrazów. [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obraz oferuje automatyczne ustawienie aspnetcore\_adresy URL do portu 80 oraz wstępnie ngend pamięci podręcznej zestawów; oba te ustawienia spowodować szybsze uruchamianie.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Tworzenie zoptymalizowane pod kątem obrazów platformy Docker z platformą ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Tworzenie aplikacji z kontenera kompilacji (CI)

Kolejną korzyścią platformy Docker jest tworzyć aplikacji w kontenerze, wstępnie skonfigurowane, jak pokazano w rysunku 8-13, dzięki czemu nie musisz utworzyć maszynę kompilacji lub maszyny Wirtualnej do budowania aplikacji. Możesz użyć lub testowania tego kontenera kompilacji, uruchamiając go na komputerze deweloperskim. Ale co to jest jeszcze bardziej interesujące może użyć tego samego kontenera kompilacji z potokiem ciągłej integracji (ciągła integracja).

![](./media/image14.png)

**Rysunek 8-13**. Kompilowanie plików binarnych .NET kompilacji — kontener platformy docker 

W tym scenariuszu firma Microsoft zapewnia [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) obrazu, który umożliwia kompilowanie i tworzenie aplikacji ASP.NET Core. Dane wyjściowe są umieszczane w obrazu na podstawie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu, który jest obrazem zoptymalizowane środowiska uruchomieniowego, zauważyć, wcześniej.

Obraz aspnetcore-build zawiera wszystko, co jest potrzebne do kompilowania aplikacji platformy ASP.NET Core, w tym .NET Core, zestawu SDK platformy ASP.NET, npm, Bower, Gulp, itp.

Potrzebujemy tych zależności w czasie kompilacji. Jednak firma Microsoft nie chcesz wykonać je z aplikacji w czasie wykonywania, ponieważ może to spowodować obraz niepotrzebnie. W ramach aplikacji eShopOnContainers aplikacji, można skompilować aplikację z kontenera, uruchamiając tylko następujące platformy docker-compose polecenia.

```
  docker-compose -f docker-compose.ci.build.yml up
```

Rysunek 8 – 14 pokazuje to polecenie działa w wierszu polecenia.

![](./media/image15.png)

**Rysunek 8 – 14.** Tworzenie aplikacji .NET w kontenerze

Jak widać, kontener, który jest uruchomiony jest kompilacji ci\_1 kontenera. Zależy to obraz aspnetcore-build, aby go można skompilować i utworzyć całej aplikacji w tym kontenerze, a nie z Twojego komputera. Oznacza to Dlaczego w rzeczywistości jest tworzenie i kompilowanie projektów .NET Core w systemie Linux — ponieważ tego kontenera jest uruchomiona na hoście platformy Docker w systemie Linux domyślne.

[Docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) pliku obrazu (część pakietu w ramach aplikacji eShopOnContainers) zawiera następujący kod. Widać, że uruchomieniu kontenera kompilacji przy użyciu [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) obrazu.

```yml
version: '3'

services:

  ci-build:

    image: microsoft/aspnetcore-build:2.0

    volumes:
      - .:/src

    working_dir: /src

    command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && popd && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"

```

* Począwszy od **.NET Core 2.0**, `dotnet restore` polecenie jest wykonywane automatycznie po `dotnet publish` polecenie jest wykonywane.

Po skonfigurowaniu i uruchomieniu kontenera kompilacji działa przywracania dotnet zestawu SDK platformy .NET i dotnet publikowania poleceń dla wszystkich projektów w rozwiązaniu aby można było skompilować bitów .NET. W tym przypadku ponieważ w ramach aplikacji eShopOnContainers ma również SPA na podstawie TypeScript i Angular w przypadku kodu klienta, również musi ona Sprawdź zależności języka JavaScript za pomocą pakietu npm, ale ta akcja nie jest powiązana z bitami .NET.

Dotnet, jak opublikować polecenia kompilacji i publikuje skompilowanych danych wyjściowych w folderze każdego projektu... folder /obj/Docker/publish, jak pokazano w rysunek 8 – 15.

![](./media/image16.png)

**Rysunek 8 – 15.** Pliki binarne wygenerowane przez dotnet polecenia publikowania

#### <a name="creating-the-docker-images-from-the-cli"></a>Tworzenie obrazów platformy Docker z interfejsu wiersza polecenia

Po opublikowaniu dane wyjściowe aplikacji do powiązanych folderów (w ramach każdego projektu), następnym krokiem jest faktycznie kompilowanie obrazów platformy Docker. W tym celu należy użyć kompilacji docker-compose i docker-compose się polecenia, jak pokazano w rysunek 8-16.

![](./media/image17.png)

**Rysunek 8-16.** Tworzenie obrazów platformy Docker i uruchamianie kontenerów

Na rysunku 8-17 można zobaczyć jak docker-compose tworzyć polecenia uruchomienia.

![](./media/image18.png)

**Rysunek 8-17**. Tworzenie obrazów platformy Docker z platformą docker-compose polecenia kompilacji

Różnica między docker-compose kompilacji i narzędzia docker compose zapasowej poleceń jest to, że narzędzia docker compose zarówno kompilacje i uruchomieniu obrazami.

Gdy używasz programu Visual Studio, wszystkie te kroki są wykonywane w sposób niewidoczny. Visual Studio kompiluje aplikację platformy .NET, tworzy obrazy platformy Docker i służy do wdrażania kontenerów do hosta platformy Docker. Program Visual Studio udostępnia dodatkowe funkcje, takie jak możliwość debugowania kontenery uruchomione na platformie Docker, bezpośrednio z programu Visual Studio.

Ogólny takeway w tym miejscu jest, że jesteś w stanie do budowania aplikacji, w taki sam sposób potok ciągłej integracji/ciągłego wdrażania należy ją skompilować — z kontenera zamiast z komputera lokalnego. Po obrazów utworzonych, następnie wystarczy do uruchomienia obrazów platformy Docker przy użyciu platformy docker-compose się polecenia.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Tworzenia usługi bits z kontenera: konfigurowanie rozwiązania w ramach aplikacji eShopOnContainers w środowisku Windows interfejsu wiersza polecenia (wiersz polecenia dotnet, interfejsu wiersza polecenia platformy Docker i program VS Code)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, — Docker — interfejs wiersza polecenia platformy- i -VS-kodu)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Poprzednie](data-driven-crud-microservice.md)
[dalej](database-server-container.md)
