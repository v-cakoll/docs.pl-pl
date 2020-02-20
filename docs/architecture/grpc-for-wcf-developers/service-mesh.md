---
title: Siatki usług — gRPC dla deweloperów WCF
description: Kierowanie i równoważenie żądań do usług gRPC w klastrze Kubernetes przy użyciu sieci siatkowej usługi.
ms.date: 09/02/2019
ms.openlocfilehash: a29d6893e585c7eb60c847cef0149afeeaebcdab
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503387"
---
# <a name="service-meshes"></a><span data-ttu-id="6effb-103">Siatki usług</span><span class="sxs-lookup"><span data-stu-id="6effb-103">Service meshes</span></span>

<span data-ttu-id="6effb-104">Siatka usług to składnik infrastruktury, który kontroluje żądania usługi routingu w ramach sieci.</span><span class="sxs-lookup"><span data-stu-id="6effb-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="6effb-105">Siatki usług mogą obsługiwać wszelkiego rodzaju problemy dotyczące poziomu sieci w klastrze Kubernetes, w tym:</span><span class="sxs-lookup"><span data-stu-id="6effb-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="6effb-106">Odnajdowanie usług</span><span class="sxs-lookup"><span data-stu-id="6effb-106">Service discovery</span></span>
- <span data-ttu-id="6effb-107">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="6effb-107">Load balancing</span></span>
- <span data-ttu-id="6effb-108">Odporność na uszkodzenia</span><span class="sxs-lookup"><span data-stu-id="6effb-108">Fault tolerance</span></span>
- <span data-ttu-id="6effb-109">Szyfrowanie</span><span class="sxs-lookup"><span data-stu-id="6effb-109">Encryption</span></span>
- <span data-ttu-id="6effb-110">Monitorowanie</span><span class="sxs-lookup"><span data-stu-id="6effb-110">Monitoring</span></span>

<span data-ttu-id="6effb-111">Oczka usługi Kubernetes działają przez dodanie dodatkowego kontenera zwanego *serwerem proxy przyczepki*do każdego z nich znajdującego się w sieci.</span><span class="sxs-lookup"><span data-stu-id="6effb-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="6effb-112">Serwer proxy przejmuje obsługę wszystkich żądań sieci przychodzących i wychodzących.</span><span class="sxs-lookup"><span data-stu-id="6effb-112">The proxy takes over handling all inbound and outbound network requests.</span></span> <span data-ttu-id="6effb-113">Następnie można zachować konfigurację i zarządzanie kwestiami sieci oddzielnymi od kontenerów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6effb-113">You can then keep configuration and management of networking matters separate from the application containers.</span></span> <span data-ttu-id="6effb-114">W wielu przypadkach separacja nie wymaga żadnych zmian w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6effb-114">In many cases, this separation doesn't require any changes to the application code.</span></span>

<span data-ttu-id="6effb-115">W [poprzednim przykładzie rozdziału](kubernetes.md#test-the-application)żądania gRPC z aplikacji sieci Web były kierowane do pojedynczego wystąpienia usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="6effb-115">In the [previous chapter's example](kubernetes.md#test-the-application), the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="6effb-116">Dzieje się tak, ponieważ nazwa hosta usługi jest rozpoznawana jako adres IP, a adres IP jest buforowany przez okres istnienia wystąpienia `HttpClientHandler`.</span><span class="sxs-lookup"><span data-stu-id="6effb-116">This happens because the service's host name is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="6effb-117">Może być możliwe obejście tego problemu przez obsługę wyszukiwania DNS ręcznie lub tworzenie wielu klientów.</span><span class="sxs-lookup"><span data-stu-id="6effb-117">It might be possible to work around this by handling DNS lookups manually or creating multiple clients.</span></span> <span data-ttu-id="6effb-118">Jednak to obejście komplikuje kod aplikacji bez dodawania żadnej wartości biznesowej ani klienta.</span><span class="sxs-lookup"><span data-stu-id="6effb-118">But this workaround would complicate the application code without adding any business or customer value.</span></span>

<span data-ttu-id="6effb-119">W przypadku korzystania z sieci usługi, żądania z kontenera aplikacji są wysyłane do serwera proxy przyczepki.</span><span class="sxs-lookup"><span data-stu-id="6effb-119">When you use a service mesh, the requests from the application container are sent to the sidecar proxy.</span></span> <span data-ttu-id="6effb-120">Serwer proxy przyczepki może następnie rozproszyć je w sposób inteligentny we wszystkich wystąpieniach innej usługi.</span><span class="sxs-lookup"><span data-stu-id="6effb-120">The sidecar proxy can then distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="6effb-121">Siatka może również:</span><span class="sxs-lookup"><span data-stu-id="6effb-121">The mesh can also:</span></span>

- <span data-ttu-id="6effb-122">Bezproblemowo reaguj na błędy poszczególnych wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="6effb-122">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="6effb-123">Obsługuj semantykę ponownych prób dla wywołań zakończonych niepowodzeniem lub przekroczeń limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="6effb-123">Handle retry semantics for failed calls or timeouts.</span></span>
- <span data-ttu-id="6effb-124">Przekieruj żądania zakończone niepowodzeniem do alternatywnego wystąpienia bez powrotu do aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="6effb-124">Reroute failed requests to an alternate instance without returning to the client application.</span></span>

<span data-ttu-id="6effb-125">Poniższy zrzut ekranu przedstawia aplikację StockWeb z uruchomioną siatką usługi.</span><span class="sxs-lookup"><span data-stu-id="6effb-125">The following screenshot shows the StockWeb application running with the Linkerd service mesh.</span></span> <span data-ttu-id="6effb-126">Nie wprowadzono żadnych zmian w kodzie aplikacji, a obraz platformy Docker nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="6effb-126">There are no changes to the application code, and the Docker image isn't being used.</span></span> <span data-ttu-id="6effb-127">Jedyną wymaganą zmianą jest dodanie adnotacji do wdrożenia w plikach YAML dla usług `stockdata` i `stockweb`.</span><span class="sxs-lookup"><span data-stu-id="6effb-127">The only change required was the addition of an annotation to the deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb z siatką usługi](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="6effb-129">W kolumnie **serwer** można zobaczyć, że żądania z aplikacji StockWeb zostały rozesłane do obu replik usługi StockData, mimo że nie pochodzą one z jednego wystąpienia `HttpClient` w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6effb-129">You can see from the **Server** column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="6effb-130">W rzeczywistości, Jeśli przeglądasz kod, zobaczysz, że wszystkie żądania 100 do usługi StockData są nawiązywane równocześnie przy użyciu tego samego wystąpienia `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="6effb-130">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously by using the same `HttpClient` instance.</span></span> <span data-ttu-id="6effb-131">Z siatką usług te żądania będą zrównoważone dla wielu wystąpień usługi, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="6effb-131">With the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="6effb-132">Siatki usług dotyczą tylko ruchu w klastrze.</span><span class="sxs-lookup"><span data-stu-id="6effb-132">Service meshes apply only to traffic within a cluster.</span></span> <span data-ttu-id="6effb-133">W przypadku klientów zewnętrznych zapoznaj się z następnym rozdziałem, [równoważenia obciążenia](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="6effb-133">For external clients, see the next chapter, [Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="6effb-134">Opcje siatki usługi</span><span class="sxs-lookup"><span data-stu-id="6effb-134">Service mesh options</span></span>

<span data-ttu-id="6effb-135">Trzy implementacje usług ogólnego przeznaczenia są obecnie dostępne do użycia z Kubernetes: [Istio](https://istio.io), [Konsolidatored](https://linkerd.io)i [Consul Connect](https://consul.io/mesh.html).</span><span class="sxs-lookup"><span data-stu-id="6effb-135">Three general-purpose service mesh implementations are currently available for use with Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io), and [Consul Connect](https://consul.io/mesh.html).</span></span> <span data-ttu-id="6effb-136">Wszystkie trzy żądania routingu/proxy żądań, szyfrowania ruchu, odporności, uwierzytelniania hosta do hosta i kontroli ruchu.</span><span class="sxs-lookup"><span data-stu-id="6effb-136">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="6effb-137">Wybór sieci usługi zależy od wielu czynników:</span><span class="sxs-lookup"><span data-stu-id="6effb-137">Choosing a service mesh depends on multiple factors:</span></span>

- <span data-ttu-id="6effb-138">Specyficzne dla organizacji wymagania dotyczące kosztów, zgodności, płatnych planów pomocy technicznej itd.</span><span class="sxs-lookup"><span data-stu-id="6effb-138">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="6effb-139">Charakter klastra, jego rozmiar, liczba wdrożonych usług i ilość ruchu sieciowego w sieci klastra.</span><span class="sxs-lookup"><span data-stu-id="6effb-139">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="6effb-140">Łatwość wdrażania i zarządzania siatką oraz używania jej z usługami.</span><span class="sxs-lookup"><span data-stu-id="6effb-140">Ease of deploying and managing the mesh and using it with services.</span></span>

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="6effb-141">Przykład: Dodaj konsolidator do wdrożenia</span><span class="sxs-lookup"><span data-stu-id="6effb-141">Example: Add Linkerd to a deployment</span></span>

<span data-ttu-id="6effb-142">W tym przykładzie dowiesz się, jak używać łączącej się sieci usługi z aplikacją *StockKube* z [poprzedniej sekcji](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="6effb-142">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="6effb-143">Aby postępować zgodnie z tym przykładem, należy [zainstalować konsolidator interfejsu wiersza polecenia](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="6effb-143">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="6effb-144">Pliki binarne systemu Windows można pobrać z sekcji zawierającej listę wydań usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="6effb-144">You can download Windows binaries from the section that lists GitHub releases.</span></span> <span data-ttu-id="6effb-145">Upewnij się, że korzystasz z najnowszej *stabilnej* wersji, a nie jednego z wersji brzegowych.</span><span class="sxs-lookup"><span data-stu-id="6effb-145">Be sure to use the most recent *stable* release and not one of the edge releases.</span></span>

<span data-ttu-id="6effb-146">Mając zainstalowany interfejs wiersza polecenia z konsolidatorem, postępuj zgodnie z instrukcjami [wprowadzenie](https://linkerd.io/2/getting-started/index.html) , aby zainstalować elementy konsolidatora w klastrze Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="6effb-146">With the Linkerd CLI installed, follow the [Getting Started](https://linkerd.io/2/getting-started/index.html) instructions to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="6effb-147">Instrukcje są proste, a instalacja powinna trwać tylko kilka minut na lokalnym wystąpieniu Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="6effb-147">The instructions are straightforward, and installation should take only a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="6effb-148">Dodawanie konsolidatora do wdrożeń Kubernetes</span><span class="sxs-lookup"><span data-stu-id="6effb-148">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="6effb-149">Konsolidatord CLI udostępnia polecenie `inject`, aby dodać niezbędne sekcje i właściwości do plików Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="6effb-149">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="6effb-150">Można uruchomić polecenie i zapisać dane wyjściowe do nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="6effb-150">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="6effb-151">Możesz sprawdzić nowe pliki, aby zobaczyć, jakie zmiany zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="6effb-151">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="6effb-152">W przypadku obiektów wdrożenia adnotacja metadanych jest dodawana w celu poinformowania o konieczności dodania kontenera proxy przyczepki do elementu pod, gdy zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="6effb-152">For deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the pod when it's created.</span></span>

<span data-ttu-id="6effb-153">Możliwe jest również potokowanie danych wyjściowych polecenia `linkerd inject`, aby `kubectl` bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="6effb-153">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="6effb-154">Następujące polecenia będą działały w programie PowerShell lub dowolnej powłoce systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="6effb-154">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="6effb-155">Inspekcja usług na wbudowanym pulpicie nawigacyjnym</span><span class="sxs-lookup"><span data-stu-id="6effb-155">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="6effb-156">Otwórz łączący pulpit nawigacyjny za pomocą interfejsu wiersza polecenia `linkerd`.</span><span class="sxs-lookup"><span data-stu-id="6effb-156">Open the Linkerd dashboard by using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="6effb-157">Pulpit nawigacyjny zawiera szczegółowe informacje o wszystkich usługach, które są połączone z siatką.</span><span class="sxs-lookup"><span data-stu-id="6effb-157">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Łączący się pulpit nawigacyjny pokazujący aplikacje StockKube](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="6effb-159">Jeśli zwiększy się liczbę replik usługi StockData gRPC, jak pokazano w poniższym przykładzie, i Odśwież stronę StockWeb w przeglądarce, w kolumnie **serwer** powinny być widoczne różne identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="6effb-159">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the **Server** column.</span></span> <span data-ttu-id="6effb-160">Ten miks wskazuje, że wszystkie dostępne wystąpienia obsługują żądania.</span><span class="sxs-lookup"><span data-stu-id="6effb-160">This mix indicates that all the available instances are serving requests.</span></span>

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
><span data-ttu-id="6effb-161">[Poprzednie](kubernetes.md)
>[dalej](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="6effb-161">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
