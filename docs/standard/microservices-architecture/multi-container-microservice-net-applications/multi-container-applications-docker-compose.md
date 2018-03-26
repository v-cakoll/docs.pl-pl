---
title: Definiowanie aplikacji usługi kontenera przy użyciu rozwiązania docker-compose.yml
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Definiowanie aplikacji usługi kontenera przy użyciu rozwiązania docker-compose.yml
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4fed5c7ba5c2048d103f22bd2b463c143013280
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definiowanie aplikacji usługi kontenera przy użyciu rozwiązania docker-compose.yml 

W tym przewodniku [docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku została wprowadzona w sekcji [krok 4. Zdefiniuj usług w rozwiązaniu docker-compose.yml podczas kompilowania aplikacji usługi kontenera Docker](#step4_define_svcs_in_docker_compose_yml). Istnieją dodatkowe sposoby używania plików docker-compose, które warto eksploracji bardziej szczegółowo.

Na przykład można jawnie opisano, jak chcesz wdrożyć aplikację usługi kontenera w plik docker-compose.yml. Opcjonalnie można opisano, jak zamierzasz utworzyć niestandardowe obrazy usługi Docker. (Niestandardowe obrazy usługi Docker mogą być również tworzone z poziomu interfejsu wiersza polecenia Docker).

Zasadniczo należy zdefiniować wszystkich kontenerów, do których chcesz wdrożyć plus niektórych parametrów dla każdego wdrożenia kontenera. Po utworzeniu pliku opisu wdrożenia usługi kontenera, można wdrożyć całe rozwiązanie w ramach jednej akcji zorkiestrowana przez [rozwiązania docker compose się](https://docs.docker.com/compose/overview/) polecenia interfejsu wiersza polecenia lub można go wdrożyć sposób niewidoczny dla użytkownika z programu Visual Studio. W przeciwnym razie należy użyć interfejsu wiersza polecenia Docker w celu wdrożenia kontenera przez kontener w wielu kroków przy użyciu rozwiązania docker, uruchom polecenie w wierszu polecenia. W związku z tym każda usługa zdefiniowane w rozwiązaniu docker-compose.yml określić dokładnie jeden obraz lub kompilacji. Inne klucze są opcjonalne i są podobne do ich docker Uruchom odpowiedników wiersza polecenia.

Poniższy kod yaml programu znajduje się definicja metody możliwe globalnych, ale pojedynczy plik docker-compose.yml przykładowej eShopOnContainers. To nie jest plikiem rzeczywiste docker-compose z eShopOnContainers. Zamiast tego jest to wersja uproszczonym i skonsolidowanych w jednym pliku, który nie jest najlepszy sposób pracy z rozwiązania docker-compose plików, jak opisano później.

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

Klucz główny, w tym pliku jest usług. W tym kluczu zdefiniuj usług, należy wdrożyć i uruchomić podczas wykonywania rozwiązania docker compose polecenia lub podczas wdrażania w programie Visual Studio przy użyciu tego plik docker-compose.yml. W takim przypadku plik docker-compose.yml ma wiele usług zdefiniowane, zgodnie z opisem w poniższej liście.

-   webmvc kontenera, w tym aplikacji ASP.NET Core MVC zużywa mikrousług z C po stronie serwera\#

-   Catalog.API kontenera, w tym mikrousługi katalogu platformy ASP.NET Core sieci Web API

-   Ordering.API mikrousługi porządkowanie Core Web API platformy ASP.NET w tym kontenerze

-   SQL.Data kontenera z programem SQL Server dla systemu Linux, zawierający mikrousług baz danych

-   basket.API kontenera z mikrousługi koszyka ASP.NET Core Web API

-   basket.Data kontenera uruchomiona usługa pamięci podręcznej REDIS z koszyka bazy danych jako pamięci podręcznej REDIS

### <a name="a-simple-web-service-api-container"></a>Kontener prosty interfejs API usługi sieci Web

Skupienie się na jeden kontener, catalog.api kontenera mikrousługi ma definicję prosta:

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=catalog.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
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

Ta usługa konteneryzowanych ma następującą konfigurację podstawowe:

-   Jest on oparty na eshop/catalog.api niestandardowego obrazu. Dla sake dla uproszczenia nie istnieje żadne kompilacji: ustawienia w pliku klucza. Oznacza to, że obraz musi wcześniej skompilowano (z kompilacją docker) lub zostały pobrane z dowolnego rejestru Docker (z poleceniem ściągania docker).

-   Definiuje zmienną środowiskową o nazwie ConnectionString ciągu połączenia używanego przez program Entity Framework do wystąpienia programu SQL Server, który zawiera model danych katalogu. W takim przypadku tego samego kontenera programu SQL Server jest zawierający wiele baz danych. W związku z tym należy mniejszej ilości pamięci w komputerze deweloperskim for Docker. Jednak można także wdrożyć jeden kontener programu SQL Server dla każdej bazy danych mikrousługi.

-   Nazwa programu SQL Server jest sql.data, która jest nazwą tego samego kontenera, w którym działa wystąpienie serwera SQL dla systemu Linux. Jest to wygodny; możliwości używania tego rozpoznawania nazw (wewnętrzny hosta Docker) rozwiąże adres sieci, więc nie trzeba znać wewnętrznego adresu IP dla kontenerów, do których masz dostęp z innych kontenerów.

Ponieważ ciągu połączenia jest zdefiniowana przez zmienną środowiskową, można ustawić tej zmiennej za pośrednictwem innego mechanizmu i w innym czasie. Na przykład można ustawić różne parametry w przypadku wdrażania w środowisku produkcyjnym w ostatnim hostów lub wykonywanie czynności z Twojej potoków CI/CD w VSTS lub preferowany system DevOps.

-   Prezentuje ona port 80 dla wewnętrznego dostęp do usługi catalog.api w ramach hosta Docker. Host jest obecnie Maszynę wirtualną systemu Linux, ponieważ jest ona oparta na obrazie Docker dla systemu Linux, ale można skonfigurować kontenera należy zamiast tego uruchomić w obrazie systemu Windows.

-   Przekazuje dostępnego portu 80 kontenera do portu 5101 na komputerze hosta Docker (maszyny Wirtualnej systemu Linux).

-   Łączy usługę sieci web do usługi sql.data (wystąpienie programu SQL Server dla bazy danych systemu Linux uruchomione w kontenerze). Po określeniu tę zależność kontenera catalog.api nie uruchomi kontener sql.data została już rozpoczęta; najpierw to ważne, ponieważ catalog.api musi mieć bazy danych programu SQL Server w i uruchomiona. Jednak tego rodzaju zależności kontenera nie jest wystarczająco w wielu przypadkach, ponieważ Docker sprawdza tylko na poziomie kontenera. Czasami usługi (w tym przypadku SQL Server) nie będą gotowe, dlatego zaleca się implementację logiki ponawiania próby z wykładniczego wycofywania w Twojej mikrousług klienta. W ten sposób, jeśli kontener zależności nie jest gotowy do przez krótki czas aplikacji będą odporne.

-   Skonfigurowano w celu umożliwienia dostępu do zewnętrznych serwerów: nadmiarowe\_hostów ustawienie umożliwia dostęp do zewnętrznych serwerów lub maszyny poza hostów Docker (to znaczy poza domyślną maszyny Wirtualnej systemu Linux, który jest programowanie Docker hosta), takich jak lokalna baza SQL Wystąpienie serwera na komputerze.

Istnieją także inne, bardziej zaawansowane ustawienia docker-compose.yml, które omówimy w poniższych sekcjach.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Przy użyciu rozwiązania docker-compose plików pod kątem wiele środowisk

Pliki docker-compose.yml są definicji i mogą być używane przez wiele infrastruktury, które rozumieją tego formatu. Narzędzie to najprostszy jest docker-tworzą polecenia, ale innych narzędzi, takich jak orchestrators (na przykład Docker Swarm) należy również zapoznać się tego pliku.

W związku z tym przy użyciu rozwiązania docker compose polecenia można wskazać następujące główne scenariusze.

#### <a name="development-environments"></a>Środowisk deweloperskich

Podczas tworzenia aplikacji, jest ważne można było uruchomić aplikację w środowisku projektowym izolowanym. Można użyć rozwiązania docker compose polecenia interfejsu wiersza polecenia do utworzenia tego środowiska lub użyć programu Visual Studio, który używa rozwiązania docker-compose w obszarze obejmuje.

Plik docker-compose.yml służy do konfigurowania i zarządzania dokumentami zależności usługi wszystkich aplikacji (inne usługi, pamięci podręcznej, baz danych, kolejki itd.). Przy użyciu rozwiązania docker compose polecenia interfejsu wiersza polecenia, można utworzyć i uruchomić kontenerach dla każdego zależności za pomocą jednego polecenia (docker tworzą się).

Docker-compose.yml są interpretowane przez aparat Docker pliki konfiguracji, ale również służyć jako pliki dokumentacji wygodny o kompozycji wielu kontenera aplikacji.

#### <a name="testing-environments"></a>Środowisk testowych

Ważnym elementem procesu ciągłej integracji (CI) lub ciągłe wdrażanie (CD) są testów jednostkowych i integracji. Te testy automatyczne wymaga izolowanym środowisku, dzięki czemu można ich nie ma wpływ na użytkowników lub inne zmiany w danych aplikacji.

Z rozwiązania Docker Compose możesz tworzyć i zniszcz tego środowiska izolowanego bardzo łatwo w kilku poleceń z wiersza polecenia lub skryptów, takich jak następujące polecenia:

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Wdrożeń produkcyjnych

Redaguj służy również do wdrażania na zdalnym aparatem platformy Docker. Typowy przypadek jest wdrożenie do pojedynczego wystąpienia hosta Docker (produkcji maszyny Wirtualnej lub udostępniane z serwera, takich jak [maszyny Docker](https://docs.docker.com/machine/overview/)). Ale może być również cały [Docker Swarm](https://docs.docker.com/swarm/overview/) klastra, ponieważ klastrów również są zgodne z plikami docker-compose.yml.

Jeśli używane są inne orchestrator (sieć szkieletowa usług Azure, Mesos DC/OS, Kubernetes itp.), może być konieczne dodanie ustawienia konfiguracji instalacji i metadanych, podobnie jak w docker-compose.yml, ale w formacie wymagane przez inne orchestrator.

W każdym przypadku rozwiązania docker compose jest wygodnym formacie narzędzia i metadanych dla przepływów pracy programowania, testowania i produkcji, mimo że produkcji przepływu pracy mogą różnić się dla modułu aranżującego używasz.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Przy użyciu wielu docker tworzą pliki do obsługi kilku środowiskach

Gdy przeznaczonych dla różnych środowisk, należy używać wielu tworzą pliki. Dzięki temu można utworzyć wiele wariantami konfiguracji, w zależności od środowiska.

#### <a name="overriding-the-base-docker-compose-file"></a>Zastępowanie pliku docker-compose podstawowej

Można użyć pliku pojedynczego docker-compose.yml jak uproszczone przykłady zamieszczone w poprzednich sekcjach. Jednak, że nie zaleca się dla większości aplikacji.

Domyślnie Redaguj odczytuje dwóch plików, docker-compose.yml i plik docker-compose.override.yml opcjonalne. Jak pokazano w rysunek 8-11, gdy za pomocą programu Visual Studio i również włączania obsługi Docker, Visual Studio tworzy plik dodatkowe compose.ci.build,yml docker do użycia z Twojej potoków CI/CD, podobnie jak w VSTS.

![](./media/image12.png)

**Rysunek 8-11**. rozwiązania docker compose plików w Visual Studio 2017 r.

Możesz edytować pliki docker-compose w dowolnym edytorze, takich jak Visual Studio Code lub Sublime i uruchom aplikację klawiszem rozwiązania docker compose Konfigurowanie polecenia.

Konwencja plik docker-compose.yml zawiera podstawową konfigurację i inne ustawienia statycznych. Oznacza to, że konfiguracji usługi nie należy zmieniać w zależności od środowiska wdrażania, który ma być przeznaczona dla.

Plik docker-compose.override.yml sugeruje nazwa, zawiera ustawienia konfiguracji, które zastępują konfiguracji podstawowej, takie jak konfiguracja, która jest zależna od środowiska wdrażania. Również może mieć wiele plików zastąpienie o różnych nazwach. Pliki zastąpienie zwykle zawierają dodatkowe informacje wymagane przez aplikację ale określonego środowiska lub do wdrożenia.

#### <a name="targeting-multiple-environments"></a>Celem wiele środowisk

Typowy przypadek użycia jest podczas definiowania wielu tworzą pliki, można kierować wielu środowiskach, takich jak środowiska produkcyjnego, przemieszczania, CI lub programowanie. Aby obsługiwać te różnice, można podzielić konfigurację Redaguj na wiele plików, jak pokazano na rysunku 8-12.

![](./media/image13.png)

**Rysunek 8-12**. Wiele docker tworzą pliki zastępowania wartości w pliku podstawowego docker-compose.yml

Możesz uruchomić plik docker-compose.yml podstawowej. Tego pliku podstawowego musi zawierać ustawienia konfiguracji podstawowej lub statycznej, które nie zmieniają się w zależności od środowiska. Na przykład eShopOnContainers ma następujący plik docker-compose.yml jako pliku podstawowego.

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

Wartości w pliku podstawowego docker-compose.yml nie należy zmieniać ze względu na inny element docelowy wdrożenia środowiska.

Jeśli można skupić się na webmvc definicji usługi, na przykład spowoduje jak jest znacznie taki sam, niezależnie od tego, jakiego środowiska może być przeznaczonych dla tych informacji. Masz następujące informacje:

-   Nazwa usługi: webmvc.

-   Obraz niestandardowy kontenera: eshop/webmvc.

-   Polecenie, aby utworzyć niestandardowy obraz Docker, wskazującą, który plik Dockerfile do użycia.

-   W zależności od innych usług, dlatego ten kontener nie uruchamia się, dopóki nie zostały uruchomione inne kontenery zależności.

Masz dodatkowe czynności konfiguracyjne, ale ważne punkt znajduje się w pliku podstawowego docker-compose.yml po prostu chcesz ustawić informacje, które są wspólne w środowiskach. Następnie w docker compose.override.yml lub podobnych plików do produkcji lub przemieszczania, należy umieścić konfiguracji, które są specyficzne dla każdego środowiska.

Zazwyczaj docker compose.override.yml jest używana dla swojego środowiska programowania, jak w poniższym przykładzie z eShopOnContainers:

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

W tym przykładzie programowanie zastępczą konfigurację przedstawia niektóre porty do hosta, definiuje zmiennych środowiskowych poleceniem przekierowania adresów URL i określa parametry połączenia dla środowiska programowania. Te ustawienia dotyczą wszystkich tylko Środowisko deweloperskie.

Po uruchomieniu `docker-compose up` (lub uruchomić go w programie Visual Studio), polecenia odczytuje automatycznie zastąpienia, tak jakby były scalanie oba pliki.

Załóżmy, że ma inny plik tworzenia w środowisku produkcyjnym, za pomocą wartości różnych konfiguracji, portów lub parametry połączenia. Można utworzyć inny plik zastąpienie, takich jak plik o nazwie `docker-compose.prod.yml` z różnymi ustawieniami i zmiennych środowiskowych.  Ten plik może być przechowywane w różnych repozytorium Git lub zarządzane i zabezpieczone przez inny zespół.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Jak wdrożyć przy użyciu określonego zastąpienia pliku

Aby używać wielu zastąpienie plików lub zastąpienie pliku o innej nazwie, można użyć opcji -f z rozwiązania docker compose polecenia i określ pliki. Tworzenie plików scalenia w kolejności, w których są one określone w wierszu polecenia. Poniższy przykład przedstawia sposób wdrażania z plikami zastąpienie.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Korzystanie ze zmiennych środowiskowych docker tworzą pliki

Jest wygodną, szczególnie w środowiskach produkcyjnych, aby można było uzyskać informacje o konfiguracji z zmiennych środowiskowych, jak firma Microsoft wykazały w poprzednich przykładach. Odwołania zmiennej środowiskowej w plikach docker-compose przy użyciu składni \${MY\_VAR}. Następujący wiersz z pliku docker compose.prod.yml pokazuje, jak odwoływać się do wartości zmiennej środowiskowej.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Zmienne środowiskowe są tworzone i zainicjowana na różne sposoby, w zależności od środowiska hosta (Linux, Windows, chmury klastra itp.). Jednak wygodny rozwiązaniem jest użycie pliku .env. Obsługa plików docker-compose deklarowania zmiennych środowiskowych w pliku .env domyślne. Te wartości zmiennych środowiskowych są wartościami domyślnymi. Ale mogą być zastąpione przez wartości, które może być zdefiniowane w poszczególnych środowisk (systemu operacyjnego hosta lub zmiennych środowiskowych z klastra). Ten plik .env zostanie umieszczony w folderze gdzie rozwiązania docker compose z wykonaniem polecenia.

W poniższym przykładzie przedstawiono plik .env, takich jak [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pliku eShopOnContainers aplikacji.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Rozwiązania docker compose oczekuje, że każdy wiersz w pliku .env w formacie &lt;zmiennej&gt;=&lt;wartość&gt;.

Należy pamiętać, że wartości środowiska uruchomieniowego zawsze zastąpienie wartości zdefiniowanych w pliku .env. W podobny sposób wartości przekazane za pośrednictwem argumentów wiersza polecenia polecenie zastąpić wartości domyślne ustawione w pliku .env.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Omówienie rozwiązania Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Wiele plików Redaguj**
    [*https://docs.docker.com/compose/extends/\#wielu tworzą — pliki*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Kompilowanie zoptymalizowanych obrazów ASP.NET Core Docker

Jeśli są eksploracji Docker i .NET Core źródeł w Internecie, będą dostępne Dockerfiles, które pokazują łatwość tworzenia obrazu Docker przez skopiowanie źródła do kontenera. Te przykłady sugerują, za pomocą prostego konfiguracji, może występować obrazu Docker ze środowiskiem spakować z aplikacją. Poniższy przykład przedstawia prosty plik Dockerfile w tym szyjnej.

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

Plik Dockerfile jak to działa. Jednak można zoptymalizować znacznie obrazów, szczególnie obrazów produkcji.

Kontener i mikrousług modelu są stale uruchamianie kontenerów. Typowy sposób użycia kontenery nie uruchamiaj ponownie pojemnik uśpiony, ponieważ kontener jest możliwe do rozporządzania. Orchestrators (na przykład Docker Swarm, Kubernetes, DCOS lub sieć szkieletowa usług Azure), po prostu utworzyć nowe wystąpienia obrazów. Co to oznacza że konieczne będzie zoptymalizować wstępnej kompilacji aplikacji, gdy jest ona wbudowana tak procesu tworzenia wystąpienia będzie przebiegać szybciej. Po uruchomieniu kontenera, powinien być gotowy do uruchomienia. Nie należy przywrócić i kompilacji w czasie wykonywania, za pomocą dotnet przywracania i dotnet tworzenia poleceń z dotnet interfejsu wiersza polecenia, jak widać w wielu wpisy na blogu dotyczące .NET Core i Docker.

Zespół platformy .NET ma zostały wykonywanie pracy ważne, aby oprogramowanie .NET Core i ASP.NET Core zoptymalizowaną kontenera. Nie tylko słowo .NET Core lekkie framework z zużycie pamięci; zespół ma fokus na wydajność uruchamiania i tak samo, jak wyprodukowanych niektórych zoptymalizowanych obrazów Docker [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu dostępne pod adresem [Centrum Docker](https://hub.docker.com/r/microsoft/aspnetcore/), w odróżnieniu od zwykłej [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) lub [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) obrazów. [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obraz umożliwia automatyczne ustawienie aspnetcore\_adresy URL do portu 80 i wstępnie ngend pamięci podręcznej zestawów; oba te ustawienia powoduje szybsze uruchamianie.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Kompilowanie zoptymalizowanych pod kątem obrazy usługi Docker z platformy ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Tworzenie aplikacji kontenera kompilacji (CI)

Inną zaletą Docker jest, że można skompilować aplikację z kontenera wstępnie skonfigurowane, jak pokazano w rysunek 8-13, dzięki czemu nie trzeba tworzyć maszynie kompilacji lub maszyny Wirtualnej, aby skompilować aplikację. Możesz użyć lub że kontener kompilacji testu przez uruchomienie jej na komputerze deweloperskim. Ale co to jest bardziej interesujące jest, których można używać tego samego kontenera kompilacji z potoku sieci CI (ciągłej integracji).

![](./media/image14.png)

**Rysunek 8-13**. Kompilowanie plików binarnych programu .NET kompilacji kontenera docker 

W tym scenariuszu udzielamy [aspnetcore-microsoft Zbuduj](https://hub.docker.com/r/microsoft/aspnetcore-build/) obrazu, który służy do kompilowania i tworzenie aplikacji programu ASP.NET Core. Dane wyjściowe są umieszczane w obrazu na podstawie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu, który jest obrazem zoptymalizowanego środowiska uruchomieniowego zauważyć, jak wcześniej.

Obraz aspnetcore kompilacji zawiera wszystko, co jest potrzebne do kompilacji aplikacji platformy ASP.NET Core, w tym oprogramowanie .NET Core, zestaw SDK platformy ASP.NET, npm, Bower, Gulp, itp.

Potrzebujemy tych zależności w czasie kompilacji. Ale nie chcemy wykonać je z aplikacją w czasie wykonywania, ponieważ może to spowodować obrazu niepotrzebnie. W aplikacji eShopOnContainers można utworzyć aplikację z kontenera tylko uruchamiając następujące rozwiązania docker-compose polecenia.

```
  docker-compose -f docker-compose.ci.build.yml up
```

Rysunek 8-14 pokazuje to polecenie uruchomione w wierszu polecenia.

![](./media/image15.png)

**Rysunek 8-14.** Tworzenie aplikacji .NET z kontenera

Jak widać, kontenera, w którym jest uruchomiona jest kompilacji integracji ciągłej\_1 kontenera. Jest oparta na obrazie aspnetcore kompilacji, aby można go skompilować i utworzyć całej aplikacji w danym kontenerze, a nie z komputera użytkownika. Oznacza to Dlaczego w rzeczywistości jest tworzenie i kompilowanie projektów .NET Core w systemie Linux, ponieważ ten kontener jest uruchomiona na hoście systemu Linux Docker domyślne.

[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) plik obrazu (część eShopOnContainers) zawiera następujący kod. Widać uruchamiania kontenera kompilacji za pomocą [aspnetcore-microsoft Zbuduj](https://hub.docker.com/r/microsoft/aspnetcore-build/) obrazu.

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

* Począwszy od **.NET Core 2.0**, `dotnet restore` polecenie zostanie wykonane automatycznie po `dotnet publish` polecenie jest wykonywane.

Po skonfigurowaniu i uruchomieniu kontenera kompilacji uruchomieniu przywracania dotnet zestawu .NET SDK i dotnet publikowania poleceń w odniesieniu do wszystkich projektów w rozwiązaniu Aby skompilować bitów .NET. W takim przypadku eShopOnContainers ma również SPA oparte na maszynie i kątową kodu klienta, również musi Sprawdź zależności JavaScript z pakietu npm, ale ta akcja nie jest powiązana z bitów .NET.

Dotnet publikowanie polecenie kompilacji i publikuje skompilowanych danych wyjściowych znajdujących się w folderze każdego projektu... folder /obj/Docker/publish, jak pokazano w rysunek 8 – 15.

![](./media/image16.png)

**Rysunek 8 – 15.** Polecenie Publikuj pliki binarne wygenerowane przez dotnet

#### <a name="creating-the-docker-images-from-the-cli"></a>Tworzenie obrazów Docker z poziomu interfejsu wiersza polecenia

Po opublikowaniu danych wyjściowych aplikacji do powiązanych folderów (w każdym projekcie), następnym krokiem jest rzeczywiście tworzyć obrazy Docker. Aby to zrobić, użyj kompilacji docker-compose i docker tworzą się poleceń, jak pokazano w rysunek 8-16.

![](./media/image17.png)

**Rysunek 8-16.** Tworzenie obrazy usługi Docker i uruchamianie kontenerów

Na rysunku 8-17 widać, jak docker-compose kompilacji uruchamia polecenia.

![](./media/image18.png)

**Rysunek 8-17**. Tworzenie obrazów Docker z docker-tworzą polecenie kompilacji

Różnica między docker-compose kompilacji i rozwiązania docker compose zapasowej poleceń jest to, że rozwiązania docker compose zarówno kompilacji i uruchomieniu obrazów.

Korzystając z programu Visual Studio, te kroki są wykonywane w tle. Visual Studio kompiluje aplikacji .NET, tworzy obrazy usługi Docker i wdraża kontenerów do hostów Docker. Program Visual Studio oferuje dodatkowe funkcje, takie jak możliwość debugowania kontenerów uruchomionych w Docker, bezpośrednio z programu Visual Studio.

Tutaj ogólną takeway jest zdolny do skompilowania aplikacji, w taki sam sposób planowaną CI/CD powinno utworzyć go — z kontenera zamiast z komputera lokalnego. Po obrazy utworzone, następnie wystarczy uruchomić obrazów Docker przy użyciu rozwiązania docker-tworzą zapasowej polecenia.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Tworzenie usługi bits z kontenera: konfigurowanie rozwiązania eShopOnContainers w środowisku interfejsu wiersza polecenia systemu Windows (dotnet interfejsu wiersza polecenia, interfejsu wiersza polecenia Docker i kodzie VS)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, — Docker - CLI- i -VS — kodu)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)
