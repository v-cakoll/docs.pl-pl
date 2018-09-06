---
title: Używanie działania CancellationScope
ms.date: 03/30/2017
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
ms.openlocfilehash: 82d44fff869f207c09dc7685fc3470630e001a59
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731524"
---
# <a name="using-cancellationscope"></a>Używanie działania CancellationScope
W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.Statements.CancellationScope> działania można anulować pracy w aplikacji.  
  
 Wiele składniki warstwy środkowej i usługi zależą od dobrze znanych konstrukcji programowania transakcji w celu obsługi anulowania dla nich.  Jednak istnieje wiele sytuacji, w których nie można wykonać w ramach transakcji pracy musi zostać anulowana.  Za pomocą anulowania jest trudniejsze niż za pomocą transakcji, ponieważ najpierw musi być śledzona pracy, która musi zostać anulowana. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ułatwia to, zapewniając <xref:System.Activities.Statements.CancellationScope> działania.  
  
 Anulowanie mogą być wyzwalane, lub z w ramach działania z elementu nadrzędnego tego działania.  Działania podrzędne odbywa się przy ich działania nadrzędnego (takie jak <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.Flowchart>, lub niestandardowych działań złożonych).  Działania nadrzędnego może anulować działania podrzędne jakiegokolwiek powodu.  Na przykład <xref:System.Activities.Statements.Parallel> działania o trzy gałęzie podrzędne spowoduje anulowanie pozostałych gałęzie podrzędne w każdym przypadku, gdy zostanie zakończona gałęzi i <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> wyrażenie daje w wyniku `true`. Przepływ pracy może być anulowane zewnętrznie przez aplikację hosta przez wywołanie metody <xref:System.Activities.WorkflowApplication.Cancel%2A>.  
  
 Do użycia <xref:System.Activities.Statements.CancellationScope> działania, umieść pracy, którą musi zostać anulowane w <xref:System.Activities.Statements.CancellationScope.Body%2A> właściwość i umieść pracy, która jest wykonywana po anulowaniu do <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> właściwości.  
  
 Niniejszy przykład pokazuje, anulowanie działania z w ramach działania.  
  
 Scenariusz, w którym w przykładzie użyto w celu zademonstrowania <xref:System.Activities.Statements.CancellationScope> działania jest klientem, chce kupić biletu do Miami tak szybko, jak to możliwe. Istnieją dwa biura w podróży, które firmy. W przykładzie użyto dwóch <xref:System.Activities.Statements.CancellationScope> w ramach <xref:System.Activities.Statements.Parallel> działania do modelowania tej logiki biznesowej. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> z <xref:System.Activities.Statements.Parallel> działania jest ustawiona na `true`; od <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> jest zaznaczone, po zakończeniu dowolnej innej gałęzi, spowoduje to pozostałych gałęzi zostaną anulowane po zakończeniu pierwszej gałęzi. Aplikacja kliencka żąda zarówno agencje kupić--ticket, a gdy pierwsza z nich potwierdzi zakupionych--ticket, aplikacji spowoduje anulowanie zamówienia w innych agencji.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CancelationScopeXAML.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`