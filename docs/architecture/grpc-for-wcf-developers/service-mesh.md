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
# <a name="service-meshes"></a>Siatki usług

Siatka usług to składnik infrastruktury, który kontroluje żądania usługi routingu w ramach sieci. Siatki usług mogą obsługiwać wszelkiego rodzaju problemy dotyczące poziomu sieci w klastrze Kubernetes, w tym:

- Odnajdowanie usług
- Równoważenie obciążenia
- Odporność na uszkodzenia
- Szyfrowanie
- Monitorowanie

Oczka usługi Kubernetes działają przez dodanie dodatkowego kontenera zwanego *serwerem proxy przyczepki*do każdego z nich znajdującego się w sieci. Serwer proxy przejmuje obsługę wszystkich żądań sieci przychodzących i wychodzących. Następnie można zachować konfigurację i zarządzanie kwestiami sieci oddzielnymi od kontenerów aplikacji. W wielu przypadkach separacja nie wymaga żadnych zmian w kodzie aplikacji.

W [poprzednim przykładzie rozdziału](kubernetes.md#test-the-application)żądania gRPC z aplikacji sieci Web były kierowane do pojedynczego wystąpienia usługi gRPC. Dzieje się tak, ponieważ nazwa hosta usługi jest rozpoznawana jako adres IP, a adres IP jest buforowany przez okres istnienia wystąpienia `HttpClientHandler`. Może być możliwe obejście tego problemu przez obsługę wyszukiwania DNS ręcznie lub tworzenie wielu klientów. Jednak to obejście komplikuje kod aplikacji bez dodawania żadnej wartości biznesowej ani klienta.

W przypadku korzystania z sieci usługi, żądania z kontenera aplikacji są wysyłane do serwera proxy przyczepki. Serwer proxy przyczepki może następnie rozproszyć je w sposób inteligentny we wszystkich wystąpieniach innej usługi. Siatka może również:

- Bezproblemowo reaguj na błędy poszczególnych wystąpień usługi.
- Obsługuj semantykę ponownych prób dla wywołań zakończonych niepowodzeniem lub przekroczeń limitu czasu.
- Przekieruj żądania zakończone niepowodzeniem do alternatywnego wystąpienia bez powrotu do aplikacji klienckiej.

Poniższy zrzut ekranu przedstawia aplikację StockWeb z uruchomioną siatką usługi. Nie wprowadzono żadnych zmian w kodzie aplikacji, a obraz platformy Docker nie jest używany. Jedyną wymaganą zmianą jest dodanie adnotacji do wdrożenia w plikach YAML dla usług `stockdata` i `stockweb`.

![StockWeb z siatką usługi](media/service-mesh/stockweb-servicemesh-screenshot.png)

W kolumnie **serwer** można zobaczyć, że żądania z aplikacji StockWeb zostały rozesłane do obu replik usługi StockData, mimo że nie pochodzą one z jednego wystąpienia `HttpClient` w kodzie aplikacji. W rzeczywistości, Jeśli przeglądasz kod, zobaczysz, że wszystkie żądania 100 do usługi StockData są nawiązywane równocześnie przy użyciu tego samego wystąpienia `HttpClient`. Z siatką usług te żądania będą zrównoważone dla wielu wystąpień usługi, które są dostępne.

Siatki usług dotyczą tylko ruchu w klastrze. W przypadku klientów zewnętrznych zapoznaj się z następnym rozdziałem, [równoważenia obciążenia](load-balancing.md).

## <a name="service-mesh-options"></a>Opcje siatki usługi

Trzy implementacje usług ogólnego przeznaczenia są obecnie dostępne do użycia z Kubernetes: [Istio](https://istio.io), [Konsolidatored](https://linkerd.io)i [Consul Connect](https://consul.io/mesh.html). Wszystkie trzy żądania routingu/proxy żądań, szyfrowania ruchu, odporności, uwierzytelniania hosta do hosta i kontroli ruchu.

Wybór sieci usługi zależy od wielu czynników:

- Specyficzne dla organizacji wymagania dotyczące kosztów, zgodności, płatnych planów pomocy technicznej itd.
- Charakter klastra, jego rozmiar, liczba wdrożonych usług i ilość ruchu sieciowego w sieci klastra.
- Łatwość wdrażania i zarządzania siatką oraz używania jej z usługami.

## <a name="example-add-linkerd-to-a-deployment"></a>Przykład: Dodaj konsolidator do wdrożenia

W tym przykładzie dowiesz się, jak używać łączącej się sieci usługi z aplikacją *StockKube* z [poprzedniej sekcji](kubernetes.md).
Aby postępować zgodnie z tym przykładem, należy [zainstalować konsolidator interfejsu wiersza polecenia](https://linkerd.io/2/getting-started/#step-1-install-the-cli). Pliki binarne systemu Windows można pobrać z sekcji zawierającej listę wydań usługi GitHub. Upewnij się, że korzystasz z najnowszej *stabilnej* wersji, a nie jednego z wersji brzegowych.

Mając zainstalowany interfejs wiersza polecenia z konsolidatorem, postępuj zgodnie z instrukcjami [wprowadzenie](https://linkerd.io/2/getting-started/index.html) , aby zainstalować elementy konsolidatora w klastrze Kubernetes. Instrukcje są proste, a instalacja powinna trwać tylko kilka minut na lokalnym wystąpieniu Kubernetes.

### <a name="add-linkerd-to-kubernetes-deployments"></a>Dodawanie konsolidatora do wdrożeń Kubernetes

Konsolidatord CLI udostępnia polecenie `inject`, aby dodać niezbędne sekcje i właściwości do plików Kubernetes. Można uruchomić polecenie i zapisać dane wyjściowe do nowego pliku.

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

Możesz sprawdzić nowe pliki, aby zobaczyć, jakie zmiany zostały wprowadzone. W przypadku obiektów wdrożenia adnotacja metadanych jest dodawana w celu poinformowania o konieczności dodania kontenera proxy przyczepki do elementu pod, gdy zostanie on utworzony.

Możliwe jest również potokowanie danych wyjściowych polecenia `linkerd inject`, aby `kubectl` bezpośrednio. Następujące polecenia będą działały w programie PowerShell lub dowolnej powłoce systemu Linux.

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a>Inspekcja usług na wbudowanym pulpicie nawigacyjnym

Otwórz łączący pulpit nawigacyjny za pomocą interfejsu wiersza polecenia `linkerd`.

```console
linkerd dashboard
```

Pulpit nawigacyjny zawiera szczegółowe informacje o wszystkich usługach, które są połączone z siatką.

![Łączący się pulpit nawigacyjny pokazujący aplikacje StockKube](media/service-mesh/linkerd-screenshot.png)

Jeśli zwiększy się liczbę replik usługi StockData gRPC, jak pokazano w poniższym przykładzie, i Odśwież stronę StockWeb w przeglądarce, w kolumnie **serwer** powinny być widoczne różne identyfikatory. Ten miks wskazuje, że wszystkie dostępne wystąpienia obsługują żądania.

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
>[Poprzednie](kubernetes.md)
>[dalej](load-balancing.md)
