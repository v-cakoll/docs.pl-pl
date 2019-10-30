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
# <a name="service-meshes"></a>Siatki usług

Siatka usług to składnik infrastruktury, który kontroluje żądania usługi routingu w ramach sieci. Siatki usług mogą obsługiwać wszelkiego rodzaju problemy dotyczące poziomu sieci w klastrze Kubernetes, w tym:

- Odnajdowanie usług
- Równoważenie obciążenia
- Odporność na uszkodzenia
- Szyfrowanie
- Monitorowanie

Oczka usługi Kubernetes działają przez dodanie dodatkowego kontenera zwanego *serwerem proxy przyczepki*do każdego z nich znajdującego się w sieci. Serwer proxy przejmuje obsługę wszystkich żądań sieci przychodzących i wychodzących, umożliwiając Konfigurowanie i zarządzanie kwestiami sieci, które mają być oddzielone od kontenerów aplikacji, a także w wielu przypadkach, bez konieczności wprowadzania jakichkolwiek zmian w kodzie aplikacji.

Zapoznaj się z [poprzednim przykładem rozdziału](kubernetes.md#testing-the-application), w którym wszystkie żądania gRPC z aplikacji sieci Web były kierowane do pojedynczego wystąpienia usługi gRPC. Dzieje się tak, ponieważ nazwa hosta usługi jest rozpoznawana jako adres IP, a adres IP jest buforowany przez okres istnienia wystąpienia `HttpClientHandler`. Możliwe jest obejście tego problemu przez obsługę wyszukiwań DNS ręcznie lub tworzenie wielu klientów, ale może to znacząco poskomplikowanić kod aplikacji bez konieczności dodawania żadnej wartości biznesowej lub klientów.

Za pomocą sieci usługi, żądania z kontenera aplikacji są wysyłane do serwera proxy przyczepki, który może być wzajemnie dystrybuowany we wszystkich wystąpieniach innej usługi. Siatka może również:

- Bezproblemowo reaguj na błędy poszczególnych wystąpień usługi.
- Obsługa semantyki ponawiania dla wywołań zakończonych niepowodzeniem lub przekroczeń limitu czasu
- Przekieruj żądania zakończone niepowodzeniem do alternatywnego wystąpienia bez powrotu do aplikacji klienckiej.

Poniższy zrzut ekranu przedstawia aplikację StockWeb z uruchomioną siatką usługi, bez zmian w kodzie aplikacji, a nawet w używanym obrazie platformy Docker. Jedyną wymaganą zmianą jest dodanie adnotacji do wdrożenia w plikach YAML dla usług `stockdata` i `stockweb`.

![StockWeb z siatką usługi](media/service-mesh/stockweb-servicemesh-screenshot.png)

W kolumnie serwer można zobaczyć, że żądania z aplikacji StockWeb zostały rozesłane do obu replik usługi StockData, mimo że nie pochodzą one z jednego wystąpienia `HttpClient` w kodzie aplikacji. W rzeczywistości, Jeśli przeglądasz kod, zobaczysz, że wszystkie żądania 100 do usługi StockData są nawiązywane równocześnie przy użyciu tego samego wystąpienia `HttpClient`, ale z siatką usługi, te żądania będą równoważone w przypadku dostępności wielu wystąpień usługi.

Siatki usług dotyczą tylko ruchu w klastrze. W przypadku klientów zewnętrznych zapoznaj [się z następnym rozdziałem, równoważenia obciążenia](load-balancing.md).

## <a name="service-mesh-options"></a>Opcje siatki usługi

Istnieją trzy implementacje usług ogólnego przeznaczenia, które są obecnie dostępne do użycia z Kubernetes: Istio, Konsolidatored i Consul Connect. Wszystkie trzy żądania routingu/proxy żądań, szyfrowania ruchu, odporności, uwierzytelniania hosta do hosta i kontroli ruchu.

Wybór sieci usług zależy od wielu czynników:

- Specyficzne dla organizacji wymagania dotyczące kosztów, zgodności, płatnych planów pomocy technicznej itd.
- Charakter klastra, jego rozmiar, liczba wdrożonych usług i ilość ruchu sieciowego w sieci klastra.
- Łatwość wdrażania i zarządzania siatką oraz używania jej z usługami.

Więcej informacji na temat każdej sieci usługi jest dostępnych w swoich witrynach sieci Web.

- [**Istio** — istio.IO](https://istio.io)
- [**Konsolidatored** -linkerd.IO](https://linkerd.io)
- [**Consul** — Consul.IO/Mesh.html](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a>Przykład: Dodaj konsolidator do wdrożenia

W tym przykładzie dowiesz się, jak używać łączącej się sieci usługi z aplikacją *StockKube* z [poprzedniej sekcji](kubernetes.md).
Aby postępować zgodnie z tym przykładem, należy [zainstalować konsolidator interfejsu wiersza polecenia](https://linkerd.io/2/getting-started/#step-1-install-the-cli). Pliki binarne systemu Windows można pobrać z sekcji wydań usługi GitHub. Upewnij się, że korzystasz z najnowszej **stabilnej** wersji, a nie jednego z wersji brzegowych.

Mając zainstalowany interfejs wiersza polecenia z konsolidatorem, postępuj zgodnie z instrukcjami [*wprowadzenie* na konsolidatorze witryny sieci Web], aby zainstalować elementy konsolidatora w klastrze Kubernetes. Instrukcje są bezpośrednie i instalacja powinna trwać tylko kilka minut na lokalnym wystąpieniu usługi Kubernetes.

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

Uruchom konsolidator pulpitu nawigacyjnego za pomocą interfejsu wiersza polecenia `linkerd`.

```console
linkerd dashboard
```

Pulpit nawigacyjny zawiera szczegółowe informacje o wszystkich usługach, które są połączone z siatką.

![Łączący się pulpit nawigacyjny pokazujący aplikacje StockKube](media/service-mesh/linkerd-screenshot.png)

W przypadku zwiększenia liczby replik usługi StockData gRPC, jak pokazano w poniższym przykładzie, i odświeżanie strony StockWeb w przeglądarce, w kolumnie serwer powinien być widoczny szereg identyfikatorów wskazujący, że żądania są obsługiwane przez wszystkie dostępne wystąpienia .

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
>[Poprzedni](kubernetes.md)
>[Następny](load-balancing.md)
