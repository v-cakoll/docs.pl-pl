---
title: Nieogólny ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: ea7f57b8812dca3dfcb4908730dd788182d50c5c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347618"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="70067-102">Nieogólny ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="70067-102">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="70067-103">dostarcza w swoim przyborniku zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ParallelForEach%601>, które umożliwiają iterację przez kolekcje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="70067-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="70067-104"><xref:System.Activities.Statements.ParallelForEach%601> wymaga, aby Właściwość <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> była typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="70067-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="70067-105">Uniemożliwia to użytkownikom iterację struktur danych, które implementują interfejs <xref:System.Collections.Generic.IEnumerable%601> (na przykład <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="70067-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="70067-106">Nieogólna wersja <xref:System.Activities.Statements.ParallelForEach%601> przekroczy to wymaganie, kosztem większej złożoności w czasie wykonywania w celu zapewnienia zgodności typów wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="70067-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="70067-107">Ten przykład pokazuje, jak zaimplementować nieogólne działanie <xref:System.Activities.Statements.ParallelForEach%601> i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="70067-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="70067-108">To działanie może służyć do iterowania przez <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="70067-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="70067-109">Działanie ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="70067-109">ParallelForEach activity</span></span>

<span data-ttu-id="70067-110">Instrukcja C#/Visual Basic `foreach` wylicza elementy kolekcji, wykonując osadzoną instrukcję dla każdego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="70067-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="70067-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] równoważne działania są <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="70067-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="70067-112">Działanie <xref:System.Activities.Statements.ForEach%601> zawiera listę wartości i treść.</span><span class="sxs-lookup"><span data-stu-id="70067-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="70067-113">W czasie wykonywania lista jest powtarzana i jest wykonywana dla każdej wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="70067-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="70067-114"><xref:System.Activities.Statements.ParallelForEach%601> ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, dzięki czemu działanie <xref:System.Activities.Statements.ParallelForEach%601> może zakończyć się wcześnie, jeśli Obliczanie <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="70067-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="70067-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> jest oceniane po zakończeniu każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="70067-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="70067-116">W większości przypadków ogólna wersja działania powinna być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których jest używana, i zapewnia kontrolę typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70067-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="70067-117">Wersja nieogólna może być używana do iterowania za pomocą typów implementujących nieogólny interfejs <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="70067-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="70067-118">Definicja klasy</span><span class="sxs-lookup"><span data-stu-id="70067-118">Class definition</span></span>

<span data-ttu-id="70067-119">Poniższy przykład kodu pokazuje definicję działania nieogólnego `ParallelForEach`.</span><span class="sxs-lookup"><span data-stu-id="70067-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

<span data-ttu-id="70067-120">Treść (opcjonalnie) </span><span class="sxs-lookup"><span data-stu-id="70067-120">Body (optional)</span></span>\
<span data-ttu-id="70067-121"><xref:System.Activities.ActivityAction> typu <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="70067-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="70067-122">Każdy pojedynczy element jest przesyłany do treści za pomocą jego właściwości argument.</span><span class="sxs-lookup"><span data-stu-id="70067-122">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="70067-123">Wartości (opcjonalnie) </span><span class="sxs-lookup"><span data-stu-id="70067-123">Values (optional)</span></span>\
<span data-ttu-id="70067-124">Kolekcja elementów, które są powtarzane.</span><span class="sxs-lookup"><span data-stu-id="70067-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="70067-125">Upewnienie się, że wszystkie elementy kolekcji są zgodne typy wykonywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="70067-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="70067-126">CompletionCondition (opcjonalnie) </span><span class="sxs-lookup"><span data-stu-id="70067-126">CompletionCondition (optional)</span></span>\
<span data-ttu-id="70067-127">Właściwość <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> jest szacowana po zakończeniu każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="70067-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="70067-128">Jeśli zostanie obliczona `true`, zaplanowane oczekujące iteracje zostaną anulowane.</span><span class="sxs-lookup"><span data-stu-id="70067-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="70067-129">Jeśli ta właściwość nie jest ustawiona, wszystkie działania w kolekcji gałęzi są wykonywane do momentu ukończenia.</span><span class="sxs-lookup"><span data-stu-id="70067-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="70067-130">Przykład użycia ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="70067-130">Example of using ParallelForEach</span></span>

<span data-ttu-id="70067-131">Poniższy kod ilustruje sposób używania działania ParallelForEach w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70067-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
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

## <a name="parallelforeach-designer"></a><span data-ttu-id="70067-132">Projektant ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="70067-132">ParallelForEach designer</span></span>

<span data-ttu-id="70067-133">Projektant działań dla przykładu jest podobny do projektanta dostępnego dla wbudowanego działania <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="70067-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="70067-134">Projektant pojawia się w przyborniku w kategorii **przykłady**, **nieogólne działania** .</span><span class="sxs-lookup"><span data-stu-id="70067-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="70067-135">Projektant ma nazwę **ParallelForEachWithBodyFactory** w przyborniku, ponieważ działanie uwidacznia <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, który tworzy działanie z prawidłowo skonfigurowanym <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="70067-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
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

## <a name="to-run-the-sample"></a><span data-ttu-id="70067-136">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="70067-136">To run the sample</span></span>

1. <span data-ttu-id="70067-137">Ustaw wybrany projekt jako projekt startowy rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="70067-137">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="70067-138">**CodeTestClient** pokazuje, jak używać działania przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="70067-138">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="70067-139">**DesignerTestClient** pokazuje, jak używać działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="70067-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="70067-140">Skompiluj i uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="70067-140">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70067-141">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="70067-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="70067-142">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="70067-142">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="70067-143">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70067-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="70067-144">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="70067-144">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
