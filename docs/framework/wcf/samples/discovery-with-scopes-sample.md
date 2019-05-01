---
title: Przykład odnajdywania z zakresami
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 9ad20e63e00464ed615620b9d0ec83fb90d07444
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789379"
---
# <a name="discovery-with-scopes-sample"></a>Przykład odnajdywania z zakresami
Ten przykład przedstawia sposób użycia zakresów do kategoryzowania punktów końcowych wykrywalne jako dobrze, jak używać <xref:System.ServiceModel.Discovery.DiscoveryClient> z asynchronicznego wyszukiwania dla punktów końcowych. W usłudze w tym przykładzie pokazano, jak dostosować odnajdywania dla każdego punktu końcowego, dodając zachowanie punktu końcowego odnajdywania i dodawanie przy użyciu jego zakres do punktu końcowego, a także kontrolowanie punktu końcowego odnajdywania. Na komputerze klienckim, przykładzie pokazano, jak klienci mogą tworzyć <xref:System.ServiceModel.Discovery.DiscoveryClient> i dostosowanie parametrów do dołączania zakresów, dodając zakres wyszukiwania <xref:System.ServiceModel.Discovery.FindCriteria>. Niniejszy przykład pokazuje również, jak ograniczyć odpowiedzi przez dodanie kryterium kończenia żądań klientów.  
  
## <a name="service-features"></a>Funkcje usługi  
 Ten projekt zawiera dwa punkty końcowe usługi dodawane do <xref:System.ServiceModel.ServiceHost>. Każdy punkt końcowy ma <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> skojarzonych z nim. To zachowanie służy do dodania zakresy identyfikator URI dla obu punktów końcowych. Zakresy są używane w celu rozróżnienia każdego z tych punktów końcowych, dzięki czemu klienci mogą dostosować wyszukiwania. Dla drugiego punktu końcowego odnajdywania można wyłączyć, ustawiając <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> właściwość `false`. Dzięki temu skojarzone z tym punktem końcowym metadanych odnajdywania nie są wysyłane w ramach każdego komunikatu odnajdywania.  
  
## <a name="client-features"></a>Funkcje klienta  
 `FindCalculatorServiceAddress()` Metoda ma pokazać, jak używać <xref:System.ServiceModel.Discovery.DiscoveryClient> i przekazać <xref:System.ServiceModel.Discovery.FindCriteria> z dwa ograniczenia. Zakres jest dodana do kryteriów i <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwość jest ustawiona na 1. Zakres ogranicza wyniki do usług, które publikują w tym samym zakresie. Ustawienie <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 1 ogranicza odpowiedzi <xref:System.ServiceModel.Discovery.DiscoveryClient> czeka na maksymalnie 1 punkt końcowy. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Wywołanie jest operacja synchroniczna, która blokuje wątek, dopóki nie zostanie osiągnięty limit czasu lub znajduje się jeden punkt końcowy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. W tym przykładzie użyto punktów końcowych HTTP i aby uruchomić ten przykład, muszą zostać dodane odpowiednie listy ACL adresu URL. Zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Aby uzyskać szczegółowe informacje. Wykonując następujące polecenie w podwyższonym poziomem uprawnień, należy dodać odpowiednie listy ACL. Można zastąpić Twoja domena i nazwa użytkownika o wprowadzenie następujących argumentów, jeśli polecenie nie działa, ponieważ: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Skompiluj rozwiązanie.  
  
3. Uruchomić pliku wykonywalnego usługi z katalogu kompilacji.  
  
4. Uruchom ten plik. Należy pamiętać, że klient jest w stanie do lokalizowania usługi.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
