---
title: Definiowanie aplikacji z wieloma kontenerami za pomocą pliku docker-compose.yml
description: Jak określić kompozycji mikrousług dla aplikacji z wieloma kontenerami w celu za pomocą platformy docker-compose.yml.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 4f4918a6f26a617fad38c7955415c4ff559a9187
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920782"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="e771a-103">Definiowanie aplikacji z wieloma kontenerami za pomocą pliku docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="e771a-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="e771a-104">W tym przewodniku [docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku została wprowadzona w sekcji [krok 4. Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania aplikacji platformy Docker z wieloma kontenerami](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="e771a-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="e771a-105">Istnieją dodatkowe sposoby korzystania z plików docker-compose, które jest wart poznania bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="e771a-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="e771a-106">Na przykład można jawnie opisano, jak chcesz wdrożyć aplikację obsługującą wiele kontenerów w pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="e771a-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="e771a-107">Opcjonalnie można opisać, jak zamierzasz skompilować niestandardowe obrazy usługi Docker.</span><span class="sxs-lookup"><span data-stu-id="e771a-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="e771a-108">(Niestandardowe obrazy platformy Docker może być także kompilowane przy użyciu interfejsu wiersza polecenia platformy Docker).</span><span class="sxs-lookup"><span data-stu-id="e771a-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="e771a-109">Zasadniczo należy zdefiniować wszystkich kontenerów, do których chcesz wdrożyć, a także niektórych parametrów dla każdego wdrożenia kontenera.</span><span class="sxs-lookup"><span data-stu-id="e771a-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="e771a-110">Po utworzeniu pliku opisu wdrożenia z wieloma kontenerami, można wdrożyć całego rozwiązania w ramach jednej akcji dzięki [narzędzia docker compose się](https://docs.docker.com/compose/overview/) interfejsu wiersza polecenia, albo wdrożyć go sposób niewidoczny dla użytkownika w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e771a-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="e771a-111">W przeciwnym razie będziesz potrzebować na potrzeby wdrażania kontenerów przez kontener kilku kroków za pomocą interfejsu wiersza polecenia Docker `docker run` polecenie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e771a-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="e771a-112">W związku z tym każda usługa zdefiniowane w docker-compose.yml należy określić dokładnie jeden obraz lub kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e771a-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="e771a-113">Inne klucze są opcjonalne i są analogiczne do ich `docker run` odpowiedniki wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e771a-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="e771a-114">Poniższego kodu YAML jest definicja możliwe globalnych, ale pojedynczego pliku docker-compose.yml dla przykładu w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e771a-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="e771a-115">To nie jest plikiem docker-compose rzeczywistych, w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e771a-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="e771a-116">Zamiast tego jest to wersja uproszczony i skonsolidowane w jednym pliku, który nie jest najlepszy sposób pracy z plików docker-compose, ponieważ zostaną wyjaśnione później.</span><span class="sxs-lookup"><span data-stu-id="e771a-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="e771a-117">Klucz główny, w tym pliku jest usług.</span><span class="sxs-lookup"><span data-stu-id="e771a-117">The root key in this file is services.</span></span> <span data-ttu-id="e771a-118">W ramach tego klucza, należy zdefiniować usług, należy wdrożyć i uruchomić podczas wykonywania `docker-compose up` polecenia lub podczas wdrażania w programie Visual Studio przy użyciu tego pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="e771a-118">Under that key you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="e771a-119">W takim przypadku plik docker-compose.yml ma wiele usług zdefiniowane, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e771a-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="e771a-120">Nazwa usługi</span><span class="sxs-lookup"><span data-stu-id="e771a-120">Service name</span></span> | <span data-ttu-id="e771a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e771a-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="e771a-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="e771a-122">webmvc</span></span>       | <span data-ttu-id="e771a-123">Kontener, w tym aplikacji ASP.NET Core MVC, korzystanie z mikrousług from C po stronie serwera\#</span><span class="sxs-lookup"><span data-stu-id="e771a-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="e771a-124">catalog.api</span><span class="sxs-lookup"><span data-stu-id="e771a-124">catalog.api</span></span>  | <span data-ttu-id="e771a-125">Kontener, w tym mikrousług katalogu ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="e771a-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="e771a-126">Ordering.API</span><span class="sxs-lookup"><span data-stu-id="e771a-126">ordering.api</span></span> | <span data-ttu-id="e771a-127">Kontenera w tym mikrousług porządkowanie Core Web API platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e771a-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="e771a-128">sql.data</span><span class="sxs-lookup"><span data-stu-id="e771a-128">sql.data</span></span>     | <span data-ttu-id="e771a-129">Działanie programu SQL Server dla systemu Linux, zawierający bazy danych mikrousług kontenera</span><span class="sxs-lookup"><span data-stu-id="e771a-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="e771a-130">basket.api</span><span class="sxs-lookup"><span data-stu-id="e771a-130">basket.api</span></span>   | <span data-ttu-id="e771a-131">Kontener z mikrousług koszyka ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="e771a-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="e771a-132">basket.data</span><span class="sxs-lookup"><span data-stu-id="e771a-132">basket.data</span></span>  | <span data-ttu-id="e771a-133">Usługi za pomocą bazy danych koszyka jako pamięci podręcznej REDIS w pamięci podręcznej kontenera z systemem usługi REDIS</span><span class="sxs-lookup"><span data-stu-id="e771a-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="e771a-134">Prosty kontener interfejsu API usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="e771a-134">A simple Web Service API container</span></span>

<span data-ttu-id="e771a-135">Koncentrujących się na jednym kontenerze, catalog.api container mikrousług ma proste definicji:</span><span class="sxs-lookup"><span data-stu-id="e771a-135">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="e771a-136">Ta usługa konteneryzowanych ma podstawowe następującą konfigurację:</span><span class="sxs-lookup"><span data-stu-id="e771a-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="e771a-137">Jest ona oparta na obrazie eshop/catalog.api niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e771a-137">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="e771a-138">Dla sake dla uproszczenia nie istnieje żadne kompilacji: ustawienia w pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="e771a-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="e771a-139">Oznacza to, że obraz muszą wcześniej utworzone (z kompilacji platformy docker) lub zostały pobrane (za pomocą polecenie docker pull) z dowolnego rejestru platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="e771a-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="e771a-140">Definiuje zmienną środowiskową o nazwie ConnectionString przy użyciu parametrów połączenia używany przez program Entity Framework do dostępu do wystąpienia programu SQL Server, który zawiera model danych wykazu.</span><span class="sxs-lookup"><span data-stu-id="e771a-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="e771a-141">W takim przypadku ten sam kontener programu SQL Server zawiera wiele baz danych.</span><span class="sxs-lookup"><span data-stu-id="e771a-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="e771a-142">W związku z tym potrzebujesz mniejszej ilości pamięci w komputerze deweloperskim dla platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="e771a-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="e771a-143">Jednak możesz również wdrożyć jeden kontener programu SQL Server dla każdej bazy danych z mikrousług.</span><span class="sxs-lookup"><span data-stu-id="e771a-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="e771a-144">Nazwa programu SQL Server jest sql.data, który ma taką samą nazwę, używany do kontenera, w którym jest uruchomione wystąpienie programu SQL Server dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e771a-144">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="e771a-145">Jest to wygodne; możliwości używania to rozpoznawanie nazw (wewnętrzne hosta platformy Docker) zostanie rozwiązany adresu sieciowego, dzięki czemu nie trzeba znać wewnętrznego adresu IP dla kontenerów, do których uzyskujesz dostęp do innych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="e771a-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="e771a-146">Ponieważ ciąg połączenia jest zdefiniowana przez zmienną środowiskową, można ustawić tę zmienną za pomocą innego mechanizmu, a w innym czasie.</span><span class="sxs-lookup"><span data-stu-id="e771a-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="e771a-147">Na przykład można ustawić parametrów połączenia różnych podczas wdrażania do produkcji w ostatnim hostów lub wykonując z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure lub preferowanego systemu metodyki DevOps.</span><span class="sxs-lookup"><span data-stu-id="e771a-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="e771a-148">Udostępnia ona port 80 dla wewnętrznego dostęp do usługi catalog.api w ramach hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="e771a-148">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="e771a-149">Host jest obecnie Maszynę wirtualną systemu Linux, ponieważ jest ona oparta na obrazie platformy Docker dla systemu Linux, ale można skonfigurować kontenera dla obrazu Windows należy zamiast tego uruchomić.</span><span class="sxs-lookup"><span data-stu-id="e771a-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="e771a-150">Przekazuje narażonych port 80 w kontenerze do portu 5101 na maszynie hosta platformy Docker (maszyny Wirtualnej systemu Linux).</span><span class="sxs-lookup"><span data-stu-id="e771a-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="e771a-151">Łączy on usługę sieci web w usłudze sql.data (wystąpienie programu SQL Server dla bazy danych systemu Linux uruchomiony w kontenerze).</span><span class="sxs-lookup"><span data-stu-id="e771a-151">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="e771a-152">Po określeniu tej zależności, kontener catalog.api nie uruchomi kontener sql.data został już uruchomiony; jest to ważne, ponieważ catalog.api musi mieć bazy danych programu SQL Server i uruchamianie najpierw.</span><span class="sxs-lookup"><span data-stu-id="e771a-152">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="e771a-153">Jednak tego rodzaju zależności kontenera nie jest wystarczające w wielu przypadkach, ponieważ Docker testy tylko na poziomie kontenera.</span><span class="sxs-lookup"><span data-stu-id="e771a-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="e771a-154">Czasami usługi (w tym przypadku SQL Server) może być nadal nie będzie gotowe, więc zaleca się, aby zaimplementować logikę ponawiania próby z wykorzystaniem wykładniczego wycofywania w mikrousługi klienta.</span><span class="sxs-lookup"><span data-stu-id="e771a-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="e771a-155">Dzięki temu, jeśli kontener zależność nie jest gotowy, przez krótki czas aplikacji nadal będą odporne na błędy.</span><span class="sxs-lookup"><span data-stu-id="e771a-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="e771a-156">Jest skonfigurowana, aby zezwolić na dostęp do zewnętrznych serwerów: nadmiarowe\_hostów ustawienie umożliwia dostęp do zewnętrznych serwerach lub maszynach poza hosta platformy Docker (czyli poza domyślne maszyny Wirtualnej systemu Linux, czyli programowania Docker hosta), takie jak lokalna baza SQL Wystąpienie serwera na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e771a-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="e771a-157">Istnieją także inne, bardziej zaawansowane ustawienia docker-compose.yml, które omówimy w kolejnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="e771a-157">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="e771a-158">Przy użyciu plików docker-compose pod kątem wielu środowisk</span><span class="sxs-lookup"><span data-stu-id="e771a-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="e771a-159">Pliki docker-compose.yml są plikami definicji i mogą być używane przez wiele infrastruktury, które zrozumieć tego formatu.</span><span class="sxs-lookup"><span data-stu-id="e771a-159">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="e771a-160">To najprostszy narzędzia docker-compose polecenia.</span><span class="sxs-lookup"><span data-stu-id="e771a-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="e771a-161">W związku z tym, za pomocą platformy docker-compose polecenia można wskazać następujące główne scenariusze.</span><span class="sxs-lookup"><span data-stu-id="e771a-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="e771a-162">Środowiska deweloperskie</span><span class="sxs-lookup"><span data-stu-id="e771a-162">Development environments</span></span>

<span data-ttu-id="e771a-163">Podczas tworzenia aplikacji jest ważne, aby można było uruchomić aplikację w środowisku izolowanym rozwoju.</span><span class="sxs-lookup"><span data-stu-id="e771a-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="e771a-164">Możesz użyć narzędzia docker-compose polecenia interfejsu wiersza polecenia do tworzenia tego środowiska, lub użyć programu Visual Studio, która używa aparatu docker-compose dzieje się w tle.</span><span class="sxs-lookup"><span data-stu-id="e771a-164">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="e771a-165">Plik docker-compose.yml pozwala na konfigurowanie i udokumentować wszystkie usługi zależności aplikacji (inne usługi, pamięci podręcznej, baz danych, kolejki itd.).</span><span class="sxs-lookup"><span data-stu-id="e771a-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="e771a-166">Przy użyciu interfejsu wiersza polecenia platformy docker-compose, możesz utworzyć i uruchomić co najmniej jeden kontener dla poszczególnych zależności za pomocą jednego polecenia (docker-compose się).</span><span class="sxs-lookup"><span data-stu-id="e771a-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="e771a-167">Pliki docker-compose.yml znajdują się pliki konfiguracyjne interpretowane przez aparat platformy Docker, ale także służyć jako pliki dokumentacji wygodne temat układu aplikacji z wieloma kontenerami.</span><span class="sxs-lookup"><span data-stu-id="e771a-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="e771a-168">Środowisk testowych</span><span class="sxs-lookup"><span data-stu-id="e771a-168">Testing environments</span></span>

<span data-ttu-id="e771a-169">Ważnym dowolnego ciągłe wdrażanie (CD) lub procesu ciągłej integracji (CI) są testy jednostkowe i testy integracji.</span><span class="sxs-lookup"><span data-stu-id="e771a-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="e771a-170">Tych zautomatyzowanych testów wymagają izolowanym środowisku, więc one nie ma wpływ na użytkowników lub innych zmian w danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e771a-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="e771a-171">Przy użyciu narzędzia Docker Compose możesz tworzyć i niszczyć tego środowiska izolowanego w bardzo prosty sposób za pomocą kilku poleceń z wiersza polecenia lub skryptów, takich jak następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="e771a-171">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="e771a-172">Wdrożenia produkcyjne</span><span class="sxs-lookup"><span data-stu-id="e771a-172">Production deployments</span></span>

<span data-ttu-id="e771a-173">Umożliwia także tworzenia do wdrażania na zdalny aparat platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="e771a-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="e771a-174">Typowy przypadek jest wdrożenie w ramach pojedynczego wystąpienia hosta platformy Docker (produkcyjna maszyna wirtualna lub udostępniane z serwera, takie jak [maszyny platformy Docker](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="e771a-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="e771a-175">Jeśli używasz innych orchestrator (z usługi Azure Service Fabric, Kubernetes itp.), może być konieczne dodać ustawienia konfiguracji instalacji i metadanych, podobnie jak w docker-compose.yml, ale w formacie wymaganym przez program orchestrator.</span><span class="sxs-lookup"><span data-stu-id="e771a-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="e771a-176">W każdym przypadku docker-compose jest wygodne narzędzie i metadanych formatu dla przepływów pracy programowania, testowania i produkcji, mimo że przepływ pracy produkcji mogą się różnić na programu orchestrator, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="e771a-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="e771a-177">Przy użyciu wielu plików docker-compose do obsługi wielu środowisk</span><span class="sxs-lookup"><span data-stu-id="e771a-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="e771a-178">Gdy przeznaczonych dla różnych środowisk, należy użyć wielu tworzą pliki.</span><span class="sxs-lookup"><span data-stu-id="e771a-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="e771a-179">Dzięki temu można tworzyć wiele wariantów konfiguracji, w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="e771a-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="e771a-180">Zastępowanie pliku podstawowego docker-compose</span><span class="sxs-lookup"><span data-stu-id="e771a-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="e771a-181">Można użyć pliku docker-compose.yml w jednym, jak uproszczone przykłady zamieszczone w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="e771a-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="e771a-182">Nie jest, jednak zalecane w przypadku większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e771a-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="e771a-183">Domyślnie Compose odczytuje dwa pliki docker-compose.yml i plik docker-compose.override.yml opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e771a-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="e771a-184">Jak pokazano w rysunek 6-11, gdy używasz programu Visual Studio i włączenia obsługi programu Docker, Visual Studio tworzy również plik dodatkowe compose.vs.debug.g.yml platformy docker do debugowania aplikacji, możesz zapoznaj się z tego pliku w folderze obj.\\platformy Docker \\ w folderze głównym rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e771a-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Struktura plików projektów docker-compose: .dockerignore do ignorowania plików. docker-compose.yml do redagowania mikrousług; docker-compose.override.yml, aby skonfigurować środowisko mikrousług.](./media/image12.png)

<span data-ttu-id="e771a-186">**Rysunek 6-11**.</span><span class="sxs-lookup"><span data-stu-id="e771a-186">**Figure 6-11**.</span></span> <span data-ttu-id="e771a-187">docker-compose plików w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e771a-187">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="e771a-188">Możesz edytować pliki docker-compose w dowolnym edytorze, np. Visual Studio Code lub Sublime i uruchomić aplikację za pomocą platformy docker-compose up polecenia.</span><span class="sxs-lookup"><span data-stu-id="e771a-188">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="e771a-189">Zgodnie z Konwencją pliku docker-compose.yml zawiera podstawowej konfiguracji i inne statyczne ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e771a-189">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="e771a-190">Czy oznacza to, że konfiguracja usługi nie należy zmieniać w zależności od środowiska wdrażania przeznaczonych do pracy.</span><span class="sxs-lookup"><span data-stu-id="e771a-190">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="e771a-191">Pliku docker-compose.override.yml sugeruje nazwa, zawiera ustawienia konfiguracji, które zastępują konfiguracji podstawowej, takie jak konfiguracja, który zależy od środowiska wdrażania.</span><span class="sxs-lookup"><span data-stu-id="e771a-191">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="e771a-192">Również może mieć wiele plików przesłonięcie pod różnymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="e771a-192">You can have multiple override files with different names also.</span></span> <span data-ttu-id="e771a-193">Pliki zastąpienie zwykle zawierają dodatkowe informacje wymagane przez aplikację, ale określonego środowiska lub do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e771a-193">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="e771a-194">Przeznaczone dla wielu środowisk</span><span class="sxs-lookup"><span data-stu-id="e771a-194">Targeting multiple environments</span></span>

<span data-ttu-id="e771a-195">Typowym przypadkiem użycia jest podczas definiowania wielu tworzą pliki tak możliwe jest Określanie wielu środowisk, takich jak środowiska produkcyjnego, przemieszczania, ciągłej integracji i programowania.</span><span class="sxs-lookup"><span data-stu-id="e771a-195">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="e771a-196">Aby obsługiwać te różnice, możesz podzielić konfigurację Compose na wiele plików, jak pokazano w rysunek 6-i 12.</span><span class="sxs-lookup"><span data-stu-id="e771a-196">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Można połączyć wiele plików compose\*.fml platformy docker do obsługi różnych środowisk.](./media/image13.png)

<span data-ttu-id="e771a-198">**Rysunek 6-i 12**.</span><span class="sxs-lookup"><span data-stu-id="e771a-198">**Figure 6-12**.</span></span> <span data-ttu-id="e771a-199">Wiele plików docker-compose zastępowanie wartości z pliku docker-compose.yml podstawowy</span><span class="sxs-lookup"><span data-stu-id="e771a-199">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="e771a-200">Możesz uruchomić za pomocą pliku docker-compose.yml podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e771a-200">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="e771a-201">Ten plik podstawowy musi zawierają ustawienia konfiguracji bazowej lub statycznych, które nie zmieniają się w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="e771a-201">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="e771a-202">Na przykład ramach aplikacji eShopOnContainers ma następujący plik docker-compose.yml (uproszczone dzięki mniej usługi) jako pliku podstawowego.</span><span class="sxs-lookup"><span data-stu-id="e771a-202">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with less services) as the base file.</span></span>

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

<span data-ttu-id="e771a-203">Wartości w pliku docker-compose.yml podstawowego nie należy zmieniać ze względu na inną docelową wdrożenia środowiska.</span><span class="sxs-lookup"><span data-stu-id="e771a-203">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="e771a-204">Jeśli możesz skoncentrować się na webmvc definicji usługi, na przykład widać jak te informacje są bardzo podobne do niezależnie od tego, jakiego środowiska mogą być przeznaczone dla.</span><span class="sxs-lookup"><span data-stu-id="e771a-204">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="e771a-205">Masz następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="e771a-205">You have the following information:</span></span>

- <span data-ttu-id="e771a-206">Nazwa usługi: webmvc.</span><span class="sxs-lookup"><span data-stu-id="e771a-206">The service name: webmvc.</span></span>

- <span data-ttu-id="e771a-207">Niestandardowy obraz kontenera: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="e771a-207">The container’s custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="e771a-208">Polecenie do tworzenia niestandardowego obrazu platformy Docker, wskazującą, które pliku Dockerfile do użycia.</span><span class="sxs-lookup"><span data-stu-id="e771a-208">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="e771a-209">W zależności od innych usług, dzięki czemu ten kontener nie uruchamia się, dopóki nie uruchomiono innych kontenerów zależności.</span><span class="sxs-lookup"><span data-stu-id="e771a-209">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="e771a-210">Masz dodatkowe czynności konfiguracyjne, ale istotną kwestią jest, że w pliku docker-compose.yml podstawowego, po prostu chcesz ustawić informacje, które są wspólne w środowiskach.</span><span class="sxs-lookup"><span data-stu-id="e771a-210">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="e771a-211">Następnie w docker-compose.override.yml lub podobnych plików do produkcyjnego lub tymczasowego, należy umieścić konfiguracji, które są specyficzne dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="e771a-211">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="e771a-212">Zazwyczaj docker-compose.override.yml jest używany dla swojego środowiska programowania, jak w poniższym przykładzie w ramach aplikacji eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="e771a-212">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="e771a-213">W tym przykładzie rozwoju zastępczą konfigurację ujawnia Niektóre porty do hosta, definiuje zmiennych środowiskowych poleceniem przekierowania adresów URL i określa parametry połączenia dla środowiska programistycznego.</span><span class="sxs-lookup"><span data-stu-id="e771a-213">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="e771a-214">Te ustawienia dotyczą wszystkich tylko w środowisku deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="e771a-214">These settings are all just for the development environment.</span></span>

<span data-ttu-id="e771a-215">Po uruchomieniu `docker-compose up` (lub uruchomić go w programie Visual Studio), polecenie odczytuje automatycznie zastąpienia, tak jakby były scalania, oba pliki.</span><span class="sxs-lookup"><span data-stu-id="e771a-215">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="e771a-216">Załóżmy, że ma inny plik Compose w środowisku produkcyjnym, przy użyciu wartości różnych konfiguracji, portów lub parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="e771a-216">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="e771a-217">Możesz utworzyć inny plik zastąpienie, np. plik o nazwie `docker-compose.prod.yml` z różnymi ustawieniami i zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="e771a-217">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="e771a-218">Ten plik, mogą być przechowywane w różnych repozytorium Git lub zarządzane i chronione przez inny zespół.</span><span class="sxs-lookup"><span data-stu-id="e771a-218">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="e771a-219">Jak wdrożyć za pomocą pliku określone zastąpienia</span><span class="sxs-lookup"><span data-stu-id="e771a-219">How to deploy with a specific override file</span></span>

<span data-ttu-id="e771a-220">Aby korzystać z wielu plików zastąpienia lub zastąpienie pliku o innej nazwie, można użyć opcji -f, przy użyciu narzędzia docker-compose polecenia i określić pliki.</span><span class="sxs-lookup"><span data-stu-id="e771a-220">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="e771a-221">Tworzenie plików scalenia w kolejności, w której są one określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e771a-221">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="e771a-222">Poniższy przykład pokazuje, jak wdrożyć zastąpienie plików.</span><span class="sxs-lookup"><span data-stu-id="e771a-222">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="e771a-223">Korzystanie ze zmiennych środowiskowych w plików docker-compose</span><span class="sxs-lookup"><span data-stu-id="e771a-223">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="e771a-224">Jest to wygodne, szczególnie w środowiskach produkcyjnych, aby można było pobrać informacji o konfiguracji ze zmiennych środowiskowych, jak firma Microsoft ma w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="e771a-224">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="e771a-225">Zmienna środowiskowa można się odwoływać w docker-compose plików przy użyciu składni ${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="e771a-225">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="e771a-226">Następujący wiersz z pliku docker-compose.prod.yml pokazuje, jak odwoływać się do wartości zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="e771a-226">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="e771a-227">Zmienne środowiskowe są tworzone i inicjowane na różne sposoby, w zależności od środowiska hosta (Linux, Windows, klaster Cloud itp.).</span><span class="sxs-lookup"><span data-stu-id="e771a-227">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="e771a-228">Jednak wygodne podejściem jest użycie pliku env.</span><span class="sxs-lookup"><span data-stu-id="e771a-228">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="e771a-229">Obsługa plików docker-compose deklarowanie domyślną zmiennych środowiskowych w pliku env.</span><span class="sxs-lookup"><span data-stu-id="e771a-229">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="e771a-230">Wartości domyślne są to wartości zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="e771a-230">These values for the environment variables are the default values.</span></span> <span data-ttu-id="e771a-231">Jednak mogą być zastąpione przez wartości, które może być zdefiniowane we wszystkich środowiskach (system operacyjny hosta lub zmiennych środowiskowych z klastra).</span><span class="sxs-lookup"><span data-stu-id="e771a-231">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="e771a-232">Umieść ten plik ENV w folderze gdzie narzędzia docker compose polecenie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="e771a-232">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="e771a-233">W poniższym przykładzie pokazano plik ENV, takich jak [ENV](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pliku dla aplikacji w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e771a-233">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="e771a-234">Narzędzia docker compose oczekuje, że każdy wiersz w pliku ENV, aby być w formacie \<zmiennej\>=\<wartość\>.</span><span class="sxs-lookup"><span data-stu-id="e771a-234">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="e771a-235">Należy pamiętać, że wartości ustawione w środowisku uruchomieniowym zawsze zastąpić wartości zdefiniowanych w pliku env.</span><span class="sxs-lookup"><span data-stu-id="e771a-235">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="e771a-236">W podobny sposób wartości przekazane za pośrednictwem argumentów wiersza polecenia Zastąp wartości domyślne ustawione w pliku env.</span><span class="sxs-lookup"><span data-stu-id="e771a-236">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e771a-237">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e771a-237">Additional resources</span></span>

- <span data-ttu-id="e771a-238">**Przegląd platformy Docker Compose** \\</span><span class="sxs-lookup"><span data-stu-id="e771a-238">**Overview of Docker Compose** \\</span></span>
    [https://docs.docker.com/compose/overview/](https://docs.docker.com/compose/overview/)

- <span data-ttu-id="e771a-239">**Wiele pliki narzędzia Compose** \\</span><span class="sxs-lookup"><span data-stu-id="e771a-239">**Multiple Compose files** \\</span></span>
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="e771a-240">Tworzenie zoptymalizowanych obrazów platformy Docker programu ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e771a-240">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="e771a-241">Jeśli platforma Docker i platformy .NET Core analizujesz źródeł w Internecie, można znaleźć plików Dockerfile, które przedstawiają uproszczenia tworzenia obrazu platformy Docker, kopiując źródła w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="e771a-241">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="e771a-242">Te przykłady sugeruje, że za pomocą prostej konfiguracji, masz obraz platformy Docker ze środowiskiem spakować z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="e771a-242">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="e771a-243">Poniższy przykład pokazuje prosty plik Dockerfile, w tym względzie.</span><span class="sxs-lookup"><span data-stu-id="e771a-243">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="e771a-244">Plik Dockerfile, takich jak to będzie działać.</span><span class="sxs-lookup"><span data-stu-id="e771a-244">A Dockerfile like this will work.</span></span> <span data-ttu-id="e771a-245">Można jednak znacznie zoptymalizować obrazów, szczególnie obrazów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="e771a-245">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="e771a-246">W modelu mikrousług i kontenerów, są stale uruchamianie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="e771a-246">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="e771a-247">Typowy sposób korzystania z kontenerów nie jest ponownie uruchamiany kontener uśpiony, ponieważ kontener jest możliwe do likwidacji.</span><span class="sxs-lookup"><span data-stu-id="e771a-247">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="e771a-248">Koordynatorów (takich jak Kubernetes i usługi Azure Service Fabric) jest po prostu utworzyć nowe wystąpienia obrazów.</span><span class="sxs-lookup"><span data-stu-id="e771a-248">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="e771a-249">Oznacza to, że będziesz potrzebować Optymalizowanie wstępnej kompilacji aplikacji, podczas tworzenia procesu tworzenia wystąpienia będą szybciej.</span><span class="sxs-lookup"><span data-stu-id="e771a-249">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="e771a-250">Po uruchomieniu kontenera, powinno być gotowe do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="e771a-250">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="e771a-251">Nie powinny przywracania i skompilować wykonywania użycie `dotnet restore` i `dotnet build` poleceń z wiersz polecenia dotnet tym, jak widać w wielu wpisów w blogu o platformy .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="e771a-251">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="e771a-252">Zespołem platformy .NET ma zostały wykonywania pracy zapewnienie platformy .NET Core i ASP.NET Core platforma zoptymalizowane pod kątem kontenera.</span><span class="sxs-lookup"><span data-stu-id="e771a-252">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="e771a-253">Nie tylko to platformy .NET Core uproszczone środowisko z zużycie pamięci; zespół koncentruje się na zoptymalizowane obrazy platformy Docker dla trzech głównych scenariuszy i opublikowane je w rejestrze usługi Docker Hub w *dotnet/core*, zaczynające się od wersji 2.1:</span><span class="sxs-lookup"><span data-stu-id="e771a-253">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="e771a-254">**Programowanie**: Gdzie jest możliwość osiągnięcie elastyczności potrzebnej do debugowania zmiany priorytetu, a gdy rozmiar to dodatkowa baza danych.</span><span class="sxs-lookup"><span data-stu-id="e771a-254">**Development**: Where the priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="e771a-255">**Tworzenie**: Priorytet jest Kompilowanie aplikacji i zawiera pliki binarne i inne zależności, aby zoptymalizować pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="e771a-255">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="e771a-256">**Produkcji**: Gdy fokus jest szybkie wdrażanie i uruchamianie kontenerów, dzięki czemu te obrazy są ograniczone do plików binarnych i zawartość wymaganą do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e771a-256">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content needed to run the application.</span></span>

<span data-ttu-id="e771a-257">Aby to osiągnąć, zespół .NET dostarcza cztery podstawowego warianty w [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (w usłudze Docker Hub):</span><span class="sxs-lookup"><span data-stu-id="e771a-257">To achieve this, the .NET team is providing four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="e771a-258">**zestaw SDK**: dla scenariuszy projektowania i kompilowania</span><span class="sxs-lookup"><span data-stu-id="e771a-258">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="e771a-259">**ASPNET**: na potrzeby scenariuszy produkcyjnych platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e771a-259">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="e771a-260">**środowisko uruchomieniowe**: na potrzeby scenariuszy produkcyjnych platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e771a-260">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="e771a-261">**środowisko uruchomieniowe deps**: dla scenariuszy produkcyjnych [aplikacje samodzielne](../../../core/deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="e771a-261">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#self-contained-deployments-scd).</span></span>

<span data-ttu-id="e771a-262">W celu przyspieszenia uruchamiania obrazów środowiska uruchomieniowego również automatycznie ustawiony aspnetcore\_adresów URL do portu 80, a następnie utworzyć pamięci podręcznej obrazów natywnych zestawów za pomocą programu Ngen.</span><span class="sxs-lookup"><span data-stu-id="e771a-262">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e771a-263">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e771a-263">Additional resources</span></span>

- <span data-ttu-id="e771a-264">**Tworzenie zoptymalizowane pod kątem obrazów platformy Docker z platformą ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="e771a-264">**Building Optimized Docker Images with ASP.NET Core** \\</span></span>
    [https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

- <span data-ttu-id="e771a-265">**Tworzenie obrazów platformy Docker dla aplikacji .NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="e771a-265">**Building Docker Images for .NET Core Applications** \\</span></span>
    [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

> [!div class="step-by-step"]
> <span data-ttu-id="e771a-266">[Poprzednie](data-driven-crud-microservice.md)
> [dalej](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="e771a-266">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
