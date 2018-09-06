---
title: Pomijanie zakresu transakcji
ms.date: 03/30/2017
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
ms.openlocfilehash: 44814d66a4de4b3e72bb33eb46019eb1088ab040
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788042"
---
# <a name="suppress-transaction-scope"></a>Pomijanie zakresu transakcji
W przykładzie pokazano, jak utworzyć niestandardowy `SuppressTransactionScope` działanie, aby pominąć otoczenia transakcji czasu wykonywania, jeśli jest obecny.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Niestandardowe działanie jest przydatne zapobiec transakcji z przekazane go do innej usługi się, jeśli przepływu transakcji jest niepożądane dla konkretnego scenariusza. Środowisko wykonawcze przepływów pracy ma wbudowaną obsługę pomijanie otoczenia transakcji w <xref:System.Activities.NativeActivity> klasy, ale aby użyć tej obsługi, należy utworzyć niestandardowy <xref:System.Activities.NativeActivity> znajdującego się w tym przykładzie.  
  
 Scenariusz składa się z trzech części. Po pierwsze, <xref:System.Activities.Statements.TransactionScope> tworzy transakcji środowiska wykonawczego, która staje się otoczenia. To jest weryfikowana przez niestandardowe działanie, które Wyświetla identyfikatory lokalnych i rozproszonych transakcji. Transakcja jest następnie przekazane do usługi zdalnej przed rozpoczęciem drugiej części. W drugiej części przepływu pracy przechodzi `SuppressTransactionScope` i ponownie powtarza proces drukowania identyfikatorów transakcji i przepływu transakcji. Jednak działanie niestandardowe nie znajdzie otoczenia transakcji, a komunikat przekazane do usługi nie zawiera transakcji. Co w efekcie usługa tworzy transakcji, która oznacza, że identyfikator rozproszone są drukowane na klienta i usługi nie są zgodne. Ostatnia sekcja występuje po `SuppressTransactionScope` wyjść i ponownie wykonać transakcję środowiska wykonawczego staje się otoczenia, jako zweryfikowany przez kolejną wiadomość w usłudze przy użyciu rozproszonej identyfikator, który jest zgodny z identyfikatorem pierwszego komunikatu.  
  
 Pochodzi od klasy działania <xref:System.Activities.NativeActivity> ponieważ należy zaplanować działania podrzędnego i Dodaj właściwość wykonywania. `SuppressTransactionScope` Ma <xref:System.Activities.Variable> typu <xref:System.Activities.RuntimeTransactionHandle>, które muszą być zastosowane, a nie pola wystąpienia typu <xref:System.Activities.RuntimeTransactionHandle> ponieważ dojścia musi zostać zainicjowany. `Variable<RuntimeTransactionHandle>` Zostanie dodany do metadanych tego działania jako zmienną implementacji, ponieważ jest używany tylko wewnętrznie.  
  
 Gdy jest wykonywane działanie najpierw sprawdza, czy treść został określony, a jeśli tak jest, ustawia `SuppressTransaction` właściwość <xref:System.Activities.RuntimeTransactionHandle>. Po ustawieniu właściwości jest dodawany do właściwości wykonania i staje się otoczenia. Oznacza to, że wszystkie działania, które jest elementem podrzędnym `SuppressTransactionScope` jest w stanie wyświetlić właściwości i w związku z tym wymusza pomijanie czasu wykonywania transakcji i powoduje, że zagnieżdżone <xref:System.Activities.Statements.TransactionScope> do zgłoszenia wyjątku. Gdy uchwyt zostanie dodany do właściwości wykonania treści jest zaplanowane do uruchomienia.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie SuppressTransactionScope.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B, lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**. W oknie dialogowym wybierz **wiele projektów startowych** i upewnić się jest działanie w obu projektach **Start**.  
  
4.  Naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Alternatywnie, naciśnij klawisze CTRL + F5 lub wybierz **Rozpocznij bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
    > [!NOTE]
    >  Na serwerze muszą działać przed rozpoczęciem klienta. Dane wyjściowe z okna konsoli, który jest hostem usługi wskazuje, kiedy została uruchomiona.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`