---
title: "Działanie CommentOut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: df5faa2aacf6b86d708dad4b157b27d2609a0a93
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="commentout-activity"></a>Działanie CommentOut
W tym przykładzie pokazano, jak zapisać działań niestandardowych, które usuwa innych działań ze ścieżki wykonywania skutecznie komentowania je.  
  
## <a name="the-commentout-activity"></a>Działanie CommentOut  
 Do osiągnięcia tego celu, działanie CommentOut pochodną <xref:System.Activities.CodeActivity> klasa podstawowa i implementuje pustą <xref:System.Activities.CodeActivity.Execute%2A> metody.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 Zadeklarowana jest klasa, jak pokazano w poniższym przykładzie.  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 `Designer` Atrybut określa klasę, która implementuje interfejs visual działania w czasie projektowania. `ContentProperty` Atrybutu deklaruje, że `"Body"` właściwości można pominięte w reprezentacji XAML wystąpienia tego działania.  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 W klasie projektanta XAML służy do tworzenia niestandardowych wizualną reprezentację działania. <xref:System.Activities.Presentation.WorkflowItemPresenter>jest klasa, która zawiera Edytor wizualny.  
  
 Pojedyncze działanie może być upuszczone na `CommentOut` powierzchni działania. Jeśli chcesz dodać wielu działań do tej warstwy, przeciągnij działanie sekwencji tutaj najpierw.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz CommentOut.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom próbkę bez debugowania, naciskając klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
