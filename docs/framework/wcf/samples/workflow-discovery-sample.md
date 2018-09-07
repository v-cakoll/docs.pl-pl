---
title: Odnajdywanie przepływu pracy — przykład
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069754"
---
# <a name="workflow-discovery-sample"></a>Odnajdywanie przepływu pracy — przykład
Niniejszy przykład pokazuje, jak stał się wykrywalny usługi przepływu pracy i jak tworzyć działania kodu niestandardowego, wyszukująca określonej usługi.  
  
## <a name="demonstrates"></a>Demonstracje  
 Działanie funkcji Znajdź odnajdywania i użycie przepływu pracy  
  
## <a name="discussion"></a>Dyskusja  
 W pierwszej części przykładu, jest wykrywalne usługi przepływu pracy przy użyciu konfiguracji. Konfiguracja może również Zastosuj usługę odpowiednio przy użyciu niestandardowych metadanych (np. zakresy). Na komputerze klienckim w przykładzie użyto działania kodu niestandardowego, które używa odnajdywania do wyszukiwania usługi dopasowania określonej umowy. Identyfikator URI, który jest później używany przez działanie wysyłania wyjściem działania kodu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  W tym przykładzie użyto punktów końcowych HTTP, które musi mieć odpowiednie ACL adresu URL do uruchomienia (zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Aby uzyskać szczegółowe informacje). Wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, należy dodać odpowiednie listy ACL. Zastąp Twoja domena i nazwa użytkownika o wprowadzenie następujących argumentów, jeśli powłoki nie rozpoznaje formatu zmiennej.  
  
     **netsh http Dodaj adres url urlacl =http://+:8000/ użytkownika domeny % =\\% UserName %**  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
