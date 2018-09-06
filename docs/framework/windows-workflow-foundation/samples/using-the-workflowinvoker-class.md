---
title: Używanie klasy WorkflowInvoker
ms.date: 03/30/2017
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
ms.openlocfilehash: d6525dbbd30aae95be4c4ee1de267736e557a541
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748714"
---
# <a name="using-the-workflowinvoker-class"></a>Używanie klasy WorkflowInvoker
W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.WorkflowInvoker> klasy, aby wywołać działanie tak, jakby był metodą.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Za pomocą <xref:System.Activities.WorkflowInvoker> klasa jest najprostszym sposobem wykonania działania. Jest ona przeznaczona do bezpośredniego uruchamiania działania, jak w przypadku wywołania metody. Jest uproszczone, o wysokiej wydajności, łatwy w użyciu interfejsu API do użytku w scenariuszach, gdzie wykonania działania nie wymaga infrastruktury kontroli zapewnianej przez inne odmiany hostingu.  
  
 W przykładzie użyto niestandardowego działania, która pochodzi od klasy <xref:System.Activities.CodeActivity%601>< Int32\> o nazwie `Add` który dodaje dwa <xref:System.Activities.InArgument%601>, `X` i `Y`i zwraca `Result` <xref:System.Activities.OutArgument%601>. (<xref:System.Activities.CodeActivity%601>\<T > pochodzi od klasy <xref:System.Activities.Activity%601>< T\>, który ma <xref:System.Activities.OutArgument%601> \<T > o nazwie `Result`.) A `Dictionary` \<string, object > służy do przekazywania argumentów do działania są wywoływane za pośrednictwem <xref:System.Activities.WorkflowInvoker>. Klucz ze słownika odnosi się do nazwy argumentów dla wywołanej działanie. Wartość skojarzoną z określonym kluczem jest powiązany z argumentem identyfikowany przez klucz.  
  
 Przykład wywołania <xref:System.Activities.WorkflowInvoker.Invoke%2A> i przekazuje słownik, który zawiera wartości `X` i `Y`. <xref:System.Activities.WorkflowInvoker> Klasy wiąże tych wartości, aby `Add` działania argumentów, wykonuje działanie i zwraca wynik.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Invoker.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`