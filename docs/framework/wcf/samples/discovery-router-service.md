---
title: Usługa routera odnajdywania
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: b98568dd00841b3f2e86ee1fd69390b690e2bf73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500337"
---
# <a name="discovery-router-service"></a>Usługa routera odnajdywania
W tym przykładzie przedstawiono sposób przekazywania komunikatów odnajdywania do innego punktu końcowego.  
  
## <a name="demonstrates"></a>Demonstracje  
 Routing odnajdywania  
  
## <a name="discussion"></a>Omówienie  
 Routing odnajdywania jest przydatne w sytuacji, w którym potrzebuje usługi przy użyciu serwera proxy klienta i serwera proxy nie rozpoznaje takiej usługi, ale zna innego serwera proxy. Ten serwer proxy można przekazywać pakiet odnajdywania z klienta do drugiego serwera proxy. Drugi serwer proxy można wyszukać usługę i zwracać odpowiedzi do klienta oryginalnym.  
  
 W tym przykładzie klient wysyła komunikat do odnajdywania składnik routingu. Ten komunikat jest wysyłane do określonego punktu końcowego na routerze odnajdywania. Router następnie przesyła komunikat do UDP multiemisji punktu końcowego. Wiadomości sondy trafia do multiemisji punktu końcowego i usługa Nasłuchiwanie multiemisji UDP się, że adres odpowiada routera odnajdywania. Router odnajdywania zbiera odpowiedzi i wysyła je z powrotem do klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Tworzenie przykładowej.  
  
2.  Uruchom plik wykonywalny DiscoveryRouter.  
  
3.  Uruchom plik wykonywalny usługi z katalogu kompilacji.  
  
4.  Uruchom plik wykonywalny klienta. Należy pamiętać, że klient lokalizuje usługę.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
