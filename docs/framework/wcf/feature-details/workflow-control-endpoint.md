---
title: "Punkt końcowy kontroli przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 676451ac3dce4ff9d328bf4c46809444e0e7cb7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-control-endpoint"></a>Punkt końcowy kontroli przepływu pracy
Punkt końcowy kontroli przepływu pracy umożliwia deweloperom wywołanie operacji kontroli do zdalnego sterowania hostowane przy użyciu wystąpienia przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Ta funkcja może być używana do programowo wykonywać operacji kontroli, jak wstrzymać, wznowić, a następnie Zakończ.  
  
> [!WARNING]
>  Jeśli przy użyciu punkt końcowy kontroli przepływu pracy w ramach transakcji i są kontrolowane przez przepływ pracy zawiera <xref:System.Activities.Statements.Persist> działania wystąpienia przepływu pracy zawiesza się dopóki nie upłynie limit czasu transakcji.  
  
## <a name="workflow-instance-management"></a>Zarządzanie wystąpieniami przepływu pracy  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]Definiuje kontraktu o nazwie <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Ten kontrakt definiuje serię kontroli czynności umożliwiających zdalne sterowanie wystąpień przepływów pracy obsługiwanych przez <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>Standardowy punkt końcowy, który zawiera implementację jest <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontraktu. <xref:System.ServiceModel.Activities.WorkflowControlClient>jest klasa, która służy do wysyłania operacje kontroli <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 Wystąpienia przepływu pracy może być w jednym z następujących stanów:  
  
 Aktywne  
 Stan wystąpienia przepływu pracy przed jego stanu ukończenia i gdy go nie jest w stanie wstrzymania. W tym stanie, wystąpienie przepływu pracy jest uruchamiany i przetwarzający komunikaty o aplikacji.  
  
 Suspended  
 Znajduje się w tym stanie wystąpienia przepływu pracy nie jest uruchamiany nawet w przypadku działań, które nie rozpoczęły uruchomiony lub częściowo zostało uruchomione.  
  
 Zakończone  
 Stan końcowy wystąpienia przepływu pracy. Wystąpienie przepływu pracy nie można uruchomić po osiągnięciu stanu ukończenia.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Interfejs definiuje zestaw operacji kontroli wersji synchroniczne i asynchroniczne. Transakcyjne wersji stosowanie obsługujących transakcji powiązania. W poniższej tabeli wymieniono obsługiwane operacje kontroli.  
  
|Operacja kontroli|Opis|  
|-----------------------|-----------------|  
|Przerwania|Wymuszone zatrzymuje wykonywanie wystąpienia przepływu pracy.|  
|Anuluj|Przechodzi wystąpienia przepływu pracy ze stanu aktywnych lub wstrzymane do stanu ukończenia.|  
|Uruchom|Zapewnia możliwość wykonywania wystąpienia przepływu pracy.|  
|Wstrzymaj|Przechodzi wystąpienia przepływu pracy ze stanu active w stan wstrzymania.|  
|Zakończenie|Przechodzi wystąpienia przepływu pracy ze stanu aktywnych lub wstrzymane do stanu ukończenia.|  
|Anuluj zawieszenie|Przejścia ze stanu wstrzymania wystąpienia przepływu pracy do stanu aktywnego.|  
|TransactedCancel|Wykonuje operacji anulowania w transakcji (przepływ w od klienta lub utworzony lokalnie). Jeśli system ma trwałego stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalony podczas wykonywania tej operacji.|  
|TransactedRun|Wykonuje operację wykonywania w transakcji (przepływ w od klienta lub utworzony lokalnie). Jeśli system ma trwałego stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalony podczas wykonywania tej operacji.|  
|TransactedSuspend|Wykonuje operację zawieszania w transakcji (przepływ w od klienta lub utworzony lokalnie). Jeśli system ma trwałego stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalony podczas wykonywania tej operacji.|  
|TransactedTerminate|Wykonuje operację przerwania w ramach transakcji (przepływ w od klienta lub utworzony lokalnie). Jeśli system ma trwałego stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalony podczas wykonywania tej operacji.|  
|TransactedUnsuspend|Wykonuje operację Unsuspend w transakcji (przepływ w od klienta lub utworzony lokalnie). Jeśli system ma trwałego stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalony podczas wykonywania tej operacji.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Kontraktu nie zapewnia sposób utworzenia nowego wystąpienia przepływu pracy, tylko do zarządzania istniejącego wystąpienia przepływu pracy. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zdalnie Tworzenie nowego wystąpienia przepływu pracy, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>Obiektu WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>jest to standardowy punkt końcowy ze stałym kontraktem <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Po dodaniu do <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia, może to punktu końcowego, a następnie używane do wysyłania poleceń do dowolnego wystąpienia przepływu pracy obsługiwanych przez wystąpienie hosta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]standardowych punktów końcowych, zobacz [standardowych punktów końcowych](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient>jest klasa, która pozwala na wysyłanie wiadomości kontroli <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> na <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Zawiera metodę dla każdej operacji obsługiwanych przez <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontraktu, z wyjątkiem Operacje transakcyjne. <xref:System.ServiceModel.Activities.WorkflowControlClient>używa transakcja otoczenia, aby określić, czy operacja transakcyjne powinien być używany.
