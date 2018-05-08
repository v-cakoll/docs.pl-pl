---
title: Co&#39;s nowe w programie Windows Workflow Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: d45c16d4f16c239d1c1c8116b4b41dd41f8a953d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="what39s-new-in-windows-workflow-foundation"></a>Co&#39;s nowe w programie Windows Workflow Foundation
Windows Workflow Foundation (WF) w [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] zmienia kilka wzorcami programowanie z poprzednich wersji. Przepływy pracy są teraz łatwiejsze do tworzenia, zostanie wykonane, obsługi i wdrożenie hosta funkcji. Aby uzyskać więcej informacji na temat migrowania aplikacji .NET 3.0 i .NET 3.5 przepływu pracy korzysta z najnowszej wersji, zobacz [wskazówki dotyczące migracji](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>Model działania przepływu pracy  
 Działanie jest teraz podstawowa jednostka tworzenia przepływu pracy, a nie za pomocą <xref:System.Workflow.Activities.SequentialWorkflowActivity> lub <xref:System.Workflow.Activities.StateMachineWorkflowActivity> klasy. <xref:System.Activities.Activity> Klasa udostępnia podstawowe abstrakcji działania przepływu pracy. Autorzy działania można następnie wdrożyć to rozwiązanie albo <xref:System.Activities.CodeActivity> funkcji podstawowych działań niestandardowych lub <xref:System.Activities.NativeActivity> dla działań niestandardowych funkcje, które używa szerokość środowiska uruchomieniowego. <xref:System.Activities.Activity> jest klasą używaną przez autorów działania Express nowe zachowania deklaratywnie pod względem innych <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.DynamicActivity> obiekty, czy są one opracowany niestandardowe lub składnikach uwzględnionych w [wbudowane działania Biblioteka](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Złożone zaawansowanej opcji działania  
 <xref:System.Activities.Statements.Flowchart> to wydajne nowe działanie przepływu sterowania, który umożliwia autorom model dowolnego pętle i rozgałęzień warunkowych. <xref:System.Activities.Statements.Flowchart> udostępnia sterowane zdarzeniami model programowania, który wcześniej tylko mogło zostać wykonane z <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. Procedurach przepływy pracy korzystają z nowych działań przepływu sterowania modelującymi sterowanie przepływem tradycyjnych struktur, takich jak <xref:System.Activities.Statements.TryCatch> i <xref:System.Activities.Statements.Switch%601>.  
  
## <a name="expanded-built-in-activity-library"></a>Biblioteka działań wbudowanych rozszerzonej  
 Nowe funkcje biblioteki działania:  
  
-   Nowy przepływ sterowania działań, takich jak <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601>, i <xref:System.Activities.Statements.ParallelForEach%601>.  
  
-   Działania do manipulowania danych elementów członkowskich, takich jak <xref:System.Activities.Statements.Assign> i kolekcji działań, takich jak <xref:System.Activities.Statements.AddToCollection%601>.  
  
-   Działania takie jak kontrolowanie transakcji, <xref:System.Activities.Statements.TransactionScope> i <xref:System.Activities.Statements.Compensate>.  
  
-   Nowych działań dotyczących komunikatów takich jak <xref:System.ServiceModel.Activities.SendContent> i <xref:System.ServiceModel.Activities.ReceiveReply>.  
  
## <a name="explicit-activity-data-model"></a>Jawne działania modelu danych  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] zawiera nowe opcje przechowywania lub przenoszenia danych. Dane mogą być przechowywane w działania przy użyciu <xref:System.Activities.Variable>. Podczas przenoszenia danych do i z działania, typy argumentów specjalne są używane do określenia porusza się dane, które kierunku. Te typy są <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument>, i <xref:System.Activities.OutArgument>. Aby uzyskać więcej informacji, zobacz [systemu Windows Workflow Foundation danych modelu](../../../docs/framework/windows-workflow-foundation/data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Ulepszone Hosting trwałości, opcje i śledzenia  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] zawiera ulepszenia trwałości, takie jak następujące:  
  
-   Istnieją dodatkowe opcje do uruchamiania przepływów pracy, włącznie z <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication>, i <xref:System.Activities.WorkflowInvoker>.  
  
-   Dane stanu przepływu pracy można jawnie utrwalona, za pomocą <xref:System.Activities.Statements.Persist> działania.  
  
-   Hosta można utrwalić <xref:System.Activities.ActivityInstance> bez wyładowywanie.  
  
-   Przepływ pracy można określić nie utrzymują stref podczas pracy z danymi nie może zostać utrwalona, dzięki czemu trwałości zostanie odłożona do momentu strefy no-persist kończy działanie.  
  
-   Transakcje mogą przepływać do przepływu pracy przy użyciu <xref:System.Activities.Statements.TransactionScope>.  
  
-   Śledzenie łatwiej odbywa się przy użyciu <xref:System.Activities.Tracking.TrackingParticipant>.  
  
-   Śledzenie w dzienniku zdarzeń systemowych jest realizowane przy użyciu <xref:System.Activities.Tracking.EtwTrackingParticipant>.  
  
-   Wznawianie działania oczekującej przepływu pracy jest teraz zarządzane za pomocą <xref:System.Activities.Bookmark> obiektu.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Łatwiejsze możliwości rozszerzania projektanta WF środowisko  
 Nowy Designer WF jest oparty na systemie Windows Presentation Foundation (WPF) i udostępnia model łatwiejsze do użycia podczas rehosting projektanta WF poza Visual Studio i udostępnia także mechanizmy łatwiejsze do tworzenia projektantów działań niestandardowych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie projektu przepływu pracy](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md).
