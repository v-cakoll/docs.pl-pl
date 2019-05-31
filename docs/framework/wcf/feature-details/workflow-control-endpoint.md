---
title: Punkt końcowy kontroli przepływu pracy
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: 781a7cefaeeb8cd9cd21298471c59de2e7815244
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424016"
---
# <a name="workflow-control-endpoint"></a>Punkt końcowy kontroli przepływu pracy
Punkt końcowy kontroli przepływu pracy umożliwia deweloperom wywołanie operacji kontroli na zdalne sterowanie wystąpienia przepływu pracy, hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Ta funkcja może służyć do programowo wykonywać operacje kontroli, takie jak wstrzymać, wznowić i zakończyć.  
  
> [!WARNING]
>  Jeśli przy użyciu punkt końcowy kontroli przepływu pracy w ramach transakcji i przepływu pracy kontrolowany zawiera <xref:System.Activities.Statements.Persist> działania spowoduje zablokowanie wystąpienia przepływu pracy, dopóki nie upłynie limit czasu transakcji.  
  
## <a name="workflow-instance-management"></a>Zarządzanie wystąpieniami przepływu pracy  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Określa nową umowę o nazwie <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Ten kontrakt definiuje szereg kontroli operacje, które pozwalają zdalnie sterować wystąpienia przepływu pracy pracujących na <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> jest standardowy punkt końcowy, który zawiera implementację <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontraktu. <xref:System.ServiceModel.Activities.WorkflowControlClient> to klasa, która służy do wysyłania operacje kontroli do <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 Wystąpienia przepływu pracy może mieć jeden z następujących stanów:  
  
 Aktywne  
 Stan wystąpienia przepływu pracy przed osiągnięciem przez nią stanu ukończenia, a jeśli go nie jest w stanie wstrzymania. W tym stanie wystąpienia przepływu pracy jest uruchamiany i przetwarza komunikaty aplikacji.  
  
 Suspended  
 Wystąpienie przepływu pracy znajduje się w tym stanie nie jest uruchamiany, nawet w przypadku działania, które nie zostały uruchomione, uruchamiania lub częściowo zostały uruchomione.  
  
 Zakończone  
 Końcowy stan wystąpienia przepływu pracy. Wystąpienie przepływu pracy nie można uruchomić po osiągnięciu stanu ukończenia.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Interfejs definiuje zestaw operacji kontroli z wersjami synchroniczne i asynchroniczne. Transakcyjne wersje wymagają użycia obsługujących transakcja powiązania. W poniższej tabeli wymieniono obsługiwane operacje kontroli.  
  
|Operacja kontroli|Opis|  
|-----------------------|-----------------|  
|Przerwij|Wymuszone zatrzymuje wykonywania wystąpienia przepływu pracy.|  
|Anuluj|Przechodzi wystąpienia przepływu pracy ze stanu active lub wstrzymane do stanu ukończenia.|  
|Uruchom|Umożliwia wystąpienia przepływu pracy do wykonania.|  
|Wstrzymywanie|Przejście ze stanu aktywnego wystąpienia przepływu pracy do stanu wstrzymania.|  
|Zakończenie|Przechodzi wystąpienia przepływu pracy ze stanu active lub wstrzymane do stanu ukończenia.|  
|Anulować zawieszenie użytkownika|Przejście ze stanu wstrzymania wystąpienia przepływu pracy do stanu aktywna.|  
|TransactedCancel|Wykonuje operację anulowania w ramach transakcji (przekazane w od klienta lub utworzone lokalnie). Jeśli system obsługuje trwałość stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalona, podczas wykonywania tej operacji.|  
|TransactedRun|Wykonuje operację wykonywania w ramach transakcji (przekazane w od klienta lub utworzone lokalnie). Jeśli system obsługuje trwałość stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalona, podczas wykonywania tej operacji.|  
|TransactedSuspend|Wykonuje operację zawieszania w ramach transakcji (przekazane w od klienta lub utworzone lokalnie). Jeśli system obsługuje trwałość stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalona, podczas wykonywania tej operacji.|  
|TransactedTerminate|Wykonuje operację przerwania w ramach transakcji (przekazane w od klienta lub utworzone lokalnie). Jeśli system obsługuje trwałość stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalona, podczas wykonywania tej operacji.|  
|TransactedUnsuspend|Wykonuje operację wstrzymanie w ramach transakcji (przekazane w od klienta lub utworzone lokalnie). Jeśli system obsługuje trwałość stanu wystąpienia przepływu pracy, wystąpienie przepływu pracy musi zostać utrwalona, podczas wykonywania tej operacji.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Umowy nie zapewnia sposób utworzenia nowego wystąpienia przepływu pracy, tylko do zarządzania istniejącego wystąpienia przepływu pracy. Aby uzyskać więcej informacji na temat zdalnego tworzenia nowego wystąpienia przepływu pracy, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> jest to standardowy punkt końcowy ze stałym kontraktem <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Po dodaniu do <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia, może to punkt końcowy, a następnie używane do wysyłania poleceń do dowolnego wystąpienia przepływu pracy pracujących na wystąpienie hosta. Aby uzyskać więcej informacji na temat standardowych punktów końcowych, zobacz [standardowe punkty końcowe](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient> to klasa, która umożliwia wysyłanie komunikatów sterowania <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> na <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Zawiera metody dla każdej operacji obsługiwanych przez <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontraktu, z wyjątkiem Operacje transakcyjne. <xref:System.ServiceModel.Activities.WorkflowControlClient> używa otoczenia transakcji, aby określić, czy można używać operacji transakcyjnych.
