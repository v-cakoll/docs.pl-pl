---
title: "Za pomocą działania InvokeMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0c2333c14eaebdb6409323bb6b92aa2b29d2ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokemethod-activity"></a>Za pomocą działania InvokeMethod
W tym przykładzie przedstawiono sposób użycia <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) działania w celu wywołania metody publiczne klas publicznych. <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) Działanie zezwala przepływu pracy do wywołania metody obiektów, przekazywanie parametrów przechowywana wartość zwracana, określić typy metod ogólnych i określ, czy metoda jest synchroniczne lub asynchroniczne. 
  
Dostępna jest wersja nieogólnego <xref:System.Activities.Statements.InvokeMethod> działania, których wartość zwracana jest wartość <xref:System.Activities.Statements.InvokeMethod.Result%2A> właściwości i rodzajowy wersja <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) działania, w której jest zwracana wartość zwracana za pomocą <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) właściwości typu `TResult`. 
  
 W tym przykładzie pokazano, jak wywołać metodę różnego. Poniższe szczegóły listy typów metody zostało to pokazane w tym przykładzie:  
  
-   Wywołanie metody wystąpienia bez parametrów.  
  
-   Wywołanie metody wystąpienia z dwoma parametrami (System.String i System.Int32).  
  
-   Wywołanie metody wystąpienia z dwóch parametrów (System.String i System.Int32) i tablicy parametrów typu System.String [].  
  
-   Wywołanie metody wystąpienia z dwoma parametrami (dwie liczb System.Int32) i wyniku typu System.Int32.  
  
     Wartość zwracana jest powiązany ze zmienną i wydrukować przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
-   Wywołanie metody statycznej z dwoma parametrami (System.String i System.Int32).  
  
-   Wywołanie metody wystąpienia z jednego parametru ogólnego (System.String).  
  
-   Wywołanie metody statycznej z dwa parametry ogólne (System.String i System.Int32).  
  
-   Wywołanie metody wystąpienia, który ma jeden parametr przekazywany przez odwołanie (System.String).  
  
     Parametr przywoływanego jest powiązany ze zmienną i wydrukować przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
-   Wywołanie metody asynchronicznej wystąpienia.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln.  
  
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