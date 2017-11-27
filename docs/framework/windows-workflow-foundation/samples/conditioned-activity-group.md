---
title: "Przygotowane grupy działań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab8f47601f84267d1ac357b313fa5d2215a586d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="conditioned-activity-group"></a>Przygotowane grupy działań
W przykładzie pokazano aplikacji rezerwacji podróży. <xref:System.Workflow.Activities.ConditionedActivityGroup> (Innego niż CAG) udostępnia dwa działania kodu: działanie Car i działania linii lotniczych. W `SimpleCAGWorkflow` konstruktora, obiektu ArrayList "travelNeedType" jest wypełniana typów rezerwacje podróży, które są wymagane. Przez dodawanie komentarza do jednej lub obu `travelNeeds.Add` instrukcje, odpowiednio zmodyfikować zachowanie innego niż CAG. Działania samochodu i linii lotniczych mają ich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> warunku wypełniane przy użyciu <xref:System.Workflow.Activities.CodeCondition>. Wykonuje działanie samochodu tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Car` wpisu i lotniczego wykonuje działanie tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Airline` wpisu.  
  
 Wykonanie wszystkich czynności usuwa odpowiadający mu wpis z kolekcji. Wartość domyślna <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> warunek określa, czy innego niż CAG powinny być kończone, gdy bez żadnych elementów podrzędnych są wykonywane lub są gotowe do wykonania (na podstawie ich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> warunków). W tym przykładzie, oznacza to, innego niż CAG opuszcza, kiedy `travelNeeds` kolekcja jest pusta.  
  
### <a name="to-build-the-sample"></a>Aby samodzielnie tworzyć przykładowy  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
-   W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimpleCAG\bin\debug (lub folderu SimpleCAG\bin dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
