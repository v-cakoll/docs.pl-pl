---
title: Usługa routera odnajdywania
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 166f6b9d1055e36f987e6b9a81fe69dc8bd548b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980567"
---
# <a name="discovery-router-service"></a>Usługa routera odnajdywania
W tym przykładzie przedstawiono sposób przekazywania komunikatów odnajdywania do innego punktu końcowego.  
  
## <a name="demonstrates"></a>Demonstracje  
 Wykrywanie routingu  
  
## <a name="discussion"></a>Dyskusja  
 Odnajdywanie routing jest przydatne w sytuacji, w której klient szuka usługi przy użyciu serwera proxy i serwer proxy nie rozpoznaje taką usługę, ale zna innego serwera proxy. Ten serwer proxy można przekazać pakiet odnajdywania z tego klienta, do drugiego serwera proxy. Drugi serwer proxy można wyszukać usługę i zwracania odpowiedzi do klienta, oryginalnym.  
  
 W tym przykładzie klient wysyła komunikat do składnika routingu odnajdywania. Ta wiadomość jest wysyłana do określonego punktu końcowego na routerze odnajdywania. Następnie router przesyła wiadomość na UDP multiemisji punktu końcowego. Wiadomości sondy trafia do multiemisji punktu końcowego i usługa nasłuchuje na multiemisji UDP, że adres odpowiada routera odnajdywania. Router odnajdywanie umożliwia zbieranie informacji o odpowiedzi i wysyła je z powrotem do klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Skompiluj przykład.  
  
2. Uruchom plik wykonywalny DiscoveryRouter.  
  
3. Uruchomić pliku wykonywalnego usługi z katalogu kompilacji.  
  
4. Uruchom ten plik. Należy pamiętać, że klient zlokalizuje usługi.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
