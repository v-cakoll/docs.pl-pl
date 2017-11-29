---
title: "Usługa routera odnajdywania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 663ece44a18ae073412376bc11a1d70927740e8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
