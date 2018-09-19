---
title: Przykład punktu końcowego zarządzania przepływu pracy
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: 3d99cbef20895381f5e40ee939e1d94a409f1391
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45998544"
---
# <a name="workflow-management-endpoint-sample"></a>Przykład punktu końcowego zarządzania przepływu pracy
Niniejszy przykład pokazuje, jak punkt końcowy kontroli przepływu pracy może służyć do tworzenia i uruchamiania przepływów pracy, lokalnie i zdalnie. W przykładzie pokazano sposób hostowania punkt końcowy kontroli i zapisać klientów, które wywołują punkt końcowy kontroli, aby utworzyć i uruchomić wystąpienia przepływu pracy. Przepływ pracy nie jest usługą.  
  
 Po stronie usługi próbki przepływ pracy znajduje się za pomocą elementu WorkflowServiceHost i WorkflowControlEndpoint jest dodawany, dzięki czemu klienci mogą wykonywać operacje kontroli (Wstrzymaj, Start itp.). CreationEndpoint zdefiniowanych przez użytkownika jest także dodawane do Zezwalaj na przepływ pracy, który ma zostać utworzony. Usługa następnie używa tych punktów końcowych, aby uruchomić przepływ pracy w stanie wstrzymania i wznowienia przepływu pracy. Klient wykonuje te same operacje, ale z poziomu kodu klienta. Aby dowiedzieć się więcej o tych interfejsów, zobacz [punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) i [instrukcje: hostowanie przepływu pracy bez usługi w usługach IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.  
  
2.  Otwórz rozwiązanie ManagementEndpoint.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B, lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
4.  Uruchom aplikację ManagementEndpoint.exe.  
  
5.  Uruchom aplikację Client.exe.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`