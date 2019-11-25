---
title: Biblioteka działań
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 15260fc2ad96e1761a8a41ccc84b2c199e3d448a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283152"
---
# <a name="activity-library"></a>Biblioteka działań
Ta sekcja zawiera przykłady demonstrujące zaawansowane działania niestandardowe w Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>W tej sekcji

 [Niestandardowe działanie SendMail](sendmail-custom-activity.md)  
 Pokazuje, jak utworzyć niestandardowe działanie, które wynika z <xref:System.Activities.AsyncCodeActivity> do wysyłania wiadomości e-mail przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy.  
  
 [Działanie ThrottledParallelForEach](throttled-parallel-foreach.md)  
 Pokazuje, w jaki sposób działanie `ThrottleParallelForEach` jest podobne do działania <xref:System.Activities.Statements.ParallelForEach%601> z jednym wyjątkiem, że umożliwia ustawienie współczynnika współbieżności, aby ograniczyć liczbę równoczesnych gałęzi do wykonania.
  
 [Działania dostępu do bazy danych](database-access-activities.md)  
 Pokazuje, jak tworzyć działania umożliwiające dostęp do baz danych w celu pobierania lub modyfikowania informacji oraz korzystania z [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) w celu uzyskania dostępu do bazy danych.  
  
 [Działanie zasad zewnętrznych w programie .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)  
 Pokazuje, w jaki sposób działanie ExternalizedPolicy4 umożliwia wykonywanie istniejących Windows Workflow Foundation w .NET Framework 3,5 (WF 3,5) <xref:System.Workflow.Activities.Rules.RuleSet> obiektów w Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4,5) bezpośrednio przy użyciu aparatu reguł, który jest dostarczany w programie WF 3,5. 
  
 [Nieogólne działanie ForEach](non-generic-foreach.md)  
 Demonstruje sposób tworzenia nieogólnej wersji działania <xref:System.Activities.Statements.ForEach%601>.  
  
 [Nieogólne działanie ParallelForEach](non-generic-parallelforeach.md)  
 Demonstruje sposób tworzenia nieogólnej wersji działania <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 [Działanie GetWorkflowInstanceId](get-workflowinstanceid.md)  
 Demonstruje sposób używania działania niestandardowego `GetWorkflowInstanceId`, aby zwrócić identyfikator wystąpienia przepływu pracy.
