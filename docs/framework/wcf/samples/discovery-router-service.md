---
title: Usługa routera odnajdywania
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 149dd69cdd1972465f4b7cb48ab657492d3f21d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183725"
---
# <a name="discovery-router-service"></a>Usługa routera odnajdywania
W tym przykładzie pokazano, jak przekazywać dalej komunikaty odnajdywania do innego punktu końcowego.  
  
## <a name="demonstrates"></a>Demonstracje  
 Routing odnajdowania  
  
## <a name="discussion"></a>Dyskusji  
 Routing odnajdowania jest przydatne w scenariuszu, w którym klient szuka usługi przy użyciu serwera proxy i serwer proxy nie jest świadomy takiej usługi, ale zna inny serwer proxy. Ten serwer proxy może przesłać dalej pakiet odnajdywania z tego klienta do drugiego serwera proxy. Drugi serwer proxy może wyszukać usługę i zwrócić odpowiedzi do oryginalnego klienta.  
  
 W tym przykładzie klient wysyła wiadomość do składnika routingu odnajdywania. Ten komunikat jest wysyłany do określonego punktu końcowego na routerze odnajdywania. Następnie router przekazuje wiadomość do punktu końcowego multiemisji UDP. Komunikat sondy wychodzi do punktu końcowego multiemisji, a usługa nasłuchująca na adresie multiemisji UDP odpowiada na ten router odnajdywania. Router odnajdywania zbiera odpowiedzi i wysyła je z powrotem do klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Skompiluj przykład.  
  
2. Uruchom plik wykonywalny DiscoveryRouter.  
  
3. Uruchom plik wykonywalny usługi z katalogu kompilacji.  
  
4. Uruchom plik wykonywalny klienta. Należy zauważyć, że klient lokalizuje usługę.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
