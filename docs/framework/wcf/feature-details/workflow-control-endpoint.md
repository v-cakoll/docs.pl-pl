---
title: Punkt końcowy kontroli przepływu pracy
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: 3c826147d9d3ad452957230adb8f32659b4d1352
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988548"
---
# <a name="workflow-control-endpoint"></a>Punkt końcowy kontroli przepływu pracy
Punkt końcowy sterowania przepływem pracy umożliwia deweloperom wywoływanie operacji sterowania zdalnego sterowania wystąpieniami <xref:System.ServiceModel.Activities.WorkflowServiceHost>przepływu pracy hostowanymi przy użyciu. Ta funkcja może służyć do programistycznego wykonywania operacji sterowania, takich jak Wstrzymywanie, wznawianie i przerywanie.  
  
> [!WARNING]
> W przypadku korzystania z punktu końcowego sterowania przepływem pracy w ramach transakcji i kontrolowanego <xref:System.Activities.Statements.Persist> przepływu pracy, wystąpienie przepływu pracy będzie blokowane do momentu przełączenia transakcji.  
  
## <a name="workflow-instance-management"></a>Zarządzanie wystąpieniem przepływu pracy  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]definiuje nowy kontrakt o nazwie <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Ta umowa definiuje szereg operacji sterowania, które umożliwiają zdalne sterowanie wystąpieniami przepływu pracy hostowanych <xref:System.ServiceModel.Activities.WorkflowServiceHost>przez program. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>jest standardowym punktem końcowym, który zapewnia implementację <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontraktu. <xref:System.ServiceModel.Activities.WorkflowControlClient>jest klasą, która jest używana do wysyłania operacji kontroli do <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 Wystąpienia przepływu pracy mogą być w jednym z następujących stanów:  
  
 Aktywne  
 Stan wystąpienia przepływu pracy, zanim osiągnie on stan ukończenia i gdy nie jest w stanie wstrzymania. W tym stanie wystąpienie przepływu pracy uruchamia i przetwarza komunikaty aplikacji.  
  
 Suspended  
 W tym stanie wystąpienie przepływu pracy nie działa, nawet jeśli istnieją działania, które nie zostały uruchomione lub częściowo uruchomione.  
  
 Zakończone  
 Końcowy stan wystąpienia przepływu pracy. Nie można uruchomić wystąpienia przepływu pracy po osiągnięciu stanu ukończenia.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Interfejs definiuje zestaw operacji sterowania z synchronicznymi i asynchronicznymi wersjami. Wersje transakcyjne wymagają użycia powiązania z obsługą transakcji. Poniższa tabela zawiera listę obsługiwanych operacji sterowania.  
  
|Operacja sterowania|Opis|  
|-----------------------|-----------------|  
|Przerwij|Wymuszone zatrzymywanie wykonywania wystąpienia przepływu pracy.|  
|Anuluj|Przejście wystąpienia przepływu pracy ze stanu aktywnego lub wstrzymanego do stanu ukończone.|  
|Uruchom|Oferuje wystąpienie przepływu pracy, które można wykonać.|  
|Wstrzymywanie|Przejście wystąpienia przepływu pracy ze stanu aktywnego do stanu wstrzymania.|  
|Kończyć|Przejście wystąpienia przepływu pracy ze stanu aktywnego lub wstrzymanego do stanu ukończone.|  
|Anuluj zawieszenie|Przechodzi do stanu aktywności wystąpienia przepływu pracy ze stanu wstrzymania.|  
|TransactedCancel|Wykonuje operację anulowania w ramach transakcji (przechodzącą z klienta lub utworzoną lokalnie). Jeśli system utrzymuje trwały stan wystąpienia przepływu pracy, wystąpienie przepływu pracy musi być utrwalone podczas wykonywania tej operacji.|  
|TransactedRun|Wykonuje operację uruchamiania w ramach transakcji (przepływanej z klienta lub utworzona lokalnie). Jeśli system utrzymuje trwały stan wystąpienia przepływu pracy, wystąpienie przepływu pracy musi być utrwalone podczas wykonywania tej operacji.|  
|TransactedSuspend|Wykonuje operację wstrzymania w ramach transakcji (przechodzącą z klienta lub utworzoną lokalnie). Jeśli system utrzymuje trwały stan wystąpienia przepływu pracy, wystąpienie przepływu pracy musi być utrwalone podczas wykonywania tej operacji.|  
|TransactedTerminate|Wykonuje operację przerwania w ramach transakcji (przepływanej z klienta lub utworzona lokalnie). Jeśli system utrzymuje trwały stan wystąpienia przepływu pracy, wystąpienie przepływu pracy musi być utrwalone podczas wykonywania tej operacji.|  
|TransactedUnsuspend|Wykonuje operację wstrzymywania zawieszenia w ramach transakcji (z poziomu klienta lub utworzoną lokalnie). Jeśli system utrzymuje trwały stan wystąpienia przepływu pracy, wystąpienie przepływu pracy musi być utrwalone podczas wykonywania tej operacji.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Kontrakt nie zapewnia metody tworzenia nowego wystąpienia przepływu pracy, tylko w celu zarządzania istniejącymi wystąpieniami przepływu pracy. Aby uzyskać więcej informacji na temat zdalnego tworzenia nowego wystąpienia przepływu pracy, zobacz [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>jest standardowym punktem końcowym ze stałą umową <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Po dodaniu do <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia ten punkt końcowy może zostać użyty do wysłania operacji polecenia do dowolnego wystąpienia przepływu pracy hostowanego przez wystąpienie hosta. Aby uzyskać więcej informacji na temat standardowych punktów końcowych, zobacz [standardowe punkty końcowe](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient>jest klasą, która umożliwia wysyłanie komunikatów kontroli do <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Zawiera ona metodę dla każdej operacji obsługiwanej przez <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontrakt z wyjątkiem operacji transakcyjnych. <xref:System.ServiceModel.Activities.WorkflowControlClient>używa otoczenia transakcji, aby określić, czy należy użyć operacji transakcyjnej.
