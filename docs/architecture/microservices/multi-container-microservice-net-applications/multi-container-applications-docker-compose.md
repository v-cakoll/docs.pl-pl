---
title: Definiowanie aplikacji z wieloma kontenerami za pomocą pliku docker-compose.yml
description: Jak określić skład mikrousług dla aplikacji wielokontenerowej z docker-compose.yml.
ms.date: 01/30/2020
ms.openlocfilehash: 86d6feda343df7f4b72374f93fc45b3246780cdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502477"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definiowanie aplikacji z wieloma kontenerami za pomocą pliku docker-compose.yml

W tym przewodniku plik [docker-compose.yml](https://docs.docker.com/compose/compose-file/) został wprowadzony w sekcji [Krok 4. Zdefiniuj swoje usługi w pliku docker-compose.yml podczas tworzenia aplikacji platformy Docker z wieloma kontenerami](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application). Istnieją jednak dodatkowe sposoby używania plików docker-compose, które warto zbadać bardziej szczegółowo.

Na przykład można jawnie opisać, jak chcesz wdrożyć aplikację wielokontenerową w pliku docker-compose.yml. Opcjonalnie można również opisać, jak zamierzasz tworzyć niestandardowe obrazy platformy Docker. (Niestandardowe obrazy platformy Docker mogą być również tworzone za pomocą platformy Docker CLI).

Zasadniczo należy zdefiniować każdy z kontenerów, które chcesz wdrożyć oraz pewne cechy dla każdego wdrożenia kontenera. Po uzyskaniu pliku opisu wdrożenia wielokontenerowego można wdrożyć całe rozwiązanie w jednej akcji zaaranżowanej przez polecenie wiersza polecenia wiersza polecenia wiersza polecenia [docker-compose lub](https://docs.docker.com/compose/overview/) można go wdrożyć w sposób przezroczysty z programu Visual Studio. W przeciwnym razie należy użyć polecenia wiersza wiersza wiersza polecenia platformy `docker run` Docker do wdrażania kontenera po kontenerze w wielu krokach przy użyciu polecenia z wiersza polecenia. W związku z tym każda usługa zdefiniowana w docker-compose.yml musi określić dokładnie jeden obraz lub kompilacji. Inne klucze są opcjonalne i `docker run` są analogiczne do ich odpowiedników wiersza polecenia.

Poniższy kod YAML jest definicją możliwego globalnego, ale pojedynczego pliku docker-compose.yml dla próbki eShopOnContainers. Nie jest to rzeczywisty plik docker-compose z eShopOnContainers. Zamiast tego jest to uproszczona i skonsolidowana wersja w jednym pliku, co nie jest najlepszym sposobem pracy z plikami docker-compose, jak wyjaśniono później.

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

Kluczem głównym w tym pliku są usługi. W obszarze tego klucza można zdefiniować usługi, które `docker-compose up` mają zostać wdrożone i uruchomione podczas wykonywania polecenia lub podczas wdrażania z programu Visual Studio przy użyciu tego pliku docker-compose.yml. W takim przypadku plik docker-compose.yml ma zdefiniowano wiele usług, zgodnie z opisem w poniższej tabeli.

| Nazwa usługi | Opis |
|--------------|-------------|
| webmvc       | Kontener, w tym ASP.NET core mvc aplikacji korzystających z mikrousług z c stronie serwera\#|
| katalog-api  | Kontener zawierający katalog ASP.NET mikrousług interfejsu API podstawowej sieci Web |
| zamawianie-api | Kontener zawierający mikrousługę interfejsu API podstawowej ASP.NET podstawowej sieci Web |
| sqldata (dane sqldata)     | Kontener z uruchomionym programem SQL Server dla systemu Linux, zawierający bazy danych mikrousług |
| kosz-api   | Kontener z mikrousługą interfejsu API ASP.NET podstawowej sieci Web |
| basketdata (dane koszykowe)  | Kontener z uruchomioną usługą pamięci podręcznej REDIS z bazą danych koszyka jako pamięcipodręcznej REDIS |

### <a name="a-simple-web-service-api-container"></a>Prosty kontener interfejsu API usługi sieci Web

Koncentrując się na pojedynczykontener, katalog-api container-microservice ma prostą definicję:

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

Ta usługa konteneryzowana ma następującą podstawową konfigurację:

- Jest on oparty na niestandardowych **eshop / katalog-api** obrazu. Dla uproszczenia nie ma kompilacji: ustawienie klucza w pliku. Oznacza to, że obraz musi być wcześniej zbudowany (z kompilacją docker) lub zostały pobrane (z poleceniem docker pull) z dowolnego rejestru platformy Docker.

- Definiuje zmienną środowiskową o nazwie ConnectionString z parametryą połączenia, która ma być używana przez entity framework, aby uzyskać dostęp do wystąpienia programu SQL Server, który zawiera model danych katalogu. W takim przypadku ten sam kontener programu SQL Server zawiera wiele baz danych. W związku z tym potrzebujesz mniej pamięci w komputerze deweloperskim dla platformy Docker. Można jednak również wdrożyć jeden kontener programu SQL Server dla każdej bazy danych mikrousług.

- Nazwa programu SQL Server to **sqldata**, która jest tą samą nazwą, która jest używana dla kontenera z wystąpieniem programu SQL Server dla systemu Linux. Jest to wygodne; możliwość korzystania z tej rozdzielczości nazwy (wewnętrzna hosta platformy Docker) rozwiąże adres sieciowy, dzięki czemu nie trzeba znać wewnętrznego adresu IP kontenerów, do których uzyskujesz dostęp z innych kontenerów.

Ponieważ parametry połączenia są definiowane przez zmienną środowiskową, można ustawić tę zmienną za pomocą innego mechanizmu i w innym czasie. Na przykład można ustawić inny ciąg połączenia podczas wdrażania w środowisku produkcyjnym w hostach końcowych lub wykonując go z potoków ciągłej integracji/ciągłego wdrażania w usłudze Azure DevOps Services lub preferowanym systemie DevOps.

- Udostępnia port 80 dla wewnętrznego dostępu do usługi **katalogu api** w hoście platformy Docker. Host jest obecnie maszyną wirtualną systemu Linux, ponieważ jest ona oparta na obrazie platformy Docker dla systemu Linux, ale można skonfigurować kontener do uruchamiania na obrazie systemu Windows.

- Przekazuje narażony port 80 w kontenerze do portu 5101 na komputerze hosta platformy Docker (maszyna wirtualna systemu Linux).

- Łączy usługę sieci web z usługą **sqldata** (wystąpienie programu SQL Server dla bazy danych systemu Linux działającej w kontenerze). Po określeniu tej zależności kontener api katalogu nie zostanie uruchomiony, dopóki kontener sqldata nie został już uruchomiony; jest to ważne, ponieważ katalog-api musi mieć bazę danych programu SQL Server w pierwszej kolejności i działa. Jednak tego rodzaju zależności kontenera nie wystarczy w wielu przypadkach, ponieważ docker sprawdza tylko na poziomie kontenera. Czasami usługa (w tym przypadku SQL Server) może nadal nie być gotowy, więc zaleca się zaimplementować logikę ponawiania prób y z wykładniczym wycofywaniem w mikrousługach klienta. W ten sposób, jeśli kontener zależności nie jest gotowy na krótki czas, aplikacja nadal będzie odporna.

- Jest skonfigurowany tak, aby zezwalał\_na dostęp do serwerów zewnętrznych: ustawienie dodatkowych hostów umożliwia dostęp do zewnętrznych serwerów lub komputerów poza hostem platformy Docker (czyli poza domyślną maszyną wirtualną systemu Linux, która jest deweloperskim hostem platformy Docker), takim jak wystąpienie lokalnego programu SQL Server na komputerze deweloperskim.

Istnieją również inne, `docker-compose.yml` bardziej zaawansowane ustawienia, które omówimy w poniższych sekcjach.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Używanie plików docker-compose do obsługi wielu środowisk

Pliki `docker-compose.*.yml` są plikami definicji i mogą być używane przez wiele infrastruktur, które rozumieją ten format. Najprostszym narzędziem jest polecenie docker-compose.

W związku z tym za pomocą polecenia docker-compose można kierować następujące główne scenariusze.

#### <a name="development-environments"></a>Środowiska deweloperskie

Podczas tworzenia aplikacji, ważne jest, aby móc uruchamiać aplikację w izolowanym środowisku programistycznym. Polecenia wiersza polecenia wiersza polecenia wiersza polecenia docker-coms można utworzyć to środowisko lub program Visual Studio, który używa docker-compose pod okładkami.

Plik docker-compose.yml umożliwia konfigurowanie i dokumentowanie wszystkich zależności usługi aplikacji (inne usługi, pamięć podręczna, bazy danych, kolejki itp.). Za pomocą polecenia wiersza polecenia wiersza polecenia docker-compose można utworzyć i uruchomić jeden lub więcej kontenerów dla każdej zależności za pomocą jednego polecenia (docker-compose up).

Pliki docker-compose.yml są plikami konfiguracyjnymi interpretowane przez aparat platformy Docker, ale służą również jako wygodne pliki dokumentacji dotyczące składu aplikacji wielokontenerowej.

#### <a name="testing-environments"></a>Środowiska testowe

Ważną częścią każdego procesu ciągłego wdrażania (CD) lub ciągłej integracji (CI) są testy jednostkowe i testy integracji. Te zautomatyzowane testy wymagają izolowanego środowiska, więc nie mają wpływu na użytkowników lub żadnych innych zmian w danych aplikacji.

Za pomocą platformy Docker Compose można bardzo łatwo tworzyć i niszczyć to izolowane środowisko za pomocą kilku poleceń z wiersza polecenia lub skryptów, takich jak następujące polecenia:

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>Wdrożenia produkcyjne

Można również użyć Compose do wdrożenia do zdalnego aparatu platformy Docker. Typowym przypadkiem jest wdrożenie w jednym wystąpieniu hosta platformy Docker (takiej jak produkcyjna maszyna wirtualna lub serwer aprowizowany za pomocą [komputera platformy Docker).](https://docs.docker.com/machine/overview/)

If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.

W każdym przypadku docker-compose jest wygodnym narzędziem i formatem metadanych dla przepływu pracy programowania, testowania i produkcji, chociaż przepływ pracy produkcji może się różnić w zależności od koordynatora, którego używasz.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Używanie wielu plików docker-compose do obsługi kilku środowisk

Podczas kierowania na różne środowiska należy używać wielu plików redagowania. Dzięki temu można utworzyć wiele wariantów konfiguracji w zależności od środowiska.

#### <a name="overriding-the-base-docker-compose-file"></a>Zastępowanie podstawowego pliku docker-compose

Można użyć pojedynczego pliku docker-compose.yml, jak w uproszczonych przykładów wyświetlanych w poprzednich sekcjach. Jednak nie jest to zalecane w przypadku większości aplikacji.

Domyślnie Compose odczytuje dwa pliki, plik docker-compose.yml i opcjonalny plik docker-compose.override.yml. Jak pokazano na rysunku 6-11, gdy używasz programu Visual Studio i włączanie obsługi platformy Docker, Visual Studio tworzy również dodatkowy plik docker-compose.vs.debug.g.yml do debugowania aplikacji, można spojrzeć na ten plik w folderze obj\\folderu\\ w głównym folderze rozwiązania.

![Zrzut ekranu przedstawiający pliki w docker compose project.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

**Rysunek 6-11**. pliki docker-compose w programie Visual Studio 2019

struktura pliku projektu **docker-compose:**

- *.dockerignore* - służy do ignorowania plików
- *docker-compose.yml* — służy do tworzenia mikrousług
- *docker-compose.override.yml* — służy do konfigurowania środowiska mikrousług

Można edytować pliki docker-compose z dowolnego edytora, takich jak Visual Studio Code lub Sublime i uruchomić aplikację za pomocą polecenia docker-compose up.

Zgodnie z konwencją plik docker-compose.yml zawiera konfigurację podstawową i inne ustawienia statyczne. Oznacza to, że konfiguracja usługi nie powinna ulec zmianie w zależności od środowiska wdrażania, na które jest kierowana.

Plik docker-compose.override.yml, jak sama nazwa wskazuje, zawiera ustawienia konfiguracji, które zastępują konfigurację podstawową, takie jak konfiguracja, która zależy od środowiska wdrażania. Można mieć wiele plików zastępowania o różnych nazwach również. Pliki zastępowania zwykle zawierają dodatkowe informacje wymagane przez aplikację, ale specyficzne dla środowiska lub wdrożenia.

#### <a name="targeting-multiple-environments"></a>Kierowanie na wiele środowisk

Typowy przypadek użycia jest podczas definiowania wielu plików redagowania, dzięki czemu można kierować wiele środowisk, takich jak produkcja, przemieszczania, ci lub rozwoju. Aby uwzględnić te różnice, można podzielić konfigurację Compose na wiele plików, jak pokazano na rysunku 6-12.

![Diagram trzech plików docker-compose ustawionych w celu zastąpienia pliku podstawowego.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

**Rysunek 6-12**. Wiele plików docker-compose overriding wartości w pliku docker-compose.yml podstawowego

Można połączyć wiele plików docker-compose*.yml do obsługi różnych środowisk. Zacznij od pliku base docker-compose.yml. Ten plik podstawowy musi zawierać podstawowe lub statyczne ustawienia konfiguracji, które nie zmieniają się w zależności od środowiska. Na przykład eShopOnContainers ma następujący plik docker-compose.yml (uproszczony z mniejszą liczbą usług) jako plik podstawowy.

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

Wartości w pliku docker-compose.yml podstawowej nie powinny ulec zmianie z powodu różnych środowisk wdrażania docelowego.

Jeśli na przykład skupisz się na definicji usługi webmvc, możesz zobaczyć, jak te informacje są takie same bez względu na to, na jakim środowisku możesz być kierowany. Masz następujące informacje:

- Nazwa usługi: webmvc.

- Niestandardowy obraz kontenera: eshop/webmvc.

- Polecenie do tworzenia niestandardowego obrazu platformy Docker, wskazując, który dockerfile do użycia.

- Zależności od innych usług, więc ten kontener nie uruchamia się, dopóki nie uruchomiono innych kontenerów zależności.

Można mieć dodatkową konfigurację, ale ważnym punktem jest to, że w podstawowym pliku docker-compose.yml, po prostu chcesz ustawić informacje, które są wspólne dla środowisk. Następnie w pliku docker-compose.override.yml lub podobnych plików dla produkcji lub przemieszczania, należy umieścić konfigurację, która jest specyficzna dla każdego środowiska.

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

W tym przykładzie konfiguracja zastępowania rozwoju udostępnia niektóre porty do hosta, definiuje zmienne środowiskowe z adresami URL przekierowań i określa parametry połączenia dla środowiska programistycznego. Te ustawienia są tylko dla środowiska programistycznego.

Po uruchomieniu `docker-compose up` (lub uruchomieniu go z programu Visual Studio) polecenie automatycznie odczytuje zastąpienia, tak jakby scalało oba pliki.

Załóżmy, że chcesz innego pliku Compose dla środowiska produkcyjnego, z różnymi wartościami konfiguracji, portami lub ciągami połączeń. Można utworzyć inny plik zastępowania, taki jak plik o nazwie `docker-compose.prod.yml` z różnymi ustawieniami i zmiennymi środowiskowymi. Ten plik może być przechowywany w innym repocie Git lub zarządzany i zabezpieczony przez inny zespół.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Jak wdrożyć z określonym plikiem zastępowania

Aby użyć wielu plików zastępowania lub pliku zastępowania o innej nazwie, można użyć opcji -f z poleceniem docker-compose i określić pliki. Redagowanie scala pliki w kolejności, w jakiej są określone w wierszu polecenia. W poniższym przykładzie pokazano, jak wdrożyć z plików zastępowania.

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Używanie zmiennych środowiskowych w plikach docker-compose

Jest to wygodne, szczególnie w środowiskach produkcyjnych, aby móc uzyskać informacje o konfiguracji ze zmiennych środowiskowych, jak wykazano w poprzednich przykładach. Zmienną środowiskową można odwoływać się do plików docker-compose przy użyciu składni ${MY\_VAR}. W następującym wierszu pliku docker-compose.prod.yml pokazano, jak odwoływać się do wartości zmiennej środowiskowej.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Zmienne środowiskowe są tworzone i inicjowane na różne sposoby, w zależności od środowiska hosta (Linux, Windows, Klastra w chmurze itp.). Jednak wygodnym podejściem jest użycie pliku env. Pliki docker-compose obsługują deklarowanie domyślnych zmiennych środowiskowych w pliku env. Te wartości dla zmiennych środowiskowych są wartościami domyślnymi. Można je jednak zastąpić wartościami zdefiniowanymi w każdym środowisku (host os lub zmienne środowiskowe z klastra). Ten plik env można umieścić w folderze, z którego jest wykonywane polecenie docker-compose.

W poniższym przykładzie przedstawiono plik env, taki jak plik [env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) dla aplikacji eShopOnContainers.

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose oczekuje, że każdy wiersz w pliku env\>=\<\>będzie w wartości zmiennej formatu \<.

Wartości ustawione w środowisku wykonywania zawsze zastępują wartości zdefiniowane wewnątrz pliku env. W podobny sposób wartości przekazywane za pomocą argumentów wiersza polecenia również zastępują wartości domyślne ustawione w pliku env.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Omówienie docker Compose** \
    <https://docs.docker.com/compose/overview/>

- **Wiele plików redagowania** \
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Tworzenie zoptymalizowanych obrazów platformy ASP.NET core docker

Jeśli eksplorujesz platformę Docker i .NET Core na źródłach w Internecie, znajdziesz pliki dockerfiles, które demonstrują prostotę tworzenia obrazu platformy Docker, kopiując źródło do kontenera. Te przykłady sugerują, że przy użyciu prostej konfiguracji można mieć obraz platformy Docker ze środowiskiem spakowanym z aplikacją. W poniższym przykładzie przedstawiono prosty plik Dockerfile w tym duchu.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Dockerfile jak to będzie działać. Można jednak znacznie zoptymalizować obrazy, zwłaszcza obrazy produkcyjne.

W modelu kontenera i mikrousług stale uruchamiasz kontenery. Typowy sposób używania kontenerów nie uruchamia ponownie kontenera uśpionego, ponieważ kontener jest jednorazowy. Koordynatorzy (jak Kubernetes i sieci szkieletowej usług Azure) po prostu utworzyć nowe wystąpienia obrazów. Oznacza to, że należy zoptymalizować przez prekompilacji aplikacji, gdy jest zbudowany tak proces wystąpienia będzie szybszy. Po uruchomieniu kontenera powinien być gotowy do uruchomienia. Nie należy przywracać i kompilować `dotnet restore` w `dotnet build` czasie wykonywania, przy użyciu i polecenia z wiersza polecenia dotnet, które, jak widać w wielu wpisów w blogu o .NET Core i Docker.

Zespół .NET wykonuje ważną pracę, aby program .NET Core i ASP.NET Core były platformą zoptymalizowaną pod kątem kontenera. Program .NET Core jest nie tylko lekką strukturą o niewielkim rozmiarze pamięci; zespół skupił się na zoptymalizowanych obrazach platformy Docker dla trzech głównych scenariuszy i opublikował je w rejestrze docker hub w *dotnet/core*, począwszy od wersji 2.1:

1. **Rozwój**: Gdzie priorytetem jest możliwość szybkiego iterate i debugowania zmian, a gdzie rozmiar jest drugorzędny.

2. **Kompilacja:** Priorytetem jest kompilowanie aplikacji i zawiera pliki binarne i inne zależności w celu optymalizacji plików binarnych.

3. **Produkcja:** W przypadku, gdy fokus jest szybki wdrażania i uruchamiania kontenerów, więc te obrazy są ograniczone do plików binarnych i zawartości potrzebnej do uruchomienia aplikacji.

Aby to osiągnąć, zespół .NET udostępnia cztery podstawowe warianty w [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (w docker Hub):

1. **sdk**: scenariusze rozwoju i budowania
1. **aspnet**: dla ASP.NET scenariuszy produkcyjnych
1. **runtime**: dla scenariuszy produkcyjnych .NET
1. **runtime-deps**: dla scenariuszy produkcyjnych [aplikacji samodzielnych](../../../core/deploying/index.md#publish-self-contained).

Aby przyspieszyć uruchamianie, obrazy w czasie wykonywania również automatycznie ustawiają adresy URL aspnetcore\_do portu 80 i używają Ngen do tworzenia natywnej pamięci podręcznej obrazów zestawów.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Tworzenie zoptymalizowanych obrazów platformy Docker z ASP.NET core**  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- **Tworzenie obrazów platformy Docker dla aplikacji .NET Core**  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> [Poprzedni](data-driven-crud-microservice.md)
> [następny](database-server-container.md)
