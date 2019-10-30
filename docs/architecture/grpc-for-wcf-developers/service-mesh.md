---
title: Siatki usług — gRPC dla deweloperów WCF
description: Kierowanie i równoważenie żądań do usług gRPC w klastrze Kubernetes przy użyciu sieci siatkowej usługi.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6bdfa57ba47ba0105092d1c140705599b7023c78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090176"
---
# <a name="service-meshes"></a><span data-ttu-id="8bbac-103">Siatki usług</span><span class="sxs-lookup"><span data-stu-id="8bbac-103">Service meshes</span></span>

<span data-ttu-id="8bbac-104">Siatka usług to składnik infrastruktury, który kontroluje żądania usługi routingu w ramach sieci.</span><span class="sxs-lookup"><span data-stu-id="8bbac-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="8bbac-105">Siatki usług mogą obsługiwać wszelkiego rodzaju problemy dotyczące poziomu sieci w klastrze Kubernetes, w tym:</span><span class="sxs-lookup"><span data-stu-id="8bbac-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="8bbac-106">Odnajdowanie usług</span><span class="sxs-lookup"><span data-stu-id="8bbac-106">Service discovery</span></span>
- <span data-ttu-id="8bbac-107">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="8bbac-107">Load balancing</span></span>
- <span data-ttu-id="8bbac-108">Odporność na uszkodzenia</span><span class="sxs-lookup"><span data-stu-id="8bbac-108">Fault tolerance</span></span>
- <span data-ttu-id="8bbac-109">Szyfrowanie</span><span class="sxs-lookup"><span data-stu-id="8bbac-109">Encryption</span></span>
- <span data-ttu-id="8bbac-110">Monitorowanie</span><span class="sxs-lookup"><span data-stu-id="8bbac-110">Monitoring</span></span>

<span data-ttu-id="8bbac-111">Oczka usługi Kubernetes działają przez dodanie dodatkowego kontenera zwanego *serwerem proxy przyczepki*do każdego z nich znajdującego się w sieci.</span><span class="sxs-lookup"><span data-stu-id="8bbac-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="8bbac-112">Serwer proxy przejmuje obsługę wszystkich żądań sieci przychodzących i wychodzących, umożliwiając Konfigurowanie i zarządzanie kwestiami sieci, które mają być oddzielone od kontenerów aplikacji, a także w wielu przypadkach, bez konieczności wprowadzania jakichkolwiek zmian w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bbac-112">The proxy takes over handling all inbound and outbound network requests, allowing configuration and management of networking matters to be kept separate from the application containers and, in many cases, without requiring any changes to the application code.</span></span>

<span data-ttu-id="8bbac-113">Zapoznaj się z [poprzednim przykładem rozdziału](kubernetes.md#testing-the-application), w którym wszystkie żądania gRPC z aplikacji sieci Web były kierowane do pojedynczego wystąpienia usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="8bbac-113">Take the [previous chapter's example](kubernetes.md#testing-the-application), where the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="8bbac-114">Dzieje się tak, ponieważ nazwa hosta usługi jest rozpoznawana jako adres IP, a adres IP jest buforowany przez okres istnienia wystąpienia `HttpClientHandler`.</span><span class="sxs-lookup"><span data-stu-id="8bbac-114">This happens because the service's hostname is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="8bbac-115">Możliwe jest obejście tego problemu przez obsługę wyszukiwań DNS ręcznie lub tworzenie wielu klientów, ale może to znacząco poskomplikowanić kod aplikacji bez konieczności dodawania żadnej wartości biznesowej lub klientów.</span><span class="sxs-lookup"><span data-stu-id="8bbac-115">It might be possible to work around this by handling DNS lookups manually or creating multiple clients, but this would complicate the application code considerably without adding any business or customer value.</span></span>

<span data-ttu-id="8bbac-116">Za pomocą sieci usługi, żądania z kontenera aplikacji są wysyłane do serwera proxy przyczepki, który może być wzajemnie dystrybuowany we wszystkich wystąpieniach innej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bbac-116">Using a service mesh, the requests from the application container are sent to the sidecar proxy, which can distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="8bbac-117">Siatka może również:</span><span class="sxs-lookup"><span data-stu-id="8bbac-117">The mesh can also:</span></span>

- <span data-ttu-id="8bbac-118">Bezproblemowo reaguj na błędy poszczególnych wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="8bbac-118">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="8bbac-119">Obsługa semantyki ponawiania dla wywołań zakończonych niepowodzeniem lub przekroczeń limitu czasu</span><span class="sxs-lookup"><span data-stu-id="8bbac-119">Handle retry semantics for failed calls or timeouts</span></span>
- <span data-ttu-id="8bbac-120">Przekieruj żądania zakończone niepowodzeniem do alternatywnego wystąpienia bez powrotu do aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="8bbac-120">Reroute failed requests to an alternate instance without returning to the client application at all.</span></span>

<span data-ttu-id="8bbac-121">Poniższy zrzut ekranu przedstawia aplikację StockWeb z uruchomioną siatką usługi, bez zmian w kodzie aplikacji, a nawet w używanym obrazie platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8bbac-121">The following screenshot shows the StockWeb application running with the Linkerd service mesh, with no changes to the application code, or even the Docker image being used.</span></span> <span data-ttu-id="8bbac-122">Jedyną wymaganą zmianą jest dodanie adnotacji do wdrożenia w plikach YAML dla usług `stockdata` i `stockweb`.</span><span class="sxs-lookup"><span data-stu-id="8bbac-122">The only change required was the addition of an annotation to the Deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb z siatką usługi](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="8bbac-124">W kolumnie serwer można zobaczyć, że żądania z aplikacji StockWeb zostały rozesłane do obu replik usługi StockData, mimo że nie pochodzą one z jednego wystąpienia `HttpClient` w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bbac-124">You can see from the Server column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="8bbac-125">W rzeczywistości, Jeśli przeglądasz kod, zobaczysz, że wszystkie żądania 100 do usługi StockData są nawiązywane równocześnie przy użyciu tego samego wystąpienia `HttpClient`, ale z siatką usługi, te żądania będą równoważone w przypadku dostępności wielu wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="8bbac-125">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously using the same `HttpClient` instance, yet with the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="8bbac-126">Siatki usług dotyczą tylko ruchu w klastrze.</span><span class="sxs-lookup"><span data-stu-id="8bbac-126">Service meshes only apply to traffic within a cluster.</span></span> <span data-ttu-id="8bbac-127">W przypadku klientów zewnętrznych zapoznaj [się z następnym rozdziałem, równoważenia obciążenia](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="8bbac-127">For external clients, see [the next chapter, Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="8bbac-128">Opcje siatki usługi</span><span class="sxs-lookup"><span data-stu-id="8bbac-128">Service mesh options</span></span>

<span data-ttu-id="8bbac-129">Istnieją trzy implementacje usług ogólnego przeznaczenia, które są obecnie dostępne do użycia z Kubernetes: Istio, Konsolidatored i Consul Connect.</span><span class="sxs-lookup"><span data-stu-id="8bbac-129">There are three general-purpose service mesh implementations currently available for use with Kubernetes: Istio, Linkerd, and Consul Connect.</span></span> <span data-ttu-id="8bbac-130">Wszystkie trzy żądania routingu/proxy żądań, szyfrowania ruchu, odporności, uwierzytelniania hosta do hosta i kontroli ruchu.</span><span class="sxs-lookup"><span data-stu-id="8bbac-130">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="8bbac-131">Wybór sieci usług zależy od wielu czynników:</span><span class="sxs-lookup"><span data-stu-id="8bbac-131">Choosing a service mesh depends multiple factors:</span></span>

- <span data-ttu-id="8bbac-132">Specyficzne dla organizacji wymagania dotyczące kosztów, zgodności, płatnych planów pomocy technicznej itd.</span><span class="sxs-lookup"><span data-stu-id="8bbac-132">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="8bbac-133">Charakter klastra, jego rozmiar, liczba wdrożonych usług i ilość ruchu sieciowego w sieci klastra.</span><span class="sxs-lookup"><span data-stu-id="8bbac-133">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="8bbac-134">Łatwość wdrażania i zarządzania siatką oraz używania jej z usługami.</span><span class="sxs-lookup"><span data-stu-id="8bbac-134">Ease of deploying and managing the mesh and using it with services.</span></span>

<span data-ttu-id="8bbac-135">Więcej informacji na temat każdej sieci usługi jest dostępnych w swoich witrynach sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8bbac-135">More information on each service mesh is available from their respective websites.</span></span>

- [<span data-ttu-id="8bbac-136">**Istio** — istio.IO</span><span class="sxs-lookup"><span data-stu-id="8bbac-136">**Istio** - istio.io</span></span>](https://istio.io)
- [<span data-ttu-id="8bbac-137">**Konsolidatored** -linkerd.IO</span><span class="sxs-lookup"><span data-stu-id="8bbac-137">**Linkerd** - linkerd.io</span></span>](https://linkerd.io)
- [<span data-ttu-id="8bbac-138">**Consul** — Consul.IO/Mesh.html</span><span class="sxs-lookup"><span data-stu-id="8bbac-138">**Consul** - consul.io/mesh.html</span></span>](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="8bbac-139">Przykład: Dodaj konsolidator do wdrożenia</span><span class="sxs-lookup"><span data-stu-id="8bbac-139">Example: add Linkerd to a deployment</span></span>

<span data-ttu-id="8bbac-140">W tym przykładzie dowiesz się, jak używać łączącej się sieci usługi z aplikacją *StockKube* z [poprzedniej sekcji](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="8bbac-140">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="8bbac-141">Aby postępować zgodnie z tym przykładem, należy [zainstalować konsolidator interfejsu wiersza polecenia](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="8bbac-141">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="8bbac-142">Pliki binarne systemu Windows można pobrać z sekcji wydań usługi GitHub. Upewnij się, że korzystasz z najnowszej **stabilnej** wersji, a nie jednego z wersji brzegowych.</span><span class="sxs-lookup"><span data-stu-id="8bbac-142">Windows binaries can be downloaded from the GitHub releases section; make sure to use the most recent **stable** release and not one of the edge releases.</span></span>

<span data-ttu-id="8bbac-143">Mając zainstalowany interfejs wiersza polecenia z konsolidatorem, postępuj zgodnie z instrukcjami [*wprowadzenie* na konsolidatorze witryny sieci Web], aby zainstalować elementy konsolidatora w klastrze Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="8bbac-143">With the Linkerd CLI installed, follow the [*Getting Started* instructions on the Linkerd web site] to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="8bbac-144">Instrukcje są bezpośrednie i instalacja powinna trwać tylko kilka minut na lokalnym wystąpieniu usługi Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="8bbac-144">The instructions are straight-forward and installation should only take a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="8bbac-145">Dodawanie konsolidatora do wdrożeń Kubernetes</span><span class="sxs-lookup"><span data-stu-id="8bbac-145">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="8bbac-146">Konsolidatord CLI udostępnia polecenie `inject`, aby dodać niezbędne sekcje i właściwości do plików Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="8bbac-146">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="8bbac-147">Można uruchomić polecenie i zapisać dane wyjściowe do nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="8bbac-147">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="8bbac-148">Możesz sprawdzić nowe pliki, aby zobaczyć, jakie zmiany zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="8bbac-148">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="8bbac-149">W przypadku obiektów wdrożenia adnotacja metadanych jest dodawana w celu poinformowania o konieczności dodania kontenera proxy przyczepki do elementu pod, gdy zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="8bbac-149">For Deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the Pod when it's created.</span></span>

<span data-ttu-id="8bbac-150">Możliwe jest również potokowanie danych wyjściowych polecenia `linkerd inject`, aby `kubectl` bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8bbac-150">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="8bbac-151">Następujące polecenia będą działały w programie PowerShell lub dowolnej powłoce systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="8bbac-151">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="8bbac-152">Inspekcja usług na wbudowanym pulpicie nawigacyjnym</span><span class="sxs-lookup"><span data-stu-id="8bbac-152">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="8bbac-153">Uruchom konsolidator pulpitu nawigacyjnego za pomocą interfejsu wiersza polecenia `linkerd`.</span><span class="sxs-lookup"><span data-stu-id="8bbac-153">Launch the Linkerd dashboard using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="8bbac-154">Pulpit nawigacyjny zawiera szczegółowe informacje o wszystkich usługach, które są połączone z siatką.</span><span class="sxs-lookup"><span data-stu-id="8bbac-154">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Łączący się pulpit nawigacyjny pokazujący aplikacje StockKube](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="8bbac-156">W przypadku zwiększenia liczby replik usługi StockData gRPC, jak pokazano w poniższym przykładzie, i odświeżanie strony StockWeb w przeglądarce, w kolumnie serwer powinien być widoczny szereg identyfikatorów wskazujący, że żądania są obsługiwane przez wszystkie dostępne wystąpienia .</span><span class="sxs-lookup"><span data-stu-id="8bbac-156">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the Server column, indicating that requests are being served by all the available instances.</span></span>

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
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
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

>[!div class="step-by-step"]
><span data-ttu-id="8bbac-157">[Poprzedni](kubernetes.md)
>[Następny](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="8bbac-157">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
