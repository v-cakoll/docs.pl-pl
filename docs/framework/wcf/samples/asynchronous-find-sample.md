---
title: "Znajdowanie asynchroniczne — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a793945906bb1a106916d59ff07ea813f38469d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-find-sample"></a>Znajdowanie asynchroniczne — przykład
Ten przykład przedstawia sposób użycia operację znajdowanie asynchroniczne w aplikacji klienta.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Zaletą tego wzorca projektu po to, czy klient jest powiadamiany o asynchronicznie punktów końcowych, znajduje się w wyniku żądania wyszukiwania. Aby zobaczyć, jak to działa, otwórz plik Client.cs. Uwaga <xref:System.ServiceModel.Discovery.DiscoveryClient> obiekt ma dwa obiekty delegowane dołączony do jego obsługi zdarzeń. Jednego delegata jest wywoływane, gdy <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> zdarzenia i inny jest wywoływana za każdym razem <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia. Przykład pokazuje, jak możesz użyć tego wzorca w aplikacji.  
  
> [!NOTE]
>  W przykładzie użyto punktów końcowych HTTP i do uruchomienia, muszą zostać dodane odpowiednie listy ACL adresu URL. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL. Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AsyncFind.sln.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia i przejdź do katalogu \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug lub \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug i uruchom Service.exe.  
  
4.  Po uruchomieniu usługi, przejdź do \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug lub WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug katalogu i uruchom Client.exe.  
  
5.  Sprawdź, czy klient jest w stanie zlokalizować i wywołania tej usługi.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>Zobacz też
