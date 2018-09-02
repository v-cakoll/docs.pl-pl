---
title: Działanie CommentOut
ms.date: 03/30/2017
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
ms.openlocfilehash: 3e9f6945755bd60c551674ea8a3471a9f612da52
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404753"
---
# <a name="commentout-activity"></a>Działanie CommentOut
Niniejszy przykład pokazuje sposób pisania działania niestandardowego, który usuwa innych działań ze ścieżki wykonywania i efektywne Dodawanie komentarza do ich.  
  
## <a name="the-commentout-activity"></a>Działanie CommentOut  
 Do osiągnięcia tego celu, działanie CommentOut pochodzi od klasy <xref:System.Activities.CodeActivity> klasy bazowej i implementuje pustą <xref:System.Activities.CodeActivity.Execute%2A> metody.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 Klasa jest zadeklarowana, jak pokazano w poniższym przykładzie.  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 `Designer` Atrybut określa klasę, która implementuje interfejs graficzny działania w czasie projektowania. `ContentProperty` Atrybut oświadcza, że `"Body"` właściwości mogą pominięte w reprezentacji XAML wystąpienia tego działania.  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 W klasie projektanta XAML jest używany do tworzenia niestandardowych wizualnej reprezentacji działania. <xref:System.Activities.Presentation.WorkflowItemPresenter> jest klasą, która zawiera Edytor wizualny.  
  
 Pojedyncze działanie może być upuszczone na `CommentOut` powierzchni działania. Jeśli chcesz dodać wiele działań na tę powierzchnię, przeciągnij działania sequence tutaj najpierw.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz CommentOut.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom przykład bez debugowania, naciskając klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
