---
title: Kubernetes — gRPC dla deweloperów WCF
description: Uruchamianie ASP.NET Core gRPC Services w klastrze Kubernetes.
ms.date: 09/02/2019
ms.openlocfilehash: 22271343f8f0d0454469b2f35e717f5b7e939294
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711287"
---
# <a name="kubernetes"></a><span data-ttu-id="a0fca-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a0fca-103">Kubernetes</span></span>

<span data-ttu-id="a0fca-104">Chociaż istnieje możliwość ręcznego uruchamiania kontenerów na hostach platformy Docker, w przypadku niezawodnych systemów produkcyjnych lepiej jest używać aparatu aranżacji kontenera do zarządzania wieloma wystąpieniami uruchomionymi na kilku serwerach w klastrze.</span><span class="sxs-lookup"><span data-stu-id="a0fca-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's better to use a container orchestration engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="a0fca-105">Dostępne są różne aparaty aranżacji kontenerów, w tym Kubernetes, Docker Swarm i Apache Mesos.</span><span class="sxs-lookup"><span data-stu-id="a0fca-105">There are various container orchestration engines available, including Kubernetes, Docker Swarm, and Apache Mesos.</span></span> <span data-ttu-id="a0fca-106">Jednak te aparaty Kubernetes są daleko i daleko najczęściej używane, więc będą skoncentrowane na tym rozdziale.</span><span class="sxs-lookup"><span data-stu-id="a0fca-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="a0fca-107">Kubernetes obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="a0fca-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="a0fca-108">**Planowanie** przebiegów kontenerów na wielu węzłach w klastrze, zapewniając zrównoważone użycie dostępnego zasobu, utrzymywanie kontenerów w przypadku awarii i obsługę aktualizacji stopniowych w nowych wersjach obrazów lub nowych konfiguracjach.</span><span class="sxs-lookup"><span data-stu-id="a0fca-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="a0fca-109">**Testy kondycji** monitorują kontenery, aby zapewnić ciągłość usługi.</span><span class="sxs-lookup"><span data-stu-id="a0fca-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="a0fca-110">**Funkcja odnajdywania usługi & DNS** obsługuje routing między usługami w ramach klastra.</span><span class="sxs-lookup"><span data-stu-id="a0fca-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="a0fca-111">Ruch przychodzący udostępnia wybrane usługi zewnętrznie i **ogólnie udostępnia równoważenie** obciążenia między wystąpieniami tych usług.</span><span class="sxs-lookup"><span data-stu-id="a0fca-111">**Ingress** exposes selected services externally and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="a0fca-112">**Zarządzanie zasobami** dołącza zasoby zewnętrzne, takie jak magazyn, do kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a0fca-112">**Resource management** attaches external resources like storage to containers.</span></span>

<span data-ttu-id="a0fca-113">W tym rozdziale szczegółowo opisano sposób wdrażania usługi ASP.NET Core gRPC i witryny sieci Web, która korzysta z usługi w klastrze Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a0fca-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="a0fca-114">Używana przykładowa aplikacja jest dostępna w repozytorium [dotnet-architectur/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="a0fca-114">The sample application used is available in the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="a0fca-115">Terminologia Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a0fca-115">Kubernetes terminology</span></span>

<span data-ttu-id="a0fca-116">Kubernetes korzysta z *konfiguracji żądanego stanu*: interfejs API służy do opisywania *obiektów, takich jak*zbiory, *wdrożenia*i *usługi*, a *płaszczyzna kontroli* wymaga wdrożenia żądanego stanu we wszystkich *węzłach* w *klastrze*.</span><span class="sxs-lookup"><span data-stu-id="a0fca-116">Kubernetes uses *desired state configuration*: the API is used to describe objects like *Pods*, *Deployments*, and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="a0fca-117">Klaster Kubernetes ma węzeł *główny* z uruchomionym *interfejsem API Kubernetes*, do którego można się komunikować programowo lub za pomocą narzędzia wiersza polecenia `kubectl`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which you can communicate with programmatically or by using the `kubectl` command-line tool.</span></span> <span data-ttu-id="a0fca-118">`kubectl` może tworzyć obiekty i zarządzać nimi za pomocą argumentów wiersza polecenia, ale najlepiej sprawdza się w przypadku plików YAML zawierających dane deklaracji dla obiektów Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a0fca-118">`kubectl` can create and manage objects through command-line arguments, but it works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="a0fca-119">Pliki YAML Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a0fca-119">Kubernetes YAML files</span></span>

<span data-ttu-id="a0fca-120">Każdy plik Kubernetes YAML będzie miał co najmniej trzy właściwości najwyższego poziomu:</span><span class="sxs-lookup"><span data-stu-id="a0fca-120">Every Kubernetes YAML file will have at least three top-level properties:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="a0fca-121">Właściwość `apiVersion` służy do określenia wersji (i interfejsu API), do której jest przeznaczony plik.</span><span class="sxs-lookup"><span data-stu-id="a0fca-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="a0fca-122">Właściwość `kind` określa rodzaj obiektu reprezentowanego przez YAML.</span><span class="sxs-lookup"><span data-stu-id="a0fca-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="a0fca-123">Właściwość `metadata` zawiera właściwości obiektu, takie jak `name`, `namespace`i `labels`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-123">The `metadata` property contains object properties like `name`, `namespace`, and `labels`.</span></span>

<span data-ttu-id="a0fca-124">Większość plików YAML Kubernetes zawiera również sekcję `spec` opisującą zasoby i konfigurację niezbędne do utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="a0fca-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="a0fca-125">Zasobników</span><span class="sxs-lookup"><span data-stu-id="a0fca-125">Pods</span></span>

<span data-ttu-id="a0fca-126">Podstawowe jednostki wykonywania w Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a0fca-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="a0fca-127">Mogą uruchamiać wiele kontenerów, ale są również używane do uruchamiania pojedynczych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a0fca-127">They can run multiple containers, but they're also used to run single containers.</span></span> <span data-ttu-id="a0fca-128">W obszarze uwzględniono również wszystkie zasoby magazynu wymagane przez kontenery oraz adres IP sieci.</span><span class="sxs-lookup"><span data-stu-id="a0fca-128">The pod also includes any storage resources required by the containers, and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="a0fca-129">Usługi</span><span class="sxs-lookup"><span data-stu-id="a0fca-129">Services</span></span>

<span data-ttu-id="a0fca-130">Usługi są meta obiektów, które opisują (lub zbiory) i umożliwiają dostęp do nich w ramach klastra, takie jak mapowanie nazwy usługi na zestaw adresów IP pod za pomocą usługi DNS klastra.</span><span class="sxs-lookup"><span data-stu-id="a0fca-130">Services are meta-objects that describe Pods (or sets of Pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses by using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="a0fca-131">Wdrożenia</span><span class="sxs-lookup"><span data-stu-id="a0fca-131">Deployments</span></span>

<span data-ttu-id="a0fca-132">Wdrożenia są obiektami *żądanych stanów* dla zasobników.</span><span class="sxs-lookup"><span data-stu-id="a0fca-132">Deployments are the *desired state* objects for Pods.</span></span> <span data-ttu-id="a0fca-133">Jeśli utworzysz element pod ręcznie, nie zostanie on ponownie uruchomiony po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="a0fca-133">If you create a pod manually, it won't be restarted when it terminates.</span></span> <span data-ttu-id="a0fca-134">Wdrożenia są używane do poinformowania klastra, którego zasobniki i ile replik tych zasobników powinna działać w obecnym czasie.</span><span class="sxs-lookup"><span data-stu-id="a0fca-134">Deployments are used to tell the cluster which Pods, and how many replicas of those Pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="a0fca-135">Inne obiekty</span><span class="sxs-lookup"><span data-stu-id="a0fca-135">Other objects</span></span>

<span data-ttu-id="a0fca-136">Klasy, usługi i wdrożenia to trzy najbardziej podstawowe typy obiektów.</span><span class="sxs-lookup"><span data-stu-id="a0fca-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="a0fca-137">Istnieją dziesiątki innych typów obiektów, które są zarządzane przez klastry Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a0fca-137">There are dozens of other object types that are managed by Kubernetes clusters.</span></span> <span data-ttu-id="a0fca-138">Aby uzyskać więcej informacji, zapoznaj się z dokumentacją dotyczącą [pojęć Kubernetes](https://kubernetes.io/docs/concepts/) .</span><span class="sxs-lookup"><span data-stu-id="a0fca-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="a0fca-139">{1&gt;Przestrzenie nazw&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a0fca-139">Namespaces</span></span>

<span data-ttu-id="a0fca-140">Klastry Kubernetes są przeznaczone do skalowania do setek lub tysięcy węzłów oraz do uruchamiania podobnych liczb usług.</span><span class="sxs-lookup"><span data-stu-id="a0fca-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes and to run similar numbers of services.</span></span> <span data-ttu-id="a0fca-141">Aby uniknąć konfliktów między nazwami obiektów, przestrzenie nazw są używane do grupowania obiektów razem w ramach większych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0fca-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="a0fca-142">Usługi Kubernetes działają w przestrzeni nazw `default`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-142">Kubernetes's own services run in a `default` namespace.</span></span> <span data-ttu-id="a0fca-143">Wszystkie obiekty użytkownika należy utworzyć we własnych przestrzeniach nazw, aby uniknąć potencjalnych konfliktów z obiektami domyślnymi lub innymi dzierżawcami w klastrze.</span><span class="sxs-lookup"><span data-stu-id="a0fca-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="a0fca-144">Wprowadzenie do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a0fca-144">Get started with Kubernetes</span></span>

<span data-ttu-id="a0fca-145">Jeśli używasz programu Docker Desktop dla systemu Windows lub pulpitu Docker dla komputerów Mac, Kubernetes jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="a0fca-145">If you're running Docker Desktop for Windows or Docker Desktop for Mac, Kubernetes is already available.</span></span> <span data-ttu-id="a0fca-146">Po prostu włącz je w sekcji **Kubernetes** w oknie **Ustawienia** :</span><span class="sxs-lookup"><span data-stu-id="a0fca-146">Just enable it in the **Kubernetes** section of the **Settings** window:</span></span>

![Włączanie Kubernetes w programie Docker Desktop](media/kubernetes/enable-kubernetes-docker-desktop.png)

<span data-ttu-id="a0fca-148">Aby uruchomić lokalny klaster Kubernetes w systemie Linux, należy wziąć pod uwagę [minikube](https://github.com/kubernetes/minikube)lub [MicroK8s](https://microk8s.io/) , jeśli dystrybucja systemu Linux obsługuje funkcję [przyciągania](https://snapcraft.io/).</span><span class="sxs-lookup"><span data-stu-id="a0fca-148">To run a local Kubernetes cluster on Linux, consider [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="a0fca-149">Aby upewnić się, że klaster działa i jest dostępny, uruchom polecenie `kubectl version`:</span><span class="sxs-lookup"><span data-stu-id="a0fca-149">To confirm that your cluster is running and accessible, run the `kubectl version` command:</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="a0fca-150">W tym przykładzie zarówno interfejs wiersza polecenia `kubectl`, jak i serwer Kubernetes mają uruchomioną wersję 1.14.6.</span><span class="sxs-lookup"><span data-stu-id="a0fca-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="a0fca-151">Każda wersja `kubectl` powinna obsługiwać poprzednią i następną wersję serwera, więc `kubectl` 1,14 powinna współpracować z wersjami Server 1,13 i 1,15.</span><span class="sxs-lookup"><span data-stu-id="a0fca-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="a0fca-152">Uruchamianie usług w usłudze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a0fca-152">Run services on Kubernetes</span></span>

<span data-ttu-id="a0fca-153">Przykładowa aplikacja ma katalog `kube`, który zawiera trzy pliki YAML.</span><span class="sxs-lookup"><span data-stu-id="a0fca-153">The sample application has a `kube` directory that contains three YAML files.</span></span> <span data-ttu-id="a0fca-154">Plik `namespace.yml` deklaruje niestandardową przestrzeń nazw: `stocks`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-154">The `namespace.yml` file declares a custom namespace: `stocks`.</span></span> <span data-ttu-id="a0fca-155">Plik `stockdata.yml` deklaruje wdrożenie i usługę dla aplikacji gRPC, a plik `stockweb.yml` deklaruje wdrożenie i usługę dla aplikacji internetowej ASP.NET Core 3,0 MVC korzystającej z usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="a0fca-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 3.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="a0fca-156">Aby użyć pliku `YAML` z `kubectl`, uruchom polecenie `apply -f`:</span><span class="sxs-lookup"><span data-stu-id="a0fca-156">To use a `YAML` file with `kubectl`, run the `apply -f` command:</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="a0fca-157">Polecenie `apply` sprawdza poprawność pliku YAML i wyświetla wszystkie błędy otrzymane z interfejsu API, ale nie czeka na utworzenie wszystkich obiektów zadeklarowanych w pliku, ponieważ może to potrwać pewien czas.</span><span class="sxs-lookup"><span data-stu-id="a0fca-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created because this can take some time.</span></span> <span data-ttu-id="a0fca-158">Użyj `kubectl get` polecenia z odpowiednimi typami obiektów, aby sprawdzić Tworzenie obiektów w klastrze.</span><span class="sxs-lookup"><span data-stu-id="a0fca-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="a0fca-159">Deklaracja przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="a0fca-159">The namespace declaration</span></span>

<span data-ttu-id="a0fca-160">Deklaracja przestrzeni nazw jest prosta i wymaga przypisania tylko `name`:</span><span class="sxs-lookup"><span data-stu-id="a0fca-160">Namespace declaration is simple and requires only assigning a `name`:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="a0fca-161">Użyj `kubectl`, aby zastosować plik `namespace.yml` i potwierdzić, że przestrzeń nazw została utworzona pomyślnie:</span><span class="sxs-lookup"><span data-stu-id="a0fca-161">Use `kubectl` to apply the `namespace.yml` file and to confirm the namespace is created successfully:</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="a0fca-162">Aplikacja StockData</span><span class="sxs-lookup"><span data-stu-id="a0fca-162">The StockData application</span></span>

<span data-ttu-id="a0fca-163">Plik `stockdata.yml` deklaruje dwa obiekty: wdrożenie i usługa.</span><span class="sxs-lookup"><span data-stu-id="a0fca-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="a0fca-164">Wdrożenie StockData</span><span class="sxs-lookup"><span data-stu-id="a0fca-164">The StockData Deployment</span></span>

<span data-ttu-id="a0fca-165">Część wdrożenia pliku YAML zawiera `spec` dla samego wdrożenia, w tym liczbę wymaganych replik i `template` dla obiektów pod, które mają być utworzone i zarządzane przez wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="a0fca-165">The Deployment part of the YAML file provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="a0fca-166">Należy pamiętać, że obiekty wdrożenia są zarządzane przez interfejs API `apps`, jak określono w `apiVersion`, a nie na głównym interfejsie API Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a0fca-166">Note that Deployment objects are managed by the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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

<span data-ttu-id="a0fca-167">Właściwość `spec.selector` jest używana do dopasowania uruchomionych zasobników do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="a0fca-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="a0fca-168">Właściwość `metadata.labels` pod musi być zgodna z właściwością `matchLabels` lub wywołanie interfejsu API zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a0fca-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="a0fca-169">Sekcja `template.spec` deklaruje kontener, który ma zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a0fca-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="a0fca-170">Podczas pracy z lokalnym klastrem Kubernetes, takim jak udostępniony przez program Docker Desktop, można określić obrazy, które zostały skompilowane lokalnie, o ile mają tag wersji.</span><span class="sxs-lookup"><span data-stu-id="a0fca-170">When you're working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a0fca-171">Domyślnie Kubernetes będzie zawsze sprawdzać i próbować ściągnąć nowy obraz.</span><span class="sxs-lookup"><span data-stu-id="a0fca-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="a0fca-172">Jeśli nie można znaleźć obrazu w żadnym ze znanych repozytoriów, tworzenie pod zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a0fca-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="a0fca-173">Aby można było korzystać z obrazów lokalnych, należy ustawić `imagePullPolicy` na `Never`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="a0fca-174">Właściwość `ports` określa, które porty kontenerów powinny być publikowane w obszarze.</span><span class="sxs-lookup"><span data-stu-id="a0fca-174">The `ports` property specifies which container ports should be published on the Pod.</span></span> <span data-ttu-id="a0fca-175">Obraz `stockservice` uruchamia usługę na standardowym porcie HTTP, więc jest publikowany port 80.</span><span class="sxs-lookup"><span data-stu-id="a0fca-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="a0fca-176">Sekcja `resources` stosuje limity zasobów do kontenera działającego w ramach.</span><span class="sxs-lookup"><span data-stu-id="a0fca-176">The `resources` section applies resource limits to the container running within the Pod.</span></span> <span data-ttu-id="a0fca-177">Jest to dobre rozwiązanie, ponieważ uniemożliwia osobie korzystającej z używania całego dostępnego procesora lub pamięci w węźle.</span><span class="sxs-lookup"><span data-stu-id="a0fca-177">This is a good practice because it prevents an individual Pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="a0fca-178">ASP.NET Core 3,0 został zoptymalizowany i dostrojony do uruchamiania w kontenerach z ograniczoną ilością zasobów.</span><span class="sxs-lookup"><span data-stu-id="a0fca-178">ASP.NET Core 3.0 has been optimized and tuned to run in resource-limited containers.</span></span> <span data-ttu-id="a0fca-179">Obraz `dotnet/core/aspnet` Docker ustawia zmienną środowiskową, aby poinformować środowisko uruchomieniowe `dotnet`, że znajduje się w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="a0fca-179">The `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="a0fca-180">Usługa StockData</span><span class="sxs-lookup"><span data-stu-id="a0fca-180">The StockData Service</span></span>

<span data-ttu-id="a0fca-181">Część usługi pliku YAML deklaruje usługę, która zapewnia dostęp do zasobników w klastrze.</span><span class="sxs-lookup"><span data-stu-id="a0fca-181">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

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

<span data-ttu-id="a0fca-182">`spec` usługi używa właściwości `selector` w celu dopasowania `Pods`, w tym przypadku jest to wyszukiwanie w przypadku, gdy są używane etykiety `run: stockdata`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-182">The Service `spec` uses the `selector` property to match running `Pods`, in this case looking for Pods that have a label `run: stockdata`.</span></span> <span data-ttu-id="a0fca-183">Określony `port` na zgodnych podst. jest publikowany przez nazwę usługi.</span><span class="sxs-lookup"><span data-stu-id="a0fca-183">The specified `port` on matching Pods is published by the named service.</span></span> <span data-ttu-id="a0fca-184">Inne zasobniki działające w przestrzeni nazw `stocks` mogą uzyskać dostęp do protokołu HTTP w tej usłudze, używając `http://stockdata` jako adresu.</span><span class="sxs-lookup"><span data-stu-id="a0fca-184">Other Pods running in the `stocks` namespace can access HTTP on this service by using `http://stockdata` as the address.</span></span> <span data-ttu-id="a0fca-185">Na podst. w innych przestrzeniach nazw można używać nazwy hosta `http://stockdata.stocks`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-185">Pods running in other namespaces can use the `http://stockdata.stocks` host name.</span></span> <span data-ttu-id="a0fca-186">Dostęp do usługi wzajemnej przestrzeni nazw można kontrolować przy użyciu [zasad sieciowych](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span><span class="sxs-lookup"><span data-stu-id="a0fca-186">You can control cross-namespace service access by using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="a0fca-187">Wdrażanie aplikacji StockData</span><span class="sxs-lookup"><span data-stu-id="a0fca-187">Deploy the StockData application</span></span>

<span data-ttu-id="a0fca-188">Użyj `kubectl`, aby zastosować plik `stockdata.yml` i potwierdzić, że wdrożenie i usługa zostały utworzone:</span><span class="sxs-lookup"><span data-stu-id="a0fca-188">Use `kubectl` to apply the `stockdata.yml` file and confirm that the Deployment and Service were created:</span></span>

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

### <a name="the-stockweb-application"></a><span data-ttu-id="a0fca-189">Aplikacja StockWeb</span><span class="sxs-lookup"><span data-stu-id="a0fca-189">The StockWeb application</span></span>

<span data-ttu-id="a0fca-190">Plik `stockweb.yml` deklaruje wdrożenie i usługę dla aplikacji MVC.</span><span class="sxs-lookup"><span data-stu-id="a0fca-190">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

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

#### <a name="environment-variables"></a><span data-ttu-id="a0fca-191">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="a0fca-191">Environment variables</span></span>

<span data-ttu-id="a0fca-192">Sekcja `env` obiektu wdrożenia określa zmienne środowiskowe, które mają być ustawiane w kontenerze, w którym są uruchomione obrazy `stockweb:1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-192">The `env` section of the Deployment object specifies environment variables to be set in the container that's running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="a0fca-193">Zmienna środowiskowa **`StockData__Address`** zostanie zamapowana na ustawienie konfiguracji `StockData:Address` z dostawcą konfiguracji EnvironmentVariables.</span><span class="sxs-lookup"><span data-stu-id="a0fca-193">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="a0fca-194">To ustawienie powoduje użycie podwójnego podkreślenia między nazwami w oddzielnymi sekcjach.</span><span class="sxs-lookup"><span data-stu-id="a0fca-194">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="a0fca-195">Adres używa nazwy usługi `stockdata`, która działa w tej samej przestrzeni nazw Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a0fca-195">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="a0fca-196">Zmienna środowiskowa **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** ustawia przełącznik <xref:System.AppContext>, który włącza nieszyfrowane połączenia HTTP/2 dla <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="a0fca-196">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="a0fca-197">Ta zmienna środowiskowa wykonuje te same czynności co w przypadku ustawienia przełącznika w kodzie, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="a0fca-197">This environment variable does the same thing as setting the switch in code, as shown here:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="a0fca-198">Jeśli użyjesz zmiennej środowiskowej dla przełącznika, możesz łatwo zmienić kontekst w zależności od kontekstu, w którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="a0fca-198">If you use an environment variable for the switch, you can easily change the context depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="a0fca-199">Typy usług</span><span class="sxs-lookup"><span data-stu-id="a0fca-199">Service types</span></span>

<span data-ttu-id="a0fca-200">Właściwość `type: NodePort` służy do udostępniania aplikacji sieci Web spoza klastra.</span><span class="sxs-lookup"><span data-stu-id="a0fca-200">The `type: NodePort` property is used to make the web application accessible from outside the cluster.</span></span> <span data-ttu-id="a0fca-201">Ten typ właściwości powoduje, że Kubernetes publikuje port 80 w usłudze do dowolnego portu w zewnętrznych gniazdach sieciowych klastra.</span><span class="sxs-lookup"><span data-stu-id="a0fca-201">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="a0fca-202">Przypisany port można znaleźć za pomocą polecenia `kubectl get service`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-202">You can find the assigned port by using the `kubectl get service` command.</span></span>

<span data-ttu-id="a0fca-203">Usługa `stockdata` nie powinna być dostępna spoza klastra, dlatego używa typu domyślnego, `ClusterIP`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-203">The `stockdata` Service shouldn't be accessible from outside the cluster, so it uses the default type, `ClusterIP`.</span></span>

<span data-ttu-id="a0fca-204">Systemy produkcyjne najprawdopodobniej będą korzystać z zintegrowanego modułu równoważenia obciążenia w celu udostępnienia aplikacji publicznych klientom zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="a0fca-204">Production systems will most likely use an integrated load balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="a0fca-205">Usługi uwidocznione w ten sposób powinny używać typu `LoadBalancer`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-205">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="a0fca-206">Aby uzyskać więcej informacji na temat typów usług, zobacz dokumentację [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .</span><span class="sxs-lookup"><span data-stu-id="a0fca-206">For more information on Service types, see the [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="a0fca-207">Wdrażanie aplikacji StockWeb</span><span class="sxs-lookup"><span data-stu-id="a0fca-207">Deploy the StockWeb application</span></span>

<span data-ttu-id="a0fca-208">Użyj `kubectl`, aby zastosować plik `stockweb.yml` i potwierdzić, że wdrożenie i usługa zostały utworzone:</span><span class="sxs-lookup"><span data-stu-id="a0fca-208">Use `kubectl` to apply the `stockweb.yml` file and confirm that the Deployment and Service were created:</span></span>

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

<span data-ttu-id="a0fca-209">Dane wyjściowe polecenia `get service` pokazują, że port HTTP został opublikowany na porcie 32564 w sieci zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="a0fca-209">The output of the `get service` command shows that the HTTP port has been published to port 32564 on the external network.</span></span> <span data-ttu-id="a0fca-210">W przypadku programu Docker Desktop będzie to localhost.</span><span class="sxs-lookup"><span data-stu-id="a0fca-210">For Docker Desktop, this will be localhost.</span></span> <span data-ttu-id="a0fca-211">Możesz uzyskać dostęp do aplikacji, przechodząc do `http://localhost:32564`.</span><span class="sxs-lookup"><span data-stu-id="a0fca-211">You can access the application by browsing to `http://localhost:32564`.</span></span>

### <a name="test-the-application"></a><span data-ttu-id="a0fca-212">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a0fca-212">Test the application</span></span>

<span data-ttu-id="a0fca-213">Aplikacja StockWeb wyświetla listę zasobów NASDAQ, które są pobierane z prostej usługi żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="a0fca-213">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="a0fca-214">W tej demonstracji każdy wiersz zawiera również unikatowy identyfikator wystąpienia usługi, która go zwróciła.</span><span class="sxs-lookup"><span data-stu-id="a0fca-214">For this demonstration, each line also shows the unique ID of the Service instance that returned it.</span></span>

![Zrzut ekranu StockWeb](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="a0fca-216">Jeśli liczba replik usługi `stockdata` została zwiększona, może wystąpić konieczność zmiany wartości **serwera** z wiersza na wiersz, ale w rzeczywistości wszystkie rekordy 100 są zawsze zwracane z tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a0fca-216">If the number of replicas of the `stockdata` Service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="a0fca-217">Po odświeżeniu strony co kilka sekund identyfikator serwera pozostaje taki sam.</span><span class="sxs-lookup"><span data-stu-id="a0fca-217">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="a0fca-218">Dlaczego tak się dzieje?</span><span class="sxs-lookup"><span data-stu-id="a0fca-218">Why does this happen?</span></span> <span data-ttu-id="a0fca-219">W tym miejscu znajdują się dwa czynniki.</span><span class="sxs-lookup"><span data-stu-id="a0fca-219">There are two factors at play here.</span></span>

<span data-ttu-id="a0fca-220">Najpierw system odnajdowania usług Kubernetes domyślnie używa równoważenia obciążenia z działaniem okrężnym.</span><span class="sxs-lookup"><span data-stu-id="a0fca-220">First, the Kubernetes Service discovery system uses round-robin load balancing by default.</span></span> <span data-ttu-id="a0fca-221">Podczas pierwszej kwerendy serwera DNS zostanie zwrócony pierwszy pasujący adres IP dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a0fca-221">The first time the DNS server is queried, it will return the first matching IP address for the Service.</span></span> <span data-ttu-id="a0fca-222">Następnym razem zwróci Następny adres IP z listy i tak dalej, aż do końca.</span><span class="sxs-lookup"><span data-stu-id="a0fca-222">The next time, it will return the next IP address in the list, and so on, until the end.</span></span> <span data-ttu-id="a0fca-223">W tym momencie pętla wraca do początku.</span><span class="sxs-lookup"><span data-stu-id="a0fca-223">At that point it loops back to the start.</span></span>

<span data-ttu-id="a0fca-224">Następnie `HttpClient` używany dla klienta gRPC aplikacji StockWeb jest tworzony i zarządzany przez [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), a jedno wystąpienie tego klienta jest używane dla każdego wywołania strony.</span><span class="sxs-lookup"><span data-stu-id="a0fca-224">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="a0fca-225">Klient wykonuje tylko jedno wyszukiwanie DNS, więc wszystkie żądania są kierowane na ten sam adres IP.</span><span class="sxs-lookup"><span data-stu-id="a0fca-225">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="a0fca-226">I ponieważ `HttpClientHandler` jest buforowana ze względu na wydajność, wiele żądań w szybkim pomyślnym będzie używać tego samego adresu IP, do momentu wygaśnięcia zbuforowanego wpisu DNS lub wystąpienia programu *obsługi zostanie usunięte* z jakiegoś powodu.</span><span class="sxs-lookup"><span data-stu-id="a0fca-226">And because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="a0fca-227">Wynika to z tego, że domyślne żądania do usługi gRPC nie są zrównoważone dla wszystkich wystąpień tej usługi w klastrze.</span><span class="sxs-lookup"><span data-stu-id="a0fca-227">The result is that by default requests to a gRPC Service aren't balanced across all instances of that Service in the cluster.</span></span> <span data-ttu-id="a0fca-228">Różni klienci będą korzystać z różnych wystąpień, ale nie zagwarantuje dobrego rozkładu żądań lub zrównoważonego użycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="a0fca-228">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests or a balanced use of resources.</span></span>

<span data-ttu-id="a0fca-229">Następny rozdział, [siatki usług](service-mesh.md), spowoduje rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="a0fca-229">The next chapter, [Service meshes](service-mesh.md), will address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a0fca-230">[Poprzednie](docker.md)
>[dalej](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="a0fca-230">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
