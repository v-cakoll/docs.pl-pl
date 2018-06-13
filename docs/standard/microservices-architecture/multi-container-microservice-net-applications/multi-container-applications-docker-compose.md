---
title: Definiowanie aplikacji usługi kontenera przy użyciu rozwiązania docker-compose.yml
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Definiowanie aplikacji usługi kontenera przy użyciu rozwiązania docker-compose.yml
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: ded2e5399938be25005776963b0310b6a49d0353
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592356"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="df105-103">Definiowanie aplikacji usługi kontenera przy użyciu rozwiązania docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="df105-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="df105-104">W tym przewodniku [docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku została wprowadzona w sekcji [krok 4. Zdefiniuj usług w rozwiązaniu docker-compose.yml podczas kompilowania aplikacji usługi kontenera Docker](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="df105-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="df105-105">Istnieją dodatkowe sposoby używania plików docker-compose, które warto eksploracji bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="df105-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="df105-106">Na przykład można jawnie opisano, jak chcesz wdrożyć aplikację usługi kontenera w plik docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="df105-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="df105-107">Opcjonalnie można opisano, jak zamierzasz utworzyć niestandardowe obrazy usługi Docker.</span><span class="sxs-lookup"><span data-stu-id="df105-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="df105-108">(Niestandardowe obrazy usługi Docker mogą być również tworzone z poziomu interfejsu wiersza polecenia Docker).</span><span class="sxs-lookup"><span data-stu-id="df105-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="df105-109">Zasadniczo należy zdefiniować wszystkich kontenerów, do których chcesz wdrożyć plus niektórych parametrów dla każdego wdrożenia kontenera.</span><span class="sxs-lookup"><span data-stu-id="df105-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="df105-110">Po utworzeniu pliku opisu wdrożenia usługi kontenera, można wdrożyć całe rozwiązanie w ramach jednej akcji zorkiestrowana przez [rozwiązania docker compose się](https://docs.docker.com/compose/overview/) polecenia interfejsu wiersza polecenia lub można go wdrożyć sposób niewidoczny dla użytkownika z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df105-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="df105-111">W przeciwnym razie należy użyć interfejsu wiersza polecenia Docker w celu wdrożenia kontenera przez kontener w wielu kroków przy użyciu rozwiązania docker, uruchom polecenie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="df105-112">W związku z tym każda usługa zdefiniowane w rozwiązaniu docker-compose.yml określić dokładnie jeden obraz lub kompilacji.</span><span class="sxs-lookup"><span data-stu-id="df105-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="df105-113">Inne klucze są opcjonalne i są podobne do ich docker Uruchom odpowiedników wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-113">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="df105-114">Poniższy kod yaml programu znajduje się definicja metody możliwe globalnych, ale pojedynczy plik docker-compose.yml przykładowej eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="df105-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="df105-115">To nie jest plikiem rzeczywiste docker-compose z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="df105-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="df105-116">Zamiast tego jest to wersja uproszczonym i skonsolidowanych w jednym pliku, który nie jest najlepszy sposób pracy z rozwiązania docker-compose plików, jak opisano później.</span><span class="sxs-lookup"><span data-stu-id="df105-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="df105-117">Klucz główny, w tym pliku jest usług.</span><span class="sxs-lookup"><span data-stu-id="df105-117">The root key in this file is services.</span></span> <span data-ttu-id="df105-118">W tym kluczu zdefiniuj usług, należy wdrożyć i uruchomić podczas wykonywania rozwiązania docker compose polecenia lub podczas wdrażania w programie Visual Studio przy użyciu tego plik docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="df105-118">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="df105-119">W takim przypadku plik docker-compose.yml ma wiele usług zdefiniowane, zgodnie z opisem w poniższej liście.</span><span class="sxs-lookup"><span data-stu-id="df105-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="df105-120">webmvc kontenera, w tym aplikacji ASP.NET Core MVC zużywa mikrousług z C po stronie serwera\#</span><span class="sxs-lookup"><span data-stu-id="df105-120">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="df105-121">Catalog.API kontenera, w tym mikrousługi katalogu platformy ASP.NET Core sieci Web API</span><span class="sxs-lookup"><span data-stu-id="df105-121">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="df105-122">Ordering.API mikrousługi porządkowanie Core Web API platformy ASP.NET w tym kontenerze</span><span class="sxs-lookup"><span data-stu-id="df105-122">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="df105-123">SQL.Data kontenera z programem SQL Server dla systemu Linux, zawierający mikrousług baz danych</span><span class="sxs-lookup"><span data-stu-id="df105-123">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="df105-124">basket.API kontenera z mikrousługi koszyka ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="df105-124">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="df105-125">basket.Data kontenera uruchomiona usługa pamięci podręcznej REDIS z koszyka bazy danych jako pamięci podręcznej REDIS</span><span class="sxs-lookup"><span data-stu-id="df105-125">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="df105-126">Kontener prosty interfejs API usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="df105-126">A simple Web Service API container</span></span>

<span data-ttu-id="df105-127">Skupienie się na jeden kontener, catalog.api kontenera mikrousługi ma definicję prosta:</span><span class="sxs-lookup"><span data-stu-id="df105-127">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="df105-128">Ta usługa konteneryzowanych ma następującą konfigurację podstawowe:</span><span class="sxs-lookup"><span data-stu-id="df105-128">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="df105-129">Jest on oparty na eshop/catalog.api niestandardowego obrazu.</span><span class="sxs-lookup"><span data-stu-id="df105-129">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="df105-130">Dla sake dla uproszczenia nie istnieje żadne kompilacji: ustawienia w pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="df105-130">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="df105-131">Oznacza to, że obraz musi wcześniej skompilowano (z kompilacją docker) lub zostały pobrane z dowolnego rejestru Docker (z poleceniem ściągania docker).</span><span class="sxs-lookup"><span data-stu-id="df105-131">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="df105-132">Definiuje zmienną środowiskową o nazwie ConnectionString ciągu połączenia używanego przez program Entity Framework do wystąpienia programu SQL Server, który zawiera model danych katalogu.</span><span class="sxs-lookup"><span data-stu-id="df105-132">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="df105-133">W takim przypadku tego samego kontenera programu SQL Server jest zawierający wiele baz danych.</span><span class="sxs-lookup"><span data-stu-id="df105-133">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="df105-134">W związku z tym należy mniejszej ilości pamięci w komputerze deweloperskim for Docker.</span><span class="sxs-lookup"><span data-stu-id="df105-134">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="df105-135">Jednak można także wdrożyć jeden kontener programu SQL Server dla każdej bazy danych mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="df105-135">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="df105-136">Nazwa programu SQL Server jest sql.data, która jest nazwą tego samego kontenera, w którym działa wystąpienie serwera SQL dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="df105-136">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="df105-137">Jest to wygodny; możliwości używania tego rozpoznawania nazw (wewnętrzny hosta Docker) rozwiąże adres sieci, więc nie trzeba znać wewnętrznego adresu IP dla kontenerów, do których masz dostęp z innych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="df105-137">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="df105-138">Ponieważ ciągu połączenia jest zdefiniowana przez zmienną środowiskową, można ustawić tej zmiennej za pośrednictwem innego mechanizmu i w innym czasie.</span><span class="sxs-lookup"><span data-stu-id="df105-138">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="df105-139">Na przykład można ustawić różne parametry w przypadku wdrażania w środowisku produkcyjnym w ostatnim hostów lub wykonywanie czynności z Twojej potoków CI/CD w VSTS lub preferowany system DevOps.</span><span class="sxs-lookup"><span data-stu-id="df105-139">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="df105-140">Prezentuje ona port 80 dla wewnętrznego dostęp do usługi catalog.api w ramach hosta Docker.</span><span class="sxs-lookup"><span data-stu-id="df105-140">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="df105-141">Host jest obecnie Maszynę wirtualną systemu Linux, ponieważ jest ona oparta na obrazie Docker dla systemu Linux, ale można skonfigurować kontenera należy zamiast tego uruchomić w obrazie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="df105-141">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="df105-142">Przekazuje dostępnego portu 80 kontenera do portu 5101 na komputerze hosta Docker (maszyny Wirtualnej systemu Linux).</span><span class="sxs-lookup"><span data-stu-id="df105-142">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="df105-143">Łączy usługę sieci web do usługi sql.data (wystąpienie programu SQL Server dla bazy danych systemu Linux uruchomione w kontenerze).</span><span class="sxs-lookup"><span data-stu-id="df105-143">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="df105-144">Po określeniu tę zależność kontenera catalog.api nie uruchomi kontener sql.data została już rozpoczęta; najpierw to ważne, ponieważ catalog.api musi mieć bazy danych programu SQL Server w i uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="df105-144">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="df105-145">Jednak tego rodzaju zależności kontenera nie jest wystarczająco w wielu przypadkach, ponieważ Docker sprawdza tylko na poziomie kontenera.</span><span class="sxs-lookup"><span data-stu-id="df105-145">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="df105-146">Czasami usługi (w tym przypadku SQL Server) nie będą gotowe, dlatego zaleca się implementację logiki ponawiania próby z wykładniczego wycofywania w Twojej mikrousług klienta.</span><span class="sxs-lookup"><span data-stu-id="df105-146">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="df105-147">W ten sposób, jeśli kontener zależności nie jest gotowy do przez krótki czas aplikacji będą odporne.</span><span class="sxs-lookup"><span data-stu-id="df105-147">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="df105-148">Skonfigurowano w celu umożliwienia dostępu do zewnętrznych serwerów: nadmiarowe\_hostów ustawienie umożliwia dostęp do zewnętrznych serwerów lub maszyny poza hostów Docker (to znaczy poza domyślną maszyny Wirtualnej systemu Linux, który jest programowanie Docker hosta), takich jak lokalna baza SQL Wystąpienie serwera na komputerze.</span><span class="sxs-lookup"><span data-stu-id="df105-148">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="df105-149">Istnieją także inne, bardziej zaawansowane ustawienia docker-compose.yml, które omówimy w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="df105-149">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="df105-150">Przy użyciu rozwiązania docker-compose plików pod kątem wiele środowisk</span><span class="sxs-lookup"><span data-stu-id="df105-150">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="df105-151">Pliki docker-compose.yml są definicji i mogą być używane przez wiele infrastruktury, które rozumieją tego formatu.</span><span class="sxs-lookup"><span data-stu-id="df105-151">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="df105-152">Narzędzie to najprostszy jest docker-tworzą polecenia, ale innych narzędzi, takich jak orchestrators (na przykład Docker Swarm) należy również zapoznać się tego pliku.</span><span class="sxs-lookup"><span data-stu-id="df105-152">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="df105-153">W związku z tym przy użyciu rozwiązania docker compose polecenia można wskazać następujące główne scenariusze.</span><span class="sxs-lookup"><span data-stu-id="df105-153">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="df105-154">Środowisk deweloperskich</span><span class="sxs-lookup"><span data-stu-id="df105-154">Development environments</span></span>

<span data-ttu-id="df105-155">Podczas tworzenia aplikacji, jest ważne można było uruchomić aplikację w środowisku projektowym izolowanym.</span><span class="sxs-lookup"><span data-stu-id="df105-155">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="df105-156">Można użyć rozwiązania docker compose polecenia interfejsu wiersza polecenia do utworzenia tego środowiska lub użyć programu Visual Studio, który używa rozwiązania docker-compose w obszarze obejmuje.</span><span class="sxs-lookup"><span data-stu-id="df105-156">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="df105-157">Plik docker-compose.yml służy do konfigurowania i zarządzania dokumentami zależności usługi wszystkich aplikacji (inne usługi, pamięci podręcznej, baz danych, kolejki itd.).</span><span class="sxs-lookup"><span data-stu-id="df105-157">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="df105-158">Przy użyciu rozwiązania docker compose polecenia interfejsu wiersza polecenia, można utworzyć i uruchomić kontenerach dla każdego zależności za pomocą jednego polecenia (docker tworzą się).</span><span class="sxs-lookup"><span data-stu-id="df105-158">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="df105-159">Docker-compose.yml są interpretowane przez aparat Docker pliki konfiguracji, ale również służyć jako pliki dokumentacji wygodny o kompozycji wielu kontenera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df105-159">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="df105-160">Środowisk testowych</span><span class="sxs-lookup"><span data-stu-id="df105-160">Testing environments</span></span>

<span data-ttu-id="df105-161">Ważnym elementem procesu ciągłej integracji (CI) lub ciągłe wdrażanie (CD) są testów jednostkowych i integracji.</span><span class="sxs-lookup"><span data-stu-id="df105-161">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="df105-162">Te testy automatyczne wymaga izolowanym środowisku, dzięki czemu można ich nie ma wpływ na użytkowników lub inne zmiany w danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df105-162">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="df105-163">Z rozwiązania Docker Compose możesz tworzyć i zniszcz tego środowiska izolowanego bardzo łatwo w kilku poleceń z wiersza polecenia lub skryptów, takich jak następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="df105-163">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="df105-164">Wdrożeń produkcyjnych</span><span class="sxs-lookup"><span data-stu-id="df105-164">Production deployments</span></span>

<span data-ttu-id="df105-165">Redaguj służy również do wdrażania na zdalnym aparatem platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="df105-165">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="df105-166">Typowy przypadek jest wdrożenie do pojedynczego wystąpienia hosta Docker (produkcji maszyny Wirtualnej lub udostępniane z serwera, takich jak [maszyny Docker](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="df105-166">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="df105-167">Ale może być również cały [Docker Swarm](https://docs.docker.com/swarm/overview/) klastra, ponieważ klastrów również są zgodne z plikami docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="df105-167">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="df105-168">Jeśli używane są inne orchestrator (sieć szkieletowa usług Azure, Mesos DC/OS, Kubernetes itp.), może być konieczne dodanie ustawienia konfiguracji instalacji i metadanych, podobnie jak w docker-compose.yml, ale w formacie wymagane przez inne orchestrator.</span><span class="sxs-lookup"><span data-stu-id="df105-168">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="df105-169">W każdym przypadku rozwiązania docker compose jest wygodnym formacie narzędzia i metadanych dla przepływów pracy programowania, testowania i produkcji, mimo że produkcji przepływu pracy mogą różnić się dla modułu aranżującego używasz.</span><span class="sxs-lookup"><span data-stu-id="df105-169">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="df105-170">Przy użyciu wielu docker tworzą pliki do obsługi kilku środowiskach</span><span class="sxs-lookup"><span data-stu-id="df105-170">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="df105-171">Gdy przeznaczonych dla różnych środowisk, należy używać wielu tworzą pliki.</span><span class="sxs-lookup"><span data-stu-id="df105-171">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="df105-172">Dzięki temu można utworzyć wiele wariantami konfiguracji, w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="df105-172">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="df105-173">Zastępowanie pliku docker-compose podstawowej</span><span class="sxs-lookup"><span data-stu-id="df105-173">Overriding the base docker-compose file</span></span>

<span data-ttu-id="df105-174">Można użyć pliku pojedynczego docker-compose.yml jak uproszczone przykłady zamieszczone w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="df105-174">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="df105-175">Jednak, że nie zaleca się dla większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df105-175">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="df105-176">Domyślnie Redaguj odczytuje dwóch plików, docker-compose.yml i plik docker-compose.override.yml opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="df105-176">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="df105-177">Jak pokazano w rysunek 8-11, gdy za pomocą programu Visual Studio i również włączania obsługi Docker, Visual Studio tworzy plik dodatkowe compose.ci.build,yml docker do użycia z Twojej potoków CI/CD, podobnie jak w VSTS.</span><span class="sxs-lookup"><span data-stu-id="df105-177">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in VSTS.</span></span>

![](./media/image12.png)

<span data-ttu-id="df105-178">**Rysunek 8-11**.</span><span class="sxs-lookup"><span data-stu-id="df105-178">**Figure 8-11**.</span></span> <span data-ttu-id="df105-179">rozwiązania docker compose plików w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="df105-179">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="df105-180">Możesz edytować pliki docker-compose w dowolnym edytorze, takich jak Visual Studio Code lub Sublime i uruchom aplikację klawiszem rozwiązania docker compose Konfigurowanie polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-180">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="df105-181">Konwencja plik docker-compose.yml zawiera podstawową konfigurację i inne ustawienia statycznych.</span><span class="sxs-lookup"><span data-stu-id="df105-181">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="df105-182">Oznacza to, że konfiguracji usługi nie należy zmieniać w zależności od środowiska wdrażania, który ma być przeznaczona dla.</span><span class="sxs-lookup"><span data-stu-id="df105-182">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="df105-183">Plik docker-compose.override.yml sugeruje nazwa, zawiera ustawienia konfiguracji, które zastępują konfiguracji podstawowej, takie jak konfiguracja, która jest zależna od środowiska wdrażania.</span><span class="sxs-lookup"><span data-stu-id="df105-183">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="df105-184">Również może mieć wiele plików zastąpienie o różnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="df105-184">You can have multiple override files with different names also.</span></span> <span data-ttu-id="df105-185">Pliki zastąpienie zwykle zawierają dodatkowe informacje wymagane przez aplikację ale określonego środowiska lub do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="df105-185">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="df105-186">Celem wiele środowisk</span><span class="sxs-lookup"><span data-stu-id="df105-186">Targeting multiple environments</span></span>

<span data-ttu-id="df105-187">Typowy przypadek użycia jest podczas definiowania wielu tworzą pliki, można kierować wielu środowiskach, takich jak środowiska produkcyjnego, przemieszczania, CI lub programowanie.</span><span class="sxs-lookup"><span data-stu-id="df105-187">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="df105-188">Aby obsługiwać te różnice, można podzielić konfigurację Redaguj na wiele plików, jak pokazano na rysunku 8-12.</span><span class="sxs-lookup"><span data-stu-id="df105-188">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="df105-189">**Rysunek 8-12**.</span><span class="sxs-lookup"><span data-stu-id="df105-189">**Figure 8-12**.</span></span> <span data-ttu-id="df105-190">Wiele docker tworzą pliki zastępowania wartości w pliku podstawowego docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="df105-190">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="df105-191">Możesz uruchomić plik docker-compose.yml podstawowej.</span><span class="sxs-lookup"><span data-stu-id="df105-191">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="df105-192">Tego pliku podstawowego musi zawierać ustawienia konfiguracji podstawowej lub statycznej, które nie zmieniają się w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="df105-192">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="df105-193">Na przykład eShopOnContainers ma następujący plik docker-compose.yml jako pliku podstawowego.</span><span class="sxs-lookup"><span data-stu-id="df105-193">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

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

<span data-ttu-id="df105-194">Wartości w pliku podstawowego docker-compose.yml nie należy zmieniać ze względu na inny element docelowy wdrożenia środowiska.</span><span class="sxs-lookup"><span data-stu-id="df105-194">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="df105-195">Jeśli można skupić się na webmvc definicji usługi, na przykład spowoduje jak jest znacznie taki sam, niezależnie od tego, jakiego środowiska może być przeznaczonych dla tych informacji.</span><span class="sxs-lookup"><span data-stu-id="df105-195">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="df105-196">Masz następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="df105-196">You have the following information:</span></span>

-   <span data-ttu-id="df105-197">Nazwa usługi: webmvc.</span><span class="sxs-lookup"><span data-stu-id="df105-197">The service name: webmvc.</span></span>

-   <span data-ttu-id="df105-198">Obraz niestandardowy kontenera: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="df105-198">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="df105-199">Polecenie, aby utworzyć niestandardowy obraz Docker, wskazującą, który plik Dockerfile do użycia.</span><span class="sxs-lookup"><span data-stu-id="df105-199">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="df105-200">W zależności od innych usług, dlatego ten kontener nie uruchamia się, dopóki nie zostały uruchomione inne kontenery zależności.</span><span class="sxs-lookup"><span data-stu-id="df105-200">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="df105-201">Masz dodatkowe czynności konfiguracyjne, ale ważne punkt znajduje się w pliku podstawowego docker-compose.yml po prostu chcesz ustawić informacje, które są wspólne w środowiskach.</span><span class="sxs-lookup"><span data-stu-id="df105-201">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="df105-202">Następnie w docker compose.override.yml lub podobnych plików do produkcji lub przemieszczania, należy umieścić konfiguracji, które są specyficzne dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="df105-202">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="df105-203">Zazwyczaj docker compose.override.yml jest używana dla swojego środowiska programowania, jak w poniższym przykładzie z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="df105-203">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="df105-204">W tym przykładzie programowanie zastępczą konfigurację przedstawia niektóre porty do hosta, definiuje zmiennych środowiskowych poleceniem przekierowania adresów URL i określa parametry połączenia dla środowiska programowania.</span><span class="sxs-lookup"><span data-stu-id="df105-204">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="df105-205">Te ustawienia dotyczą wszystkich tylko Środowisko deweloperskie.</span><span class="sxs-lookup"><span data-stu-id="df105-205">These settings are all just for the development environment.</span></span>

<span data-ttu-id="df105-206">Po uruchomieniu `docker-compose up` (lub uruchomić go w programie Visual Studio), polecenia odczytuje automatycznie zastąpienia, tak jakby były scalanie oba pliki.</span><span class="sxs-lookup"><span data-stu-id="df105-206">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="df105-207">Załóżmy, że ma inny plik tworzenia w środowisku produkcyjnym, za pomocą wartości różnych konfiguracji, portów lub parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="df105-207">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="df105-208">Można utworzyć inny plik zastąpienie, takich jak plik o nazwie `docker-compose.prod.yml` z różnymi ustawieniami i zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="df105-208">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="df105-209">Ten plik może być przechowywane w różnych repozytorium Git lub zarządzane i zabezpieczone przez inny zespół.</span><span class="sxs-lookup"><span data-stu-id="df105-209">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="df105-210">Jak wdrożyć przy użyciu określonego zastąpienia pliku</span><span class="sxs-lookup"><span data-stu-id="df105-210">How to deploy with a specific override file</span></span>

<span data-ttu-id="df105-211">Aby używać wielu zastąpienie plików lub zastąpienie pliku o innej nazwie, można użyć opcji -f z rozwiązania docker compose polecenia i określ pliki.</span><span class="sxs-lookup"><span data-stu-id="df105-211">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="df105-212">Tworzenie plików scalenia w kolejności, w których są one określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-212">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="df105-213">Poniższy przykład przedstawia sposób wdrażania z plikami zastąpienie.</span><span class="sxs-lookup"><span data-stu-id="df105-213">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="df105-214">Korzystanie ze zmiennych środowiskowych docker tworzą pliki</span><span class="sxs-lookup"><span data-stu-id="df105-214">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="df105-215">Jest wygodną, szczególnie w środowiskach produkcyjnych, aby można było uzyskać informacje o konfiguracji z zmiennych środowiskowych, jak firma Microsoft wykazały w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="df105-215">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="df105-216">Odwołania zmiennej środowiskowej w plikach docker-compose przy użyciu składni \${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="df105-216">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="df105-217">Następujący wiersz z pliku docker compose.prod.yml pokazuje, jak odwoływać się do wartości zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="df105-217">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="df105-218">Zmienne środowiskowe są tworzone i zainicjowana na różne sposoby, w zależności od środowiska hosta (Linux, Windows, chmury klastra itp.).</span><span class="sxs-lookup"><span data-stu-id="df105-218">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="df105-219">Jednak wygodny rozwiązaniem jest użycie pliku .env.</span><span class="sxs-lookup"><span data-stu-id="df105-219">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="df105-220">Obsługa plików docker-compose deklarowania zmiennych środowiskowych w pliku .env domyślne.</span><span class="sxs-lookup"><span data-stu-id="df105-220">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="df105-221">Te wartości zmiennych środowiskowych są wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="df105-221">These values for the environment variables are the default values.</span></span> <span data-ttu-id="df105-222">Ale mogą być zastąpione przez wartości, które może być zdefiniowane w poszczególnych środowisk (systemu operacyjnego hosta lub zmiennych środowiskowych z klastra).</span><span class="sxs-lookup"><span data-stu-id="df105-222">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="df105-223">Ten plik .env zostanie umieszczony w folderze gdzie rozwiązania docker compose z wykonaniem polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-223">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="df105-224">W poniższym przykładzie przedstawiono plik .env, takich jak [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pliku eShopOnContainers aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df105-224">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="df105-225">Rozwiązania docker compose oczekuje, że każdy wiersz w pliku .env w formacie &lt;zmiennej&gt;=&lt;wartość&gt;.</span><span class="sxs-lookup"><span data-stu-id="df105-225">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="df105-226">Należy pamiętać, że wartości środowiska uruchomieniowego zawsze zastąpienie wartości zdefiniowanych w pliku .env.</span><span class="sxs-lookup"><span data-stu-id="df105-226">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="df105-227">W podobny sposób wartości przekazane za pośrednictwem argumentów wiersza polecenia polecenie zastąpić wartości domyślne ustawione w pliku .env.</span><span class="sxs-lookup"><span data-stu-id="df105-227">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="df105-228">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="df105-228">Additional resources</span></span>

-   <span data-ttu-id="df105-229">**Omówienie rozwiązania Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="df105-229">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="df105-230">**Wiele plików Redaguj**
    [*https://docs.docker.com/compose/extends/\#wielu tworzą — pliki*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="df105-230">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="df105-231">Kompilowanie zoptymalizowanych obrazów ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="df105-231">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="df105-232">Jeśli są eksploracji Docker i .NET Core źródeł w Internecie, będą dostępne Dockerfiles, które pokazują łatwość tworzenia obrazu Docker przez skopiowanie źródła do kontenera.</span><span class="sxs-lookup"><span data-stu-id="df105-232">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="df105-233">Te przykłady sugerują, za pomocą prostego konfiguracji, może występować obrazu Docker ze środowiskiem spakować z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="df105-233">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="df105-234">Poniższy przykład przedstawia prosty plik Dockerfile w tym szyjnej.</span><span class="sxs-lookup"><span data-stu-id="df105-234">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="df105-235">Plik Dockerfile jak to działa.</span><span class="sxs-lookup"><span data-stu-id="df105-235">A Dockerfile like this will work.</span></span> <span data-ttu-id="df105-236">Jednak można zoptymalizować znacznie obrazów, szczególnie obrazów produkcji.</span><span class="sxs-lookup"><span data-stu-id="df105-236">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="df105-237">Kontener i mikrousług modelu są stale uruchamianie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="df105-237">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="df105-238">Typowy sposób użycia kontenery nie uruchamiaj ponownie pojemnik uśpiony, ponieważ kontener jest możliwe do rozporządzania.</span><span class="sxs-lookup"><span data-stu-id="df105-238">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="df105-239">Orchestrators (na przykład Docker Swarm, Kubernetes, DCOS lub sieć szkieletowa usług Azure), po prostu utworzyć nowe wystąpienia obrazów.</span><span class="sxs-lookup"><span data-stu-id="df105-239">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="df105-240">Co to oznacza że konieczne będzie zoptymalizować wstępnej kompilacji aplikacji, gdy jest ona wbudowana tak procesu tworzenia wystąpienia będzie przebiegać szybciej.</span><span class="sxs-lookup"><span data-stu-id="df105-240">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="df105-241">Po uruchomieniu kontenera, powinien być gotowy do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="df105-241">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="df105-242">Nie należy przywrócić i kompilacji w czasie wykonywania, za pomocą dotnet przywracania i dotnet tworzenia poleceń z dotnet interfejsu wiersza polecenia, jak widać w wielu wpisy na blogu dotyczące .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="df105-242">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="df105-243">Zespół platformy .NET ma zostały wykonywanie pracy ważne, aby oprogramowanie .NET Core i ASP.NET Core zoptymalizowaną kontenera.</span><span class="sxs-lookup"><span data-stu-id="df105-243">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="df105-244">Nie tylko słowo .NET Core lekkie framework z zużycie pamięci; zespół ma fokus na wydajność uruchamiania i tak samo, jak wyprodukowanych niektórych zoptymalizowanych obrazów Docker [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu dostępne pod adresem [Centrum Docker](https://hub.docker.com/r/microsoft/aspnetcore/), w odróżnieniu od zwykłej [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) lub [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) obrazów.</span><span class="sxs-lookup"><span data-stu-id="df105-244">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="df105-245">[Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obraz umożliwia automatyczne ustawienie aspnetcore\_adresy URL do portu 80 i wstępnie ngend pamięci podręcznej zestawów; oba te ustawienia powoduje szybsze uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="df105-245">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="df105-246">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="df105-246">Additional resources</span></span>

-   <span data-ttu-id="df105-247">**Kompilowanie zoptymalizowanych pod kątem obrazy usługi Docker z platformy ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="df105-247">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="df105-248">Tworzenie aplikacji kontenera kompilacji (CI)</span><span class="sxs-lookup"><span data-stu-id="df105-248">Building the application from a build (CI) container</span></span>

<span data-ttu-id="df105-249">Inną zaletą Docker jest, że można skompilować aplikację z kontenera wstępnie skonfigurowane, jak pokazano w rysunek 8-13, dzięki czemu nie trzeba tworzyć maszynie kompilacji lub maszyny Wirtualnej, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="df105-249">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="df105-250">Możesz użyć lub że kontener kompilacji testu przez uruchomienie jej na komputerze deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="df105-250">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="df105-251">Ale co to jest bardziej interesujące jest, których można używać tego samego kontenera kompilacji z potoku sieci CI (ciągłej integracji).</span><span class="sxs-lookup"><span data-stu-id="df105-251">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="df105-252">**Rysunek 8-13**.</span><span class="sxs-lookup"><span data-stu-id="df105-252">**Figure 8-13**.</span></span> <span data-ttu-id="df105-253">Kompilowanie plików binarnych programu .NET kompilacji kontenera docker</span><span class="sxs-lookup"><span data-stu-id="df105-253">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="df105-254">W tym scenariuszu udzielamy [aspnetcore-microsoft Zbuduj](https://hub.docker.com/r/microsoft/aspnetcore-build/) obrazu, który służy do kompilowania i tworzenie aplikacji programu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="df105-254">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="df105-255">Dane wyjściowe są umieszczane w obrazu na podstawie [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazu, który jest obrazem zoptymalizowanego środowiska uruchomieniowego zauważyć, jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="df105-255">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="df105-256">Obraz aspnetcore kompilacji zawiera wszystko, co jest potrzebne do kompilacji aplikacji platformy ASP.NET Core, w tym oprogramowanie .NET Core, zestaw SDK platformy ASP.NET, npm, Bower, Gulp, itp.</span><span class="sxs-lookup"><span data-stu-id="df105-256">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="df105-257">Potrzebujemy tych zależności w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="df105-257">We need these dependencies at build time.</span></span> <span data-ttu-id="df105-258">Ale nie chcemy wykonać je z aplikacją w czasie wykonywania, ponieważ może to spowodować obrazu niepotrzebnie.</span><span class="sxs-lookup"><span data-stu-id="df105-258">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="df105-259">W aplikacji eShopOnContainers można utworzyć aplikację z kontenera tylko uruchamiając następujące rozwiązania docker-compose polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-259">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="df105-260">Rysunek 8-14 pokazuje to polecenie uruchomione w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-260">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="df105-261">**Rysunek 8-14.**</span><span class="sxs-lookup"><span data-stu-id="df105-261">**Figure 8-14.**</span></span> <span data-ttu-id="df105-262">Tworzenie aplikacji .NET z kontenera</span><span class="sxs-lookup"><span data-stu-id="df105-262">Building your .NET application from a container</span></span>

<span data-ttu-id="df105-263">Jak widać, kontenera, w którym jest uruchomiona jest kompilacji integracji ciągłej\_1 kontenera.</span><span class="sxs-lookup"><span data-stu-id="df105-263">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="df105-264">Jest oparta na obrazie aspnetcore kompilacji, aby można go skompilować i utworzyć całej aplikacji w danym kontenerze, a nie z komputera użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df105-264">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="df105-265">Oznacza to Dlaczego w rzeczywistości jest tworzenie i kompilowanie projektów .NET Core w systemie Linux, ponieważ ten kontener jest uruchomiona na hoście systemu Linux Docker domyślne.</span><span class="sxs-lookup"><span data-stu-id="df105-265">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="df105-266">[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) plik obrazu (część eShopOnContainers) zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="df105-266">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="df105-267">Widać uruchamiania kontenera kompilacji za pomocą [aspnetcore-microsoft Zbuduj](https://hub.docker.com/r/microsoft/aspnetcore-build/) obrazu.</span><span class="sxs-lookup"><span data-stu-id="df105-267">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

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

* <span data-ttu-id="df105-268">Począwszy od **.NET Core 2.0**, `dotnet restore` polecenie zostanie wykonane automatycznie po `dotnet publish` polecenie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="df105-268">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="df105-269">Po skonfigurowaniu i uruchomieniu kontenera kompilacji uruchomieniu przywracania dotnet zestawu .NET SDK i dotnet publikowania poleceń w odniesieniu do wszystkich projektów w rozwiązaniu Aby skompilować bitów .NET.</span><span class="sxs-lookup"><span data-stu-id="df105-269">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="df105-270">W takim przypadku eShopOnContainers ma również SPA oparte na maszynie i kątową kodu klienta, również musi Sprawdź zależności JavaScript z pakietu npm, ale ta akcja nie jest powiązana z bitów .NET.</span><span class="sxs-lookup"><span data-stu-id="df105-270">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="df105-271">Dotnet publikowanie polecenie kompilacji i publikuje skompilowanych danych wyjściowych znajdujących się w folderze każdego projektu... folder /obj/Docker/publish, jak pokazano w rysunek 8 – 15.</span><span class="sxs-lookup"><span data-stu-id="df105-271">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="df105-272">**Rysunek 8 – 15.**</span><span class="sxs-lookup"><span data-stu-id="df105-272">**Figure 8-15.**</span></span> <span data-ttu-id="df105-273">Polecenie Publikuj pliki binarne wygenerowane przez dotnet</span><span class="sxs-lookup"><span data-stu-id="df105-273">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="df105-274">Tworzenie obrazów Docker z poziomu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="df105-274">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="df105-275">Po opublikowaniu danych wyjściowych aplikacji do powiązanych folderów (w każdym projekcie), następnym krokiem jest rzeczywiście tworzyć obrazy Docker.</span><span class="sxs-lookup"><span data-stu-id="df105-275">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="df105-276">Aby to zrobić, użyj kompilacji docker-compose i docker tworzą się poleceń, jak pokazano w rysunek 8-16.</span><span class="sxs-lookup"><span data-stu-id="df105-276">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="df105-277">**Rysunek 8-16.**</span><span class="sxs-lookup"><span data-stu-id="df105-277">**Figure 8-16.**</span></span> <span data-ttu-id="df105-278">Tworzenie obrazy usługi Docker i uruchamianie kontenerów</span><span class="sxs-lookup"><span data-stu-id="df105-278">Building Docker images and running the containers</span></span>

<span data-ttu-id="df105-279">Na rysunku 8-17 widać, jak docker-compose kompilacji uruchamia polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-279">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="df105-280">**Rysunek 8-17**.</span><span class="sxs-lookup"><span data-stu-id="df105-280">**Figure 8-17**.</span></span> <span data-ttu-id="df105-281">Tworzenie obrazów Docker z docker-tworzą polecenie kompilacji</span><span class="sxs-lookup"><span data-stu-id="df105-281">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="df105-282">Różnica między docker-compose kompilacji i rozwiązania docker compose zapasowej poleceń jest to, że rozwiązania docker compose zarówno kompilacji i uruchomieniu obrazów.</span><span class="sxs-lookup"><span data-stu-id="df105-282">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="df105-283">Korzystając z programu Visual Studio, te kroki są wykonywane w tle.</span><span class="sxs-lookup"><span data-stu-id="df105-283">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="df105-284">Visual Studio kompiluje aplikacji .NET, tworzy obrazy usługi Docker i wdraża kontenerów do hostów Docker.</span><span class="sxs-lookup"><span data-stu-id="df105-284">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="df105-285">Program Visual Studio oferuje dodatkowe funkcje, takie jak możliwość debugowania kontenerów uruchomionych w Docker, bezpośrednio z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df105-285">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="df105-286">Tutaj ogólną takeway jest zdolny do skompilowania aplikacji, w taki sam sposób planowaną CI/CD powinno utworzyć go — z kontenera zamiast z komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="df105-286">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="df105-287">Po obrazy utworzone, następnie wystarczy uruchomić obrazów Docker przy użyciu rozwiązania docker-tworzą zapasowej polecenia.</span><span class="sxs-lookup"><span data-stu-id="df105-287">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="df105-288">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="df105-288">Additional resources</span></span>

-   <span data-ttu-id="df105-289">**Tworzenie usługi bits z kontenera: konfigurowanie rozwiązania eShopOnContainers w środowisku interfejsu wiersza polecenia systemu Windows (dotnet interfejsu wiersza polecenia, interfejsu wiersza polecenia Docker i kodzie VS)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, — Docker - CLI- i -VS — kodu)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="df105-289">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="df105-290">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="df105-290">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span></span>
