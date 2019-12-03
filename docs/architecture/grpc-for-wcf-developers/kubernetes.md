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
# <a name="kubernetes"></a>Kubernetes

Chociaż istnieje możliwość ręcznego uruchamiania kontenerów na hostach platformy Docker, w przypadku niezawodnych systemów produkcyjnych lepiej jest używać aparatu aranżacji kontenera do zarządzania wieloma wystąpieniami uruchomionymi na kilku serwerach w klastrze. Dostępne są różne aparaty aranżacji kontenerów, w tym Kubernetes, Docker Swarm i Apache Mesos. Jednak te aparaty Kubernetes są daleko i daleko najczęściej używane, więc będą skoncentrowane na tym rozdziale.

Kubernetes obejmuje następujące funkcje:

- **Planowanie** przebiegów kontenerów na wielu węzłach w klastrze, zapewniając zrównoważone użycie dostępnego zasobu, utrzymywanie kontenerów w przypadku awarii i obsługę aktualizacji stopniowych w nowych wersjach obrazów lub nowych konfiguracjach.
- **Testy kondycji** monitorują kontenery, aby zapewnić ciągłość usługi.
- **Funkcja odnajdywania usługi & DNS** obsługuje routing między usługami w ramach klastra.
- Ruch przychodzący udostępnia wybrane usługi zewnętrznie i **ogólnie udostępnia równoważenie** obciążenia między wystąpieniami tych usług.
- **Zarządzanie zasobami** dołącza zasoby zewnętrzne, takie jak magazyn, do kontenerów.

W tym rozdziale szczegółowo opisano sposób wdrażania usługi ASP.NET Core gRPC i witryny sieci Web, która korzysta z usługi w klastrze Kubernetes. Używana przykładowa aplikacja jest dostępna w repozytorium [dotnet-architectur/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w witrynie GitHub.

## <a name="kubernetes-terminology"></a>Terminologia Kubernetes

Kubernetes korzysta z *konfiguracji żądanego stanu*: interfejs API służy do opisywania *obiektów, takich jak*zbiory, *wdrożenia*i *usługi*, a *płaszczyzna kontroli* wymaga wdrożenia żądanego stanu we wszystkich *węzłach* w *klastrze*. Klaster Kubernetes ma węzeł *główny* z uruchomionym *interfejsem API Kubernetes*, do którego można się komunikować programowo lub za pomocą narzędzia wiersza polecenia `kubectl`. `kubectl` może tworzyć obiekty i zarządzać nimi za pomocą argumentów wiersza polecenia, ale najlepiej sprawdza się w przypadku plików YAML zawierających dane deklaracji dla obiektów Kubernetes.

### <a name="kubernetes-yaml-files"></a>Pliki YAML Kubernetes

Każdy plik Kubernetes YAML będzie miał co najmniej trzy właściwości najwyższego poziomu:

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

Właściwość `apiVersion` służy do określenia wersji (i interfejsu API), do której jest przeznaczony plik. Właściwość `kind` określa rodzaj obiektu reprezentowanego przez YAML. Właściwość `metadata` zawiera właściwości obiektu, takie jak `name`, `namespace`i `labels`.

Większość plików YAML Kubernetes zawiera również sekcję `spec` opisującą zasoby i konfigurację niezbędne do utworzenia obiektu.

### <a name="pods"></a>Zasobników

Podstawowe jednostki wykonywania w Kubernetes. Mogą uruchamiać wiele kontenerów, ale są również używane do uruchamiania pojedynczych kontenerów. W obszarze uwzględniono również wszystkie zasoby magazynu wymagane przez kontenery oraz adres IP sieci.

### <a name="services"></a>Usługi

Usługi są meta obiektów, które opisują (lub zbiory) i umożliwiają dostęp do nich w ramach klastra, takie jak mapowanie nazwy usługi na zestaw adresów IP pod za pomocą usługi DNS klastra.

### <a name="deployments"></a>Wdrożenia

Wdrożenia są obiektami *żądanych stanów* dla zasobników. Jeśli utworzysz element pod ręcznie, nie zostanie on ponownie uruchomiony po zakończeniu. Wdrożenia są używane do poinformowania klastra, którego zasobniki i ile replik tych zasobników powinna działać w obecnym czasie.

### <a name="other-objects"></a>Inne obiekty

Klasy, usługi i wdrożenia to trzy najbardziej podstawowe typy obiektów. Istnieją dziesiątki innych typów obiektów, które są zarządzane przez klastry Kubernetes. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją dotyczącą [pojęć Kubernetes](https://kubernetes.io/docs/concepts/) .

### <a name="namespaces"></a>{1&gt;Przestrzenie nazw&lt;1}

Klastry Kubernetes są przeznaczone do skalowania do setek lub tysięcy węzłów oraz do uruchamiania podobnych liczb usług. Aby uniknąć konfliktów między nazwami obiektów, przestrzenie nazw są używane do grupowania obiektów razem w ramach większych aplikacji. Usługi Kubernetes działają w przestrzeni nazw `default`. Wszystkie obiekty użytkownika należy utworzyć we własnych przestrzeniach nazw, aby uniknąć potencjalnych konfliktów z obiektami domyślnymi lub innymi dzierżawcami w klastrze.

## <a name="get-started-with-kubernetes"></a>Wprowadzenie do Kubernetes

Jeśli używasz programu Docker Desktop dla systemu Windows lub pulpitu Docker dla komputerów Mac, Kubernetes jest już dostępny. Po prostu włącz je w sekcji **Kubernetes** w oknie **Ustawienia** :

![Włączanie Kubernetes w programie Docker Desktop](media/kubernetes/enable-kubernetes-docker-desktop.png)

Aby uruchomić lokalny klaster Kubernetes w systemie Linux, należy wziąć pod uwagę [minikube](https://github.com/kubernetes/minikube)lub [MicroK8s](https://microk8s.io/) , jeśli dystrybucja systemu Linux obsługuje funkcję [przyciągania](https://snapcraft.io/).

Aby upewnić się, że klaster działa i jest dostępny, uruchom polecenie `kubectl version`:

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

W tym przykładzie zarówno interfejs wiersza polecenia `kubectl`, jak i serwer Kubernetes mają uruchomioną wersję 1.14.6. Każda wersja `kubectl` powinna obsługiwać poprzednią i następną wersję serwera, więc `kubectl` 1,14 powinna współpracować z wersjami Server 1,13 i 1,15.

## <a name="run-services-on-kubernetes"></a>Uruchamianie usług w usłudze Kubernetes

Przykładowa aplikacja ma katalog `kube`, który zawiera trzy pliki YAML. Plik `namespace.yml` deklaruje niestandardową przestrzeń nazw: `stocks`. Plik `stockdata.yml` deklaruje wdrożenie i usługę dla aplikacji gRPC, a plik `stockweb.yml` deklaruje wdrożenie i usługę dla aplikacji internetowej ASP.NET Core 3,0 MVC korzystającej z usługi gRPC.

Aby użyć pliku `YAML` z `kubectl`, uruchom polecenie `apply -f`:

```console
kubectl apply -f object.yml
```

Polecenie `apply` sprawdza poprawność pliku YAML i wyświetla wszystkie błędy otrzymane z interfejsu API, ale nie czeka na utworzenie wszystkich obiektów zadeklarowanych w pliku, ponieważ może to potrwać pewien czas. Użyj `kubectl get` polecenia z odpowiednimi typami obiektów, aby sprawdzić Tworzenie obiektów w klastrze.

### <a name="the-namespace-declaration"></a>Deklaracja przestrzeni nazw

Deklaracja przestrzeni nazw jest prosta i wymaga przypisania tylko `name`:

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

Użyj `kubectl`, aby zastosować plik `namespace.yml` i potwierdzić, że przestrzeń nazw została utworzona pomyślnie:

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>Aplikacja StockData

Plik `stockdata.yml` deklaruje dwa obiekty: wdrożenie i usługa.

#### <a name="the-stockdata-deployment"></a>Wdrożenie StockData

Część wdrożenia pliku YAML zawiera `spec` dla samego wdrożenia, w tym liczbę wymaganych replik i `template` dla obiektów pod, które mają być utworzone i zarządzane przez wdrożenie. Należy pamiętać, że obiekty wdrożenia są zarządzane przez interfejs API `apps`, jak określono w `apiVersion`, a nie na głównym interfejsie API Kubernetes.

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

Właściwość `spec.selector` jest używana do dopasowania uruchomionych zasobników do wdrożenia. Właściwość `metadata.labels` pod musi być zgodna z właściwością `matchLabels` lub wywołanie interfejsu API zakończy się niepowodzeniem.

Sekcja `template.spec` deklaruje kontener, który ma zostać uruchomiony. Podczas pracy z lokalnym klastrem Kubernetes, takim jak udostępniony przez program Docker Desktop, można określić obrazy, które zostały skompilowane lokalnie, o ile mają tag wersji.

> [!IMPORTANT]
> Domyślnie Kubernetes będzie zawsze sprawdzać i próbować ściągnąć nowy obraz. Jeśli nie można znaleźć obrazu w żadnym ze znanych repozytoriów, tworzenie pod zakończy się niepowodzeniem. Aby można było korzystać z obrazów lokalnych, należy ustawić `imagePullPolicy` na `Never`.

Właściwość `ports` określa, które porty kontenerów powinny być publikowane w obszarze. Obraz `stockservice` uruchamia usługę na standardowym porcie HTTP, więc jest publikowany port 80.

Sekcja `resources` stosuje limity zasobów do kontenera działającego w ramach. Jest to dobre rozwiązanie, ponieważ uniemożliwia osobie korzystającej z używania całego dostępnego procesora lub pamięci w węźle.

> [!NOTE]
> ASP.NET Core 3,0 został zoptymalizowany i dostrojony do uruchamiania w kontenerach z ograniczoną ilością zasobów. Obraz `dotnet/core/aspnet` Docker ustawia zmienną środowiskową, aby poinformować środowisko uruchomieniowe `dotnet`, że znajduje się w kontenerze.

#### <a name="the-stockdata-service"></a>Usługa StockData

Część usługi pliku YAML deklaruje usługę, która zapewnia dostęp do zasobników w klastrze.

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

`spec` usługi używa właściwości `selector` w celu dopasowania `Pods`, w tym przypadku jest to wyszukiwanie w przypadku, gdy są używane etykiety `run: stockdata`. Określony `port` na zgodnych podst. jest publikowany przez nazwę usługi. Inne zasobniki działające w przestrzeni nazw `stocks` mogą uzyskać dostęp do protokołu HTTP w tej usłudze, używając `http://stockdata` jako adresu. Na podst. w innych przestrzeniach nazw można używać nazwy hosta `http://stockdata.stocks`. Dostęp do usługi wzajemnej przestrzeni nazw można kontrolować przy użyciu [zasad sieciowych](https://kubernetes.io/docs/concepts/services-networking/network-policies/).

#### <a name="deploy-the-stockdata-application"></a>Wdrażanie aplikacji StockData

Użyj `kubectl`, aby zastosować plik `stockdata.yml` i potwierdzić, że wdrożenie i usługa zostały utworzone:

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

### <a name="the-stockweb-application"></a>Aplikacja StockWeb

Plik `stockweb.yml` deklaruje wdrożenie i usługę dla aplikacji MVC.

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

#### <a name="environment-variables"></a>Zmienne środowiskowe

Sekcja `env` obiektu wdrożenia określa zmienne środowiskowe, które mają być ustawiane w kontenerze, w którym są uruchomione obrazy `stockweb:1.0.0`.

Zmienna środowiskowa **`StockData__Address`** zostanie zamapowana na ustawienie konfiguracji `StockData:Address` z dostawcą konfiguracji EnvironmentVariables. To ustawienie powoduje użycie podwójnego podkreślenia między nazwami w oddzielnymi sekcjach. Adres używa nazwy usługi `stockdata`, która działa w tej samej przestrzeni nazw Kubernetes.

Zmienna środowiskowa **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** ustawia przełącznik <xref:System.AppContext>, który włącza nieszyfrowane połączenia HTTP/2 dla <xref:System.Net.Http.HttpClient>. Ta zmienna środowiskowa wykonuje te same czynności co w przypadku ustawienia przełącznika w kodzie, jak pokazano poniżej:

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Jeśli użyjesz zmiennej środowiskowej dla przełącznika, możesz łatwo zmienić kontekst w zależności od kontekstu, w którym działa aplikacja.

#### <a name="service-types"></a>Typy usług

Właściwość `type: NodePort` służy do udostępniania aplikacji sieci Web spoza klastra. Ten typ właściwości powoduje, że Kubernetes publikuje port 80 w usłudze do dowolnego portu w zewnętrznych gniazdach sieciowych klastra. Przypisany port można znaleźć za pomocą polecenia `kubectl get service`.

Usługa `stockdata` nie powinna być dostępna spoza klastra, dlatego używa typu domyślnego, `ClusterIP`.

Systemy produkcyjne najprawdopodobniej będą korzystać z zintegrowanego modułu równoważenia obciążenia w celu udostępnienia aplikacji publicznych klientom zewnętrznym. Usługi uwidocznione w ten sposób powinny używać typu `LoadBalancer`.

Aby uzyskać więcej informacji na temat typów usług, zobacz dokumentację [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .

#### <a name="deploy-the-stockweb-application"></a>Wdrażanie aplikacji StockWeb

Użyj `kubectl`, aby zastosować plik `stockweb.yml` i potwierdzić, że wdrożenie i usługa zostały utworzone:

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

Dane wyjściowe polecenia `get service` pokazują, że port HTTP został opublikowany na porcie 32564 w sieci zewnętrznej. W przypadku programu Docker Desktop będzie to localhost. Możesz uzyskać dostęp do aplikacji, przechodząc do `http://localhost:32564`.

### <a name="test-the-application"></a>Testowanie aplikacji

Aplikacja StockWeb wyświetla listę zasobów NASDAQ, które są pobierane z prostej usługi żądanie-odpowiedź. W tej demonstracji każdy wiersz zawiera również unikatowy identyfikator wystąpienia usługi, która go zwróciła.

![Zrzut ekranu StockWeb](media/kubernetes/stockweb-screenshot.png)

Jeśli liczba replik usługi `stockdata` została zwiększona, może wystąpić konieczność zmiany wartości **serwera** z wiersza na wiersz, ale w rzeczywistości wszystkie rekordy 100 są zawsze zwracane z tego samego wystąpienia. Po odświeżeniu strony co kilka sekund identyfikator serwera pozostaje taki sam. Dlaczego tak się dzieje? W tym miejscu znajdują się dwa czynniki.

Najpierw system odnajdowania usług Kubernetes domyślnie używa równoważenia obciążenia z działaniem okrężnym. Podczas pierwszej kwerendy serwera DNS zostanie zwrócony pierwszy pasujący adres IP dla usługi. Następnym razem zwróci Następny adres IP z listy i tak dalej, aż do końca. W tym momencie pętla wraca do początku.

Następnie `HttpClient` używany dla klienta gRPC aplikacji StockWeb jest tworzony i zarządzany przez [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), a jedno wystąpienie tego klienta jest używane dla każdego wywołania strony. Klient wykonuje tylko jedno wyszukiwanie DNS, więc wszystkie żądania są kierowane na ten sam adres IP. I ponieważ `HttpClientHandler` jest buforowana ze względu na wydajność, wiele żądań w szybkim pomyślnym będzie używać tego samego adresu IP, do momentu wygaśnięcia zbuforowanego wpisu DNS lub wystąpienia programu *obsługi zostanie usunięte* z jakiegoś powodu.

Wynika to z tego, że domyślne żądania do usługi gRPC nie są zrównoważone dla wszystkich wystąpień tej usługi w klastrze. Różni klienci będą korzystać z różnych wystąpień, ale nie zagwarantuje dobrego rozkładu żądań lub zrównoważonego użycia zasobów.

Następny rozdział, [siatki usług](service-mesh.md), spowoduje rozwiązanie tego problemu.

>[!div class="step-by-step"]
>[Poprzednie](docker.md)
>[dalej](service-mesh.md)
