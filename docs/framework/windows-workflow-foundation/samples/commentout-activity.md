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
# <a name="commentout-activity"></a><span data-ttu-id="a4101-102">Działanie CommentOut</span><span class="sxs-lookup"><span data-stu-id="a4101-102">CommentOut Activity</span></span>
<span data-ttu-id="a4101-103">Niniejszy przykład pokazuje sposób pisania działania niestandardowego, który usuwa innych działań ze ścieżki wykonywania i efektywne Dodawanie komentarza do ich.</span><span class="sxs-lookup"><span data-stu-id="a4101-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="a4101-104">Działanie CommentOut</span><span class="sxs-lookup"><span data-stu-id="a4101-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="a4101-105">Do osiągnięcia tego celu, działanie CommentOut pochodzi od klasy <xref:System.Activities.CodeActivity> klasy bazowej i implementuje pustą <xref:System.Activities.CodeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a4101-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="a4101-106">Klasa jest zadeklarowana, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a4101-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="a4101-107">`Designer` Atrybut określa klasę, która implementuje interfejs graficzny działania w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="a4101-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="a4101-108">`ContentProperty` Atrybut oświadcza, że `"Body"` właściwości mogą pominięte w reprezentacji XAML wystąpienia tego działania.</span><span class="sxs-lookup"><span data-stu-id="a4101-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="a4101-109">W klasie projektanta XAML jest używany do tworzenia niestandardowych wizualnej reprezentacji działania.</span><span class="sxs-lookup"><span data-stu-id="a4101-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="a4101-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> jest klasą, która zawiera Edytor wizualny.</span><span class="sxs-lookup"><span data-stu-id="a4101-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="a4101-111">Pojedyncze działanie może być upuszczone na `CommentOut` powierzchni działania.</span><span class="sxs-lookup"><span data-stu-id="a4101-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="a4101-112">Jeśli chcesz dodać wiele działań na tę powierzchnię, przeciągnij działania sequence tutaj najpierw.</span><span class="sxs-lookup"><span data-stu-id="a4101-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a4101-113">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="a4101-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="a4101-114">Otwórz CommentOut.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4101-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a4101-115">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a4101-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a4101-116">Uruchom przykład bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="a4101-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a4101-117">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a4101-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a4101-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a4101-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a4101-119">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="a4101-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a4101-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a4101-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
