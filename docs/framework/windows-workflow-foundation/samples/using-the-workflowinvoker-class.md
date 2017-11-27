---
title: "Za pomocą klasy WorkflowInvoker"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f5310b2adefa24d2d16733965395a34cc5cb69d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-workflowinvoker-class"></a>Za pomocą klasy WorkflowInvoker
W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.WorkflowInvoker> klasy można wywołać działania, tak jakby był on metodę.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Przy użyciu <xref:System.Activities.WorkflowInvoker> klasy jest najprostszym sposobem wykonania działania. Jest przeznaczony do bezpośredniego uruchamiania działania, jak w przypadku wywołania metody. Jest lekki, wysokiej wydajności, łatwy w użyciu interfejsu API w scenariuszach, w którym wykonania działania nie wymaga infrastrukturę kontroli innych zmian hostingu.  
  
 W przykładzie użyto niestandardowego działania, która jest pochodną <xref:System.Activities.CodeActivity%601>< Int32\> o nazwie `Add` dodaje dwa <xref:System.Activities.InArgument%601>, `X` i `Y`i zwraca `Result` <xref:System.Activities.OutArgument%601>. (<xref:System.Activities.CodeActivity%601>\<T > jest pochodną <xref:System.Activities.Activity%601>< T\>, który ma <xref:System.Activities.OutArgument%601> \<T > o nazwie `Result`.) A `Dictionary` \<string, object > służy do przekazania argumenty do wywoływanego przez działania <xref:System.Activities.WorkflowInvoker>. Klucz słownika odpowiada nazwa argumentu wywoływanego działania. Argument identyfikowane za pomocą klucza jest powiązana wartość skojarzoną z określonym kluczem.  
  
 Wywołania próbki <xref:System.Activities.WorkflowInvoker.Invoke%2A> i przekazuje słownik, który zawiera wartości `X` i `Y`. <xref:System.Activities.WorkflowInvoker> Klasy wiąże tych wartości `Add` działania przez argumenty, wykonuje działanie i zwraca wynik.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Invoker.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`  
  
## <a name="see-also"></a>Zobacz też
