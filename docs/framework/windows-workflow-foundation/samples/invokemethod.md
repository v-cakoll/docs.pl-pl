---
title: InvokeMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a480fac4b9dc9313834b78f4bc688c445d7adc6
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="invokemethod"></a>InvokeMethod
W tym przykładzie przedstawiono różne sposoby używania <xref:System.Activities.Statements.InvokeMethod> działania w celu wywołania metody klasy.  
  
 Metoda należy do klasy i reprezentuje zawartych w niej zestaw operacji. <xref:System.Activities.Statements.InvokeMethod> Działania daje możliwość wywołania metody względem obiektów lub typy, przekazywanie parametrów i uzyskać wartość zwracaną. Metody można wywołać synchronicznie lub asynchronicznie.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W przykładzie użyto <xref:System.Activities.Statements.InvokeMethod> działanie do wykonania w następujących scenariuszach:  
  
1.  Wywołanie metody wystąpienia bez parametrów.  
  
2.  Wywołanie metody wystąpienia z dwoma parametrami (<xref:System.String> i <xref:System.Int32>).  
  
3.  Wywołanie metody wystąpienia z dwoma parametrami (<xref:System.String> i <xref:System.Int32>) i tablicy parametrów typu <xref:System.String>[].  
  
4.  Wywołanie metody wystąpienia z dwoma parametrami typu <xref:System.Int32> i wyniku typu <xref:System.Int32>. W tym scenariuszu wartość wyniku jest powiązany ze zmienną i używane w innym działaniu. Jest wyświetlana w konsoli przy użyciu <xref:System.Activities.Statements.WriteLine> działania.  
  
5.  Wywołanie metody statycznej z dwoma parametrami typu <xref:System.String> i <xref:System.Int32>.  
  
6.  Wywołanie metody wystąpienia z jednym parametrem ogólnego typu <xref:System.String>.  
  
7.  Wywołanie metody statycznej z dwa parametry ogólne typu <xref:System.String> i <xref:System.Int32>.  
  
8.  Wywołanie metody wystąpienia, który ma jeden parametr przekazywany przez odwołanie typu <xref:System.String>. W tym scenariuszu wiązania parametru odwołanie do zmiennej (`outParam`) i używane w innym działaniu. Pojawi się przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
9. Wywołanie metody asynchronicznej wystąpienia.  
  
10. Wywołanie dwie różne metody dla tego samego wystąpienia obiektu za pomocą dwóch <xref:System.Activities.Statements.InvokeMethod> działań.  
  
11. Zapisywanie wartości w wystąpieniu obiektu.  
  
12. Pobierz wartość z wystąpienia obiektu.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
 W tym przykładzie znajduje się w dwóch wersjach. Pierwszą wersję w tym przykładzie przedstawiono użycie <xref:System.Activities.Statements.InvokeMethod> za pomocą języka C# w kodzie za pomocą [!INCLUDE[wf](../../../../includes/wf-md.md)] model programowania i znajduje się w folderze CodedWorkflow\CS. Druga wersja przedstawiono użycie <xref:System.Activities.Statements.InvokeMethod> przy użyciu kodu XAML i znajduje się w folderze DesignerWorkflow\CS.  
  
#### <a name="to-run-the-coded-workflow-sample"></a>Aby uruchomić przykład kodowane przepływu pracy  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln w folderze CodedWorkflow\CS.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
#### <a name="to-run-the-designer-workflow-sample"></a>Aby uruchomić przykład projektanta przepływów pracy  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln w folderze DesignerWorkflow\CS.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`