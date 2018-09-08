---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 861e0cf160aec9814abcf8c27c37ce13a5d88b2a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217064"
---
# <a name="invokemethod"></a>InvokeMethod
W tym przykładzie pokazano różne sposoby korzystania z <xref:System.Activities.Statements.InvokeMethod> działania w celu wywołania metody klasy.  
  
 Metoda należy do klasy i reprezentuje ograniczonego zestawu operacji. <xref:System.Activities.Statements.InvokeMethod> Działania daje możliwość wywołania metod względem obiektów lub typy, przekazanie parametrów i uzyskać wartość zwracaną. Metody może być wywołana synchronicznie lub asynchronicznie.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie użyto <xref:System.Activities.Statements.InvokeMethod> działania do wykonania w następujących scenariuszach:  
  
1.  Wywołaj metodę wystąpienia bez parametrów.  
  
2.  Wywołaj metodę wystąpienia, z dwoma parametrami (<xref:System.String> i <xref:System.Int32>).  
  
3.  Wywołaj metodę wystąpienia, z dwoma parametrami (<xref:System.String> i <xref:System.Int32>) i tablicy parametrów typu <xref:System.String>[].  
  
4.  Wywołaj metodę wystąpienia, z dwoma parametrami typu <xref:System.Int32> i wynik o typie <xref:System.Int32>. W tym scenariuszu wartość wyniku jest powiązany ze zmienną i używane w innym działaniu. Jest wyświetlana w konsoli przy użyciu <xref:System.Activities.Statements.WriteLine> działania.  
  
5.  Wywołanie metody statycznej z dwoma parametrami typu <xref:System.String> i <xref:System.Int32>.  
  
6.  Wywoływanie metody wystąpienia mającej jeden parametr ogólny typu <xref:System.String>.  
  
7.  Wywołanie metody statycznej z dwoma parametrami ogólnego typu <xref:System.String> i <xref:System.Int32>.  
  
8.  Wywołaj metodę wystąpienia, która ma jeden parametr przekazywany przez odwołanie typu <xref:System.String>. W tym scenariuszu parametr odwołania jest powiązany ze zmienną (`outParam`) i używane w innym działaniu. Jest wyświetlana w konsoli przy użyciu <xref:System.Activities.Statements.WriteLine> działania.  
  
9. Wywołaj metodę asynchroniczną wystąpienia.  
  
10. Wywołania na dwa sposoby na tym samym wystąpieniu obiektu przy użyciu dwóch <xref:System.Activities.Statements.InvokeMethod> działań.  
  
11. Store wartość w wystąpieniu obiektu.  
  
12. Pobierz wartość z wystąpienia obiektu.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
 W tym przykładzie jest dostępna w dwóch wersjach. Pierwsza wersja ten przykład pokazuje użycie <xref:System.Activities.Statements.InvokeMethod> za pomocą języka C# kodu za pomocą modelu programowania Windows Workflow Foundation (WF) i można go znaleźć w folderze CodedWorkflow\CS. Druga wersja prezentuje sposób użycia <xref:System.Activities.Statements.InvokeMethod> przy użyciu XAML i można go znaleźć w folderze DesignerWorkflow\CS.  
  
#### <a name="to-run-the-coded-workflow-sample"></a>Aby uruchomić przykład kodowane przepływu pracy  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln w folderze CodedWorkflow\CS.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
#### <a name="to-run-the-designer-workflow-sample"></a>Aby uruchomić przykład projektanta przepływu pracy  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln w folderze DesignerWorkflow\CS.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`