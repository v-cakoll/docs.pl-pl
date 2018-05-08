---
title: Potwierdzenie
ms.date: 03/30/2017
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
ms.openlocfilehash: 334ac362333565626dd2bb8dcaede27fbab16f33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="confirmation"></a>Potwierdzenie
W tym przykładzie przedstawiono cztery typowe scenariusze otaczającego stosowania <xref:System.Activities.Statements.CompensableActivity> i potwierdzenia. Przykład uruchamia cztery przepływy pracy do wyświetlenia potwierdzenia. Ten przykład jest dostępny w wersjach deklaratywne i bezwzględne.  
  
## <a name="confirm-a-compensable-activity"></a>Potwierdź Compensable działania  
 Pierwszy przepływ pracy przedstawia sposób compensable działanie confirm i składa się z dwóch sekwencji <xref:System.Activities.Statements.CompensableActivity> wystąpień. Po zakończeniu drugiego <xref:System.Activities.Statements.CompensableActivity> działanie confirm potwierdza pierwsze działanie. Po zakończeniu przepływu pracy pomyślnie, wszystkie <xref:System.Activities.Statements.CompensableActivity> wystąpień, które nie zostały potwierdzone lub skompensowane automatycznie zostało potwierdzone przy użyciu domyślnej kolejności. Bez Potwierdzanie drugi <xref:System.Activities.Statements.CompensableActivity> czy zostały potwierdzone najpierw.  
  
## <a name="explicit-compensation"></a>Jawne kompensacji  
 Drugi scenariusz prezentuje wpływ na potwierdzenie domyślne podczas <xref:System.Activities.Statements.CompensableActivity> jest jawnie skompensowane. Przepływ pracy składa się z dwóch sekwencji <xref:System.Activities.Statements.CompensableActivity> działania, po drugim zakończeniu pierwszy jest jawnie skompensowane. W związku z tym podczas tylko drugim zakończeniu przepływu pracy, <xref:System.Activities.Statements.CompensableActivity> został potwierdzony.  
  
## <a name="controlling-the-order-of-confirmation-for-nested-compensableactivity-activities"></a>Kontrolowanie kolejności potwierdzenia działania CompensableActivity zagnieżdżonych działań  
 Trzeci scenariusz pokazano, jak można sterować kolejnością potwierdzenia dla zagnieżdżone <xref:System.Activities.Statements.CompensableActivity>. Scenariusz składa się z <xref:System.Activities.Statements.CompensableActivity> jako katalogu głównego przepływu pracy. Treść głównego <xref:System.Activities.Statements.CompensableActivity> sekwencja trzech <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> Dla głównego <xref:System.Activities.Statements.CompensableActivity> jest sekwencją, która określa, aby potwierdzić pierwszy, a następnie zagnieżdżone drugi <xref:System.Activities.Statements.CompensableActivity>. Po zakończeniu przepływu pracy potwierdza głównego <xref:System.Activities.Statements.CompensableActivity>, który następnie potwierdza pierwszy, drugi i trzeci zagnieżdżone <xref:System.Activities.Statements.CompensableActivity>, w tym kolejność. W związku z tym domyślna kolejność potwierdzenia zasadniczo została odwrócona. Ponieważ trzeci <xref:System.Activities.Statements.CompensableActivity> nie potwierdzono jawnie jako część głównego <xref:System.Activities.Statements.CompensableActivity> przez <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>, został potwierdzony zgodnie z domyślną kolejność. Jednakże ponieważ jest to jedyny niepotwierdzone <xref:System.Activities.Statements.CompensableActivity> oznacza to, potwierdzono.  
  
## <a name="scoping-of-variables"></a>Zakresy zmiennych  
 Czwarty scenariuszu pokazano, jak okres istnienia zmienne definiowane dla <xref:System.Activities.Statements.CompensableActivity> lub jeden z jego elementów nadrzędnych są nadal w przypadku zakres <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> lub <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> obsługi są wykonane nawet wtedy, gdy działanie zostało zakończone lub przepływu pracy zostało ukończone. Przepływ pracy składa się z dwóch sekwencji <xref:System.Activities.Statements.CompensableActivity>. W treści pierwszy zmiennej `mySum` ustawiono sumę 5 i 10 i wydrukować wynik. W treści drugiego <xref:System.Activities.Statements.CompensableActivity>, suma jest równa Suma istniejących sum i 7 i wydrukować wynik. Niestandardowe kompensacji jest zdefiniowana w pierwszym <xref:System.Activities.Statements.CompensableActivity>, który wyświetla sumę, odejmuje 7 i wyświetla sumę ponownie. Jest jasne, sprawdzając drukowanymi sum, które zmienna znajduje się w zakresie nie tylko dla treści obu <xref:System.Activities.Statements.CompensableActivity> , ale <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> również.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Załadowanie rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Uruchom aplikację ConfirmationSample.exe.  
  
3.  Sprawdź następujące dane wyjściowe:  
  
 **Jawne potwierdzenie: Rozpocznij workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: HandlerEnd potwierdzenia z workflowCompensableActivity2: kompensacji HandlerExplicit potwierdzenie: początek workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: HandlerEnd kompensacji z workflowCompensableActivity2: HandlerCustom potwierdzenie potwierdzenie obsługi: Rozpocznij workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity3: BodyEnd workflowCompensableActivity1: HandlerCompensableActivity2 potwierdzenie: HandlerCompensableActivity3 potwierdzenie: HandlerVariable potwierdzenie dostępu programu obsługi potwierdzenia: Początek workflowCompensableActivity1: BodyCompensableActivity1: Suma: 15CompensableActivity2: BodyCompensableActivity2: dodanie 7 do sumCompensableActivity2: suma jest teraz: 22End workflowCompensableActivity2: potwierdzenia HandlerCompensableActivity1: Potwierdzenie HandlerCompensableActivity2: Suma: 22CompensableActivity2: po odjęciu 12 suma jest teraz: 10Press ENTER, aby wyjść.**  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`