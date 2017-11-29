---
title: "Obsługa w działaniu Flowchart przy użyciu TryCatch błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 490647f8ea3662f046cadecf5a97761c43b357f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Obsługa w działaniu Flowchart przy użyciu TryCatch błędów
W tym przykładzie pokazano sposób <xref:System.Activities.Statements.TryCatch> działanie może być używane w ramach działania przepływu sterowania złożonego.  
  
 W tym przykładzie kodu podwyższenia poziomu i liczbę elementów podrzędnych są przekazywane jako zmienne <xref:System.Activities.Statements.Flowchart> działanie, które oblicza rabat oparte na pochodnych, które odnoszą się do kodu podwyższenia poziomu. Przykład obejmuje konieczne wersje projektanta kodu i przepływ pracy próbki.  
  
 W poniższej tabeli przedstawiono zmienne `CreateFlowchartWithFaults` działania.  
  
|Parametry|Opis|  
|----------------|-----------------|  
|promoCode|Kod promocji. Typ: ciąg<br /><br /> Możliwe wartości z opisem w nawiasach:<br /><br /> -Pojedynczy (jeden)<br />-MNK (zamężna z nie dzieci).<br />-MWK (zamężna dla dzieci).|  
|numKids|Liczba elementów podrzędnych. Typ: int|  
  
 `CreateFlowchartWithFaults` Używa działania <xref:System.Activities.Statements.FlowSwitch%601> działanie, które zmienia się na `promoCode` argumentu i obliczanie rabatu przy użyciu następującej formuły.  
  
|Wartość`promoCode`|Rabat (%)|  
|--------------------------|--------------------|  
|Single|10|  
|MNK|15|  
|MWK|15 + (1 – 1 /`numberOfKids`)\*10 **Uwaga:** potencjalnie może zgłosić tego obliczenia <xref:System.DivideByZeroException>. Tak, otoczona obliczeń rabatu <xref:System.Activities.Statements.TryCatch> działania, który przechwytuje <xref:System.DivideByZeroException> wyjątku i ustawia rabat na zero.|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania FlowchartWithFaultHandling.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat blokowy przepływów pracy](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [Wyjątki](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
