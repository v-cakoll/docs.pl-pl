---
title: Biblioteka działań
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142904"
---
# <a name="activity-library"></a>Biblioteka działań
Ta sekcja zawiera przykłady, które pokazują zaawansowane działania niestandardowe w programie Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>W tej sekcji

 [Niestandardowe działanie SendMail](sendmail-custom-activity.md)  
 Pokazuje, jak utworzyć działanie niestandardowe, <xref:System.Activities.AsyncCodeActivity> które pochodzi z wysyłania poczty przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy.  
  
 [Działanie ThrottledParallelForEach](throttled-parallel-foreach.md)  
 Pokazuje, jak `ThrottleParallelForEach` działanie jest <xref:System.Activities.Statements.ParallelForEach%601> podobne do działania z jednym wyjątkiem, który umożliwia ustawienie współczynnik współbieżności, aby ograniczyć liczbę równoczesnych gałęzi do wykonania.
  
 [Działania dostępu do bazy danych](database-access-activities.md)  
 Pokazuje, jak tworzyć działania, które umożliwiają dostęp do baz danych do pobierania lub modyfikowania informacji i używać [ADO.NET](../../data/adonet/index.md) dostępu do bazy danych.  
  
 [Działanie zasad zewnętrznych w programie .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)  
 Pokazuje, jak działanie ExternalizedPolicy4 umożliwia wykonywanie istniejących fundacji przepływu pracy systemu Windows w obiektach .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> w programie Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] programie (WF 4.5) bezpośrednio przy użyciu aparatu reguł dostarczanych w 3.5 WF.
  
 [Nieogólne działanie ForEach](non-generic-foreach.md)  
 Pokazuje, jak utworzyć nierodową wersję <xref:System.Activities.Statements.ForEach%601> działania.  
  
 [Nieogólne działanie ParallelForEach](non-generic-parallelforeach.md)  
 Pokazuje, jak utworzyć nierodową wersję <xref:System.Activities.Statements.ParallelForEach%601> działania.  
  
 [Działanie GetWorkflowInstanceId](get-workflowinstanceid.md)  
 Pokazuje, jak używać działania `GetWorkflowInstanceId`niestandardowego, aby zwrócić identyfikator wystąpienia przepływu pracy.
