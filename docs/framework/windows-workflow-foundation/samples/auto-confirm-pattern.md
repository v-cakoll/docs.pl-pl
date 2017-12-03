---
title: "Potwierdź automatycznie wzorca"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaf4d72396438178d807f28ba8cb0ac5c5cb368e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="auto-confirm-pattern"></a>Potwierdź automatycznie wzorca
W tym przykładzie składa się z trzech scenariuszy systemem pokazujący niestandardowego `AutoConfirmScope` działania. Pierwszy pokazano pomyślne wykonanie sekwencji działań compensable cztery gdzie drugie i trzecie są zagnieżdżone w `AutoConfirmScope`. Druga próba zawiera takiej samej kolejności z powodu wyjątku występujących po wykonaniu czwarty <xref:System.Activities.Statements.CompensableActivity>. Trzeci scenariusz zawiera takiej samej kolejności z powodu wyjątku występujące w obrębie `AutoConfirmScope` po drugim <xref:System.Activities.Statements.CompensableActivity> zakończeniu.  
  
 W przykładzie pokazano wzorzec auto-confirm, gdy zostało potwierdzone wszystkie podrzędne działania compensable po pomyślnym ukończeniu zakresu. Ten wzorzec definiuje ważności wszystkich działań compensable podrzędnych, zgodnie z ich można już skompensować lub potwierdzić.  
  
 Zakres obejmuje <xref:System.Activities.Statements.TryCatch> gdzie <xref:System.Activities.Statements.TryCatch.Try%2A> wewnętrznej <xref:System.Activities.Statements.CompensableActivity>. Określony użytkownik treści `AutoConfirmScope` treść wewnętrzny <xref:System.Activities.Statements.CompensableActivity>. Po tym wewnętrzny <xref:System.Activities.Statements.CompensableActivity> zakończeniu generuje <xref:System.Activities.Statements.CompensationToken> jako argument wyjściowy. `AutoConfirmScope` Używa <xref:System.Activities.Statements.TryCatch.Finally%2A> do sprawdzenia, czy token został utworzony, a jeśli tak się stało, potwierdza to wewnętrzne <xref:System.Activities.Statements.CompensableActivity>. Wewnętrzny <xref:System.Activities.Statements.CompensableActivity> wywołuje domyślną kompensację żadnych compensable działań, które mogą wystąpić w jego treści.  
  
 Pierwszy scenariusz przedstawia pomyślnego wykonania przepływu pracy i prezentuje działanie działania compensable drugi i trzeci już są potwierdzone po zakończeniu przepływu pracy i pierwszy i czwarty. Daje to potwierdzenie kolejności trzech, dwa, cztery, a drugi.  
  
 Drugi scenariusz zawiera wyjątek, po zakończeniu działania compensable cztery. Ponieważ compensable działań 2 i 3 zostały już potwierdzone nie dotyczy to, ale jedno i czterema są wyrównane. Ta daje potwierdzić trzy, potwierdź dwa, cztery kompensacji i kompensacji jeden.  
  
 Końcowe scenariuszu pokazano, wykonanie nie powiodło się `AutoConfirmScope`. W tym scenariuszu, wystąpi wyjątek po zakończeniu drugiego <xref:System.Activities.Statements.CompensableActivity>. Ponieważ nie wykonano trzeci i czwarty compensable działań, są one nie dotyczy. Ponieważ zakres nie zakończyło się pomyślnie, drugi <xref:System.Activities.Statements.CompensableActivity> nie pobrać potwierdzone. Tworzy i kompensacji kolejność dwóch następnie jeden.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania AutoConfirmSample.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`