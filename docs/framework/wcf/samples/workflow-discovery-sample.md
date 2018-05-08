---
title: Odnajdywanie przepływu pracy — przykład
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: ec4b956a28048c0c30a4eadb0473adb34334fa92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-discovery-sample"></a>Odnajdywanie przepływu pracy — przykład
W przykładzie pokazano sposób stał się wykrywalny usługi przepływu pracy i tworzenia działania niestandardowego kodu, która wyszukuje określonej usługi.  
  
## <a name="demonstrates"></a>Demonstracje  
 Działanie funkcji odnajdywania Znajdź i użycie przepływu pracy  
  
## <a name="discussion"></a>Omówienie  
 W pierwszej części próbki jest tworzone wykrywalny usługi przepływu pracy za pomocą konfiguracji. Konfiguracja można również zastosować usługa odpowiednio o niestandardowych metadanych (np. zakresy). Na komputerze klienckim w przykładzie użyto działania kodu niestandardowego, używający odnajdywania do wyszukiwania dopasowania określonej kontraktu usługi. Działanie kodu generuje identyfikator URI, który jest później używany przez działanie wysyłania.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  W przykładzie użyto punktów końcowych HTTP, które wymaga prawidłowego adresu URL listy kontroli dostępu do uruchomienia (zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje). Wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, należy dodać odpowiednich list ACL. Zastąp użytkownika domena i nazwa użytkownika dla następujących argumentów Jeśli powłoki nie rozpoznaje formatu zmiennej.  
  
     **netsh http Dodaj adres url urlacl =http://+:8000/ użytkownika domeny % =\\% UserName %**  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
