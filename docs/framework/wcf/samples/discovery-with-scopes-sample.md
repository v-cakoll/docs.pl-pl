---
title: Przykład odnajdywania z zakresami
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 9b65a348c943b07e813e3fe690f1364b77a94890
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972002"
---
# <a name="discovery-with-scopes-sample"></a>Przykład odnajdywania z zakresami

Ten przykład pokazuje, jak używać zakresów do kategoryzacji punktów końcowych wykrywalnych, jak również <xref:System.ServiceModel.Discovery.DiscoveryClient> używania do wykonywania wyszukiwania asynchronicznego dla punktów końcowych. W tym przykładzie pokazano, jak dostosować odnajdywanie dla każdego punktu końcowego, dodając zachowanie odnajdywania punktu końcowego i używając go, aby dodać zakres do punktu końcowego, a także kontrolować wykrywalność punktu końcowego. Na kliencie przykład polega na tym, jak klienci mogą tworzyć <xref:System.ServiceModel.Discovery.DiscoveryClient> i dostrajać parametry wyszukiwania w celu uwzględnienia zakresów przez dodanie zakresów <xref:System.ServiceModel.Discovery.FindCriteria>do. Ten przykład pokazuje również, jak klienci mogą ograniczać odpowiedzi przez dodanie kryterium zakończenia.

## <a name="service-features"></a>Funkcje usługi

Ten projekt przedstawia dwa punkty końcowe usługi, <xref:System.ServiceModel.ServiceHost>które są dodawane do. Każdy punkt końcowy jest <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> skojarzony z nim. To zachowanie służy do dodawania zakresów identyfikatorów URI dla obu punktów końcowych. Zakresy są używane do rozróżniania każdego z tych punktów końcowych, aby umożliwić klientom precyzyjne dostosowanie wyszukiwania. W drugim punkcie końcowym wykrywalność można wyłączyć, ustawiając <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> właściwość na. `false` Dzięki temu metadane odnajdowania skojarzone z tym punktem końcowym nie będą wysyłane jako część komunikatów odnajdowania.

## <a name="client-features"></a>Funkcje klienta

Metoda pokazuje, w <xref:System.ServiceModel.Discovery.DiscoveryClient> <xref:System.ServiceModel.Discovery.FindCriteria> jaki sposób używać i przekazać z dwoma ograniczeniami. `FindCalculatorServiceAddress()` Do kryteriów zostanie dodany zakres, a <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwość jest ustawiona na 1. Zakres ogranicza wyniki tylko do usług, które publikują ten sam zakres. Ustawienie <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> wartości 1 powoduje ograniczenie <xref:System.ServiceModel.Discovery.DiscoveryClient> odpowiedzi dla do, maksymalnie 1 punkt końcowy. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Wywołanie jest operacją synchroniczną, która blokuje wątek do momentu osiągnięcia limitu czasu lub znalezienia jednego punktu końcowego.

### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Ten przykład korzysta z punktów końcowych HTTP i do uruchomienia tego przykładu należy dodać prawidłowe listy ACL adresów URL. Aby uzyskać szczegółowe informacje [, zobacz Konfigurowanie protokołów HTTP i https](https://go.microsoft.com/fwlink/?LinkId=70353) . Wykonanie następującego polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list ACL. Możesz chcieć zastąpić domenę i nazwę użytkownika dla następujących argumentów, jeśli polecenie nie działa w następujący sposób:`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Skompiluj rozwiązanie.

3. Uruchom plik wykonywalny usługi z katalogu kompilacji.

4. Uruchom plik wykonywalny klienta. Należy pamiętać, że klient może zlokalizować usługę.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
