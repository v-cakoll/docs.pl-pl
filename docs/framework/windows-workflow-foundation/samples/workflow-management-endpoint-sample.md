---
title: Przepływ pracy zarządzania punktu końcowego próbki
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 558591cb645de9591fd0ac770061a5fb8825d21d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`