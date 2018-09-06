---
title: Wzorzec automatycznego potwierdzania
ms.date: 03/30/2017
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
ms.openlocfilehash: a032c05743b64fe58b0b187328b5216080ba6e19
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864058"
---
# <a name="auto-confirm-pattern"></a>Wzorzec automatycznego potwierdzania
W tym przykładzie składa się z trzech scenariuszy systemem pokazujący niestandardowego `AutoConfirmScope` działania. Pierwszy przykład pokazuje pomyślne wykonanie sekwencji cztery kompensacyjne działań, w których drugie i trzecie są zagnieżdżone w `AutoConfirmScope`. Drugi przykład pokazuje tę samą sekwencję z powodu wyjątku, które pojawiają się po wykonaniu czwarty <xref:System.Activities.Statements.CompensableActivity>. Trzeci scenariusz pokazuje takiej samej kolejności, z wyjątkiem pojawiają się w `AutoConfirmScope` po drugim <xref:System.Activities.Statements.CompensableActivity> kończy.  
  
 W przykładzie pokazano wzorzec auto-confirm, gdzie wszystkie działania kompensacyjne podrzędne są potwierdzone po pomyślnym zakończeniu zakresu. Ten wzorzec definiuje okres istnienia wszystkich działań kompensacyjne podrzędnych, ponieważ one mogą nie będzie można skompensować lub potwierdzić.  
  
 Zakres, który składa się z <xref:System.Activities.Statements.TryCatch> gdzie <xref:System.Activities.Statements.TryCatch.Try%2A> wewnętrznej <xref:System.Activities.Statements.CompensableActivity>. Określone przez użytkownika treści `AutoConfirmScope` treść wewnętrzny <xref:System.Activities.Statements.CompensableActivity>. Po tym wewnętrznego <xref:System.Activities.Statements.CompensableActivity> zakończeniu generuje <xref:System.Activities.Statements.CompensationToken> jako argumentem Wy. `AutoConfirmScope` Używa <xref:System.Activities.Statements.TryCatch.Finally%2A> do sprawdzenia, czy token został utworzony i czy ma on, a następnie potwierdza wewnętrzny <xref:System.Activities.Statements.CompensableActivity>. Wewnętrzny <xref:System.Activities.Statements.CompensableActivity> wywołuje wynagrodzenie domyślne kompensacyjne działań, które mogą wystąpić w jej treści.  
  
 Pierwszy scenariusz pokazuje pomyślne wykonanie przepływu pracy i pokazuje, że działania kompensacyjne drugi i trzeci już potwierdzone po ukończeniu przepływu pracy i potwierdzone pierwszy i czwarty. Daje to potwierdzenie kolejność trzy, dwa, cztery lub jeden.  
  
 Drugi scenariusz przedstawia wyjątek, po zakończeniu działania kompensacyjne cztery. Ponieważ już potwierdzone kompensacyjne działań, 2 i 3 są bez zmian, ale wynagradzani za 1 i 4. To tworzy upewnij się, trzy, upewnij się, dwa, cztery kompensacji i kompensacji jeden.  
  
 Końcowe scenariusz pokazuje powiodło się wykonywanie `AutoConfirmScope`. W tym scenariuszu, wystąpi wyjątek, po ukończeniu drugiego <xref:System.Activities.Statements.CompensableActivity>. Ponieważ nie wykonano działania trzecia i czwarta kompensacyjne, są one nie ma wpływu. Ponieważ zakres zakończyła się niepowodzeniem, drugi <xref:System.Activities.Statements.CompensableActivity> nie uzyskać potwierdzone. Tworzy i kolejności wynagrodzenie dwa z nich następnie.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania AutoConfirmSample.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`