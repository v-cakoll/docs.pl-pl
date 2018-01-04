---
title: "Działania ParallelForEach inny niż ogólny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eb019aed7fce267506ddb495609df5a80a8f8d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="74340-102">Działania ParallelForEach inny niż ogólny</span><span class="sxs-lookup"><span data-stu-id="74340-102">Non-Generic ParallelForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="74340-103">jest dostarczany w przyborniku jego zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ParallelForEach%601>, dzięki czemu iteracja <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74340-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="74340-104"><xref:System.Activities.Statements.ParallelForEach%601>wymaga jego <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> właściwości typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="74340-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="74340-105">To wyklucza użytkowników z Iterowanie za pośrednictwem struktury danych, które implementują <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interfejsu (na przykład <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="74340-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="74340-106">Wersja nieogólnego <xref:System.Activities.Statements.ParallelForEach%601> pozwala pokonać to wymaganie, kosztem bardziej złożona czasu wykonywania dla zapewnienia zgodności z typów wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74340-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="74340-107">W tym przykładzie pokazano, jak wdrożyć nieogólnego <xref:System.Activities.Statements.ParallelForEach%601> działanie i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="74340-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="74340-108">To działanie może służyć do iterowania po <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="74340-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="parallelforeach-activity"></a><span data-ttu-id="74340-109">Działania ParallelForEach działania</span><span class="sxs-lookup"><span data-stu-id="74340-109">ParallelForEach Activity</span></span>  
 <span data-ttu-id="74340-110">C# /VB `foreach` instrukcji wylicza elementy kolekcji, wykonywania osadzona instrukcja dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74340-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="74340-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Są równoważne działania <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="74340-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="74340-112"><xref:System.Activities.Statements.ForEach%601> Działania zawiera listę wartości i treść.</span><span class="sxs-lookup"><span data-stu-id="74340-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="74340-113">W czasie wykonywania jest iterowane listy i treść jest wykonywane dla każdej wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="74340-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="74340-114"><xref:System.Activities.Statements.ParallelForEach%601>ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, dzięki czemu <xref:System.Activities.Statements.ParallelForEach%601> może ukończyć działania wczesne Jeśli oceny <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="74340-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="74340-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Jest oceniane po zakończeniu każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="74340-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>  
  
 <span data-ttu-id="74340-116">W większości przypadków ogólnego wersja działania powinny być preferowane rozwiązanie, ponieważ obejmuje większość scenariuszy, w których jest używany i zawiera typ sprawdzania w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="74340-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="74340-117">Wersja nieogólnego może służyć do iteracji typów, które implementują nieogólnego <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="74340-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="74340-118">Definicja klasy</span><span class="sxs-lookup"><span data-stu-id="74340-118">Class Definition</span></span>  
 <span data-ttu-id="74340-119">Poniższy przykładowy kod przedstawia definicję nieogólnego `ParallelForEach` jest działania.</span><span class="sxs-lookup"><span data-stu-id="74340-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>  
  
```  
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
  
 <span data-ttu-id="74340-120">Treść (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="74340-120">Body (optional)</span></span>  
 <span data-ttu-id="74340-121"><xref:System.Activities.ActivityAction> Typu <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74340-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="74340-122">Każdy element poszczególnych jest przekazywana do treści jego właściwość argumentu.</span><span class="sxs-lookup"><span data-stu-id="74340-122">Each individual element is passed into the Body through its Argument property.</span></span>  
  
 <span data-ttu-id="74340-123">Wartości (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="74340-123">Values (optional)</span></span>  
 <span data-ttu-id="74340-124">Kolekcja elementów, które są iterowane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="74340-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="74340-125">Zapewnienie, że wszystkie elementy kolekcji są zgodnych typów odbywa się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="74340-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
 <span data-ttu-id="74340-126">CompletionCondition (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="74340-126">CompletionCondition (optional)</span></span>  
 <span data-ttu-id="74340-127"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Właściwości jest oceniane po zakończeniu dowolną iterację.</span><span class="sxs-lookup"><span data-stu-id="74340-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="74340-128">Jeśli daje w wyniku `true`, następnie zaplanowanego czasu iteracji zostały anulowane.</span><span class="sxs-lookup"><span data-stu-id="74340-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="74340-129">Jeśli ta właściwość nie jest ustawiona, wszystkie działania w kolekcji gałęzie wykonywanie do momentu zakończenia.</span><span class="sxs-lookup"><span data-stu-id="74340-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>  
  
## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="74340-130">Przykład użycia działania ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="74340-130">Example of Using ParallelForEach</span></span>  
 <span data-ttu-id="74340-131">Poniższy kod przedstawia sposób użycia działania działania ParallelForEach w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="74340-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>  
  
```  
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
  
## <a name="parallelforeach-designer"></a><span data-ttu-id="74340-132">Projektant działania ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="74340-132">ParallelForEach Designer</span></span>  
 <span data-ttu-id="74340-133">Projektant działań przykładowej przypomina do projektanta przewidzianych wbudowane <xref:System.Activities.Statements.ParallelForEach%601> działania.</span><span class="sxs-lookup"><span data-stu-id="74340-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="74340-134">Projektant jest wyświetlany w przyborniku w **przykłady**, **inne niż ogólne działania** kategorii.</span><span class="sxs-lookup"><span data-stu-id="74340-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="74340-135">Projektant nosi nazwę **ParallelForEachWithBodyFactory** w przyborniku ponieważ ujawnia działania <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku tworzy działanie z odpowiednio skonfigurowanego <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="74340-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
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
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="74340-136">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="74340-136">To run the sample</span></span>  
  
1.  <span data-ttu-id="74340-137">Ustaw projekt wybranych przez użytkownika jako projekt startowy rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="74340-137">Set the project of your choice as the startup project of the solution.</span></span>  
  
    1.  <span data-ttu-id="74340-138">**CodeTestClient** przedstawia sposób użycia działanie przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="74340-138">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="74340-139">**DesignerTestClient** przedstawia sposób użycia działanie w projektancie.</span><span class="sxs-lookup"><span data-stu-id="74340-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="74340-140">Tworzenie i uruchamianie projektu.</span><span class="sxs-lookup"><span data-stu-id="74340-140">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74340-141">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="74340-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74340-142">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="74340-142">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74340-143">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="74340-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74340-144">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="74340-144">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
