---
title: Biblioteka działań
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 7e8777d0068e6cca9c9324a6fd2668e6ff9e9da7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844023"
---
# <a name="activity-library"></a>Biblioteka działań
Ta sekcja zawiera przykłady pokazujące, zaawansowanych niestandardowych działań w Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>W tej sekcji

 [Niestandardowe działanie SendMail](../../../../docs/framework/windows-workflow-foundation/samples/sendmail-custom-activity.md)  
 Pokazuje, jak utworzyć niestandardowe działanie, która pochodzi od klasy <xref:System.Activities.AsyncCodeActivity> do wysyłania wiadomości e-mail przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy.  
  
 [Działanie ThrottledParallelForEach](../../../../docs/framework/windows-workflow-foundation/samples/throttled-parallel-foreach.md)  
 Pokazuje, jak `ThrottleParallelForEach` działanie jest podobne do <xref:System.Activities.Statements.ParallelForEach%601> działania z jednym wyjątkiem że umożliwia ustawienie współczynnika współbieżności Aby ograniczyć liczbę jednoczesnych gałęzi do wykonania.
  
 [Działania dostępu do bazy danych](../../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md)  
 Pokazuje, jak utworzyć działania, które umożliwiają uzyskiwanie dostępu do bazy danych do pobierania lub modyfikowanie informacji i użycia [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) dostęp do bazy danych.  
  
 [Działanie zasad zewnętrznych w programie .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/externalized-policy-activity-in-net-framework-4-5.md)  
 Pokazuje, jak działanie ExternalizedPolicy4 zezwala na wykonywanie istniejącej Windows Workflow Foundation w [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> obiektów w programie Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) bezpośrednio za pomocą aparatu reguł to znaczy wydane w wersji 3.5 WF. 
  
 [Nieogólne działanie ForEach](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md)  
 Pokazuje, jak utworzyć wersję inną niż ogólna <xref:System.Activities.Statements.ForEach%601> działania.  
  
 [Nieogólne działanie ParallelForEach](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md)  
 Pokazuje, jak utworzyć wersję inną niż ogólna <xref:System.Activities.Statements.ParallelForEach%601> działania.  
  
 [Działanie GetWorkflowInstanceId](../../../../docs/framework/windows-workflow-foundation/samples/get-workflowinstanceid.md)  
 Pokazuje, jak użyć niestandardowego działania, `GetWorkflowInstanceId`, aby zwrócić identyfikator wystąpienia przepływu pracy
