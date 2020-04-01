---
title: Definiowanie aplikacji z wieloma kontenerami za pomocą pliku docker-compose.yml
description: Jak określić kompozycję mikrousług dla aplikacji wielokontenerowej z docker-compose.yml.
ms.date: 01/30/2020
ms.openlocfilehash: 9143801fbbffbdc5b795a232b3333edf71f05c7c
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523649"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="8cfa5-103">Definiowanie aplikacji z wieloma kontenerami za pomocą pliku docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="8cfa5-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="8cfa5-104">W tym przewodniku plik [docker-compose.yml](https://docs.docker.com/compose/compose-file/) został wprowadzony w sekcji [Krok 4. Zdefiniuj swoje usługi w pliku docker-compose.yml podczas tworzenia aplikacji platformy Docker z wieloma kontenerami](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="8cfa5-105">Istnieją jednak dodatkowe sposoby korzystania z plików docker-compose, które warto zbadać bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="8cfa5-106">Na przykład można jawnie opisać, jak chcesz wdrożyć aplikację z wieloma kontenerami w pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="8cfa5-107">Opcjonalnie można również opisać, jak zamierzasz tworzyć niestandardowe obrazy platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="8cfa5-108">(Niestandardowe obrazy platformy Docker można również tworzyć za pomocą interfejsu wiersza polecenia platformy Docker).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="8cfa5-109">Zasadniczo można zdefiniować każdy kontener, który chcesz wdrożyć plus pewne cechy dla każdego wdrożenia kontenera.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="8cfa5-110">Po uzyskaniu pliku opisu wdrożenia wielu kontenerów można wdrożyć całe rozwiązanie w pojedynczej akcji zaaranżowanej przez polecenie [docker-compose up](https://docs.docker.com/compose/overview/) CLI lub wdrożyć je w sposób przezroczysty w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="8cfa5-111">W przeciwnym razie należy użyć interfejsu wiersza polecenia platformy Docker do `docker run` wdrażania kontenera po kontenerze w wielu krokach przy użyciu polecenia z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="8cfa5-112">W związku z tym każda usługa zdefiniowana w docker-compose.yml musi określić dokładnie jeden obraz lub kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="8cfa5-113">Inne klucze są opcjonalne i `docker run` są analogiczne do ich odpowiedników wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="8cfa5-114">Poniższy kod YAML jest definicją możliwego globalnego, ale pojedynczego pliku docker-compose.yml dla przykładu eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="8cfa5-115">Nie jest to rzeczywisty plik docker-compose z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="8cfa5-116">Zamiast tego jest to uproszczona i skonsolidowana wersja w jednym pliku, co nie jest najlepszym sposobem pracy z plikami docker-compose, jak zostanie to wyjaśnione później.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="8cfa5-117">Kluczem głównym w tym pliku są usługi.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-117">The root key in this file is services.</span></span> <span data-ttu-id="8cfa5-118">W ramach tego klucza można zdefiniować usługi, które `docker-compose up` mają być wdrażane i uruchamiane podczas wykonywania polecenia lub wdrażania z programu Visual Studio przy użyciu tego pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-118">Under that key, you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="8cfa5-119">W takim przypadku plik docker-compose.yml ma zdefiniowane wiele usług, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="8cfa5-120">Nazwa usługi</span><span class="sxs-lookup"><span data-stu-id="8cfa5-120">Service name</span></span> | <span data-ttu-id="8cfa5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8cfa5-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="8cfa5-122">webmvc (webmvc)</span><span class="sxs-lookup"><span data-stu-id="8cfa5-122">webmvc</span></span>       | <span data-ttu-id="8cfa5-123">Kontener zawierający ASP.NET podstawową aplikację MVC zużywającą mikrousługi z c po stronie serwera\#</span><span class="sxs-lookup"><span data-stu-id="8cfa5-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="8cfa5-124">katalog-api</span><span class="sxs-lookup"><span data-stu-id="8cfa5-124">catalog-api</span></span>  | <span data-ttu-id="8cfa5-125">Kontener zawierający mikrousługę interfejsu API sieci Web catalog ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8cfa5-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="8cfa5-126">zamawianie-api</span><span class="sxs-lookup"><span data-stu-id="8cfa5-126">ordering-api</span></span> | <span data-ttu-id="8cfa5-127">Kontener zawierający mikrousługę interfejsu API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8cfa5-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="8cfa5-128">sqldata</span><span class="sxs-lookup"><span data-stu-id="8cfa5-128">sqldata</span></span>     | <span data-ttu-id="8cfa5-129">Kontener z systemem SQL Server dla systemu Linux, zawierający bazy danych mikrousług</span><span class="sxs-lookup"><span data-stu-id="8cfa5-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="8cfa5-130">koszyk-api</span><span class="sxs-lookup"><span data-stu-id="8cfa5-130">basket-api</span></span>   | <span data-ttu-id="8cfa5-131">Kontener z mikrousługą interfejsu API sieci Web w koszyku ASP.NET rdzenia</span><span class="sxs-lookup"><span data-stu-id="8cfa5-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="8cfa5-132">dane koszykowe</span><span class="sxs-lookup"><span data-stu-id="8cfa5-132">basketdata</span></span>  | <span data-ttu-id="8cfa5-133">Kontener z uruchomieniem usługi pamięci podręcznej REDIS z bazą danych koszyka jako pamięcią podręczną REDIS</span><span class="sxs-lookup"><span data-stu-id="8cfa5-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="8cfa5-134">Prosty kontener interfejsu API usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="8cfa5-134">A simple Web Service API container</span></span>

<span data-ttu-id="8cfa5-135">Koncentrując się na pojedynczy kontener, catalog-api container-microservice ma prostą definicję:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-135">Focusing on a single container, the catalog-api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="8cfa5-136">Ta konteneryzowana usługa ma następującą podstawową konfigurację:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="8cfa5-137">Jest on oparty na niestandardowym **eshop / katalog-api** obrazu.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-137">It is based on the custom **eshop/catalog-api** image.</span></span> <span data-ttu-id="8cfa5-138">Dla uproszczenia nie ma kompilacji: ustawienie klucza w pliku.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="8cfa5-139">Oznacza to, że obraz musi być wcześniej zbudowany (z kompilacją platformy docker) lub został pobrany (za pomocą polecenia ściągania platformy docker) z dowolnego rejestru platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="8cfa5-140">Definiuje zmienną środowiskową o nazwie ConnectionString z ciągiem połączenia, który ma być używany przez entity framework, aby uzyskać dostęp do wystąpienia programu SQL Server zawierającego model danych katalogu.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="8cfa5-141">W takim przypadku ten sam kontener programu SQL Server przechowuje wiele baz danych.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="8cfa5-142">W związku z tym potrzebujesz mniej pamięci na komputerze deweloperskim dla platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="8cfa5-143">Można jednak również wdrożyć jeden kontener programu SQL Server dla każdej bazy danych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="8cfa5-144">Nazwa programu SQL Server to **sqldata**, która jest tą samą nazwą, która jest używana dla kontenera, który jest uruchomiony wystąpienie programu SQL Server dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-144">The SQL Server name is **sqldata**, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="8cfa5-145">Jest to wygodne; możliwość użycia tej rozdzielczości nazwy (wewnętrznej do hosta platformy Docker) rozwiąże adres sieciowy, dzięki czemu nie trzeba znać wewnętrznego adresu IP kontenerów, do których uzyskujesz dostęp z innych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="8cfa5-146">Ponieważ parametry połączenia jest zdefiniowany przez zmienną środowiskową, można ustawić tę zmienną za pomocą innego mechanizmu i w innym czasie.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="8cfa5-147">Na przykład można ustawić inny ciąg połączenia podczas wdrażania do produkcji w hostach końcowych lub wykonując go z potoków ciągłej integracji/ciągłego wdrażania w usługach DevOps platformy Azure lub preferowanego systemu DevOps.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="8cfa5-148">Udostępnia port 80 dla wewnętrznego dostępu do usługi **interfejsu api katalogu** w hoście platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-148">It exposes port 80 for internal access to the **catalog-api** service within the Docker host.</span></span> <span data-ttu-id="8cfa5-149">Host jest obecnie maszyną wirtualną z systemem Linux, ponieważ jest on oparty na obrazie platformy Docker dla systemu Linux, ale można skonfigurować kontener do uruchamiania na obrazie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="8cfa5-150">Przekazuje narażony port 80 w kontenerze do portu 5101 na komputerze hosta platformy Docker (maszyna wirtualna z systemem Linux).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="8cfa5-151">Łączy usługę sieci web z usługą **sqldata** (wystąpienie programu SQL Server dla bazy danych systemu Linux uruchomionej w kontenerze).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-151">It links the web service to the **sqldata** service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="8cfa5-152">Po określeniu tej zależności kontener interfejsu api katalogu nie zostanie uruchomiony, dopóki kontener sqldata nie zostanie już uruchomiony; jest to ważne, ponieważ catalog-api musi mieć najpierw i uruchomię bazę danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-152">When you specify this dependency, the catalog-api container will not start until the sqldata container has already started; this is important because catalog-api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="8cfa5-153">Jednak tego rodzaju zależności kontenera nie wystarczy w wielu przypadkach, ponieważ docker sprawdza tylko na poziomie kontenera.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="8cfa5-154">Czasami usługa (w tym przypadku SQL Server) może nadal nie być gotowy, więc wskazane jest, aby zaimplementować logikę ponawiania z wykładniczego wycofywania w mikrousług klienta.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="8cfa5-155">W ten sposób jeśli kontener zależności nie jest gotowy na krótki czas, aplikacja będzie nadal odporne.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="8cfa5-156">Jest skonfigurowany tak, aby umożliwić dostęp\_do serwerów zewnętrznych: ustawienie dodatkowych hostów umożliwia dostęp do zewnętrznych serwerów lub maszyn poza hostem platformy Docker (czyli poza domyślną maszyną wirtualną systemu Linux, która jest deweloperskim hostem platformy Docker), na przykład lokalnym wystąpieniem programu SQL Server na komputerze deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM, which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="8cfa5-157">Istnieją również inne, `docker-compose.yml` bardziej zaawansowane ustawienia, które omówimy w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-157">There are also other, more advanced `docker-compose.yml` settings that we'll discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="8cfa5-158">Używanie plików docker-compose do kierowania na wiele środowisk</span><span class="sxs-lookup"><span data-stu-id="8cfa5-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="8cfa5-159">Pliki `docker-compose.*.yml` są plikami definicji i mogą być używane przez wiele infrastruktur, które rozumieją ten format.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-159">The `docker-compose.*.yml` files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="8cfa5-160">Najprostszym narzędziem jest polecenie docker-compose.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="8cfa5-161">W związku z tym za pomocą polecenia docker-compose można kierować następujące scenariusze główne.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="8cfa5-162">Środowiska deweloperskie</span><span class="sxs-lookup"><span data-stu-id="8cfa5-162">Development environments</span></span>

<span data-ttu-id="8cfa5-163">Podczas tworzenia aplikacji, ważne jest, aby móc uruchomić aplikację w środowisku rozwoju izolowane.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="8cfa5-164">Za pomocą polecenia docker-compose CLI można utworzyć to środowisko lub program Visual Studio, który używa docker-compose w ramach obejmuje.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-164">You can use the docker-compose CLI command to create that environment or Visual Studio, which uses docker-compose under the covers.</span></span>

<span data-ttu-id="8cfa5-165">Plik docker-compose.yml umożliwia skonfigurowanie i udokumentowanie wszystkich zależności usługi aplikacji (innych usług, pamięci podręcznej, baz danych, kolejek itp.).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="8cfa5-166">Za pomocą polecenia docker-compose CLI można utworzyć i uruchomić jeden lub więcej kontenerów dla każdej zależności za pomocą jednego polecenia (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="8cfa5-167">Pliki docker-compose.yml są plikami konfiguracyjnymi interpretowanymi przez aparat platformy Docker, ale służą również jako wygodne pliki dokumentacji dotyczące składu aplikacji wielokontenerowej.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="8cfa5-168">Środowiska testowe</span><span class="sxs-lookup"><span data-stu-id="8cfa5-168">Testing environments</span></span>

<span data-ttu-id="8cfa5-169">Ważną częścią każdego ciągłego wdrażania (CD) lub ciągłej integracji (CI) są testy jednostkowe i testy integracji.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="8cfa5-170">Te zautomatyzowane testy wymagają izolowanego środowiska, aby nie miały wpływu na użytkowników ani na inne zmiany w danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="8cfa5-171">Za pomocą docker compose można bardzo łatwo utworzyć i zniszczyć izolowane środowisko w kilku poleceniach z wiersza polecenia lub skryptów, takich jak następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-171">With Docker Compose, you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="8cfa5-172">Wdrożenia produkcyjne</span><span class="sxs-lookup"><span data-stu-id="8cfa5-172">Production deployments</span></span>

<span data-ttu-id="8cfa5-173">Można również użyć compose do wdrożenia na zdalnym aparat platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="8cfa5-174">Typowym przypadkiem jest wdrożenie w jednym wystąpieniu hosta platformy Docker (na przykład produkcyjnej maszynie wirtualnej lub serwer aprowizowana za pomocą [komputera platformy Docker Machine).](https://docs.docker.com/machine/overview/)</span><span class="sxs-lookup"><span data-stu-id="8cfa5-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="8cfa5-175">Jeśli używasz innego koordynatora (sieci szkieletowej usługi Azure, kubernetes itp.), może być konieczne dodanie ustawień konfiguracji i konfiguracji metadanych, takich jak te w docker-compose.yml, ale w formacie wymaganym przez innego koordynatora.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="8cfa5-176">W każdym przypadku docker-compose jest wygodnym narzędziem i formatem metadanych dla przepływów pracy deweloperskich, testowych i produkcyjnych, chociaż przepływ pracy produkcji może się różnić w przypadku używanego koordynatora.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="8cfa5-177">Używanie wielu plików docker-compose do obsługi kilku środowisk</span><span class="sxs-lookup"><span data-stu-id="8cfa5-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="8cfa5-178">Podczas kierowania na różne środowiska należy użyć wielu plików redagowania.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="8cfa5-179">Dzięki temu można utworzyć wiele wariantów konfiguracji w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="8cfa5-180">Zastępowanie podstawowego pliku docker-compose</span><span class="sxs-lookup"><span data-stu-id="8cfa5-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="8cfa5-181">Można użyć pojedynczego pliku docker-compose.yml, jak w uproszczonych przykładach pokazanych w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="8cfa5-182">Jednak nie jest to zalecane dla większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="8cfa5-183">Domyślnie Compose odczytuje dwa pliki: plik docker-compose.yml i opcjonalny plik docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="8cfa5-184">Jak pokazano na rysunku 6-11, podczas korzystania z programu Visual Studio i włączania obsługi platformy Docker, Visual Studio tworzy również dodatkowy plik docker-compose.vs.debug.g.yml do debugowania aplikacji, można spojrzeć na ten plik w folderze obj\\Docker\\ w głównym folderze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Zrzut ekranu przedstawiający pliki w projekcie tworzenia kompozycji docker.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

<span data-ttu-id="8cfa5-186">**Rysunek 6-11**.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-186">**Figure 6-11**.</span></span> <span data-ttu-id="8cfa5-187">pliki docker-compose w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="8cfa5-187">docker-compose files in Visual Studio 2019</span></span>

<span data-ttu-id="8cfa5-188">struktura pliku projektu **docker-compose:**</span><span class="sxs-lookup"><span data-stu-id="8cfa5-188">**docker-compose** project file structure:</span></span>

- <span data-ttu-id="8cfa5-189">*.dockerignore* — służy do ignorowania plików</span><span class="sxs-lookup"><span data-stu-id="8cfa5-189">*.dockerignore* - used to ignore files</span></span>
- <span data-ttu-id="8cfa5-190">*docker-compose.yml* - służy do tworzenia mikrousług</span><span class="sxs-lookup"><span data-stu-id="8cfa5-190">*docker-compose.yml* - used to compose microservices</span></span>
- <span data-ttu-id="8cfa5-191">*docker-compose.override.yml* — służy do konfigurowania środowiska mikrousług</span><span class="sxs-lookup"><span data-stu-id="8cfa5-191">*docker-compose.override.yml* - used to configure microservices environment</span></span>

<span data-ttu-id="8cfa5-192">Pliki docker-compose można edytować za pomocą dowolnego edytora, takiego jak Visual Studio Code lub Sublime, i uruchomić aplikację za pomocą polecenia docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-192">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="8cfa5-193">Zgodnie z konwencją plik docker-compose.yml zawiera konfigurację podstawową i inne ustawienia statyczne.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-193">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="8cfa5-194">Oznacza to, że konfiguracja usługi nie powinna się zmieniać w zależności od środowiska wdrażania, które są kierowane.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-194">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="8cfa5-195">Plik docker-compose.override.yml, jak sama nazwa wskazuje, zawiera ustawienia konfiguracji, które zastępują konfigurację podstawową, taką jak konfiguracja zależna od środowiska wdrażania.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-195">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="8cfa5-196">Można również zastąpić wiele plików o różnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-196">You can have multiple override files with different names also.</span></span> <span data-ttu-id="8cfa5-197">Pliki zastępowania zwykle zawierają dodatkowe informacje wymagane przez aplikację, ale specyficzne dla środowiska lub wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-197">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="8cfa5-198">Kierowanie na wiele środowisk</span><span class="sxs-lookup"><span data-stu-id="8cfa5-198">Targeting multiple environments</span></span>

<span data-ttu-id="8cfa5-199">Typowym przypadkiem użycia jest zdefiniowanie wielu plików redagowania, dzięki czemu można kierować wiele środowisk, takich jak produkcja, przemieszczania, ciągłości integracji lub rozwoju.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-199">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="8cfa5-200">Aby obsługiwać te różnice, można podzielić konfigurację compose na wiele plików, jak pokazano na rysunku 6-12.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-200">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Diagram trzech plików docker-compose ustawionych w celu zastąpienia pliku podstawowego.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

<span data-ttu-id="8cfa5-202">**Rysunek 6-12**.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-202">**Figure 6-12**.</span></span> <span data-ttu-id="8cfa5-203">Wiele plików docker-redpose nadrzędnych wartości w podstawowym pliku docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="8cfa5-203">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="8cfa5-204">Można połączyć wiele plików docker-compose\*.yml w celu obsługi różnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-204">You can combine multiple docker-compose\*.yml files to handle different environments.</span></span> <span data-ttu-id="8cfa5-205">Zacznij od podstawowego pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-205">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="8cfa5-206">Ten plik podstawowy musi zawierać podstawowe lub statyczne ustawienia konfiguracji, które nie zmieniają się w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-206">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="8cfa5-207">Na przykład eShopOnContainers ma następujący plik docker-compose.yml (uproszczony z mniejszą liczbą usług) jako plik podstawowy.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-207">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with fewer services) as the base file.</span></span>

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

<span data-ttu-id="8cfa5-208">Wartości w podstawowym pliku docker-compose.yml nie powinny ulec zmianie z powodu różnych docelowych środowisk wdrażania.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-208">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="8cfa5-209">Jeśli skupisz się na definicji usługi webmvc, na przykład, można zobaczyć, jak te informacje są tak samo, bez względu na środowisko, które mogą być kierowane.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-209">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="8cfa5-210">Masz następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-210">You have the following information:</span></span>

- <span data-ttu-id="8cfa5-211">Nazwa usługi: webmvc.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-211">The service name: webmvc.</span></span>

- <span data-ttu-id="8cfa5-212">Niestandardowy obraz kontenera: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-212">The container’s custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="8cfa5-213">Polecenie do tworzenia niestandardowego obrazu platformy Docker, wskazujące, którego pliku Dockerfile użyć.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-213">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="8cfa5-214">Zależności od innych usług, więc ten kontener nie uruchamia się, dopóki nie zostały uruchomione inne kontenery zależności.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-214">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="8cfa5-215">Możesz mieć dodatkową konfigurację, ale ważne jest to, że w podstawowym pliku docker-compose.yml, po prostu chcesz ustawić informacje, które są wspólne dla różnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-215">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="8cfa5-216">Następnie w docker-compose.override.yml lub podobnych plików dla produkcji lub przemieszczania, należy umieścić konfigurację, która jest specyficzna dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-216">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="8cfa5-217">Zazwyczaj docker-compose.override.yml jest używany dla środowiska programistycznego, jak w poniższym przykładzie z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-217">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="8cfa5-218">W tym przykładzie konfiguracja zastępowania rozwoju udostępnia niektóre porty do hosta, definiuje zmienne środowiskowe z adresami URL przekierowania i określa parametry połączenia dla środowiska programistycznego.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-218">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="8cfa5-219">Te ustawienia są tylko dla środowiska programistycznego.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-219">These settings are all just for the development environment.</span></span>

<span data-ttu-id="8cfa5-220">Po uruchomieniu `docker-compose up` (lub uruchomieniu go z programu Visual Studio), polecenie odczytuje zastąpienia automatycznie tak, jakby były scalanie obu plików.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-220">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="8cfa5-221">Załóżmy, że chcesz inny plik compose dla środowiska produkcyjnego, z różnymi wartościami konfiguracji, portami lub ciągami połączeń.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-221">Suppose that you want another Compose file for the production environment, with different configuration values, ports, or connection strings.</span></span> <span data-ttu-id="8cfa5-222">Można utworzyć inny plik zastępowania, `docker-compose.prod.yml` taki jak plik o nazwie z różnymi ustawieniami i zmiennymi środowiskowymi.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-222">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="8cfa5-223">Ten plik może być przechowywany w innym repozytorium Git lub zarządzany i zabezpieczony przez inny zespół.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-223">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="8cfa5-224">Jak wdrożyć za pomocą określonego pliku zastępowania</span><span class="sxs-lookup"><span data-stu-id="8cfa5-224">How to deploy with a specific override file</span></span>

<span data-ttu-id="8cfa5-225">Aby użyć wielu zastępowania plików lub zastępowania pliku o innej nazwie, można użyć opcji -f z poleceniem docker-compose i określić pliki.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-225">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="8cfa5-226">Redagowanie scala plików w kolejności, w jakiej są określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-226">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="8cfa5-227">W poniższym przykładzie pokazano, jak wdrożyć za pomocą zastępowania plików.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-227">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="8cfa5-228">Używanie zmiennych środowiskowych w plikach docker-compose</span><span class="sxs-lookup"><span data-stu-id="8cfa5-228">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="8cfa5-229">Jest to wygodne, zwłaszcza w środowiskach produkcyjnych, aby móc uzyskać informacje o konfiguracji ze zmiennych środowiskowych, jak pokazano w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-229">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="8cfa5-230">Zmienną środowiskową w plikach docker-compose można odwoływać\_się do składni ${MY VAR}.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-230">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="8cfa5-231">W poniższym wierszu z pliku docker-compose.prod.yml pokazano, jak odwoływać się do wartości zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-231">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="8cfa5-232">Zmienne środowiskowe są tworzone i inicjowane na różne sposoby, w zależności od środowiska hosta (Linux, Windows, Cloud cluster itp.).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-232">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="8cfa5-233">Jednak wygodnym podejściem jest użycie pliku .env.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-233">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="8cfa5-234">Pliki docker-compose obsługują deklarowanie domyślnych zmiennych środowiskowych w pliku env.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-234">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="8cfa5-235">Te wartości dla zmiennych środowiskowych są wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-235">These values for the environment variables are the default values.</span></span> <span data-ttu-id="8cfa5-236">Można je jednak zastąpić wartościami zdefiniowanymi w każdym środowisku (host OS lub zmienne środowiskowe z klastra).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-236">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="8cfa5-237">Ten plik env umieszcza się w folderze, z którego jest wykonywane polecenie docker-compose.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-237">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="8cfa5-238">W poniższym przykładzie pokazano plik .env, taki jak plik [env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) dla aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-238">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="8cfa5-239">Docker-compose oczekuje, że każdy wiersz w pliku env\>=\<\>będzie w wartości zmiennej formatu \<.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-239">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="8cfa5-240">Wartości ustawione w środowisku czasu wykonywania zawsze zastępują wartości zdefiniowane wewnątrz pliku .env.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-240">The values set in the run-time environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="8cfa5-241">W podobny sposób wartości przekazywane za pośrednictwem argumentów wiersza polecenia zastępują również wartości domyślne ustawione w pliku .env.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-241">In a similar way, values passed via command-line arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8cfa5-242">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="8cfa5-242">Additional resources</span></span>

- <span data-ttu-id="8cfa5-243">**Omówienie kompozycji dokowane** </span><span class="sxs-lookup"><span data-stu-id="8cfa5-243">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="8cfa5-244">**Wiele plików compose** </span><span class="sxs-lookup"><span data-stu-id="8cfa5-244">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="8cfa5-245">Tworzenie zoptymalizowanych obrazów platformy Docker ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8cfa5-245">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="8cfa5-246">Jeśli eksplorujesz platformy Docker i .NET Core na źródłach w Internecie, znajdziesz dockerfiles, które pokazują prostotę tworzenia obrazu platformy Docker, kopiując źródło do kontenera.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-246">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="8cfa5-247">Te przykłady sugerują, że za pomocą prostej konfiguracji, można mieć obraz platformy Docker ze środowiskiem spakowanym z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-247">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="8cfa5-248">W poniższym przykładzie przedstawiono prosty plik dockerfile w tym duchu.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-248">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="8cfa5-249">Dockerfile tak będzie działać.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-249">A Dockerfile like this will work.</span></span> <span data-ttu-id="8cfa5-250">Można jednak znacznie zoptymalizować obrazy, zwłaszcza obrazy produkcyjne.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-250">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="8cfa5-251">W modelu kontenera i mikrousług stale uruchamiasz kontenery.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-251">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="8cfa5-252">Typowy sposób używania kontenerów nie uruchamia ponownie kontenera sypialnego, ponieważ kontener jest jednorazowy.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-252">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="8cfa5-253">Orchestrators (jak Kubernetes i usługi Azure Service Fabric) po prostu utworzyć nowe wystąpienia obrazów.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-253">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="8cfa5-254">Oznacza to, że należy zoptymalizować przez wstępne komppilowanie aplikacji, gdy jest on zbudowany, więc proces tworzenia wystąpienia będzie szybszy.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-254">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="8cfa5-255">Po uruchomieniu kontenera powinien być gotowy do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-255">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="8cfa5-256">Nie należy przywracać i kompilować `dotnet restore` `dotnet build` w czasie wykonywania, przy użyciu i poleceń z dotnet CLI, które, jak widać w wielu blogach o .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-256">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="8cfa5-257">Zespół platformy .NET wykonuje ważną pracę, aby uczynić program .NET Core i ASP.NET Core platformą zoptymalizowaną pod kątem kontenera.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-257">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="8cfa5-258">Nie tylko .NET Core jest lekka struktura z niewielkim rozmiarze pamięci; zespół skupił się na zoptymalizowanych obrazach platformy Docker dla trzech głównych scenariuszy i opublikował je w rejestrze Docker Hub w *dotnet/core,* począwszy od wersji 2.1:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-258">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="8cfa5-259">**Rozwój**: Gdzie priorytetem jest możliwość szybkiego iteracji i debugowania zmian i gdzie rozmiar jest drugorzędny.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-259">**Development**: Where the priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="8cfa5-260">**Kompilacja:** Priorytet jest kompilowanie aplikacji i zawiera pliki binarne i inne zależności w celu optymalizacji plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-260">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="8cfa5-261">**Produkcja:** Gdzie fokus jest szybkie wdrażanie i uruchamianie kontenerów, więc te obrazy są ograniczone do plików binarnych i zawartości potrzebnej do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-261">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content needed to run the application.</span></span>

<span data-ttu-id="8cfa5-262">Aby to osiągnąć, zespół platformy .NET udostępnia cztery podstawowe warianty w [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (w centrum platformy Docker Hub):</span><span class="sxs-lookup"><span data-stu-id="8cfa5-262">To achieve this, the .NET team is providing four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="8cfa5-263">**sdk**: dla scenariuszy rozwoju i budowania</span><span class="sxs-lookup"><span data-stu-id="8cfa5-263">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="8cfa5-264">**aspnet**: dla ASP.NET scenariuszy produkcji</span><span class="sxs-lookup"><span data-stu-id="8cfa5-264">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="8cfa5-265">**środowisko uruchomieniowe:** dla scenariuszy produkcji .NET</span><span class="sxs-lookup"><span data-stu-id="8cfa5-265">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="8cfa5-266">**runtime-deps**: dla scenariuszy produkcyjnych [samodzielnych aplikacji](../../../core/deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="8cfa5-266">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="8cfa5-267">W celu szybszego uruchamiania obrazy środowiska uruchomieniowego automatycznie ustawiają adresy URL aspnetcore\_na port 80 i używają Ngen do tworzenia natywnej pamięci podręcznej obrazów zestawów.</span><span class="sxs-lookup"><span data-stu-id="8cfa5-267">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8cfa5-268">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="8cfa5-268">Additional resources</span></span>

- <span data-ttu-id="8cfa5-269">**Tworzenie zoptymalizowanych obrazów platformy Docker za pomocą ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="8cfa5-269">**Building Optimized Docker Images with ASP.NET Core**</span></span>  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- <span data-ttu-id="8cfa5-270">**Tworzenie obrazów platformy Docker dla aplikacji .NET Core**</span><span class="sxs-lookup"><span data-stu-id="8cfa5-270">**Building Docker Images for .NET Core Applications**</span></span>  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> <span data-ttu-id="8cfa5-271">[Poprzedni](data-driven-crud-microservice.md)
> [następny](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="8cfa5-271">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
