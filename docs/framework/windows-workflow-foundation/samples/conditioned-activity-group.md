---
title: Grupa działań objętych warunkami
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 144a6c76ea6314c553e201fe4e2364890d869f34
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861208"
---
# <a name="conditioned-activity-group"></a>Grupa działań objętych warunkami
W przykładzie pokazano aplikacji rezerwacji podróży. <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) ma dwa działania kodu: działanie Car i działania linii lotniczych. W `SimpleCAGWorkflow` konstruktora obiektu ArrayList "travelNeedType" jest wypełniana przy użyciu typów rezerwacje podróży, które są wymagane. Zakomentowując jedną lub obie `travelNeeds.Add` instrukcji odpowiednio zmodyfikować zachowanie CAG. Działania samochodu i linie lotnicze mają swoje <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> wypełniony warunek <xref:System.Workflow.Activities.CodeCondition>. Działanie samochód jest wykonywane tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Car` wejścia i linii lotniczych, działanie jest wykonywane tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Airline` wpisu.  
  
 Wykonanie każdego działania usuwa odpowiadający mu wpis z kolekcji. Wartość domyślna <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> warunek określa, że CAG powinno powodować wyjście, gdy żadne elementy podrzędne są wykonywane lub gotowe do wykonania (na podstawie ich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> warunki). W tym przykładzie, oznacza to, że CAG kończy działanie po `travelNeeds` kolekcja jest pusta.  
  
### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązanie bez debugowania, naciskając klawisze CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
-   W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimpleCAG\bin\debug (lub folder SimpleCAG\bin wersję przykładu w Visual Basic), który znajduje się poniżej głównego folderu dla przykładu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
