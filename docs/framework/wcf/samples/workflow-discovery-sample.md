---
title: "Odnajdywanie przepływu pracy — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f778fead0e09be36ca2a829dde9cf906f4fcaa9f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-discovery-sample"></a>Odnajdywanie przepływu pracy — przykład
W przykładzie pokazano sposób stał się wykrywalny usługi przepływu pracy i tworzenia działania niestandardowego kodu, która wyszukuje określonej usługi.  
  
## <a name="demonstrates"></a>Demonstracje  
 Działanie funkcji odnajdywania Znajdź i użycie przepływu pracy  
  
## <a name="discussion"></a>Omówienie  
 W pierwszej części próbki jest tworzone wykrywalny usługi przepływu pracy za pomocą konfiguracji. Konfiguracja można również zastosować usługa odpowiednio o niestandardowych metadanych (np. zakresy). Na komputerze klienckim w przykładzie użyto działania kodu niestandardowego, używający odnajdywania do wyszukiwania dopasowania określonej kontraktu usługi. Działanie kodu generuje identyfikator URI, który jest później używany przez działanie wysyłania.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  W przykładzie użyto punktów końcowych HTTP, które wymaga prawidłowego adresu URL listy kontroli dostępu do uruchomienia (zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje). Wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, należy dodać odpowiednich list ACL. Zastąp użytkownika domena i nazwa użytkownika dla następujących argumentów Jeśli powłoki nie rozpoznaje formatu zmiennej.  
  
     **netsh http Dodaj adres url urlacl = http: / / +: 8000 / użytkownika domeny % =\\% UserName %**  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
