---
title: Nieogólne działanie ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 93a6b1d815ef6478974ceadf8ad935be2a3bdea5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338659"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="e85e4-102">Nieogólne działanie ForEach</span><span class="sxs-lookup"><span data-stu-id="e85e4-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="e85e4-103">dostarcza w swoim przyborniku zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ForEach%601>, które umożliwiają iterację przez kolekcje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="e85e4-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="e85e4-104"><xref:System.Activities.Statements.ForEach%601> wymaga, aby Właściwość <xref:System.Activities.Statements.ForEach%601.Values%2A> była typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="e85e4-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e85e4-105">Uniemożliwia to użytkownikom iterację struktur danych, które implementują interfejs <xref:System.Collections.Generic.IEnumerable%601> (na przykład <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="e85e4-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="e85e4-106">Nieogólna wersja <xref:System.Activities.Statements.ForEach%601> przekroczy to wymaganie, kosztem większej złożoności w czasie wykonywania w celu zapewnienia zgodności typów wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e85e4-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="e85e4-107">Ten przykład pokazuje, jak zaimplementować nieogólne działanie <xref:System.Activities.Statements.ForEach%601> i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="e85e4-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="e85e4-108">To działanie może służyć do iterowania przez <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="e85e4-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="e85e4-109">Działanie ForEach</span><span class="sxs-lookup"><span data-stu-id="e85e4-109">ForEach Activity</span></span>  
 <span data-ttu-id="e85e4-110">Instrukcja C#/Visual Basic `foreach` wylicza elementy kolekcji, wykonując osadzoną instrukcję dla każdego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e85e4-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="e85e4-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] równoważne działania `foreach` są <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="e85e4-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="e85e4-112">Działanie <xref:System.Activities.Statements.ForEach%601> zawiera listę wartości i treść.</span><span class="sxs-lookup"><span data-stu-id="e85e4-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="e85e4-113">W czasie wykonywania lista jest powtarzana i jest wykonywana dla każdej wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="e85e4-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="e85e4-114">W większości przypadków ogólna wersja działania powinna być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których będzie używana, i zapewnia kontrolę typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e85e4-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="e85e4-115">Wersja nieogólna może być używana do iterowania za pomocą typów implementujących nieogólny interfejs <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="e85e4-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="e85e4-116">Definicja klasy</span><span class="sxs-lookup"><span data-stu-id="e85e4-116">Class Definition</span></span>  
 <span data-ttu-id="e85e4-117">Poniższy przykład kodu pokazuje definicję działania nieogólnego `ForEach`.</span><span class="sxs-lookup"><span data-stu-id="e85e4-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 <span data-ttu-id="e85e4-118">Treść (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e85e4-118">Body (optional)</span></span>  
 <span data-ttu-id="e85e4-119"><xref:System.Activities.ActivityAction> typu <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e85e4-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="e85e4-120">Każdy pojedynczy element jest przesyłany do treści za pomocą jego właściwości `Argument`.</span><span class="sxs-lookup"><span data-stu-id="e85e4-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="e85e4-121">Wartości (opcjonalne)</span><span class="sxs-lookup"><span data-stu-id="e85e4-121">Values (optional)</span></span>  
 <span data-ttu-id="e85e4-122">Kolekcja elementów, które są powtarzane.</span><span class="sxs-lookup"><span data-stu-id="e85e4-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="e85e4-123">Upewnienie się, że wszystkie elementy kolekcji są zgodne typy wykonywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e85e4-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="e85e4-124">Przykład użycia polecenia ForEach</span><span class="sxs-lookup"><span data-stu-id="e85e4-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="e85e4-125">Poniższy kod ilustruje sposób używania działania ForEach w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e85e4-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|<span data-ttu-id="e85e4-126">Warunek</span><span class="sxs-lookup"><span data-stu-id="e85e4-126">Condition</span></span>|<span data-ttu-id="e85e4-127">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e85e4-127">Message</span></span>|<span data-ttu-id="e85e4-128">Ważność</span><span class="sxs-lookup"><span data-stu-id="e85e4-128">Severity</span></span>|<span data-ttu-id="e85e4-129">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="e85e4-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="e85e4-130">Wartości są `null`</span><span class="sxs-lookup"><span data-stu-id="e85e4-130">Values is `null`</span></span>|<span data-ttu-id="e85e4-131">Nie podano wartości dla wymaganego argumentu działania "Values".</span><span class="sxs-lookup"><span data-stu-id="e85e4-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="e85e4-132">Błąd</span><span class="sxs-lookup"><span data-stu-id="e85e4-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="e85e4-133">Projektant ForEach</span><span class="sxs-lookup"><span data-stu-id="e85e4-133">ForEach Designer</span></span>  
 <span data-ttu-id="e85e4-134">Projektant działań dla przykładu jest podobny do projektanta dostępnego dla wbudowanego działania <xref:System.Activities.Statements.ForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="e85e4-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="e85e4-135">Projektant pojawia się w przyborniku w kategorii **przykłady**, **nieogólne działania** .</span><span class="sxs-lookup"><span data-stu-id="e85e4-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="e85e4-136">Projektant ma nazwę **ForEachWithBodyFactory** w przyborniku, ponieważ działanie uwidacznia <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, który tworzy działanie z prawidłowo skonfigurowanym <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="e85e4-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="e85e4-137">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="e85e4-137">To run this sample</span></span>  
  
1. <span data-ttu-id="e85e4-138">Ustaw wybrany projekt jako projekt startowy rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="e85e4-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="e85e4-139">**CodeTestClient** pokazuje, jak używać działania przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="e85e4-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="e85e4-140">**DesignerTestClient** pokazuje, jak używać działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="e85e4-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="e85e4-141">Skompiluj i uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="e85e4-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e85e4-142">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e85e4-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e85e4-143">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e85e4-143">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e85e4-144">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e85e4-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e85e4-145">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e85e4-145">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
