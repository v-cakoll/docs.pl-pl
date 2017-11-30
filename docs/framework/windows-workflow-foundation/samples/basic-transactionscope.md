---
title: Podstawowy element TransactionScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01d5d6f35ed9eaa64786d18c2477862594c546be
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="basic-transactionscope"></a>Podstawowy element TransactionScope
W tym przykładzie składa się z czterech scenariuszy uruchomienia przedstawiająca sposób zagnieździć <xref:System.Activities.Statements.TransactionScope> wystąpień. Pierwszy scenariusz przedstawia zagnieżdżania 3 działania firm, które autor nie zna konstrukcji. Scenariusze drugiego i trzeciego pokazują, jak są przestrzegane limity czasu i końcowe scenariuszu pokazano <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> ustawienie.  
  
## <a name="nesting-of-transactionscopeactivity"></a>Zagnieżdżanie działania TransactionScopeActivity  
 Przepływ pracy dla pierwszego scenariusza składa się z dwóch sekwencji <xref:System.Activities.Statements.WriteLine> działań i <xref:System.Activities.Statements.TransactionScope>. Treść <xref:System.Activities.Statements.TransactionScope> sekwencja dwóch więcej <xref:System.Activities.Statements.WriteLine> działań, niestandardowe działanie, które wyświetla lokalny identyfikator transakcji i innej firmy działania. Działanie innych firm `TransactionScopeTest` zawiera <xref:System.Activities.Statements.TransactionScope> mimo, że autor przepływu pracy nie ma możliwości wiedzy. W tym scenariuszu pokazano, że <xref:System.Activities.Statements.TransactionScope> działania mogą być zagnieżdżone.  
  
## <a name="time-outs"></a>Limity czasu  
 Drugi scenariusz przepływu pracy jest niemal identyczna jako pierwszy. `TransactionScopeTest` Zostało zastąpione <xref:System.Activities.Statements.TransactionScope>. Treść <xref:System.Activities.Statements.TransactionScope> opóźnienia pięciu sekund i limit czasu dla transakcji jest ustawiony na dwóch sekund. Limit czasu dla zewnętrznego <xref:System.Activities.Statements.TransactionScope> jest ustawiony na 10 sekund. Warto zauważyć, że wzięty pod uwagę najmniejszą limitu czasu w zakresie transakcji upłynie limit czasu.  
  
 Przepływ pracy dla trzeci scenariusz jest niemal identyczna z scenariusz dwa. Działanie opóźnienie została przeniesiona z treści wewnętrzny <xref:System.Activities.Statements.TransactionScope> natychmiast po nim w sekwencji, który jest treści zewnętrznego <xref:System.Activities.Statements.TransactionScope>. Transakcja nadal upłynie limit czasu, ale ponieważ dwa drugie limit wewnętrzny <xref:System.Activities.Statements.TransactionScope> nie ma zastosowania. Czasy transakcji out na 10 sekund po zewnętrznego <xref:System.Activities.Statements.TransactionScope> Przekroczono limit czasu.  
  
## <a name="aborting-on-transaction-failure"></a>Trwa przerywanie niepowodzeń transakcji  
 Ten przepływ pracy jest podobny do scenariusza trzy, z wyjątkiem limitów czasu zostały zastąpione przez <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> właściwości. Należy pamiętać, że flagi wszystkie wewnętrzne elementy podrzędne, jeśli ustawiona, muszą być zgodne zewnętrznego <xref:System.Activities.Statements.TransactionScope>. W tym scenariuszu nie i po otwarciu przepływu pracy jest zgłaszany wyjątek.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie BasicTransactionScopeSample.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Można również nacisnąć klawisze CTRL + F5 lub wybierz **uruchomić bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`