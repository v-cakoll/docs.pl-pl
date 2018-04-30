---
title: Omówienie przepływu pracy systemu Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc1aa65b413b87b27c05e7a12ce607d1cd30b89b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="windows-workflow-overview"></a>Omówienie przepływu pracy systemu Windows
Przepływ pracy to zbiór jednostek stanie wolnym wywoływana *działania* przechowywane jako model, który opisano proces rzeczywistych. Przepływy pracy umożliwiają opisu kolejność wykonywania i zależności między pracy krótko - i długotrwałe. Tę pracę przechodzi przez model od początku do końca, a działania mogą być wykonywane przez osoby lub funkcji systemu.  
  
## <a name="workflow-run-time-engine"></a>Aparat środowiska wykonawczego przepływów pracy  
 Każdy działającego wystąpienia przepływu pracy nie zostanie utworzona i obsługiwanego przez aparat środowiska wykonawczego w trakcie interakcji proces hosta z za pomocą jednego z następujących czynności:  
  
-   A <xref:System.Activities.WorkflowInvoker>, który wywołuje przepływu pracy, jak metody.  
  
-   A <xref:System.Activities.WorkflowApplication> jawne kontrolować wykonywanie wystąpienia przepływu pracy pojedynczego.  
  
-   A <xref:System.ServiceModel.WorkflowServiceHost> oparta na komunikatach interakcji w scenariuszach wielu wystąpień.  
  
 Każda z tych klas opakowuje podstawowego środowiska wykonawczego działania, reprezentowane jako <xref:System.Activities.ActivityInstance> odpowiedzialny za wykonania działania. Może istnieć kilka <xref:System.Activities.ActivityInstance> obiektów w domenie aplikacji uruchomione jednocześnie.  
  
 Każdy z powyższych obiektów interakcji trzy hosta jest tworzony w drzewie działań określonych jako program przepływu pracy. Przy użyciu tych typów lub hosta niestandardowego, który opakowuje <xref:System.Activities.ActivityInstance>, przepływy pracy mogą być wykonywane w dowolnym procesu systemu Windows, w tym aplikacji konsoli oparte na formularzach aplikacji usług systemu Windows, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] witryn sieci Web i [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]usług.  
  
 ![Składniki przepływu pracy w ramach procesu hosta](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Składniki przepływu pracy w ramach procesu hosta  
  
## <a name="interaction-between-workflow-components"></a>Interakcja między składnikami przepływu pracy  
 Poniższy diagram przedstawia interakcje składniki przepływu pracy ze sobą.  
  
 ![Przepływ pracy interakcji](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")  
  
 Na powyższym diagramie <xref:System.Activities.WorkflowInvoker.Invoke%2A> metody <xref:System.Activities.WorkflowInvoker> klasa jest używana do wywołania kilka wystąpień przepływu pracy. <xref:System.Activities.WorkflowInvoker> Służy do lekkie przepływy pracy, które nie są zarządzanie z hosta; przepływy pracy, które wymagają zarządzania z hosta (takich jak <xref:System.Activities.Bookmark> wznowienie) musi zostać wykonana przy użyciu <xref:System.Activities.WorkflowApplication.Run%2A> zamiast tego. Nie jest wymagane oczekiwania dla jednego wystąpienia przepływu pracy zakończyć przed wywołaniem innej; Aparat środowiska wykonawczego obsługuje uruchamianie wielu wystąpień przepływu pracy jednocześnie.  Przepływy pracy wywoływane są następujące:  
  
-   A <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.WriteLine> działania podrzędnego. A <xref:System.Activities.Variable> elementu nadrzędnego działania jest powiązany z <xref:System.Activities.InArgument> działania podrzędnego. Aby uzyskać więcej informacji o zmiennych, argumentów i powiązanie, zobacz [zmiennych i argumenty](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
-   Niestandardowe działania o nazwie `ReadLine`. <xref:System.Activities.OutArgument> z `ReadLine` działania jest zwracana do wywoływania <xref:System.Activities.WorkflowInvoker.Invoke%2A> metody.  
  
-   Niestandardowe działania, która pochodzi z <xref:System.Activities.CodeActivity> klasy abstrakcyjnej. <xref:System.Activities.CodeActivity> Mogą uzyskiwać dostęp do funkcji środowiska uruchomieniowego (na przykład śledzenia i właściwości) przy użyciu <xref:System.Activities.CodeActivityContext> dostępna jako parametr <xref:System.Activities.CodeActivity.Execute%2A> metody. Aby uzyskać więcej informacji o tych funkcjach środowiska wykonawczego, zobacz [przepływu pracy śledzenia i śledzenia](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [właściwości wykonania przepływu pracy](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md).  
  
## <a name="see-also"></a>Zobacz też  
 [BizTalk Server 2006 lub WF? Wybór narzędzia prawo przepływu pracy dla projektu](http://go.microsoft.com/fwlink/?LinkId=154901)
