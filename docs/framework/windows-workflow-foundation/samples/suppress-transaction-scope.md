---
title: "Pomiń zakresu transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6080eca62016cf48a0632f73ce5cd3ece4bc6972
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="suppress-transaction-scope"></a>Pomiń zakresu transakcji
Przykład pokazuje, jak utworzyć niestandardowy `SuppressTransactionScope` działanie, aby pominąć transakcja otoczenia czasu wykonywania, jeśli jest obecny.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 To niestandardowe działanie jest przydatne zapobiegające transakcji z przepływ go do innej usługi wychodzących, jeśli przepływu transakcji jest niepożądanych dla konkretnego scenariusza. Środowiska uruchomieniowego przepływu pracy ma wbudowaną obsługę pomijanie transakcja otoczenia w <xref:System.Activities.NativeActivity> klasy, ale aby użyć tej obsługi, należy utworzyć niestandardowy <xref:System.Activities.NativeActivity> znajdującego się w tym przykładzie.  
  
 Scenariusz składa się z trzech części. Najpierw <xref:System.Activities.Statements.TransactionScope> tworzy transakcji czasu wykonywania, które staje się otoczenia. To jest weryfikowany przez niestandardowe działanie, które Wyświetla identyfikatory lokalnych i rozproszonej transakcji. Transakcja jest następnie skierowana do zdalnej usługi przed rozpoczęciem drugiej części. Podczas drugiego etapu wprowadza przepływu pracy `SuppressTransactionScope` i ponownie powtarza proces drukowania identyfikatorów transakcji i przepływu transakcji. Jednak działań niestandardowych nie znajdzie transakcja otoczenia i komunikat skierowana do usługi nie zawiera transakcji. W związku z tym usługa tworzy transakcji, które oznacza, że identyfikator rozproszonej drukowane na klienta i usługi nie są zgodne. Ostatnia sekcja występuje po `SuppressTransactionScope` wyjść i transakcja czasu wykonywania ponownie staje się otoczenia jako zweryfikowany przez kolejną wiadomość do usługi z rozproszonego identyfikator, który jest zgodny z identyfikatorem pierwszego komunikatu.  
  
 Działanie sam jest pochodną <xref:System.Activities.NativeActivity> ponieważ należy zaplanować działania podrzędne i Dodaj właściwość wykonywania. `SuppressTransactionScope` Ma <xref:System.Activities.Variable> typu <xref:System.Activities.RuntimeTransactionHandle>, którego można użyć zamiast pole wystąpienia typu <xref:System.Activities.RuntimeTransactionHandle> ponieważ dojście musi zostać zainicjowany. `Variable<RuntimeTransactionHandle>` Zostanie dodany do działania metadanych jako zmienną implementacji, ponieważ jest używany tylko wewnętrznie.  
  
 Po wykonaniu działania najpierw sprawdza, czy określono treści i jeśli tak jest, ustawia `SuppressTransaction` właściwość <xref:System.Activities.RuntimeTransactionHandle>. Po ustawieniu właściwości jest dodawany do właściwości wykonania i staje się otoczenia. Oznacza to, że wszystkie działania, który jest elementem podrzędnym `SuppressTransactionScope` jest w stanie wyświetlić właściwości i w związku z tym wymusza pomijanie transakcja czasu wykonywania i powoduje, że zagnieżdżoną <xref:System.Activities.Statements.TransactionScope> do zgłoszenia wyjątku. Po dodaniu dojście do właściwości wykonania się, że treść jest zaplanowane do uruchomienia.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie SuppressTransactionScope.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**. W oknie dialogowym wybierz **wiele projektów startowych** i upewnij się, Akcja dla obu projektów jest **Start**.  
  
4.  Naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Alternatywnie, naciśnij klawisze CTRL + F5 lub wybierz **uruchomić bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
    > [!NOTE]
    >  Serwer musi być uruchomiona przed uruchomieniem klienta. Dane wyjściowe z okna konsoli, który obsługuje usługę wskazuje, kiedy został uruchomiony.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`