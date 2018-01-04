---
title: "Przy użyciu CancellationScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae41255cea4621cbcd4050a5ebb04e662102bf77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-cancellationscope"></a>Przy użyciu CancellationScope
W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.Statements.CancellationScope> działanie, aby anulować pracy w aplikacji.  
  
 Wiele składników warstwy środkowej i usług korzystają z dobrze znanego konstrukcji programującej transakcji do obsługi anulowania dla nich.  Istnieje jednak wiele sytuacji, w których można anulować pracy, które nie może zostać wykonane w transakcji.  Przy użyciu anulowania jest trudniejsze niż przy użyciu transakcji, ponieważ najpierw musi być śledzone pracy, które muszą być anulowane. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]Umożliwia to zapewniając <xref:System.Activities.Statements.CancellationScope> działania.  
  
 Anulowanie mogą być wyzwalane, albo z działania lub z działania nadrzędnego.  Działania podrzędne są planowane według ich działania nadrzędnego (takich jak <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.Flowchart>, lub niestandardowych działań złożonych).  Działanie nadrzędne anulować działań podrzędnych różnych przyczyn.  Na przykład <xref:System.Activities.Statements.Parallel> działania o trzy gałęzie podrzędne spowoduje anulowanie pozostałych gałęzie podrzędne w każdym przypadku, gdy ukończy gałęzi i <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> wyrażenie daje w wyniku `true`. Przepływu pracy mogą również zostać anulowane zewnętrznie przez aplikację hosta przez wywołanie metody <xref:System.Activities.WorkflowApplication.Cancel%2A>.  
  
 Aby użyć <xref:System.Activities.Statements.CancellationScope> działanie, włączyć pracy, który musi zostać anulowane w <xref:System.Activities.Statements.CancellationScope.Body%2A> właściwości i put pracy, które jest przeprowadzane po anulowaniu do <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> właściwości.  
  
 W przykładzie pokazano, anulowanie działania z wewnątrz działania, do samej siebie.  
  
 Scenariusz, który używa próbki do zaprezentowania <xref:System.Activities.Statements.CancellationScope> działanie jest pożądane możliwie jak kupić bilet, aby Miami klienta. Istnieją dwa agencje podróży, które mają biznesowe. W przykładzie użyto dwóch <xref:System.Activities.Statements.CancellationScope> w <xref:System.Activities.Statements.Parallel> działania umożliwia modelowanie tej logiki biznesowej. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> z <xref:System.Activities.Statements.Parallel> ustawiono działania `true`; od <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> jest zaznaczone, po zakończeniu oddziałów, spowoduje to pozostałych gałęzi do anulowania po zakończeniu pierwszej gałęzi. Aplikacja kliencka żąda zarówno agencje kupić bilet, i gdy pierwszy potwierdzi, że bilet został kupiony, aplikacja anuluje kolejności w innych agencji.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CancelationScopeXAML.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`