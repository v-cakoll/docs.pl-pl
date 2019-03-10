---
title: Biblioteka działań
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: b701d382c25644181b23f3c0f0cd8e019b8d37d1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709847"
---
# <a name="activity-library"></a>Biblioteka działań
Ta sekcja zawiera przykłady pokazujące, zaawansowanych niestandardowych działań w Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>W tej sekcji

 [Niestandardowe działanie SendMail](sendmail-custom-activity.md)  
 Pokazuje, jak utworzyć niestandardowe działanie, która pochodzi od klasy <xref:System.Activities.AsyncCodeActivity> do wysyłania wiadomości e-mail przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy.  
  
 [Działanie ThrottledParallelForEach](throttled-parallel-foreach.md)  
 Pokazuje, jak `ThrottleParallelForEach` działanie jest podobne do <xref:System.Activities.Statements.ParallelForEach%601> działania z jednym wyjątkiem że umożliwia ustawienie współczynnika współbieżności Aby ograniczyć liczbę jednoczesnych gałęzi do wykonania.
  
 [Działania dostępu do bazy danych](database-access-activities.md)  
 Pokazuje, jak utworzyć działania, które umożliwiają uzyskiwanie dostępu do bazy danych do pobierania lub modyfikowanie informacji i użycia [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) dostęp do bazy danych.  
  
 [Działanie zasad zewnętrznych w programie .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)  
 Pokazuje, jak działanie ExternalizedPolicy4 zezwala na wykonywanie istniejącej Windows Workflow Foundation w [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> obiektów w programie Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) bezpośrednio za pomocą aparatu reguł to znaczy wydane w wersji 3.5 WF. 
  
 [Nieogólne działanie ForEach](non-generic-foreach.md)  
 Pokazuje, jak utworzyć wersję inną niż ogólna <xref:System.Activities.Statements.ForEach%601> działania.  
  
 [Nieogólne działanie ParallelForEach](non-generic-parallelforeach.md)  
 Pokazuje, jak utworzyć wersję inną niż ogólna <xref:System.Activities.Statements.ParallelForEach%601> działania.  
  
 [Działanie GetWorkflowInstanceId](get-workflowinstanceid.md)  
 Pokazuje, jak użyć niestandardowego działania, `GetWorkflowInstanceId`, aby zwrócić identyfikator wystąpienia przepływu pracy
