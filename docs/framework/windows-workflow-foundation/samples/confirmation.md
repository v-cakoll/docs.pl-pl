---
title: Potwierdzenie
ms.date: 03/30/2017
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
ms.openlocfilehash: caa712aa52da01ce44335a361fd6c9f5215316bf
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368115"
---
# <a name="confirmation"></a>Potwierdzenie
W tym przykładzie przedstawiono cztery typowe scenariusze użytkowania otaczającego <xref:System.Activities.Statements.CompensableActivity> i potwierdzenie hasła. Przykład jest uruchamiany cztery przepływy pracy, aby pokazać potwierdzenia. Ten przykład jest dostępny w wersjach deklaratywnego i imperatywnego.  
  
## <a name="confirm-a-compensable-activity"></a>Potwierdź działanie kompensacyjne  
 Pierwszy przepływ pracy przedstawia sposób potwierdzić działanie kompensacyjne i składa się z dwóch sekwencji <xref:System.Activities.Statements.CompensableActivity> wystąpień. Po ukończeniu drugiego <xref:System.Activities.Statements.CompensableActivity> działania Potwierdź potwierdza pierwsze działanie. Po zakończeniu przepływu pracy pomyślnie wszystkich <xref:System.Activities.Statements.CompensableActivity> wystąpień, które nie zostały potwierdzone lub płatne automatycznie zostało potwierdzone przy użyciu domyślnej kolejności. Bez potwierdzania drugi <xref:System.Activities.Statements.CompensableActivity> czy zostały potwierdzone najpierw.  
  
## <a name="explicit-compensation"></a>Jawne Kompensacja  
 Drugi scenariusz prezentuje wpływ na potwierdzenie domyślne podczas <xref:System.Activities.Statements.CompensableActivity> jawnie wynagradzani za. Przepływ pracy składa się z dwóch sekwencji <xref:System.Activities.Statements.CompensableActivity> wyrównywane jest jawnie działania, po drugim zakończeniu pierwszej. W rezultacie podczas przepływu pracy, kończy tylko drugi <xref:System.Activities.Statements.CompensableActivity> został potwierdzony.  
  
## <a name="controlling-the-order-of-confirmation-for-nested-compensableactivity-activities"></a>Kontrolowanie kolejność potwierdzenia CompensableActivity zagnieżdżonych działań  
 Trzeci scenariusz pokazuje, jak kontrolować kolejność potwierdzenia dla zagnieżdżonych <xref:System.Activities.Statements.CompensableActivity>. Scenariusz składa się z <xref:System.Activities.Statements.CompensableActivity> jako katalogu głównego przepływu pracy. Treść głównego <xref:System.Activities.Statements.CompensableActivity> jest sekwencją trzy <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> Dla głównego <xref:System.Activities.Statements.CompensableActivity> jest sekwencji, która określa, aby potwierdzić pierwszego, drugiego zagnieżdżone, a następnie <xref:System.Activities.Statements.CompensableActivity>. Po zakończeniu przepływu pracy potwierdza to główny <xref:System.Activities.Statements.CompensableActivity>, który następnie potwierdza pierwszy, drugi i trzeci zagnieżdżone <xref:System.Activities.Statements.CompensableActivity>, w tym kolejność. W rezultacie domyślną kolejność potwierdzenia zasadniczo została odwrócona. Ponieważ trzeci <xref:System.Activities.Statements.CompensableActivity> nie potwierdzono jawnie jako część głównego <xref:System.Activities.Statements.CompensableActivity> przez <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>, potwierdzono zgodnie z kolejnością domyślną. Jednakże ponieważ jest to jedyny niepotwierdzone <xref:System.Activities.Statements.CompensableActivity> oznacza to, potwierdzono.  
  
## <a name="scoping-of-variables"></a>Wyznaczanie zakresu zmiennych  
 Czwarty scenariusz pokazuje, jak okres istnienia zmiennych są definiowane dla <xref:System.Activities.Statements.CompensableActivity> lub jeden z jego elementów nadrzędnych są nadal w przypadku zakresu <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> lub <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> obsługi są wykonywane nawet sytuacji, gdy działanie zostało zakończone lub przepływu pracy ukończone. Przepływ pracy składa się z dwóch sekwencji <xref:System.Activities.Statements.CompensableActivity>. W treści pierwszego, zmienna `mySum` jest ustawiony do sumy 5, 10 i wynik wydrukowany. W treści drugi <xref:System.Activities.Statements.CompensableActivity>, suma jest równa sumę sum istniejących i 7 i wydrukowane wynik. Program obsługi potwierdzenia niestandardowego jest zdefiniowana w pierwszym <xref:System.Activities.Statements.CompensableActivity>, która drukuje sumy, odejmuje 7 obszary, a suma ponownie. To oczywiste, sprawdzając drukowane sumy, które zmiennej znajduje się w zakresie nie tylko w przypadku grup zarówno <xref:System.Activities.Statements.CompensableActivity> ale <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> także.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Ładowanie rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Uruchom aplikację ConfirmationSample.exe.  
  
3.  Sprawdź następujące dane wyjściowe:  
  
 **Jawne potwierdzenie: początek workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: HandlerEnd potwierdzenia z workflowCompensableActivity2: wynagrodzenie HandlerExplicit potwierdzenie: początek workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: HandlerEnd odszkodowania z workflowCompensableActivity2: Potwierdzenie HandlerCustom potwierdzenie procedury obsługi: Start workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity3: BodyEnd workflowCompensableActivity1: HandlerCompensableActivity2 potwierdzenie: HandlerCompensableActivity3 potwierdzenie: HandlerVariable potwierdzenie dostępu programu obsługi potwierdzenia: Początek workflowCompensableActivity1: BodyCompensableActivity1: Suma: 15CompensableActivity2: BodyCompensableActivity2: dodanie 7, aby sumCompensableActivity2: suma jest teraz: 22End workflowCompensableActivity2: potwierdzenia HandlerCompensableActivity1: Potwierdzenie HandlerCompensableActivity2: Suma: 22CompensableActivity2: po odjęciu 12 suma jest teraz: 10Press ENTER, aby zakończyć.**  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`