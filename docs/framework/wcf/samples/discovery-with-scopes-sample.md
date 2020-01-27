---
title: Przykład odnajdywania z zakresami
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 8ba5618f472fc8a6e1751776060f99103a67a073
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728753"
---
# <a name="discovery-with-scopes-sample"></a>Przykład odnajdywania z zakresami

Ten przykład pokazuje, jak używać zakresów do kategoryzacji punktów końcowych wykrywalnych, jak również przy użyciu <xref:System.ServiceModel.Discovery.DiscoveryClient> do wykonywania wyszukiwania asynchronicznego dla punktów końcowych. W tym przykładzie pokazano, jak dostosować odnajdywanie dla każdego punktu końcowego, dodając zachowanie odnajdywania punktu końcowego i używając go, aby dodać zakres do punktu końcowego, a także kontrolować wykrywalność punktu końcowego. Na kliencie przykład polega na tym, jak klienci mogą tworzyć <xref:System.ServiceModel.Discovery.DiscoveryClient> i dostrajać parametry wyszukiwania, aby dołączać zakresy przez dodawanie zakresów do <xref:System.ServiceModel.Discovery.FindCriteria>. Ten przykład pokazuje również, jak klienci mogą ograniczać odpowiedzi przez dodanie kryterium zakończenia.

## <a name="service-features"></a>Funkcje usługi

Ten projekt przedstawia dwa punkty końcowe usługi dodawane do <xref:System.ServiceModel.ServiceHost>. Z każdym punktem końcowym jest skojarzony <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. To zachowanie służy do dodawania zakresów identyfikatorów URI dla obu punktów końcowych. Zakresy są używane do rozróżniania każdego z tych punktów końcowych, aby umożliwić klientom precyzyjne dostosowanie wyszukiwania. W przypadku drugiego punktu końcowego wykrywalność można wyłączyć, ustawiając właściwość <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> na `false`. Dzięki temu metadane odnajdowania skojarzone z tym punktem końcowym nie będą wysyłane jako część komunikatów odnajdowania.

## <a name="client-features"></a>Funkcje klienta

Metoda `FindCalculatorServiceAddress()` pokazuje, jak używać <xref:System.ServiceModel.Discovery.DiscoveryClient> i przekazywać <xref:System.ServiceModel.Discovery.FindCriteria> z dwoma ograniczeniami. Do kryteriów zostanie dodany zakres, a właściwość <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> jest ustawiona na 1. Zakres ogranicza wyniki tylko do usług, które publikują ten sam zakres. Ustawienie <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> na 1 ogranicza odpowiedzi, które <xref:System.ServiceModel.Discovery.DiscoveryClient> czeka na, co najwyżej 1 punkt końcowy. Wywołanie <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> jest operacją synchroniczną, która blokuje wątek do momentu osiągnięcia limitu czasu lub znalezienia jednego punktu końcowego.

### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Ten przykład korzysta z punktów końcowych HTTP i do uruchomienia tego przykładu należy dodać prawidłowe listy ACL adresów URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i https](../feature-details/configuring-http-and-https.md). Wykonanie następującego polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list ACL. Możesz chcieć zastąpić domenę i nazwę użytkownika dla następujących argumentów, jeśli polecenie nie działa w następujący sposób: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Skompiluj rozwiązanie.

3. Uruchom plik wykonywalny usługi z katalogu kompilacji.

4. Uruchom plik wykonywalny klienta. Należy pamiętać, że klient może zlokalizować usługę.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
