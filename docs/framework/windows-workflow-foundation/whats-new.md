---
title: What's New in Windows Workflow Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: 5ab1419a29dd77ac276681bb49dc529fc05d5b15
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711827"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>What's New in Windows Workflow Foundation
Windows Workflow Foundation (WF) w [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] kilka paradygmatów rozwoju zmienia się z poprzednich wersji. Przepływy pracy są teraz łatwiejsze do tworzenia, wykonywania, obsługa i zaimplementować wiele nowych funkcji. Aby uzyskać więcej informacji na temat migrowania aplikacji .NET 3.0 i .NET 3.5 przepływu pracy można korzystać z najnowszej wersji, zobacz [wskazówek dotyczących migracji](migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>Model działania przepływu pracy  
 Działanie jest teraz podstawowej jednostce tworzenia przepływu pracy, a nie przy użyciu <xref:System.Workflow.Activities.SequentialWorkflowActivity> lub <xref:System.Workflow.Activities.StateMachineWorkflowActivity> klasy. <xref:System.Activities.Activity> Klasa stanowi podstawowy abstrakcji działania przepływu pracy. Działanie autorzy mogą implementować albo <xref:System.Activities.CodeActivity> funkcji podstawowych, niestandardowe działanie lub <xref:System.Activities.NativeActivity> dla funkcji niestandardowego działania, które korzysta z zakresem środowiska uruchomieniowego. <xref:System.Activities.Activity> jest klasą używaną przez autorów działania programu express nowych zachowań w sposób deklaratywny pod względem innych <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.DynamicActivity> obiektów, czy są one niestandardowej lub składnikach uwzględnionych w [wbudowanego działania Biblioteka](net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Opcje działania złożonego zaawansowane  
 <xref:System.Activities.Statements.Flowchart> to zaawansowane nowe działanie przepływu sterowania, umożliwia autorom modelu dowolnego pętli i rozgałęzień warunkowych. <xref:System.Activities.Statements.Flowchart> zapewnia oparte na zdarzeniach model programowania, który mógł wcześniej tylko można zaimplementować przy użyciu <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. Proceduralne przepływy pracy korzystają z nowych działań sterowania przepływem, które modelują sterowanie przepływem tradycyjnych struktur, takich jak <xref:System.Activities.Statements.TryCatch> i <xref:System.Activities.Statements.Switch%601>.  
  
## <a name="expanded-built-in-activity-library"></a>Rozwinięte wbudowana biblioteka działań  
 Nowe funkcje biblioteki działań:  
  
-   Nowy przepływ sterowania działań, takich jak <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601>, i <xref:System.Activities.Statements.ParallelForEach%601>.  
  
-   Działania do manipulowania element członkowski danych, takich jak <xref:System.Activities.Statements.Assign> i działań kolekcji, takie jak <xref:System.Activities.Statements.AddToCollection%601>.  
  
-   Działania związane z kontrolowania transakcji, takich jak <xref:System.Activities.Statements.TransactionScope> i <xref:System.Activities.Statements.Compensate>.  
  
-   Nowe działania dotyczące komunikatów takich jak <xref:System.ServiceModel.Activities.SendContent> i <xref:System.ServiceModel.Activities.ReceiveReply>.  
  
## <a name="explicit-activity-data-model"></a>Model danych aktywności jawne  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] zawiera nowe opcje przechowywania lub przenoszenia danych. Dane mogą być przechowywane w działanie przy użyciu <xref:System.Activities.Variable>. Podczas przenoszenia danych do i z działania, typy argumentów specjalne są używane do ustalenia, które dane kierunek jest przenoszenie. Te typy są <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument>, i <xref:System.Activities.OutArgument>. Aby uzyskać więcej informacji, zobacz [modelu danych programu Windows Workflow Foundation](data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Ulepszone hostingu, trwałości, opcje i śledzenia  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] zawiera ulepszenia trwałości, takie jak następujące:  
  
-   Istnieją dodatkowe opcje do uruchamiania przepływów pracy, w tym <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication>, i <xref:System.Activities.WorkflowInvoker>.  
  
-   Dane o stanie przepływu pracy może być jawnie utrwalony, za pomocą <xref:System.Activities.Statements.Persist> działania.  
  
-   Hosta można utrwalić <xref:System.Activities.ActivityInstance> bez rozładowywania go.  
  
-   Przepływ pracy można określić nie utrwalić stref podczas pracy z danymi, które nie może zostać utrwalona, tak aby trwałości zostanie odłożona do momentu strefy no-persist kończy działanie.  
  
-   Transakcje mogą przepływać do przepływu pracy przy użyciu <xref:System.Activities.Statements.TransactionScope>.  
  
-   Śledzenie łatwiej odbywa się przy użyciu <xref:System.Activities.Tracking.TrackingParticipant>.  
  
-   Śledzenie w dzienniku zdarzeń systemowych znajduje się za pomocą <xref:System.Activities.Tracking.EtwTrackingParticipant>.  
  
-   Wznawianie oczekujące przepływu pracy są teraz zarządzane za pomocą <xref:System.Activities.Bookmark> obiektu.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Łatwiejsze mogą rozszerzyć środowisko projektanta WF  
 Nowy Designer WF jest zbudowany na Windows Presentation Foundation (WPF) i udostępnia model łatwiejsze do użycia podczas rehostowanie projektanta WF poza programem Visual Studio i udostępnia także łatwiej mechanizmy do tworzenia Projektanci działań niestandardowych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska projektowania przepływu pracy](customizing-the-workflow-design-experience.md).
