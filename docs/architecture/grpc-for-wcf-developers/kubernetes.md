---
title: Kubernetes — gRPC dla deweloperów WCF
description: Uruchamianie ASP.NET Core gRPC Services w klastrze Kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3af1b92ade106cf2338816ec69e6b13312681339
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184408"
---
# <a name="kubernetes"></a><span data-ttu-id="718ac-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="718ac-103">Kubernetes</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="718ac-104">Chociaż istnieje możliwość ręcznego uruchamiania kontenerów na hostach platformy Docker, w przypadku niezawodnych systemów produkcyjnych zaleca się używanie aparatu aranżacji kontenera do zarządzania wieloma wystąpieniami uruchomionymi na kilku serwerach w klastrze.</span><span class="sxs-lookup"><span data-stu-id="718ac-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's preferable to use a Container Orchestration Engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="718ac-105">Dostępne są różne aparaty aranżacji kontenerów, w tym Kubernetes, Docker Swarm i Apache Mesos.</span><span class="sxs-lookup"><span data-stu-id="718ac-105">There are various Container Orchestration Engines available, including Kubernetes, Docker Swarm and Apache Mesos.</span></span> <span data-ttu-id="718ac-106">Jednak te aparaty Kubernetes są daleko i daleko najczęściej używane, więc będą skoncentrowane na tym rozdziale.</span><span class="sxs-lookup"><span data-stu-id="718ac-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="718ac-107">Kubernetes obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="718ac-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="718ac-108">**Planowanie** przebiegów kontenerów na wielu węzłach w klastrze, zapewniając zrównoważone użycie dostępnego zasobu, utrzymywanie kontenerów w przypadku awarii i obsługę aktualizacji stopniowych w nowych wersjach obrazów lub nowych konfiguracjach.</span><span class="sxs-lookup"><span data-stu-id="718ac-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="718ac-109">**Testy kondycji** monitorują kontenery, aby zapewnić ciągłość usługi.</span><span class="sxs-lookup"><span data-stu-id="718ac-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="718ac-110">**Funkcja odnajdywania usługi & DNS** obsługuje routing między usługami w ramach klastra.</span><span class="sxs-lookup"><span data-stu-id="718ac-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="718ac-111">Ruch przychodzący udostępnia wybrane usługi zewnętrznie i **ogólnie udostępnia równoważenie** obciążenia między wystąpieniami tych usług.</span><span class="sxs-lookup"><span data-stu-id="718ac-111">**Ingress** exposes selected services externally, and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="718ac-112">**Zarządzanie zasobami** dołącza zasoby zewnętrzne, takie jak magazynowanie do kontenerów.</span><span class="sxs-lookup"><span data-stu-id="718ac-112">**Resource management** attaches external resources such as storage to containers.</span></span>

<span data-ttu-id="718ac-113">W tym rozdziale szczegółowo opisano sposób wdrażania usługi ASP.NET Core gRPC i witryny sieci Web, która korzysta z usługi w klastrze Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="718ac-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="718ac-114">Używana przykładowa aplikacja jest dostępna w repozytorium [RendleLabs/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="718ac-114">The sample application used is available from on the [RendleLabs/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub,</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="718ac-115">Terminologia Kubernetes</span><span class="sxs-lookup"><span data-stu-id="718ac-115">Kubernetes terminology</span></span>

<span data-ttu-id="718ac-116">Kubernetes korzysta z *konfiguracji żądanego stanu*: interfejs API jest używany do opisywania *obiektów, takich jak*zbiory, *wdrożenia* i *usługi*, a *płaszczyzna kontroli* wymaga wdrożenia żądanego stanu we wszystkich *węzłach.* w *klastrze*.</span><span class="sxs-lookup"><span data-stu-id="718ac-116">Kubernetes uses *desired state configuration*: the API is used to describe objects such as *Pods*, *Deployments* and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="718ac-117">Klaster Kubernetes ma węzeł *główny* z uruchomionym *interfejsem API Kubernetes*, który może być przekazywany programowo `kubectl` lub za pomocą narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="718ac-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which can be communicated with programmatically or using the `kubectl` command-line tool.</span></span> <span data-ttu-id="718ac-118">`kubectl`może tworzyć obiekty i zarządzać nimi za pomocą argumentów wiersza polecenia, ale najlepiej sprawdza się w przypadku plików YAML zawierających dane deklaracji dla obiektów Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="718ac-118">`kubectl` can create and manage objects using command-line arguments, but works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="718ac-119">Pliki YAML Kubernetes</span><span class="sxs-lookup"><span data-stu-id="718ac-119">Kubernetes YAML files</span></span>

<span data-ttu-id="718ac-120">Każdy plik Kubernetes YAML będzie miał co najmniej trzy właściwości najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="718ac-120">Every Kubernetes YAML file will have at least three top-level properties.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="718ac-121">`apiVersion` Właściwość służy do określenia wersji (i interfejsu API), do której jest przeznaczony plik.</span><span class="sxs-lookup"><span data-stu-id="718ac-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="718ac-122">`kind` Właściwość określa rodzaj obiektu reprezentowanego przez YAML.</span><span class="sxs-lookup"><span data-stu-id="718ac-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="718ac-123">Właściwość zawiera właściwości obiektu, takie jak `name`, `namespace`, lub `labels`. `metadata`</span><span class="sxs-lookup"><span data-stu-id="718ac-123">The `metadata` property contains object properties such as `name`, `namespace`, or `labels`.</span></span>

<span data-ttu-id="718ac-124">Większość plików YAML Kubernetes również `spec` zawiera sekcję opisującą zasoby i konfigurację niezbędne do utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="718ac-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="718ac-125">Zasobników</span><span class="sxs-lookup"><span data-stu-id="718ac-125">Pods</span></span>

<span data-ttu-id="718ac-126">Podstawowe jednostki wykonywania w Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="718ac-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="718ac-127">Mogą uruchamiać wiele kontenerów, ale są również używane do uruchamiania pojedynczych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="718ac-127">They can run multiple containers, but are also used to run single containers.</span></span> <span data-ttu-id="718ac-128">W obszarze uwzględniono również wszystkie zasoby magazynu wymagane przez kontenery oraz adres IP sieci.</span><span class="sxs-lookup"><span data-stu-id="718ac-128">The pod also includes any storage resources required by the container(s), and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="718ac-129">Usługi</span><span class="sxs-lookup"><span data-stu-id="718ac-129">Services</span></span>

<span data-ttu-id="718ac-130">Usługi są meta obiektów, które opisują (lub zbiory) i umożliwiają dostęp do nich w ramach klastra, takie jak mapowanie nazwy usługi na zestaw adresów IP pod za pomocą usługi DNS klastra.</span><span class="sxs-lookup"><span data-stu-id="718ac-130">Services are meta-objects that describe pods (or sets of pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="718ac-131">Wdrożenia</span><span class="sxs-lookup"><span data-stu-id="718ac-131">Deployments</span></span>

<span data-ttu-id="718ac-132">Wdrożenia są *opisanymi obiektami stanu* dla zasobników.</span><span class="sxs-lookup"><span data-stu-id="718ac-132">Deployments are the *described state* objects for Pods.</span></span> <span data-ttu-id="718ac-133">Jeśli utworzysz element pod ręcznie, po jego zakończeniu nie zostanie on ponownie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="718ac-133">If you create a Pod manually, when it terminates it won't be restarted.</span></span> <span data-ttu-id="718ac-134">Wdrożenia są używane do poinformowania klastra, którego zasobniki i ile replik tych zasobników powinna działać w obecnym czasie.</span><span class="sxs-lookup"><span data-stu-id="718ac-134">Deployments are used to tell the cluster which pods, and how many replicas of those pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="718ac-135">Inne obiekty</span><span class="sxs-lookup"><span data-stu-id="718ac-135">Other objects</span></span>

<span data-ttu-id="718ac-136">Klasy, usługi i wdrożenia to trzy najbardziej podstawowe typy obiektów.</span><span class="sxs-lookup"><span data-stu-id="718ac-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="718ac-137">Istnieją dziesiątki innych typów obiektów, które są zarządzane przez klaster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="718ac-137">There are dozens of other types of object that are managed by a Kubernetes cluster.</span></span> <span data-ttu-id="718ac-138">Aby uzyskać więcej informacji, zapoznaj się z dokumentacją dotyczącą [pojęć Kubernetes](https://kubernetes.io/docs/concepts/) .</span><span class="sxs-lookup"><span data-stu-id="718ac-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="718ac-139">Namespaces</span><span class="sxs-lookup"><span data-stu-id="718ac-139">Namespaces</span></span>

<span data-ttu-id="718ac-140">Klastry Kubernetes są przeznaczone do skalowania do setek lub tysięcy węzłów i uruchamiania podobnej liczby usług.</span><span class="sxs-lookup"><span data-stu-id="718ac-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes, and run similar numbers of services.</span></span> <span data-ttu-id="718ac-141">Aby uniknąć konfliktów między nazwami obiektów, przestrzenie nazw są używane do grupowania obiektów razem w ramach większych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="718ac-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="718ac-142">Kubernetes własne usługi działają w `default` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="718ac-142">Kubernetes own services run in a `default` namespace.</span></span> <span data-ttu-id="718ac-143">Wszystkie obiekty użytkownika należy utworzyć we własnych przestrzeniach nazw, aby uniknąć potencjalnych konfliktów z obiektami domyślnymi lub innymi dzierżawcami w klastrze.</span><span class="sxs-lookup"><span data-stu-id="718ac-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="718ac-144">Wprowadzenie do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="718ac-144">Get started with Kubernetes</span></span>

<span data-ttu-id="718ac-145">Jeśli używasz programu Docker Desktop dla systemu Windows lub macOS, Kubernetes jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="718ac-145">If you're running Docker Desktop for Windows or macOS, Kubernetes is already available.</span></span> <span data-ttu-id="718ac-146">Po prostu włącz go w sekcji Kubernetes w oknie Ustawienia.</span><span class="sxs-lookup"><span data-stu-id="718ac-146">Just enable it in the Kubernetes section of the Settings window.</span></span>

![Włączanie Kubernetes w programie Docker Desktop](media/kubernetes/enable-kubernetes-docker-desktop.png)

<span data-ttu-id="718ac-148">Aby uruchomić lokalny klaster Kubernetes w systemie Linux, zapoznaj się z [minikube](https://github.com/kubernetes/minikube)lub [MicroK8s](https://microk8s.io/) , jeśli dystrybucja systemu Linux obsługuje funkcję [przyciągania](https://snapcraft.io/).</span><span class="sxs-lookup"><span data-stu-id="718ac-148">To run a local Kubernetes cluster in Linux, look at [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="718ac-149">Aby sprawdzić, czy klaster działa i jest dostępny, uruchom `kubectl version` polecenie.</span><span class="sxs-lookup"><span data-stu-id="718ac-149">To check that your cluster is running and accessible, run the `kubectl version` command.</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="718ac-150">W tym przykładzie zarówno `kubectl` interfejs wiersza polecenia, jak i serwer Kubernetes mają uruchomioną wersję 1.14.6.</span><span class="sxs-lookup"><span data-stu-id="718ac-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="718ac-151">Każda wersja programu `kubectl` ma obsługiwać poprzednią i następną wersję serwera, więc `kubectl` 1,14 powinna współpracować z wersjami Server 1,13 i 1,15.</span><span class="sxs-lookup"><span data-stu-id="718ac-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="718ac-152">Uruchamianie usług w usłudze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="718ac-152">Run services on Kubernetes</span></span>

<span data-ttu-id="718ac-153">Przykładowa aplikacja ma `kube` katalog zawierający trzy pliki YAML.</span><span class="sxs-lookup"><span data-stu-id="718ac-153">The sample application has a `kube` directory containing three YAML files.</span></span> <span data-ttu-id="718ac-154">Plik deklaruje niestandardową przestrzeń `stocks`nazw,. `namespace.yml`</span><span class="sxs-lookup"><span data-stu-id="718ac-154">The `namespace.yml` file declares a custom namespace, `stocks`.</span></span> <span data-ttu-id="718ac-155">Plik deklaruje wdrożenie i usługę dla aplikacji gRPC, `stockweb.yml` a plik deklaruje wdrożenie i usługę dla aplikacji sieci Web ASP.NET Core 3,0 MVC korzystającej z usługi gRPC. `stockdata.yml`</span><span class="sxs-lookup"><span data-stu-id="718ac-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 3.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="718ac-156">Aby użyć `YAML` pliku z `kubectl`, użyj `apply -f` polecenia.</span><span class="sxs-lookup"><span data-stu-id="718ac-156">To use a `YAML` file with `kubectl`, use the `apply -f` command.</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="718ac-157">`apply` Polecenie sprawdzi ważność pliku YAML i wyświetli wszelkie błędy otrzymane z interfejsu API, ale nie poczeka na utworzenie wszystkich obiektów zadeklarowanych w pliku, ponieważ może to potrwać trochę czasu.</span><span class="sxs-lookup"><span data-stu-id="718ac-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created as this can take some time.</span></span> <span data-ttu-id="718ac-158">`kubectl get` Użyj polecenia z odpowiednimi typami obiektów, aby sprawdzić Tworzenie obiektów w klastrze.</span><span class="sxs-lookup"><span data-stu-id="718ac-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="718ac-159">Deklaracja przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="718ac-159">The namespace declaration</span></span>

<span data-ttu-id="718ac-160">Deklaracja przestrzeni nazw jest prosta i wymaga przypisania tylko `name`elementu.</span><span class="sxs-lookup"><span data-stu-id="718ac-160">Namespace declaration is simple and requires only assigning a `name`.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="718ac-161">Użyj `kubectl` , aby `namespace.yml` zastosować plik, i sprawdź, czy przestrzeń nazw została utworzona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="718ac-161">Use `kubectl` to apply the `namespace.yml` file and check the namespace is created successfully.</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="718ac-162">Aplikacja StockData</span><span class="sxs-lookup"><span data-stu-id="718ac-162">The StockData application</span></span>

<span data-ttu-id="718ac-163">`stockdata.yml` Plik deklaruje dwa obiekty: wdrożenie i usługa.</span><span class="sxs-lookup"><span data-stu-id="718ac-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="718ac-164">Wdrożenie StockData</span><span class="sxs-lookup"><span data-stu-id="718ac-164">The StockData Deployment</span></span>

<span data-ttu-id="718ac-165">Część wdrożenia zapewnia `spec` dla samego wdrożenia, w tym liczbę wymaganych replik `template` i dla obiektów pod, które mają być utworzone i zarządzane przez wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="718ac-165">The Deployment part provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="718ac-166">Należy pamiętać, że obiekty wdrożenia są zarządzane `apps` przy użyciu interfejsu API, `apiVersion`jak określono w, a nie głównego interfejsu API Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="718ac-166">Note that Deployment objects are managed with the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 1
  template:
    metadata:
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

<span data-ttu-id="718ac-167">`spec.selector` Właściwość służy do dopasowania uruchomionych zasobników do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="718ac-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="718ac-168">`metadata.labels` Właściwość "pod" musi być zgodna `matchLabels` z właściwością lub wywołanie interfejsu API zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="718ac-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="718ac-169">`template.spec` Sekcja deklaruje kontener, który ma zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="718ac-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="718ac-170">Podczas pracy z lokalnym klastrem Kubernetes, takim jak udostępniony przez program Docker Desktop, można określić obrazy, które zostały skompilowane lokalnie, o ile mają tag wersji.</span><span class="sxs-lookup"><span data-stu-id="718ac-170">When working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="718ac-171">Domyślnie Kubernetes będzie zawsze sprawdzać i próbować ściągnąć nowy obraz.</span><span class="sxs-lookup"><span data-stu-id="718ac-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="718ac-172">Jeśli nie można znaleźć obrazu w żadnym ze znanych repozytoriów, tworzenie pod zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="718ac-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="718ac-173">Aby można było korzystać z obrazów lokalnych, `imagePullPolicy` należy `Never`ustawić na.</span><span class="sxs-lookup"><span data-stu-id="718ac-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="718ac-174">`ports` Właściwość określa, które porty kontenerów powinny być publikowane w obszarze.</span><span class="sxs-lookup"><span data-stu-id="718ac-174">The `ports` property specifies which container ports should be published on the Pod.</span></span>  <span data-ttu-id="718ac-175">`stockservice` Obraz uruchamia usługę na standardowym porcie http, więc jest publikowany port 80.</span><span class="sxs-lookup"><span data-stu-id="718ac-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="718ac-176">`resources` Sekcja stosuje limity zasobów do kontenera działającego w ramach.</span><span class="sxs-lookup"><span data-stu-id="718ac-176">The `resources` section applies resource limits to the container running within the pod.</span></span> <span data-ttu-id="718ac-177">Jest to dobre rozwiązanie, ponieważ uniemożliwia to osobie korzystającej z używania całego dostępnego procesora lub pamięci w węźle.</span><span class="sxs-lookup"><span data-stu-id="718ac-177">This is good practice as it prevents an individual pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="718ac-178">ASP.NET Core 3,0 został zoptymalizowany i dostrojony do uruchamiania w kontenerach z ograniczeniami zasobów, `dotnet/core/aspnet` a obraz platformy Docker ustawia zmienną środowiskową, `dotnet` aby poinformować środowisko uruchomieniowe o tym, że znajduje się w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="718ac-178">ASP.NET Core 3.0 has been optimized and tuned to run in resource-limited containers, and the `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="718ac-179">Usługa StockData</span><span class="sxs-lookup"><span data-stu-id="718ac-179">The StockData Service</span></span>

<span data-ttu-id="718ac-180">Część usługi pliku YAML deklaruje usługę, która zapewnia dostęp do zasobników w klastrze.</span><span class="sxs-lookup"><span data-stu-id="718ac-180">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

<span data-ttu-id="718ac-181">Specyfikacja usługi używa `selector` właściwości w celu dopasowania do działania `Pods`, w tym przypadku wyszukiwanie zasobników z etykietą. `run: stockdata`</span><span class="sxs-lookup"><span data-stu-id="718ac-181">The Service spec uses the `selector` property to match running `Pods`, in this case looking for Pods with a label `run: stockdata`.</span></span> <span data-ttu-id="718ac-182">Określone `port` na zgodnych podstych są publikowane przez nazwaną usługę.</span><span class="sxs-lookup"><span data-stu-id="718ac-182">The specified `port` on matching Pods are published by the named service.</span></span> <span data-ttu-id="718ac-183">Inne zasobniki działające `stocks` w przestrzeni nazw mogą uzyskać dostęp do protokołu `http://stockdata` http w tej usłudze, używając jako adresu.</span><span class="sxs-lookup"><span data-stu-id="718ac-183">Other Pods running in the `stocks` namespace can access HTTP on this service using `http://stockdata` as the address.</span></span> <span data-ttu-id="718ac-184">Na `http://stockdata.stocks` podst. w innych przestrzeniach nazw można używać nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="718ac-184">Pods running in other namespaces can use the `http://stockdata.stocks` hostname.</span></span> <span data-ttu-id="718ac-185">Dostęp do usługi wzajemnej przestrzeni nazw można kontrolować przy użyciu [zasad sieciowych](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span><span class="sxs-lookup"><span data-stu-id="718ac-185">You can control cross-namespace service access using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="718ac-186">Wdrażanie aplikacji StockData</span><span class="sxs-lookup"><span data-stu-id="718ac-186">Deploy the StockData application</span></span>

<span data-ttu-id="718ac-187">Użyj `kubectl` , aby `stockdata.yml` zastosować plik, i sprawdź, czy zostało utworzone wdrożenie i usługa.</span><span class="sxs-lookup"><span data-stu-id="718ac-187">Use `kubectl` to apply the `stockdata.yml` file and check that the Deployment and Service were created.</span></span>

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a><span data-ttu-id="718ac-188">Aplikacja StockWeb</span><span class="sxs-lookup"><span data-stu-id="718ac-188">The StockWeb application</span></span>

<span data-ttu-id="718ac-189">`stockweb.yml` Plik deklaruje wdrożenie i usługę dla aplikacji MVC.</span><span class="sxs-lookup"><span data-stu-id="718ac-189">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a><span data-ttu-id="718ac-190">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="718ac-190">Environment variables</span></span>

<span data-ttu-id="718ac-191">Sekcja obiektu wdrożenia określa zmienne środowiskowe do ustawienia w kontenerze, w `stockweb:1.0.0` którym są uruchomione obrazy. `env`</span><span class="sxs-lookup"><span data-stu-id="718ac-191">The `env` section of the Deployment object specifies environment variables to be set in the container running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="718ac-192">Zmienna środowiskowa zostanie zamapowana `StockData:Address` na ustawienie konfiguracji z dostawcą konfiguracji EnvironmentVariables. **`StockData__Address`**</span><span class="sxs-lookup"><span data-stu-id="718ac-192">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="718ac-193">To ustawienie powoduje użycie podwójnego podkreślenia między nazwami w oddzielnymi sekcjach.</span><span class="sxs-lookup"><span data-stu-id="718ac-193">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="718ac-194">Adres używa nazwy `stockdata` usługi, która jest uruchomiona w tej samej przestrzeni nazw Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="718ac-194">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="718ac-195">Zmienna środowiskowa <xref:System.AppContext> ustawia przełącznik, który włącza nieszyfrowane połączenia HTTP/2 dla <xref:System.Net.Http.HttpClient>programu. **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`**</span><span class="sxs-lookup"><span data-stu-id="718ac-195">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="718ac-196">Ta zmienna środowiskowa jest odpowiednikiem ustawienia przełącznika w kodzie, jak pokazano tutaj.</span><span class="sxs-lookup"><span data-stu-id="718ac-196">This environment variable is the equivalent of setting the switch in code as shown here.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="718ac-197">Użycie zmiennej środowiskowej dla przełącznika oznacza, że ustawienie można łatwo zmienić w zależności od kontekstu, w którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="718ac-197">Using an environment variable for the switch means the setting can easily be changed depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="718ac-198">Typy usług</span><span class="sxs-lookup"><span data-stu-id="718ac-198">Service types</span></span>

<span data-ttu-id="718ac-199">Aby aplikacja sieci Web była dostępna spoza klastra, `type: NodePort` zostanie użyta właściwość.</span><span class="sxs-lookup"><span data-stu-id="718ac-199">To make the Web application accessible from outside the cluster, the `type: NodePort` property is used.</span></span> <span data-ttu-id="718ac-200">Ten typ właściwości powoduje, że Kubernetes publikuje port 80 w usłudze do dowolnego portu w zewnętrznych gniazdach sieciowych klastra.</span><span class="sxs-lookup"><span data-stu-id="718ac-200">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="718ac-201">Przypisany port można znaleźć za pomocą `kubectl get service` polecenia.</span><span class="sxs-lookup"><span data-stu-id="718ac-201">The port assigned can be found using the `kubectl get service` command.</span></span>

<span data-ttu-id="718ac-202">Usługa nie powinna być dostępna spoza klastra, dlatego użyto typu domyślnego, `ClusterIP`. `stockdata`</span><span class="sxs-lookup"><span data-stu-id="718ac-202">The `stockdata` service shouldn't be accessible from outside the cluster, so it used the default type, `ClusterIP`.</span></span>

<span data-ttu-id="718ac-203">Systemy produkcyjne najprawdopodobniej będą korzystać z zintegrowanego modułu równoważenia obciążenia w celu udostępnienia aplikacji publicznych klientom zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="718ac-203">Production systems will most likely use an integrated load-balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="718ac-204">Usługi uwidocznione w ten sposób powinny używać `LoadBalancer` typu.</span><span class="sxs-lookup"><span data-stu-id="718ac-204">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="718ac-205">Aby uzyskać więcej informacji na temat typów usług, zobacz dokumentację [Kubernetes "Publishing Services"](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .</span><span class="sxs-lookup"><span data-stu-id="718ac-205">For more information on service types, see the [Kubernetes' Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="718ac-206">Wdrażanie aplikacji StockWeb</span><span class="sxs-lookup"><span data-stu-id="718ac-206">Deploy the StockWeb application</span></span>

<span data-ttu-id="718ac-207">Użyj `kubectl` , aby `stockweb.yml` zastosować plik, i sprawdź, czy zostało utworzone wdrożenie i usługa.</span><span class="sxs-lookup"><span data-stu-id="718ac-207">Use `kubectl` to apply the `stockweb.yml` file and check that the Deployment and Service were created.</span></span>

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

<span data-ttu-id="718ac-208">Dane wyjściowe `get service` polecenia pokazują, że port HTTP został opublikowany na porcie `32564` w sieci zewnętrznej; dla programu Docker Desktop będzie to localhost.</span><span class="sxs-lookup"><span data-stu-id="718ac-208">The output from the `get service` command shows that the HTTP port has been published to port `32564` on the external network; for Docker Desktop, this will be localhost.</span></span> <span data-ttu-id="718ac-209">Dostęp do aplikacji można uzyskać, przechodząc `http://localhost:32564`do witryny.</span><span class="sxs-lookup"><span data-stu-id="718ac-209">The application can be accessed by browsing to `http://localhost:32564`.</span></span>

### <a name="testing-the-application"></a><span data-ttu-id="718ac-210">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="718ac-210">Testing the application</span></span>

<span data-ttu-id="718ac-211">Aplikacja StockWeb wyświetla listę zasobów NASDAQ, które są pobierane z prostej usługi żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="718ac-211">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="718ac-212">W celach demonstracyjnych każdy wiersz zawiera również unikatowy identyfikator wystąpienia usługi, która go zwróciła.</span><span class="sxs-lookup"><span data-stu-id="718ac-212">For demonstration purposes, each line also shows the unique ID of the service instance that returned it.</span></span>

![Zrzut ekranu StockWeb](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="718ac-214">Jeśli liczba replik `stockdata` usługi została zwiększona, może wystąpić konieczność zmiany wartości **serwera** z wiersza na wiersz, ale w rzeczywistości wszystkie rekordy 100 są zawsze zwracane z tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="718ac-214">If the number of replicas of the `stockdata` service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="718ac-215">Po odświeżeniu strony co kilka sekund identyfikator serwera pozostaje taki sam.</span><span class="sxs-lookup"><span data-stu-id="718ac-215">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="718ac-216">Dlaczego tak się dzieje?</span><span class="sxs-lookup"><span data-stu-id="718ac-216">Why does this happen?</span></span> <span data-ttu-id="718ac-217">W tym miejscu znajdują się dwa czynniki.</span><span class="sxs-lookup"><span data-stu-id="718ac-217">There are two factors at play here.</span></span>

<span data-ttu-id="718ac-218">Najpierw system odnajdowania usług Kubernetes domyślnie używa funkcji równoważenia obciążenia "Round-Robin".</span><span class="sxs-lookup"><span data-stu-id="718ac-218">First, the Kubernetes service discovery system uses "round-robin" load-balancing by default.</span></span> <span data-ttu-id="718ac-219">Podczas pierwszej kwerendy serwera DNS zostanie zwrócony pierwszy pasujący adres IP dla usługi.</span><span class="sxs-lookup"><span data-stu-id="718ac-219">The first time the DNS server is queried, it will return the first matching IP address for the service.</span></span> <span data-ttu-id="718ac-220">Następnym razem, następnym adresem IP na liście itd. aż do końca, w którym momencie zostanie on ponownie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="718ac-220">The next time, the next IP address in the list, and so on, until the end, at which point it loops back to the start.</span></span>

<span data-ttu-id="718ac-221">Po drugie, `HttpClient` używany dla klienta gRPC aplikacji StockWeb jest tworzony i zarządzany przez [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), a jedno wystąpienie tego klienta jest używane dla każdego wywołania strony.</span><span class="sxs-lookup"><span data-stu-id="718ac-221">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="718ac-222">Klient wykonuje tylko jedno wyszukiwanie DNS, więc wszystkie żądania są kierowane na ten sam adres IP.</span><span class="sxs-lookup"><span data-stu-id="718ac-222">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="718ac-223">Ponadto, ponieważ `HttpClientHandler` jest buforowana ze względu na wydajność, wiele żądań w szybkim pomyślnym będzie używać tego samego adresu IP, do momentu wygaśnięcia zbuforowanego wpisu DNS lub wystąpienia programu *obsługi zostanie usunięte* z jakiegoś powodu.</span><span class="sxs-lookup"><span data-stu-id="718ac-223">Furthermore, because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="718ac-224">Oznacza to, że domyślnie żądania kierowane do usługi gRPC nie są zrównoważone dla wszystkich wystąpień tej usługi w klastrze.</span><span class="sxs-lookup"><span data-stu-id="718ac-224">This means that by default requests to a gRPC service aren't balanced across all instances of that service in the cluster.</span></span> <span data-ttu-id="718ac-225">Różni klienci będą korzystać z różnych wystąpień, ale nie zagwarantuje dobrego rozkładu żądań i zrównoważonego użycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="718ac-225">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests and a balanced use of resources.</span></span>

<span data-ttu-id="718ac-226">Następny rozdział, [siatki usługi](service-mesh.md), zobacz, jak rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="718ac-226">The next chapter, [Service Meshes](service-mesh.md), will look at how to address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="718ac-227">[Poprzedni](docker.md)
>[Następny](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="718ac-227">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
