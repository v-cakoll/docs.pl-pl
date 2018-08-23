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
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="035d9-103">Definiowanie aplikacji z wieloma kontenerami za pomocą platformy docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="035d9-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="035d9-104">W tym przewodniku [docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku została wprowadzona w sekcji [krok 4. Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania aplikacji platformy Docker z wieloma kontenerami](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="035d9-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="035d9-105">Istnieją dodatkowe sposoby korzystania z plików docker-compose, które jest wart poznania bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="035d9-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="035d9-106">Na przykład można jawnie opisano, jak chcesz wdrożyć aplikację obsługującą wiele kontenerów w pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="035d9-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="035d9-107">Opcjonalnie można opisać, jak zamierzasz skompilować niestandardowe obrazy usługi Docker.</span><span class="sxs-lookup"><span data-stu-id="035d9-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="035d9-108">(Niestandardowe obrazy platformy Docker może być także kompilowane przy użyciu interfejsu wiersza polecenia platformy Docker).</span><span class="sxs-lookup"><span data-stu-id="035d9-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="035d9-109">Zasadniczo należy zdefiniować wszystkich kontenerów, do których chcesz wdrożyć, a także niektórych parametrów dla każdego wdrożenia kontenera.</span><span class="sxs-lookup"><span data-stu-id="035d9-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="035d9-110">Po utworzeniu pliku opisu wdrożenia z wieloma kontenerami, można wdrożyć całego rozwiązania w ramach jednej akcji dzięki [narzędzia docker compose się](https://docs.docker.com/compose/overview/) interfejsu wiersza polecenia, albo wdrożyć go sposób niewidoczny dla użytkownika w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="035d9-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="035d9-111">W przeciwnym razie należy użyć interfejsu wiersza polecenia platformy Docker do wdrożenia kontenera przez kontener kilku kroków przy użyciu platformy docker, uruchom polecenie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="035d9-112">W związku z tym każda usługa zdefiniowane w docker-compose.yml należy określić dokładnie jeden obraz lub kompilacji.</span><span class="sxs-lookup"><span data-stu-id="035d9-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="035d9-113">Inne klucze są opcjonalne i są analogiczne do ich platformy docker, uruchom odpowiedniki wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-113">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="035d9-114">Poniższego kodu YAML jest definicja możliwe globalnych, ale pojedynczego pliku docker-compose.yml dla przykładu w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="035d9-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="035d9-115">To nie jest plikiem docker-compose rzeczywistych, w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="035d9-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="035d9-116">Zamiast tego jest to wersja uproszczony i skonsolidowane w jednym pliku, który nie jest najlepszy sposób pracy z plików docker-compose, ponieważ zostaną wyjaśnione później.</span><span class="sxs-lookup"><span data-stu-id="035d9-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="035d9-117">Klucz główny, w tym pliku jest usług.</span><span class="sxs-lookup"><span data-stu-id="035d9-117">The root key in this file is services.</span></span> <span data-ttu-id="035d9-118">W ramach tego klucza, należy zdefiniować usług, należy wdrożyć i uruchomić podczas wykonywania narzędzia docker compose polecenia lub podczas wdrażania w programie Visual Studio przy użyciu tego pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="035d9-118">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="035d9-119">W takim przypadku plik docker-compose.yml ma wiele usług zdefiniowane, zgodnie z opisem w poniższej liście.</span><span class="sxs-lookup"><span data-stu-id="035d9-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="035d9-120">webmvc kontenera w tym aplikacji ASP.NET Core MVC, korzystanie z mikrousług from C po stronie serwera\#</span><span class="sxs-lookup"><span data-stu-id="035d9-120">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="035d9-121">Catalog.API kontenera w tym mikrousług katalogu ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="035d9-121">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="035d9-122">Ordering.API kontenera w tym mikrousług porządkowanie Core Web API platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="035d9-122">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="035d9-123">SQL.Data kontenera z programem SQL Server dla systemu Linux, zawierający bazy danych mikrousług</span><span class="sxs-lookup"><span data-stu-id="035d9-123">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="035d9-124">basket.API kontenera przy użyciu mikrousług koszyka ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="035d9-124">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="035d9-125">basket.Data kontenera z systemem usługi REDIS cache service z bazą danych koszyka jako pamięci podręcznej REDIS</span><span class="sxs-lookup"><span data-stu-id="035d9-125">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="035d9-126">Prosty kontener interfejsu API usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="035d9-126">A simple Web Service API container</span></span>

<span data-ttu-id="035d9-127">Koncentrujących się na jednym kontenerze, catalog.api container mikrousług ma proste definicji:</span><span class="sxs-lookup"><span data-stu-id="035d9-127">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="035d9-128">Ta usługa konteneryzowanych ma podstawowe następującą konfigurację:</span><span class="sxs-lookup"><span data-stu-id="035d9-128">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="035d9-129">Jest ona oparta na obrazie eshop/catalog.api niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="035d9-129">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="035d9-130">Dla sake dla uproszczenia nie istnieje żadne kompilacji: ustawienia w pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="035d9-130">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="035d9-131">Oznacza to, że obraz muszą wcześniej utworzone (z kompilacji platformy docker) lub zostały pobrane (za pomocą polecenie docker pull) z dowolnego rejestru platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="035d9-131">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="035d9-132">Definiuje zmienną środowiskową o nazwie ConnectionString przy użyciu parametrów połączenia używany przez program Entity Framework do dostępu do wystąpienia programu SQL Server, który zawiera model danych wykazu.</span><span class="sxs-lookup"><span data-stu-id="035d9-132">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="035d9-133">W takim przypadku ten sam kontener programu SQL Server zawiera wiele baz danych.</span><span class="sxs-lookup"><span data-stu-id="035d9-133">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="035d9-134">W związku z tym potrzebujesz mniejszej ilości pamięci w komputerze deweloperskim dla platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="035d9-134">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="035d9-135">Jednak możesz również wdrożyć jeden kontener programu SQL Server dla każdej bazy danych z mikrousług.</span><span class="sxs-lookup"><span data-stu-id="035d9-135">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="035d9-136">Nazwa programu SQL Server jest sql.data, który ma taką samą nazwę, używany do kontenera, w którym jest uruchomione wystąpienie programu SQL Server dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="035d9-136">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="035d9-137">Jest to wygodne; możliwości używania to rozpoznawanie nazw (wewnętrzne hosta platformy Docker) zostanie rozwiązany adresu sieciowego, dzięki czemu nie trzeba znać wewnętrznego adresu IP dla kontenerów, do których uzyskujesz dostęp do innych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="035d9-137">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="035d9-138">Ponieważ ciąg połączenia jest zdefiniowana przez zmienną środowiskową, można ustawić tę zmienną za pomocą innego mechanizmu, a w innym czasie.</span><span class="sxs-lookup"><span data-stu-id="035d9-138">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="035d9-139">Na przykład można ustawić parametrów połączenia różnych podczas wdrażania do produkcji w ostatnim hostów lub wykonując z potoków ciągłej integracji/ciągłego wdrażania w usłudze VSTS lub preferowanego systemu metodyki DevOps.</span><span class="sxs-lookup"><span data-stu-id="035d9-139">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="035d9-140">Udostępnia ona port 80 dla wewnętrznego dostęp do usługi catalog.api w ramach hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="035d9-140">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="035d9-141">Host jest obecnie Maszynę wirtualną systemu Linux, ponieważ jest ona oparta na obrazie platformy Docker dla systemu Linux, ale można skonfigurować kontenera dla obrazu Windows należy zamiast tego uruchomić.</span><span class="sxs-lookup"><span data-stu-id="035d9-141">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="035d9-142">Przekazuje narażonych port 80 w kontenerze do portu 5101 na maszynie hosta platformy Docker (maszyny Wirtualnej systemu Linux).</span><span class="sxs-lookup"><span data-stu-id="035d9-142">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="035d9-143">Łączy on usługę sieci web w usłudze sql.data (wystąpienie programu SQL Server dla bazy danych systemu Linux uruchomiony w kontenerze).</span><span class="sxs-lookup"><span data-stu-id="035d9-143">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="035d9-144">Po określeniu tej zależności, kontener catalog.api nie uruchomi kontener sql.data został już uruchomiony; jest to ważne, ponieważ catalog.api musi mieć bazy danych programu SQL Server i uruchamianie najpierw.</span><span class="sxs-lookup"><span data-stu-id="035d9-144">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="035d9-145">Jednak tego rodzaju zależności kontenera nie jest wystarczające w wielu przypadkach, ponieważ Docker testy tylko na poziomie kontenera.</span><span class="sxs-lookup"><span data-stu-id="035d9-145">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="035d9-146">Czasami usługi (w tym przypadku SQL Server) może być nadal nie będzie gotowe, więc zaleca się, aby zaimplementować logikę ponawiania próby z wykorzystaniem wykładniczego wycofywania w mikrousługi klienta.</span><span class="sxs-lookup"><span data-stu-id="035d9-146">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="035d9-147">Dzięki temu, jeśli kontener zależność nie jest gotowy, przez krótki czas aplikacji nadal będą odporne na błędy.</span><span class="sxs-lookup"><span data-stu-id="035d9-147">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="035d9-148">Jest skonfigurowana, aby zezwolić na dostęp do zewnętrznych serwerów: nadmiarowe\_hostów ustawienie umożliwia dostęp do zewnętrznych serwerach lub maszynach poza hosta platformy Docker (czyli poza domyślne maszyny Wirtualnej systemu Linux, czyli programowania Docker hosta), takie jak lokalna baza SQL Wystąpienie serwera na komputerze.</span><span class="sxs-lookup"><span data-stu-id="035d9-148">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="035d9-149">Istnieją także inne, bardziej zaawansowane ustawienia docker-compose.yml, które omówimy w kolejnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="035d9-149">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="035d9-150">Przy użyciu plików docker-compose pod kątem wielu środowisk</span><span class="sxs-lookup"><span data-stu-id="035d9-150">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="035d9-151">Pliki docker-compose.yml są plikami definicji i mogą być używane przez wiele infrastruktury, które zrozumieć tego formatu.</span><span class="sxs-lookup"><span data-stu-id="035d9-151">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="035d9-152">Narzędzie to najprostszy jest platformy docker-compose polecenia, ale innych narzędzi, takich jak koordynatorów (na przykład, Docker Swarm) również zrozumienie tego pliku.</span><span class="sxs-lookup"><span data-stu-id="035d9-152">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="035d9-153">W związku z tym, za pomocą platformy docker-compose polecenia można wskazać następujące główne scenariusze.</span><span class="sxs-lookup"><span data-stu-id="035d9-153">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="035d9-154">Środowiska deweloperskie</span><span class="sxs-lookup"><span data-stu-id="035d9-154">Development environments</span></span>

<span data-ttu-id="035d9-155">Podczas tworzenia aplikacji jest ważne, aby można było uruchomić aplikację w środowisku izolowanym rozwoju.</span><span class="sxs-lookup"><span data-stu-id="035d9-155">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="035d9-156">Możesz użyć narzędzia docker-compose polecenia interfejsu wiersza polecenia do tworzenia tego środowiska, lub użyć programu Visual Studio, która używa aparatu docker-compose dzieje się w tle.</span><span class="sxs-lookup"><span data-stu-id="035d9-156">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="035d9-157">Plik docker-compose.yml pozwala na konfigurowanie i udokumentować wszystkie usługi zależności aplikacji (inne usługi, pamięci podręcznej, baz danych, kolejki itd.).</span><span class="sxs-lookup"><span data-stu-id="035d9-157">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="035d9-158">Przy użyciu interfejsu wiersza polecenia platformy docker-compose, możesz utworzyć i uruchomić co najmniej jeden kontener dla poszczególnych zależności za pomocą jednego polecenia (docker-compose się).</span><span class="sxs-lookup"><span data-stu-id="035d9-158">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="035d9-159">Pliki docker-compose.yml znajdują się pliki konfiguracyjne interpretowane przez aparat platformy Docker, ale także służyć jako pliki dokumentacji wygodne temat układu aplikacji z wieloma kontenerami.</span><span class="sxs-lookup"><span data-stu-id="035d9-159">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="035d9-160">Środowisk testowych</span><span class="sxs-lookup"><span data-stu-id="035d9-160">Testing environments</span></span>

<span data-ttu-id="035d9-161">Ważnym dowolnego ciągłe wdrażanie (CD) lub procesu ciągłej integracji (CI) są testy jednostkowe i testy integracji.</span><span class="sxs-lookup"><span data-stu-id="035d9-161">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="035d9-162">Tych zautomatyzowanych testów wymagają izolowanym środowisku, więc one nie ma wpływ na użytkowników lub innych zmian w danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="035d9-162">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="035d9-163">Przy użyciu narzędzia Docker Compose możesz tworzyć i niszczyć tego środowiska izolowanego w bardzo prosty sposób za pomocą kilku poleceń z wiersza polecenia lub skryptów, takich jak następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="035d9-163">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="035d9-164">Wdrożenia produkcyjne</span><span class="sxs-lookup"><span data-stu-id="035d9-164">Production deployments</span></span>

<span data-ttu-id="035d9-165">Umożliwia także tworzenia do wdrażania na zdalny aparat platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="035d9-165">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="035d9-166">Typowy przypadek jest wdrożenie w ramach pojedynczego wystąpienia hosta platformy Docker (produkcyjna maszyna wirtualna lub udostępniane z serwera, takie jak [maszyny platformy Docker](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="035d9-166">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="035d9-167">Jednak może być również cały [Docker Swarm](https://docs.docker.com/swarm/overview/) klastra, ponieważ klastry są również zgodne z pliki docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="035d9-167">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="035d9-168">Jeśli używasz innych orchestrator (usługi Azure Service Fabric, Mesos DC/OS, Kubernetes itp.), może być konieczne dodać ustawienia konfiguracji instalacji i metadanych, podobnie jak w docker-compose.yml, ale w formacie wymaganym przez program orchestrator.</span><span class="sxs-lookup"><span data-stu-id="035d9-168">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="035d9-169">W każdym przypadku docker-compose jest wygodne narzędzie i metadanych formatu dla przepływów pracy programowania, testowania i produkcji, mimo że przepływ pracy produkcji mogą się różnić na programu orchestrator, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="035d9-169">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="035d9-170">Przy użyciu wielu plików docker-compose do obsługi wielu środowisk</span><span class="sxs-lookup"><span data-stu-id="035d9-170">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="035d9-171">Gdy przeznaczonych dla różnych środowisk, należy użyć wielu tworzą pliki.</span><span class="sxs-lookup"><span data-stu-id="035d9-171">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="035d9-172">Dzięki temu można tworzyć wiele wariantów konfiguracji, w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="035d9-172">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="035d9-173">Zastępowanie pliku podstawowego docker-compose</span><span class="sxs-lookup"><span data-stu-id="035d9-173">Overriding the base docker-compose file</span></span>

<span data-ttu-id="035d9-174">Można użyć pliku docker-compose.yml w jednym, jak uproszczone przykłady zamieszczone w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="035d9-174">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="035d9-175">Nie jest, jednak zalecane w przypadku większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="035d9-175">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="035d9-176">Domyślnie Compose odczytuje dwa pliki docker-compose.yml i plik docker-compose.override.yml opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="035d9-176">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="035d9-177">Jak pokazano w rysunek 8-11, gdy są przy użyciu programu Visual Studio i włączenie również obsługę platformy Docker, Visual Studio tworzy plik dodatkowe compose.ci.build,yml platformy docker do użycia z potoków ciągłej integracji/ciągłego Dostarczania, takich jak w usłudze VSTS.</span><span class="sxs-lookup"><span data-stu-id="035d9-177">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in VSTS.</span></span>

![](./media/image12.png)

<span data-ttu-id="035d9-178">**Rysunek 8-11**.</span><span class="sxs-lookup"><span data-stu-id="035d9-178">**Figure 8-11**.</span></span> <span data-ttu-id="035d9-179">docker-compose plików w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="035d9-179">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="035d9-180">Możesz edytować pliki docker-compose w dowolnym edytorze, np. Visual Studio Code lub Sublime i uruchomić aplikację za pomocą platformy docker-compose up polecenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-180">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="035d9-181">Zgodnie z Konwencją pliku docker-compose.yml zawiera podstawowej konfiguracji i inne statyczne ustawienia.</span><span class="sxs-lookup"><span data-stu-id="035d9-181">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="035d9-182">Czy oznacza to, że konfiguracja usługi nie należy zmieniać w zależności od środowiska wdrażania przeznaczonych do pracy.</span><span class="sxs-lookup"><span data-stu-id="035d9-182">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="035d9-183">Pliku docker-compose.override.yml sugeruje nazwa, zawiera ustawienia konfiguracji, które zastępują konfiguracji podstawowej, takie jak konfiguracja, który zależy od środowiska wdrażania.</span><span class="sxs-lookup"><span data-stu-id="035d9-183">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="035d9-184">Również może mieć wiele plików przesłonięcie pod różnymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="035d9-184">You can have multiple override files with different names also.</span></span> <span data-ttu-id="035d9-185">Pliki zastąpienie zwykle zawierają dodatkowe informacje wymagane przez aplikację, ale określonego środowiska lub do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-185">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="035d9-186">Przeznaczone dla wielu środowisk</span><span class="sxs-lookup"><span data-stu-id="035d9-186">Targeting multiple environments</span></span>

<span data-ttu-id="035d9-187">Typowym przypadkiem użycia jest podczas definiowania wielu tworzą pliki tak możliwe jest Określanie wielu środowisk, takich jak środowiska produkcyjnego, przemieszczania, ciągłej integracji i programowania.</span><span class="sxs-lookup"><span data-stu-id="035d9-187">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="035d9-188">Aby obsługiwać te różnice, możesz podzielić konfigurację Compose na wiele plików, jak pokazano na rysunku 8-12.</span><span class="sxs-lookup"><span data-stu-id="035d9-188">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="035d9-189">**Rysunek 8-12**.</span><span class="sxs-lookup"><span data-stu-id="035d9-189">**Figure 8-12**.</span></span> <span data-ttu-id="035d9-190">Wiele plików docker-compose zastępowanie wartości z pliku docker-compose.yml podstawowy</span><span class="sxs-lookup"><span data-stu-id="035d9-190">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="035d9-191">Możesz uruchomić za pomocą pliku docker-compose.yml podstawowej.</span><span class="sxs-lookup"><span data-stu-id="035d9-191">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="035d9-192">Ten plik podstawowy musi zawierają ustawienia konfiguracji bazowej lub statycznych, które nie zmieniają się w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="035d9-192">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="035d9-193">Na przykład ramach aplikacji eShopOnContainers ma następujący plik docker-compose.yml jako pliku podstawowego.</span><span class="sxs-lookup"><span data-stu-id="035d9-193">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

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

<span data-ttu-id="035d9-194">Wartości w pliku docker-compose.yml podstawowego nie należy zmieniać ze względu na inną docelową wdrożenia środowiska.</span><span class="sxs-lookup"><span data-stu-id="035d9-194">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="035d9-195">Jeśli możesz skoncentrować się na webmvc definicji usługi, na przykład widać jak te informacje są bardzo podobne do niezależnie od tego, jakiego środowiska mogą być przeznaczone dla.</span><span class="sxs-lookup"><span data-stu-id="035d9-195">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="035d9-196">Masz następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="035d9-196">You have the following information:</span></span>

-   <span data-ttu-id="035d9-197">Nazwa usługi: webmvc.</span><span class="sxs-lookup"><span data-stu-id="035d9-197">The service name: webmvc.</span></span>

-   <span data-ttu-id="035d9-198">Niestandardowy obraz kontenera: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="035d9-198">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="035d9-199">Polecenie do tworzenia niestandardowego obrazu platformy Docker, wskazującą, które pliku Dockerfile do użycia.</span><span class="sxs-lookup"><span data-stu-id="035d9-199">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="035d9-200">W zależności od innych usług, dzięki czemu ten kontener nie uruchamia się, dopóki nie uruchomiono innych kontenerów zależności.</span><span class="sxs-lookup"><span data-stu-id="035d9-200">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="035d9-201">Masz dodatkowe czynności konfiguracyjne, ale istotną kwestią jest, że w pliku docker-compose.yml podstawowego, po prostu chcesz ustawić informacje, które są wspólne w środowiskach.</span><span class="sxs-lookup"><span data-stu-id="035d9-201">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="035d9-202">Następnie w docker-compose.override.yml lub podobnych plików do produkcyjnego lub tymczasowego, należy umieścić konfiguracji, które są specyficzne dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="035d9-202">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="035d9-203">Zazwyczaj docker-compose.override.yml jest używany dla swojego środowiska programowania, jak w poniższym przykładzie w ramach aplikacji eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="035d9-203">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="035d9-204">W tym przykładzie rozwoju zastępczą konfigurację ujawnia Niektóre porty do hosta, definiuje zmiennych środowiskowych poleceniem przekierowania adresów URL i określa parametry połączenia dla środowiska programistycznego.</span><span class="sxs-lookup"><span data-stu-id="035d9-204">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="035d9-205">Te ustawienia dotyczą wszystkich tylko w środowisku deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="035d9-205">These settings are all just for the development environment.</span></span>

<span data-ttu-id="035d9-206">Po uruchomieniu `docker-compose up` (lub uruchomić go w programie Visual Studio), polecenie odczytuje automatycznie zastąpienia, tak jakby były scalania, oba pliki.</span><span class="sxs-lookup"><span data-stu-id="035d9-206">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="035d9-207">Załóżmy, że ma inny plik Compose w środowisku produkcyjnym, przy użyciu wartości różnych konfiguracji, portów lub parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-207">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="035d9-208">Możesz utworzyć inny plik zastąpienie, np. plik o nazwie `docker-compose.prod.yml` z różnymi ustawieniami i zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="035d9-208">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="035d9-209">Ten plik, mogą być przechowywane w różnych repozytorium Git lub zarządzane i chronione przez inny zespół.</span><span class="sxs-lookup"><span data-stu-id="035d9-209">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="035d9-210">Jak wdrożyć za pomocą pliku określone zastąpienia</span><span class="sxs-lookup"><span data-stu-id="035d9-210">How to deploy with a specific override file</span></span>

<span data-ttu-id="035d9-211">Aby korzystać z wielu plików zastąpienia lub zastąpienie pliku o innej nazwie, można użyć opcji -f, przy użyciu narzędzia docker-compose polecenia i określić pliki.</span><span class="sxs-lookup"><span data-stu-id="035d9-211">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="035d9-212">Tworzenie plików scalenia w kolejności, w której są one określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-212">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="035d9-213">Poniższy przykład pokazuje, jak wdrożyć zastąpienie plików.</span><span class="sxs-lookup"><span data-stu-id="035d9-213">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="035d9-214">Korzystanie ze zmiennych środowiskowych w plików docker-compose</span><span class="sxs-lookup"><span data-stu-id="035d9-214">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="035d9-215">Jest to wygodne, szczególnie w środowiskach produkcyjnych, aby można było pobrać informacji o konfiguracji ze zmiennych środowiskowych, jak firma Microsoft ma w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="035d9-215">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="035d9-216">Odwołania zmiennej środowiskowej w plikach docker-compose przy użyciu składni \${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="035d9-216">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="035d9-217">Następujący wiersz z pliku docker-compose.prod.yml pokazuje, jak odwoływać się do wartości zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="035d9-217">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="035d9-218">Zmienne środowiskowe są tworzone i inicjowane na różne sposoby, w zależności od środowiska hosta (Linux, Windows, klaster Cloud itp.).</span><span class="sxs-lookup"><span data-stu-id="035d9-218">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="035d9-219">Jednak wygodne podejściem jest użycie pliku env.</span><span class="sxs-lookup"><span data-stu-id="035d9-219">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="035d9-220">Obsługa plików docker-compose deklarowanie domyślną zmiennych środowiskowych w pliku env.</span><span class="sxs-lookup"><span data-stu-id="035d9-220">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="035d9-221">Wartości domyślne są to wartości zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="035d9-221">These values for the environment variables are the default values.</span></span> <span data-ttu-id="035d9-222">Jednak mogą być zastąpione przez wartości, które może być zdefiniowane we wszystkich środowiskach (system operacyjny hosta lub zmiennych środowiskowych z klastra).</span><span class="sxs-lookup"><span data-stu-id="035d9-222">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="035d9-223">Umieść ten plik ENV w folderze gdzie narzędzia docker compose polecenie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="035d9-223">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="035d9-224">W poniższym przykładzie pokazano plik ENV, takich jak [ENV](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pliku dla aplikacji w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="035d9-224">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="035d9-225">Narzędzia docker compose oczekuje, że każdy wiersz w pliku ENV, aby być w formacie &lt;zmiennej&gt;=&lt;wartość&gt;.</span><span class="sxs-lookup"><span data-stu-id="035d9-225">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="035d9-226">Należy pamiętać, że wartości ustawione w środowisku uruchomieniowym zawsze zastąpić wartości zdefiniowanych w pliku env.</span><span class="sxs-lookup"><span data-stu-id="035d9-226">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="035d9-227">W podobny sposób wartości przekazane za pośrednictwem argumentów wiersza polecenia Zastąp wartości domyślne ustawione w pliku env.</span><span class="sxs-lookup"><span data-stu-id="035d9-227">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="035d9-228">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="035d9-228">Additional resources</span></span>

-   <span data-ttu-id="035d9-229">**Przegląd platformy Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="035d9-229">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="035d9-230">**Wiele pliki narzędzia Compose**
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="035d9-230">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="035d9-231">Tworzenie zoptymalizowanych obrazów platformy Docker programu ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="035d9-231">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="035d9-232">Jeśli platforma Docker i platformy .NET Core analizujesz źródeł w Internecie, można znaleźć plików Dockerfile, które przedstawiają uproszczenia tworzenia obrazu platformy Docker, kopiując źródła w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="035d9-232">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="035d9-233">Te przykłady sugeruje, że za pomocą prostej konfiguracji, masz obraz platformy Docker ze środowiskiem spakować z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="035d9-233">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="035d9-234">Poniższy przykład pokazuje prosty plik Dockerfile, w tym względzie.</span><span class="sxs-lookup"><span data-stu-id="035d9-234">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="035d9-235">Plik Dockerfile, takich jak to będzie działać.</span><span class="sxs-lookup"><span data-stu-id="035d9-235">A Dockerfile like this will work.</span></span> <span data-ttu-id="035d9-236">Można jednak znacznie zoptymalizować obrazów, szczególnie obrazów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="035d9-236">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="035d9-237">W modelu mikrousług i kontenerów, są stale uruchamianie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="035d9-237">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="035d9-238">Typowy sposób korzystania z kontenerów nie jest ponownie uruchamiany kontener uśpiony, ponieważ kontener jest możliwe do likwidacji.</span><span class="sxs-lookup"><span data-stu-id="035d9-238">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="035d9-239">Koordynatorów (np. rozwiązania Docker Swarm, Kubernetes, DCOS lub Azure Service Fabric) jest po prostu utworzyć nowe wystąpienia obrazów.</span><span class="sxs-lookup"><span data-stu-id="035d9-239">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="035d9-240">Oznacza to, że będziesz potrzebować Optymalizowanie wstępnej kompilacji aplikacji, podczas tworzenia procesu tworzenia wystąpienia będą szybciej.</span><span class="sxs-lookup"><span data-stu-id="035d9-240">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="035d9-241">Po uruchomieniu kontenera, powinno być gotowe do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="035d9-241">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="035d9-242">Nie należy przywrócić i kompilacji w czasie wykonywania, za pomocą polecenia dotnet restore dotnet kompilacji i poleceń interfejsu wiersza polecenia platformy dotnet, jak widać w wielu wpisów w blogu o platformy .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="035d9-242">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="035d9-243">Zespołem platformy .NET ma zostały wykonywania pracy zapewnienie platformy .NET Core i ASP.NET Core platforma zoptymalizowane pod kątem kontenera.</span><span class="sxs-lookup"><span data-stu-id="035d9-243">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="035d9-244">Nie tylko to platformy .NET Core uproszczone środowisko z zużycie pamięci; zespół koncentruje się na wydajności uruchamiania i generowane niektóre zoptymalizowane obrazy platformy Docker, takie jak [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obraz dostępne pod adresem [usługi Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), w porównaniu ze zwykłych [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) lub [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) obrazów.</span><span class="sxs-lookup"><span data-stu-id="035d9-244">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="035d9-245">[Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obraz oferuje automatyczne ustawienie aspnetcore\_adresy URL do portu 80 oraz wstępnie ngend pamięci podręcznej zestawów; oba te ustawienia spowodować szybsze uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="035d9-245">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="035d9-246">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="035d9-246">Additional resources</span></span>

-   <span data-ttu-id="035d9-247">**Tworzenie zoptymalizowane pod kątem obrazów platformy Docker z platformą ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="035d9-247">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="035d9-248">Tworzenie aplikacji z kontenera kompilacji (CI)</span><span class="sxs-lookup"><span data-stu-id="035d9-248">Building the application from a build (CI) container</span></span>

<span data-ttu-id="035d9-249">Kolejną korzyścią platformy Docker jest tworzyć aplikacji w kontenerze, wstępnie skonfigurowane, jak pokazano w rysunku 8-13, dzięki czemu nie musisz utworzyć maszynę kompilacji lub maszyny Wirtualnej do budowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="035d9-249">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="035d9-250">Możesz użyć lub testowania tego kontenera kompilacji, uruchamiając go na komputerze deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="035d9-250">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="035d9-251">Ale co to jest jeszcze bardziej interesujące może użyć tego samego kontenera kompilacji z potokiem ciągłej integracji (ciągła integracja).</span><span class="sxs-lookup"><span data-stu-id="035d9-251">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="035d9-252">**Rysunek 8-13**.</span><span class="sxs-lookup"><span data-stu-id="035d9-252">**Figure 8-13**.</span></span> <span data-ttu-id="035d9-253">Kompilowanie plików binarnych .NET kompilacji — kontener platformy docker</span><span class="sxs-lookup"><span data-stu-id="035d9-253">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="035d9-254">W tym scenariuszu firma Microsoft zapewnia [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) obrazu, który umożliwia kompilowanie i tworzenie aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="035d9-254">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="035d9-255">Dane wyjściowe są umieszczane w obrazu na podstawie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu, który jest obrazem zoptymalizowane środowiska uruchomieniowego, zauważyć, wcześniej.</span><span class="sxs-lookup"><span data-stu-id="035d9-255">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="035d9-256">Obraz aspnetcore-build zawiera wszystko, co jest potrzebne do kompilowania aplikacji platformy ASP.NET Core, w tym .NET Core, zestawu SDK platformy ASP.NET, npm, Bower, Gulp, itp.</span><span class="sxs-lookup"><span data-stu-id="035d9-256">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="035d9-257">Potrzebujemy tych zależności w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="035d9-257">We need these dependencies at build time.</span></span> <span data-ttu-id="035d9-258">Jednak firma Microsoft nie chcesz wykonać je z aplikacji w czasie wykonywania, ponieważ może to spowodować obraz niepotrzebnie.</span><span class="sxs-lookup"><span data-stu-id="035d9-258">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="035d9-259">W ramach aplikacji eShopOnContainers aplikacji, można skompilować aplikację z kontenera, uruchamiając tylko następujące platformy docker-compose polecenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-259">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="035d9-260">Rysunek 8 – 14 pokazuje to polecenie działa w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-260">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="035d9-261">**Rysunek 8 – 14.**</span><span class="sxs-lookup"><span data-stu-id="035d9-261">**Figure 8-14.**</span></span> <span data-ttu-id="035d9-262">Tworzenie aplikacji .NET w kontenerze</span><span class="sxs-lookup"><span data-stu-id="035d9-262">Building your .NET application from a container</span></span>

<span data-ttu-id="035d9-263">Jak widać, kontener, który jest uruchomiony jest kompilacji ci\_1 kontenera.</span><span class="sxs-lookup"><span data-stu-id="035d9-263">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="035d9-264">Zależy to obraz aspnetcore-build, aby go można skompilować i utworzyć całej aplikacji w tym kontenerze, a nie z Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="035d9-264">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="035d9-265">Oznacza to Dlaczego w rzeczywistości jest tworzenie i kompilowanie projektów .NET Core w systemie Linux — ponieważ tego kontenera jest uruchomiona na hoście platformy Docker w systemie Linux domyślne.</span><span class="sxs-lookup"><span data-stu-id="035d9-265">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="035d9-266">[Docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) pliku obrazu (część pakietu w ramach aplikacji eShopOnContainers) zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="035d9-266">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="035d9-267">Widać, że uruchomieniu kontenera kompilacji przy użyciu [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) obrazu.</span><span class="sxs-lookup"><span data-stu-id="035d9-267">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

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

* <span data-ttu-id="035d9-268">Począwszy od **.NET Core 2.0**, `dotnet restore` polecenie jest wykonywane automatycznie po `dotnet publish` polecenie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="035d9-268">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="035d9-269">Po skonfigurowaniu i uruchomieniu kontenera kompilacji działa przywracania dotnet zestawu SDK platformy .NET i dotnet publikowania poleceń dla wszystkich projektów w rozwiązaniu aby można było skompilować bitów .NET.</span><span class="sxs-lookup"><span data-stu-id="035d9-269">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="035d9-270">W tym przypadku ponieważ w ramach aplikacji eShopOnContainers ma również SPA na podstawie TypeScript i Angular w przypadku kodu klienta, również musi ona Sprawdź zależności języka JavaScript za pomocą pakietu npm, ale ta akcja nie jest powiązana z bitami .NET.</span><span class="sxs-lookup"><span data-stu-id="035d9-270">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="035d9-271">Dotnet, jak opublikować polecenia kompilacji i publikuje skompilowanych danych wyjściowych w folderze każdego projektu... folder /obj/Docker/publish, jak pokazano w rysunek 8 – 15.</span><span class="sxs-lookup"><span data-stu-id="035d9-271">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="035d9-272">**Rysunek 8 – 15.**</span><span class="sxs-lookup"><span data-stu-id="035d9-272">**Figure 8-15.**</span></span> <span data-ttu-id="035d9-273">Pliki binarne wygenerowane przez dotnet polecenia publikowania</span><span class="sxs-lookup"><span data-stu-id="035d9-273">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="035d9-274">Tworzenie obrazów platformy Docker z interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="035d9-274">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="035d9-275">Po opublikowaniu dane wyjściowe aplikacji do powiązanych folderów (w ramach każdego projektu), następnym krokiem jest faktycznie kompilowanie obrazów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="035d9-275">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="035d9-276">W tym celu należy użyć kompilacji docker-compose i docker-compose się polecenia, jak pokazano w rysunek 8-16.</span><span class="sxs-lookup"><span data-stu-id="035d9-276">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="035d9-277">**Rysunek 8-16.**</span><span class="sxs-lookup"><span data-stu-id="035d9-277">**Figure 8-16.**</span></span> <span data-ttu-id="035d9-278">Tworzenie obrazów platformy Docker i uruchamianie kontenerów</span><span class="sxs-lookup"><span data-stu-id="035d9-278">Building Docker images and running the containers</span></span>

<span data-ttu-id="035d9-279">Na rysunku 8-17 można zobaczyć jak docker-compose tworzyć polecenia uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="035d9-279">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="035d9-280">**Rysunek 8-17**.</span><span class="sxs-lookup"><span data-stu-id="035d9-280">**Figure 8-17**.</span></span> <span data-ttu-id="035d9-281">Tworzenie obrazów platformy Docker z platformą docker-compose polecenia kompilacji</span><span class="sxs-lookup"><span data-stu-id="035d9-281">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="035d9-282">Różnica między docker-compose kompilacji i narzędzia docker compose zapasowej poleceń jest to, że narzędzia docker compose zarówno kompilacje i uruchomieniu obrazami.</span><span class="sxs-lookup"><span data-stu-id="035d9-282">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="035d9-283">Gdy używasz programu Visual Studio, wszystkie te kroki są wykonywane w sposób niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="035d9-283">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="035d9-284">Visual Studio kompiluje aplikację platformy .NET, tworzy obrazy platformy Docker i służy do wdrażania kontenerów do hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="035d9-284">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="035d9-285">Program Visual Studio udostępnia dodatkowe funkcje, takie jak możliwość debugowania kontenery uruchomione na platformie Docker, bezpośrednio z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="035d9-285">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="035d9-286">Ogólny takeway w tym miejscu jest, że jesteś w stanie do budowania aplikacji, w taki sam sposób potok ciągłej integracji/ciągłego wdrażania należy ją skompilować — z kontenera zamiast z komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="035d9-286">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="035d9-287">Po obrazów utworzonych, następnie wystarczy do uruchomienia obrazów platformy Docker przy użyciu platformy docker-compose się polecenia.</span><span class="sxs-lookup"><span data-stu-id="035d9-287">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="035d9-288">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="035d9-288">Additional resources</span></span>

-   <span data-ttu-id="035d9-289">**Tworzenia usługi bits z kontenera: konfigurowanie rozwiązania w ramach aplikacji eShopOnContainers w środowisku Windows interfejsu wiersza polecenia (wiersz polecenia dotnet, interfejsu wiersza polecenia platformy Docker i program VS Code)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, — Docker — interfejs wiersza polecenia platformy- i -VS-kodu)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="035d9-289">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="035d9-290">[Poprzednie](data-driven-crud-microservice.md)
[dalej](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="035d9-290">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
