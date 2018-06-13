---
title: Przepływ pracy zarządzania punktu końcowego próbki
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: e34a23f76edbd957b1be7caff1b18f6934b1588b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517101"
---
# <a name="workflow-management-endpoint-sample"></a>Przepływ pracy zarządzania punktu końcowego próbki
W tym przykładzie pokazano, jak punkt końcowy kontroli przepływu pracy może służyć do tworzenia i uruchamiania przepływów pracy, zarówno lokalnie, jak i zdalnie. Przykład pokazuje, jak hosta kontrolnego punktu końcowego i zapisu klientów, które wywołują kontrolnego punktu końcowego, aby utworzyć i uruchomić wystąpienia przepływu pracy. Przepływ pracy nie jest usługą.  
  
 Po stronie usługi próbki przepływu pracy jest obsługiwana przy użyciu klasy WorkflowServiceHost i obiektu WorkflowControlEndpoint zostanie dodany, dzięki czemu klienci mogą wykonywać operacje kontroli (Wstrzymaj, Start itp.). CreationEndpoint zdefiniowane przez użytkownika jest także dodawane do Zezwalaj przepływu pracy, który ma zostać utworzony. Usługa następnie używa tych punktów końcowych w celu uruchomienia przepływu pracy w stanie wstrzymania i wznowienia przepływu pracy. Klient wykonuje te same operacje, ale z kodu klienta. Dla więcej informacji o tych interfejsów, zobacz [punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) i [porady: hosta z systemem innym niż usługi przepływu pracy w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.  
  
2.  Otwórz rozwiązanie ManagementEndpoint.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
4.  Uruchom aplikację ManagementEndpoint.exe.  
  
5.  Uruchom aplikację Client.exe.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`