---
title: Podstawowy element TransactionScope
ms.date: 03/30/2017
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
ms.openlocfilehash: b3c673040d40ca91d8ab4a79e847d61e6f507ed1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415426"
---
# <a name="basic-transactionscope"></a>Podstawowy element TransactionScope
Ten przykład obejmuje cztery scenariusze uruchamianą przedstawiająca sposób zagnieździć <xref:System.Activities.Statements.TransactionScope> wystąpień. Pierwszy scenariusz pokazuje zagnieżdżania 3 działania innych firm, które autor nie zna konstrukcji. Scenariusze drugi i trzeci pokazują, jak są przestrzegane limity czasu i końcowe scenariusz pokazuje <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> ustawienie.  
  
## <a name="nesting-of-transactionscopeactivity"></a>Zagnieżdżanie działania TransactionScopeActivity  
 Przepływ pracy dla pierwszego scenariusza, który składa się z dwóch sekwencji <xref:System.Activities.Statements.WriteLine> działań i <xref:System.Activities.Statements.TransactionScope>. Treść <xref:System.Activities.Statements.TransactionScope> jest sekwencją dwóch <xref:System.Activities.Statements.WriteLine> działalności, niestandardowe działanie, które wyświetla identyfikator lokalny transakcji i trzecią innych firm działania. Działanie innych firm `TransactionScopeTest` zawiera <xref:System.Activities.Statements.TransactionScope> mimo, że autor przepływu pracy nie ma możliwości określenia. W tym scenariuszu pokazano, że <xref:System.Activities.Statements.TransactionScope> działań, które mogą być zagnieżdżone.  
  
## <a name="time-outs"></a>Limity czasu  
 Przepływ pracy w drugim scenariuszu jest niemal identyczny z pierwszym. `TransactionScopeTest` Został zastąpiony <xref:System.Activities.Statements.TransactionScope>. Treść <xref:System.Activities.Statements.TransactionScope> jest pięć sekund opóźnienia i limit czasu dla transakcji jest ustawiony na dwóch sekund. Limit czasu dla zewnętrzny <xref:System.Activities.Statements.TransactionScope> jest ustawiony na 10 sekund. Pamiętaj, że najmniejszy limitu czasu w zakresie jest zachowana upłynie limit czasu transakcji.  
  
 Przepływ pracy trzeci scenariusz jest niemal identyczny jak w przypadku scenariusza, dwa. Działanie opóźnienie została przeniesiona z treści wewnętrzny <xref:System.Activities.Statements.TransactionScope> natychmiast po nim w sekwencji, który jest treść zewnętrzny <xref:System.Activities.Statements.TransactionScope>. Transakcji nadal upłynie limit czasu, ale ponieważ dwie sekundy limitu wewnętrzny <xref:System.Activities.Statements.TransactionScope> nie ma już zastosowania. Godziny transakcji out na 10 sekund po zewnętrzny <xref:System.Activities.Statements.TransactionScope> zostanie przekroczony limit czasu.  
  
## <a name="aborting-on-transaction-failure"></a>Trwa przerywanie błędu transakcji  
 Ten przepływ pracy jest podobny do scenariusza trzy, z wyjątkiem limity czasu zostały zastąpione przez <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> właściwości. Należy pamiętać, że flagi wszystkie wewnętrzne obiekty podrzędne, jeśli ustawiona, muszą być zgodne zewnętrzny <xref:System.Activities.Statements.TransactionScope>. W tym scenariuszu nie, a wyjątek jest zgłaszany, gdy przepływ pracy zostanie otwarty.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie BasicTransactionScopeSample.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B, lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Można również nacisnąć klawisze CTRL + F5 lub wybierz **Rozpocznij bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`