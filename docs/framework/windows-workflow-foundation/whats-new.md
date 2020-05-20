---
title: Co nowego w programie Windows Workflow Foundation
description: Dowiedz się więcej o Windows Workflow Foundation zmianach w .NET Framework 4. Przepływy pracy są łatwiejsze do tworzenia, wykonywania i konserwowania.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: b25b71a61f8a96d59c79e780d9fe5cd03abfa299
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419346"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>Co nowego w programie Windows Workflow Foundation

Windows Workflow Foundation (WF) w .NET Framework 4 zmienia kilka odmian programistycznych z poprzednich wersji. Przepływy pracy są teraz łatwiejsze do tworzenia, wykonywania i konserwowania oraz implementowania hosta nowych funkcji. Aby uzyskać więcej informacji na temat migrowania aplikacji przepływu pracy .NET 3,0 i .NET 3,5 do korzystania z najnowszej wersji, zobacz [wskazówki dotyczące migracji](migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>Model działań przepływu pracy  
 Działanie jest teraz jednostką podstawową tworzenia przepływu pracy, a nie przy użyciu <xref:System.Workflow.Activities.SequentialWorkflowActivity> <xref:System.Workflow.Activities.StateMachineWorkflowActivity> klas lub. <xref:System.Activities.Activity>Klasa zawiera podstawowe abstrakcje zachowania przepływu pracy. Autorzy działań mogą następnie zaimplementować <xref:System.Activities.CodeActivity> dla podstawowych funkcji działania niestandardowego lub <xref:System.Activities.NativeActivity> dla funkcji niestandardowego działania korzystającej z szerokości środowiska uruchomieniowego. <xref:System.Activities.Activity>jest klasą używaną przez autorów działań do wyrażania nowych zachowań deklaratywnie pod względem innych <xref:System.Activities.NativeActivity> , <xref:System.Activities.CodeActivity> , <xref:System.Activities.AsyncCodeActivity> , lub <xref:System.Activities.DynamicActivity> obiektów, niezależnie od tego, czy są one opracowane przez użytkownika, czy dołączone do [wbudowanej biblioteki działań](net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Zaawansowane opcje działań złożonych  
 <xref:System.Activities.Statements.Flowchart>jest zaawansowanym nowym działaniem przepływu sterowania, które pozwala autorom na modelowanie dowolnych pętli i rozgałęzianie warunkowe. <xref:System.Activities.Statements.Flowchart>zapewnia oparty na zdarzeniach model programowania, który wcześniej był możliwy do wdrożenia przy użyciu programu <xref:System.Workflow.Activities.StateMachineWorkflowActivity> . Przepływy pracy proceduralnej korzystają z nowych działań związanych z kontrolą przepływu, które modelują tradycyjne struktury kontroli przepływu, takie jak <xref:System.Activities.Statements.TryCatch> i <xref:System.Activities.Statements.Switch%601> .  
  
## <a name="expanded-built-in-activity-library"></a>Rozwinięta wbudowana Biblioteka działań  
 Nowe funkcje biblioteki działań obejmują:  
  
- Nowe działania sterowania przepływem, takie jak,,,,, <xref:System.Activities.Statements.DoWhile> <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.Switch%601> i <xref:System.Activities.Statements.ParallelForEach%601> .  
  
- Działania związane z manipulowaniem danymi elementu członkowskiego, takimi jak <xref:System.Activities.Statements.Assign> i działaniami zbierania, takimi jak <xref:System.Activities.Statements.AddToCollection%601> .  
  
- Działania dotyczące kontrolowania transakcji, takich jak <xref:System.Activities.Statements.TransactionScope> i <xref:System.Activities.Statements.Compensate> .  
  
- Nowe działania dotyczące obsługi komunikatów, takie jak <xref:System.ServiceModel.Activities.SendContent> i <xref:System.ServiceModel.Activities.ReceiveReply> .  
  
## <a name="explicit-activity-data-model"></a>Jawny model danych działań  
 .NET Framework 4 zawiera nowe opcje przechowywania lub przeniesienia danych. Dane mogą być przechowywane w działaniu przy użyciu <xref:System.Activities.Variable> . W przypadku przeniesienia danych do i z działania, wyspecjalizowane typy argumentów są używane do określania, które dane kierunku są przenoszone. Te typy to <xref:System.Activities.InArgument> , <xref:System.Activities.InOutArgument> , i <xref:System.Activities.OutArgument> . Aby uzyskać więcej informacji, zobacz [Windows Workflow Foundation model danych](data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Ulepszone opcje hostingu, trwałości i śledzenia  
 .NET Framework 4 zawiera usprawnienia trwałości, takie jak następujące:  
  
- Istnieje więcej opcji uruchamiania przepływów pracy, w tym <xref:System.ServiceModel.Activities.WorkflowServiceHost> , <xref:System.Activities.WorkflowApplication> i <xref:System.Activities.WorkflowInvoker> .  
  
- Dane stanu przepływu pracy mogą być jawnie utrwalane przy użyciu <xref:System.Activities.Statements.Persist> działania.  
  
- Host może utrzymywać <xref:System.Activities.ActivityInstance> bez wyładowywania.  
  
- Przepływ pracy może określać strefy nie utrwalania podczas pracy z danymi, które nie mogą być utrwalane, dzięki czemu trwałość zostanie odroczona do momentu opuszczenia strefy braku utrwalania.  
  
- Transakcje można przepływać do przepływu pracy przy użyciu <xref:System.Activities.Statements.TransactionScope> .  
  
- Śledzenie jest łatwiejsze w użyciu <xref:System.Activities.Tracking.TrackingParticipant> .  
  
- Śledzenie do dziennika zdarzeń systemu jest obsługiwane przy użyciu programu <xref:System.Activities.Tracking.EtwTrackingParticipant> .  
  
- Wznawianie oczekującego przepływu pracy jest teraz zarządzane przy użyciu <xref:System.Activities.Bookmark> obiektu.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Łatwiejsza obsługa środowiska Projektant WF  
 Nowy Projektant WF jest oparty na Windows Presentation Foundation (WPF) i oferuje łatwiejszy model do użycia podczas ponownego hostowania projektanta WF poza programem Visual Studio, a także oferuje łatwiejsze mechanizmy tworzenia niestandardowych projektantów działań. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska projektowania przepływu pracy](customizing-the-workflow-design-experience.md).
