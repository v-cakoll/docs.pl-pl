---
title: Definiowanie aplikacji z wieloma kontenerami za pomocą pliku docker-compose.yml
description: Jak określić kompozycję mikrousług dla aplikacji wielokontenerowej z docker-compose.yml.
ms.date: 01/30/2020
ms.openlocfilehash: 029fad8bb912457872dd5817a2f76aed57dc53c6
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888231"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definiowanie aplikacji z wieloma kontenerami za pomocą pliku docker-compose.yml

W tym przewodniku plik [docker-compose.yml](https://docs.docker.com/compose/compose-file/) został wprowadzony w sekcji [Krok 4. Zdefiniuj swoje usługi w pliku docker-compose.yml podczas tworzenia aplikacji platformy Docker z wieloma kontenerami](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application). Istnieją jednak dodatkowe sposoby korzystania z plików docker-compose, które warto zbadać bardziej szczegółowo.

Na przykład można jawnie opisać, jak chcesz wdrożyć aplikację z wieloma kontenerami w pliku docker-compose.yml. Opcjonalnie można również opisać, jak zamierzasz tworzyć niestandardowe obrazy platformy Docker. (Niestandardowe obrazy platformy Docker można również tworzyć za pomocą interfejsu wiersza polecenia platformy Docker).

Zasadniczo można zdefiniować każdy kontener, który chcesz wdrożyć plus pewne cechy dla każdego wdrożenia kontenera. Po uzyskaniu pliku opisu wdrożenia wielu kontenerów można wdrożyć całe rozwiązanie w pojedynczej akcji zaaranżowanej przez polecenie [docker-compose up](https://docs.docker.com/compose/overview/) CLI lub wdrożyć je w sposób przezroczysty w programie Visual Studio. W przeciwnym razie należy użyć interfejsu wiersza polecenia platformy Docker do `docker run` wdrażania kontenera po kontenerze w wielu krokach przy użyciu polecenia z wiersza polecenia. W związku z tym każda usługa zdefiniowana w docker-compose.yml musi określić dokładnie jeden obraz lub kompilacji. Inne klucze są opcjonalne i `docker run` są analogiczne do ich odpowiedników wiersza polecenia.

Poniższy kod YAML jest definicją możliwego globalnego, ale pojedynczego pliku docker-compose.yml dla przykładu eShopOnContainers. Nie jest to rzeczywisty plik docker-compose z eShopOnContainers. Zamiast tego jest to uproszczona i skonsolidowana wersja w jednym pliku, co nie jest najlepszym sposobem pracy z plikami docker-compose, jak zostanie to wyjaśnione później.

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
      - BasketUrl=http://basket-api
    ports:
      - "5100:80"
    depends_on:
      - catalog-api
      - ordering-api
      - basket-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  basket-api:
    image: eshop/basket-api
    environment:
      - ConnectionString=sqldata
    ports:
      - "5103:80"
    depends_on:
      - sqldata

  sqldata:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basketdata:
    image: redis
```

Kluczem głównym w tym pliku są usługi. W ramach tego klucza można zdefiniować usługi, które `docker-compose up` mają być wdrażane i uruchamiane podczas wykonywania polecenia lub wdrażania z programu Visual Studio przy użyciu tego pliku docker-compose.yml. W takim przypadku plik docker-compose.yml ma zdefiniowane wiele usług, zgodnie z opisem w poniższej tabeli.

| Nazwa usługi | Opis |
|--------------|-------------|
| webmvc (webmvc)       | Kontener zawierający ASP.NET podstawową aplikację MVC zużywającą mikrousługi z c po stronie serwera\#|
| katalog-api  | Kontener zawierający mikrousługę interfejsu API sieci Web catalog ASP.NET Core |
| zamawianie-api | Kontener zawierający mikrousługę interfejsu API sieci Web ASP.NET Core |
| sqldata     | Kontener z systemem SQL Server dla systemu Linux, zawierający bazy danych mikrousług |
| koszyk-api   | Kontener z mikrousługą interfejsu API sieci Web w koszyku ASP.NET rdzenia |
| dane koszykowe  | Kontener z uruchomieniem usługi pamięci podręcznej REDIS z bazą danych koszyka jako pamięcią podręczną REDIS |

### <a name="a-simple-web-service-api-container"></a>Prosty kontener interfejsu API usługi sieci Web

Koncentrując się na pojedynczy kontener, catalog-api container-microservice ma prostą definicję:

```yml
  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata
```

Ta konteneryzowana usługa ma następującą podstawową konfigurację:

- Jest on oparty na niestandardowym **eshop / katalog-api** obrazu. Dla uproszczenia nie ma kompilacji: ustawienie klucza w pliku. Oznacza to, że obraz musi być wcześniej zbudowany (z kompilacją platformy docker) lub został pobrany (za pomocą polecenia ściągania platformy docker) z dowolnego rejestru platformy Docker.

- Definiuje zmienną środowiskową o nazwie ConnectionString z ciągiem połączenia, który ma być używany przez entity framework, aby uzyskać dostęp do wystąpienia programu SQL Server zawierającego model danych katalogu. W takim przypadku ten sam kontener programu SQL Server przechowuje wiele baz danych. W związku z tym potrzebujesz mniej pamięci na komputerze deweloperskim dla platformy Docker. Można jednak również wdrożyć jeden kontener programu SQL Server dla każdej bazy danych mikrousług.

- Nazwa programu SQL Server to **sqldata**, która jest tą samą nazwą, która jest używana dla kontenera, który jest uruchomiony wystąpienie programu SQL Server dla systemu Linux. Jest to wygodne; możliwość użycia tej rozdzielczości nazwy (wewnętrznej do hosta platformy Docker) rozwiąże adres sieciowy, dzięki czemu nie trzeba znać wewnętrznego adresu IP kontenerów, do których uzyskujesz dostęp z innych kontenerów.

Ponieważ parametry połączenia jest zdefiniowany przez zmienną środowiskową, można ustawić tę zmienną za pomocą innego mechanizmu i w innym czasie. Na przykład można ustawić inny ciąg połączenia podczas wdrażania do produkcji w hostach końcowych lub wykonując go z potoków ciągłej integracji/ciągłego wdrażania w usługach DevOps platformy Azure lub preferowanego systemu DevOps.

- Udostępnia port 80 dla wewnętrznego dostępu do usługi **interfejsu api katalogu** w hoście platformy Docker. Host jest obecnie maszyną wirtualną z systemem Linux, ponieważ jest on oparty na obrazie platformy Docker dla systemu Linux, ale można skonfigurować kontener do uruchamiania na obrazie systemu Windows.

- Przekazuje narażony port 80 w kontenerze do portu 5101 na komputerze hosta platformy Docker (maszyna wirtualna z systemem Linux).

- Łączy usługę sieci web z usługą **sqldata** (wystąpienie programu SQL Server dla bazy danych systemu Linux uruchomionej w kontenerze). Po określeniu tej zależności kontener interfejsu api katalogu nie zostanie uruchomiony, dopóki kontener sqldata nie zostanie już uruchomiony; jest to ważne, ponieważ catalog-api musi mieć najpierw i uruchomię bazę danych programu SQL Server. Jednak tego rodzaju zależności kontenera nie wystarczy w wielu przypadkach, ponieważ docker sprawdza tylko na poziomie kontenera. Czasami usługa (w tym przypadku SQL Server) może nadal nie być gotowy, więc wskazane jest, aby zaimplementować logikę ponawiania z wykładniczego wycofywania w mikrousług klienta. W ten sposób jeśli kontener zależności nie jest gotowy na krótki czas, aplikacja będzie nadal odporne.

- Jest skonfigurowany tak, aby umożliwić dostęp\_do serwerów zewnętrznych: ustawienie dodatkowych hostów umożliwia dostęp do zewnętrznych serwerów lub maszyn poza hostem platformy Docker (czyli poza domyślną maszyną wirtualną systemu Linux, która jest deweloperskim hostem platformy Docker), na przykład lokalnym wystąpieniem programu SQL Server na komputerze deweloperskim.

Istnieją również inne, `docker-compose.yml` bardziej zaawansowane ustawienia, które omówimy w poniższych sekcjach.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Używanie plików docker-compose do kierowania na wiele środowisk

Pliki `docker-compose.*.yml` są plikami definicji i mogą być używane przez wiele infrastruktur, które rozumieją ten format. Najprostszym narzędziem jest polecenie docker-compose.

W związku z tym za pomocą polecenia docker-compose można kierować następujące scenariusze główne.

#### <a name="development-environments"></a>Środowiska deweloperskie

Podczas tworzenia aplikacji, ważne jest, aby móc uruchomić aplikację w środowisku rozwoju izolowane. Za pomocą polecenia docker-compose CLI można utworzyć to środowisko lub program Visual Studio, który używa docker-compose w ramach obejmuje.

Plik docker-compose.yml umożliwia skonfigurowanie i udokumentowanie wszystkich zależności usługi aplikacji (innych usług, pamięci podręcznej, baz danych, kolejek itp.). Za pomocą polecenia docker-compose CLI można utworzyć i uruchomić jeden lub więcej kontenerów dla każdej zależności za pomocą jednego polecenia (docker-compose up).

Pliki docker-compose.yml są plikami konfiguracyjnymi interpretowanymi przez aparat platformy Docker, ale służą również jako wygodne pliki dokumentacji dotyczące składu aplikacji wielokontenerowej.

#### <a name="testing-environments"></a>Środowiska testowe

Ważną częścią każdego ciągłego wdrażania (CD) lub ciągłej integracji (CI) są testy jednostkowe i testy integracji. Te zautomatyzowane testy wymagają izolowanego środowiska, aby nie miały wpływu na użytkowników ani na inne zmiany w danych aplikacji.

Za pomocą docker compose można bardzo łatwo utworzyć i zniszczyć izolowane środowisko w kilku poleceniach z wiersza polecenia lub skryptów, takich jak następujące polecenia:

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml down
```

#### <a name="production-deployments"></a>Wdrożenia produkcyjne

Można również użyć compose do wdrożenia na zdalnym aparat platformy Docker. Typowym przypadkiem jest wdrożenie w jednym wystąpieniu hosta platformy Docker (na przykład produkcyjnej maszynie wirtualnej lub serwer aprowizowana za pomocą [komputera platformy Docker Machine).](https://docs.docker.com/machine/overview/)

Jeśli używasz innego koordynatora (sieci szkieletowej usługi Azure, kubernetes itp.), może być konieczne dodanie ustawień konfiguracji i konfiguracji metadanych, takich jak te w docker-compose.yml, ale w formacie wymaganym przez innego koordynatora.

W każdym przypadku docker-compose jest wygodnym narzędziem i formatem metadanych dla przepływów pracy deweloperskich, testowych i produkcyjnych, chociaż przepływ pracy produkcji może się różnić w przypadku używanego koordynatora.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Używanie wielu plików docker-compose do obsługi kilku środowisk

Podczas kierowania na różne środowiska należy użyć wielu plików redagowania. Dzięki temu można utworzyć wiele wariantów konfiguracji w zależności od środowiska.

#### <a name="overriding-the-base-docker-compose-file"></a>Zastępowanie podstawowego pliku docker-compose

Można użyć pojedynczego pliku docker-compose.yml, jak w uproszczonych przykładach pokazanych w poprzednich sekcjach. Jednak nie jest to zalecane dla większości aplikacji.

Domyślnie Compose odczytuje dwa pliki: plik docker-compose.yml i opcjonalny plik docker-compose.override.yml. Jak pokazano na rysunku 6-11, podczas korzystania z programu Visual Studio i włączania obsługi platformy Docker, Visual Studio tworzy również dodatkowy plik docker-compose.vs.debug.g.yml do debugowania aplikacji, można spojrzeć na ten plik w folderze obj\\Docker\\ w głównym folderze rozwiązania.

![Pliki w projekcie tworzenia docker.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

**Rysunek 6-11**. pliki docker-compose w programie Visual Studio 2019

struktura pliku projektu **docker-compose:**

- *.dockerignore* — służy do ignorowania plików
- *docker-compose.yml* - służy do tworzenia mikrousług
- *docker-compose.override.yml* — służy do konfigurowania środowiska mikrousług

Pliki docker-compose można edytować za pomocą dowolnego edytora, takiego jak Visual Studio Code lub Sublime, i uruchomić aplikację za pomocą polecenia docker-compose up.

Zgodnie z konwencją plik docker-compose.yml zawiera konfigurację podstawową i inne ustawienia statyczne. Oznacza to, że konfiguracja usługi nie powinna się zmieniać w zależności od środowiska wdrażania, które są kierowane.

Plik docker-compose.override.yml, jak sama nazwa wskazuje, zawiera ustawienia konfiguracji, które zastępują konfigurację podstawową, taką jak konfiguracja zależna od środowiska wdrażania. Można również zastąpić wiele plików o różnych nazwach. Pliki zastępowania zwykle zawierają dodatkowe informacje wymagane przez aplikację, ale specyficzne dla środowiska lub wdrożenia.

#### <a name="targeting-multiple-environments"></a>Kierowanie na wiele środowisk

Typowym przypadkiem użycia jest zdefiniowanie wielu plików redagowania, dzięki czemu można kierować wiele środowisk, takich jak produkcja, przemieszczania, ciągłości integracji lub rozwoju. Aby obsługiwać te różnice, można podzielić konfigurację compose na wiele plików, jak pokazano na rysunku 6-12.

![Diagram trzech plików docker-compose ustawionych w celu zastąpienia pliku podstawowego.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

**Rysunek 6-12**. Wiele plików docker-redpose nadrzędnych wartości w podstawowym pliku docker-compose.yml

Można połączyć wiele plików docker-compose*.yml w celu obsługi różnych środowisk. Zacznij od podstawowego pliku docker-compose.yml. Ten plik podstawowy zawiera podstawowe lub statyczne ustawienia konfiguracji, które nie zmieniają się w zależności od środowiska. Na przykład aplikacja eShopOnContainers ma następujący plik docker-compose.yml (uproszczony z mniejszą liczbą usług) jako plik podstawowy.

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket-api:
    image: eshop/basket-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basketdata
      - identity-api
      - rabbitmq

  catalog-api:
    image: eshop/catalog-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sqldata
      - rabbitmq

  marketing-api:
    image: eshop/marketing-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sqldata
      - nosqldata
      - identity-api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog-api
      - ordering-api
      - identity-api
      - basket-api
      - marketing-api

  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest

  nosqldata:
    image: mongo

  basketdata:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

Wartości w podstawowym pliku docker-compose.yml nie powinny ulec zmianie z powodu różnych docelowych środowisk wdrażania.

Jeśli skupisz się na definicji usługi webmvc, na przykład, można zobaczyć, jak te informacje są tak samo, bez względu na środowisko, które mogą być kierowane. Masz następujące informacje:

- Nazwa usługi: webmvc.

- Niestandardowy obraz kontenera: eshop/webmvc.

- Polecenie do tworzenia niestandardowego obrazu platformy Docker, wskazujące, którego pliku Dockerfile użyć.

- Zależności od innych usług, więc ten kontener nie uruchamia się, dopóki nie zostały uruchomione inne kontenery zależności.

Możesz mieć dodatkową konfigurację, ale ważne jest to, że w podstawowym pliku docker-compose.yml, po prostu chcesz ustawić informacje, które są wspólne dla różnych środowisk. Następnie w docker-compose.override.yml lub podobnych plików dla produkcji lub przemieszczania, należy umieścić konfigurację, która jest specyficzna dla każdego środowiska.

Zazwyczaj docker-compose.override.yml jest używany dla środowiska programistycznego, jak w poniższym przykładzie z eShopOnContainers:

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basketdata}
      - identityUrl=http://identity-api
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

  catalog-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
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

  marketing-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity-api
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
      - CatalogUrlHC=http://catalog-api/hc
      - OrderingUrlHC=http://ordering-api/hc
      - IdentityUrlHC=http://identity-api/hc
      - BasketUrlHC=http://basket-api/hc
      - MarketingUrlHC=http://marketing-api/hc
      - PaymentUrlHC=http://payment-api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
  basketdata:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

W tym przykładzie konfiguracja zastępowania rozwoju udostępnia niektóre porty do hosta, definiuje zmienne środowiskowe z adresami URL przekierowania i określa parametry połączenia dla środowiska programistycznego. Te ustawienia są tylko dla środowiska programistycznego.

Po uruchomieniu `docker-compose up` (lub uruchomieniu go z programu Visual Studio), polecenie odczytuje zastąpienia automatycznie tak, jakby były scalanie obu plików.

Załóżmy, że chcesz inny plik compose dla środowiska produkcyjnego, z różnymi wartościami konfiguracji, portami lub ciągami połączeń. Można utworzyć inny plik zastępowania, `docker-compose.prod.yml` taki jak plik o nazwie z różnymi ustawieniami i zmiennymi środowiskowymi. Ten plik może być przechowywany w innym repozytorium Git lub zarządzany i zabezpieczony przez inny zespół.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Jak wdrożyć za pomocą określonego pliku zastępowania

Aby użyć wielu zastępowania plików lub zastępowania pliku o innej nazwie, można użyć opcji -f z poleceniem docker-compose i określić pliki. Redagowanie scala plików w kolejności, w jakiej są określone w wierszu polecenia. W poniższym przykładzie pokazano, jak wdrożyć za pomocą zastępowania plików.

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Używanie zmiennych środowiskowych w plikach docker-compose

Jest to wygodne, zwłaszcza w środowiskach produkcyjnych, aby móc uzyskać informacje o konfiguracji ze zmiennych środowiskowych, jak pokazano w poprzednich przykładach. Zmienną środowiskową w plikach docker-compose można odwoływać\_się do składni ${MY VAR}. W poniższym wierszu z pliku docker-compose.prod.yml pokazano, jak odwoływać się do wartości zmiennej środowiskowej.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Zmienne środowiskowe są tworzone i inicjowane na różne sposoby, w zależności od środowiska hosta (Linux, Windows, Cloud cluster itp.). Jednak wygodnym podejściem jest użycie pliku .env. Pliki docker-compose obsługują deklarowanie domyślnych zmiennych środowiskowych w pliku env. Te wartości dla zmiennych środowiskowych są wartościami domyślnymi. Można je jednak zastąpić wartościami zdefiniowanymi w każdym środowisku (host OS lub zmienne środowiskowe z klastra). Ten plik env umieszcza się w folderze, z którego jest wykonywane polecenie docker-compose.

W poniższym przykładzie pokazano plik .env, taki jak plik [env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) dla aplikacji eShopOnContainers.

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose oczekuje, że każdy wiersz w pliku env\>=\<\>będzie w wartości zmiennej formatu \<.

Wartości ustawione w środowisku czasu wykonywania zawsze zastępują wartości zdefiniowane wewnątrz pliku .env. W podobny sposób wartości przekazywane za pośrednictwem argumentów wiersza polecenia zastępują również wartości domyślne ustawione w pliku .env.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Omówienie kompozycji dokowane** \
    <https://docs.docker.com/compose/overview/>

- **Wiele plików compose** \
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Tworzenie zoptymalizowanych obrazów platformy Docker ASP.NET Core

Jeśli eksplorujesz platformy Docker i .NET Core na źródłach w Internecie, znajdziesz dockerfiles, które pokazują prostotę tworzenia obrazu platformy Docker, kopiując źródło do kontenera. Te przykłady sugerują, że za pomocą prostej konfiguracji, można mieć obraz platformy Docker ze środowiskiem spakowanym z aplikacją. W poniższym przykładzie przedstawiono prosty plik dockerfile w tym duchu.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Dockerfile tak będzie działać. Można jednak znacznie zoptymalizować obrazy, zwłaszcza obrazy produkcyjne.

W modelu kontenera i mikrousług stale uruchamiasz kontenery. Typowy sposób używania kontenerów nie uruchamia ponownie kontenera sypialnego, ponieważ kontener jest jednorazowy. Orchestrators (jak Kubernetes i usługi Azure Service Fabric) po prostu utworzyć nowe wystąpienia obrazów. Oznacza to, że należy zoptymalizować przez wstępne komppilowanie aplikacji, gdy jest on zbudowany, więc proces tworzenia wystąpienia będzie szybszy. Po uruchomieniu kontenera powinien być gotowy do uruchomienia. Nie przywracaj i kompiluj `dotnet restore` w `dotnet build` czasie wykonywania przy użyciu poleceń i interfejsu wiersza polecenia, jak można zobaczyć w wpisach w blogu o .NET Core i Docker.

Zespół platformy .NET wykonuje ważną pracę, aby uczynić program .NET Core i ASP.NET Core platformą zoptymalizowaną pod kątem kontenera. Nie tylko .NET Core jest lekka struktura z niewielkim rozmiarze pamięci; zespół skupił się na zoptymalizowanych obrazach platformy Docker dla trzech głównych scenariuszy i opublikował je w rejestrze Docker Hub w *dotnet/core,* począwszy od wersji 2.1:

1. **Rozwój**: Priorytetem jest możliwość szybkiego iteracji i debugowania zmian, a rozmiar jest drugorzędny.

2. **Kompilacja:** Priorytetem jest kompilowanie aplikacji, a obraz zawiera pliki binarne i inne zależności w celu optymalizacji plików binarnych.

3. **Produkcja:** Fokus jest szybkie wdrażanie i uruchamianie kontenerów, więc te obrazy są ograniczone do plików binarnych i zawartości potrzebnej do uruchomienia aplikacji.

Zespół platformy .NET udostępnia cztery podstawowe warianty w [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (w centrum docker):

1. **sdk**: dla scenariuszy rozwoju i budowania
1. **aspnet**: dla ASP.NET scenariuszy produkcji
1. **środowisko uruchomieniowe:** dla scenariuszy produkcji .NET
1. **identyfikatory wykonawcze:** dla scenariuszy produkcyjnych [samodzielnych aplikacji](../../../core/deploying/index.md#publish-self-contained)

W celu szybszego uruchamiania obrazy środowiska uruchomieniowego automatycznie ustawiają adresy URL aspnetcore\_na port 80 i używają Ngen do tworzenia natywnej pamięci podręcznej obrazów zestawów.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Tworzenie zoptymalizowanych obrazów platformy Docker za pomocą ASP.NET Core**  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- **Tworzenie obrazów platformy Docker dla aplikacji .NET Core**  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> [Poprzedni](data-driven-crud-microservice.md)
> [następny](database-server-container.md)
