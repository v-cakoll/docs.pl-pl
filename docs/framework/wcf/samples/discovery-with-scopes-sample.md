---
title: "Przykład odnajdywania z zakresami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 184c4a5c31969ee060f72d937ab02af733340ca4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-with-scopes-sample"></a>Przykład odnajdywania z zakresami
Ten przykład przedstawia sposób użycia zakresów kategoryzację wykrywalny punktów końcowych, jak również sposób użycia <xref:System.ServiceModel.Discovery.DiscoveryClient> do wykonywania asynchronicznych wyszukiwania dla punktów końcowych. W usłudze w tym przykładzie pokazano, jak dostosować odnajdywania dla każdego punktu końcowego przez dodanie zachowanie odnajdowania punktu końcowego i użytkowania go, aby dodać zakres do punktu końcowego, a także kontrolowanie możliwość odnajdowania punktu końcowego. Na komputerze klienckim próbki przechodzi w jaki sposób klienci mogą tworzyć <xref:System.ServiceModel.Discovery.DiscoveryClient> i dostosowywanie wyszukiwania parametrów do dołączania zakresów przez dodawanie zakresów do <xref:System.ServiceModel.Discovery.FindCriteria>. Również w tym przykładzie pokazano, jak klienci mogą ograniczać odpowiedzi od dodania kryterium zakończenia.  
  
## <a name="service-features"></a>Funkcje usługi  
 Ten projekt zawiera dwa punkty końcowe usługi dodawane do <xref:System.ServiceModel.ServiceHost>. Każdy punkt końcowy ma <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> skojarzonych z nim. To działanie służy do dodawania zakresy identyfikatora URI dla obu punktów końcowych. Zakresy są używane do odróżnienia każdego z tych punktów końcowych, aby klienci mogą dostrojenia wyszukiwania. Dla drugiego punktu końcowego, możliwość odnajdowania można wyłączyć, ustawiając <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> właściwości `false`. Dzięki temu odnajdywania metadane skojarzone z tego punktu końcowego nie są wysyłane w ramach każdego komunikatu odnajdywania.  
  
## <a name="client-features"></a>Funkcje klienta  
 `FindCalculatorServiceAddress()` Metody przedstawia sposób użycia <xref:System.ServiceModel.Discovery.DiscoveryClient> i podaj <xref:System.ServiceModel.Discovery.FindCriteria> z dwóch ograniczenia. Zakres jest dodana do kryteriów oraz <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwość jest ustawiona na 1. Zakres ogranicza wyniki do usług, które publikują w tym samym zakresie. Ustawienie <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 1 ogranicza odpowiedzi <xref:System.ServiceModel.Discovery.DiscoveryClient> czeka na maksymalnie 1 punktu końcowego. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Wywołanie jest operacja synchroniczna, która blokuje wątek, dopóki nie zostanie osiągnięty limit czasu lub znajduje się jeden punkt końcowy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  W przykładzie użyto punktów końcowych HTTP i do uruchomienia tego przykładu, muszą zostać dodane odpowiednie listy ACL adresu URL. Zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje. Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL. Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest:`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Skompiluj rozwiązanie.  
  
3.  Uruchom plik wykonywalny usługi z katalogu kompilacji.  
  
4.  Uruchom plik wykonywalny klienta. Należy pamiętać, że klient jest w stanie do lokalizowania usługi.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## <a name="see-also"></a>Zobacz też
