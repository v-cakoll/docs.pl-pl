---
title: Nieogólne działanie ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 70d5de587dda3cb61205a8d77f2173df9b93498b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881814"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="23dc2-102">Nieogólne działanie ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="23dc2-102">Non-Generic ParallelForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="23dc2-103"> jest dostarczany w przyborniku jej zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ParallelForEach%601>, co pozwala iteracja <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23dc2-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="23dc2-104"><xref:System.Activities.Statements.ParallelForEach%601> wymaga jego <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> właściwość typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="23dc2-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="23dc2-105">Użytkownicy to wyklucza z Iterowanie struktur danych, które implementują <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interfejsu (na przykład <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="23dc2-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="23dc2-106">Wersja nieogólnego <xref:System.Activities.Statements.ParallelForEach%601> pozwala pokonać ten wymóg, kosztem więcej złożoności środowiska wykonawczego dla zapewnienia zgodności z typów wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23dc2-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="23dc2-107">Ten przykład przedstawia sposób implementowania nieogólnego <xref:System.Activities.Statements.ParallelForEach%601> działanie i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="23dc2-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="23dc2-108">To działanie może służyć do iterowania po <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="23dc2-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="parallelforeach-activity"></a><span data-ttu-id="23dc2-109">Działanie ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="23dc2-109">ParallelForEach Activity</span></span>  
 <span data-ttu-id="23dc2-110">C# /VB `foreach` instrukcji wylicza elementów kolekcji, wykonywania osadzonych instrukcji dla każdego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23dc2-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="23dc2-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Są równoważne działania <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="23dc2-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="23dc2-112"><xref:System.Activities.Statements.ForEach%601> Aktywności zawiera listę wartości i treść.</span><span class="sxs-lookup"><span data-stu-id="23dc2-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="23dc2-113">W czasie wykonywania jest postanowiliśmy listy, a następnie zostaje wykonana dla każdej wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="23dc2-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="23dc2-114"><xref:System.Activities.Statements.ParallelForEach%601> ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, dzięki czemu <xref:System.Activities.Statements.ParallelForEach%601> działania można ukończyć wcześnie, jeśli oceny <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="23dc2-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="23dc2-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Jest oceniane, po zakończeniu każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="23dc2-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>  
  
 <span data-ttu-id="23dc2-116">W większości przypadków ogólnego wersję działania powinny być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których jest używany i zawiera typ sprawdzanie w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="23dc2-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="23dc2-117">Wersja nieogólnego może służyć do iteracji przez typy, które implementują niepodstawowy <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="23dc2-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="23dc2-118">Definicja klasy</span><span class="sxs-lookup"><span data-stu-id="23dc2-118">Class Definition</span></span>  
 <span data-ttu-id="23dc2-119">Poniższy przykład kodu pokazuje definicji nieogólnego `ParallelForEach` jest działanie.</span><span class="sxs-lookup"><span data-stu-id="23dc2-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>  
  
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
  
 <span data-ttu-id="23dc2-120">Treść (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="23dc2-120">Body (optional)</span></span>  
 <span data-ttu-id="23dc2-121"><xref:System.Activities.ActivityAction> Typu <xref:System.Object>, które jest wykonywane dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23dc2-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="23dc2-122">Każdego pojedynczego elementu jest przekazywane do treści jego właściwość argumentu.</span><span class="sxs-lookup"><span data-stu-id="23dc2-122">Each individual element is passed into the Body through its Argument property.</span></span>  
  
 <span data-ttu-id="23dc2-123">Wartości (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="23dc2-123">Values (optional)</span></span>  
 <span data-ttu-id="23dc2-124">Kolekcja elementów, które są powtarzana.</span><span class="sxs-lookup"><span data-stu-id="23dc2-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="23dc2-125">Upewnić się, że wszystkie elementy kolekcji są zgodnych typów odbywa się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="23dc2-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
 <span data-ttu-id="23dc2-126">CompletionCondition (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="23dc2-126">CompletionCondition (optional)</span></span>  
 <span data-ttu-id="23dc2-127"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Właściwość jest oceniane, po zakończeniu dowolną iterację.</span><span class="sxs-lookup"><span data-stu-id="23dc2-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="23dc2-128">Jeśli daje w wyniku `true`, następnie zaplanowane do czasu iteracji są anulowane.</span><span class="sxs-lookup"><span data-stu-id="23dc2-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="23dc2-129">Jeśli ta właściwość nie jest ustawiona, wszystkie działania w kolekcji gałęzi jest wykonywanie aż do zakończenia.</span><span class="sxs-lookup"><span data-stu-id="23dc2-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>  
  
## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="23dc2-130">Przykład użycia ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="23dc2-130">Example of Using ParallelForEach</span></span>  
 <span data-ttu-id="23dc2-131">Poniższy kod przedstawia sposób użycia działanie ParallelForEach w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23dc2-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>  
  
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
  
## <a name="parallelforeach-designer"></a><span data-ttu-id="23dc2-132">Projektant ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="23dc2-132">ParallelForEach Designer</span></span>  
 <span data-ttu-id="23dc2-133">Projektant działań dla przykładu przypomina projektanta podane dla wbudowanej <xref:System.Activities.Statements.ParallelForEach%601> działania.</span><span class="sxs-lookup"><span data-stu-id="23dc2-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="23dc2-134">Pojawi się okno projektanta w przyborniku, w **przykłady**, **działania Nieuniwersalne** kategorii.</span><span class="sxs-lookup"><span data-stu-id="23dc2-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="23dc2-135">Projektant jest o nazwie **ParallelForEachWithBodyFactory** w przyborniku, ponieważ ujawnia działania <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, który tworzy działanie z prawidłowo skonfigurowane <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="23dc2-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
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
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="23dc2-136">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="23dc2-136">To run the sample</span></span>  
  
1.  <span data-ttu-id="23dc2-137">Ustaw projekt wybranego jako projekt startowy rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="23dc2-137">Set the project of your choice as the startup project of the solution.</span></span>  
  
    1.  <span data-ttu-id="23dc2-138">**CodeTestClient** pokazuje, jak użyć działania przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="23dc2-138">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="23dc2-139">**DesignerTestClient** pokazuje, jak użyć działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="23dc2-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="23dc2-140">Skompiluj i uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="23dc2-140">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="23dc2-141">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="23dc2-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="23dc2-142">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="23dc2-142">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="23dc2-143">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="23dc2-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="23dc2-144">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="23dc2-144">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
