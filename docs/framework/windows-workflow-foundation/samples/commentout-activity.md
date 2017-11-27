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
# <a name="commentout-activity"></a><span data-ttu-id="698f9-102">Działanie CommentOut</span><span class="sxs-lookup"><span data-stu-id="698f9-102">CommentOut Activity</span></span>
<span data-ttu-id="698f9-103">W tym przykładzie pokazano, jak zapisać działań niestandardowych, które usuwa innych działań ze ścieżki wykonywania skutecznie komentowania je.</span><span class="sxs-lookup"><span data-stu-id="698f9-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="698f9-104">Działanie CommentOut</span><span class="sxs-lookup"><span data-stu-id="698f9-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="698f9-105">Do osiągnięcia tego celu, działanie CommentOut pochodną <xref:System.Activities.CodeActivity> klasa podstawowa i implementuje pustą <xref:System.Activities.CodeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="698f9-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="698f9-106">Zadeklarowana jest klasa, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="698f9-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="698f9-107">`Designer` Atrybut określa klasę, która implementuje interfejs visual działania w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="698f9-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="698f9-108">`ContentProperty` Atrybutu deklaruje, że `"Body"` właściwości można pominięte w reprezentacji XAML wystąpienia tego działania.</span><span class="sxs-lookup"><span data-stu-id="698f9-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="698f9-109">W klasie projektanta XAML służy do tworzenia niestandardowych wizualną reprezentację działania.</span><span class="sxs-lookup"><span data-stu-id="698f9-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="698f9-110"><xref:System.Activities.Presentation.WorkflowItemPresenter>jest klasa, która zawiera Edytor wizualny.</span><span class="sxs-lookup"><span data-stu-id="698f9-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="698f9-111">Pojedyncze działanie może być upuszczone na `CommentOut` powierzchni działania.</span><span class="sxs-lookup"><span data-stu-id="698f9-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="698f9-112">Jeśli chcesz dodać wielu działań do tej warstwy, przeciągnij działanie sekwencji tutaj najpierw.</span><span class="sxs-lookup"><span data-stu-id="698f9-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="698f9-113">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="698f9-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="698f9-114">Otwórz CommentOut.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="698f9-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="698f9-115">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="698f9-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="698f9-116">Uruchom próbkę bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="698f9-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="698f9-117">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="698f9-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="698f9-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="698f9-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="698f9-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="698f9-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="698f9-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="698f9-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
