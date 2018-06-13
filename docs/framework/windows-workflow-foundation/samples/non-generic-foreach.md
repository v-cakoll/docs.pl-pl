---
title: ForEach inny niż ogólny
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: c67f6e3c3afb893f7bb5713d64ce2f119eebc157
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519483"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="a3fa3-102">ForEach inny niż ogólny</span><span class="sxs-lookup"><span data-stu-id="a3fa3-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="a3fa3-103"> jest dostarczany w przyborniku jego zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ForEach%601>, dzięki czemu iteracja <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="a3fa3-104"><xref:System.Activities.Statements.ForEach%601> wymaga jego <xref:System.Activities.Statements.ForEach%601.Values%2A> właściwości typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="a3fa3-105">To wyklucza użytkowników z Iterowanie za pośrednictwem struktury danych, które implementują <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interfejsu (na przykład <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="a3fa3-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="a3fa3-106">Wersja nieogólnego <xref:System.Activities.Statements.ForEach%601> pozwala pokonać to wymaganie, kosztem bardziej złożona czasu wykonywania dla zapewnienia zgodności z typów wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="a3fa3-107">W tym przykładzie pokazano, jak wdrożyć nieogólnego <xref:System.Activities.Statements.ForEach%601> działanie i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="a3fa3-108">To działanie może służyć do iterowania po <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="a3fa3-109">Działania ForEach</span><span class="sxs-lookup"><span data-stu-id="a3fa3-109">ForEach Activity</span></span>  
 <span data-ttu-id="a3fa3-110">C# /VB `foreach` instrukcji wylicza elementy kolekcji, wykonywania osadzona instrukcja dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="a3fa3-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Równoważne działania `foreach` są <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="a3fa3-112"><xref:System.Activities.Statements.ForEach%601> Działania zawiera listę wartości i treść.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="a3fa3-113">W czasie wykonywania jest iterowane listy i treść jest wykonywane dla każdej wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="a3fa3-114">W większości przypadków ogólnego wersja działania powinny być preferowane rozwiązanie, ponieważ obejmuje większość scenariuszy, w których on mają być używane i zawiera typ sprawdzania w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="a3fa3-115">Wersja nieogólnego może służyć do iteracji typów, które implementują nieogólnego <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="a3fa3-116">Definicja klasy</span><span class="sxs-lookup"><span data-stu-id="a3fa3-116">Class Definition</span></span>  
 <span data-ttu-id="a3fa3-117">Poniższy przykładowy kod przedstawia definicję nieogólnego `ForEach` działania.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```  
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
  
 <span data-ttu-id="a3fa3-118">Treść (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a3fa3-118">Body (optional)</span></span>  
 <span data-ttu-id="a3fa3-119"><xref:System.Activities.ActivityAction> Typu <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="a3fa3-120">Każdy element poszczególnych została przekazana do treści za pośrednictwem jego `Argument` właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="a3fa3-121">Wartości (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a3fa3-121">Values (optional)</span></span>  
 <span data-ttu-id="a3fa3-122">Kolekcja elementów, które są iterowane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="a3fa3-123">Zapewnienie, że wszystkie elementy kolekcji są zgodnych typów odbywa się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="a3fa3-124">Przykład za pomocą instrukcji ForEach</span><span class="sxs-lookup"><span data-stu-id="a3fa3-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="a3fa3-125">Poniższy kod przedstawia sposób użycia działania ForEach w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```  
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
  
|<span data-ttu-id="a3fa3-126">Warunek</span><span class="sxs-lookup"><span data-stu-id="a3fa3-126">Condition</span></span>|<span data-ttu-id="a3fa3-127">Komunikat</span><span class="sxs-lookup"><span data-stu-id="a3fa3-127">Message</span></span>|<span data-ttu-id="a3fa3-128">Ważność</span><span class="sxs-lookup"><span data-stu-id="a3fa3-128">Severity</span></span>|<span data-ttu-id="a3fa3-129">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="a3fa3-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="a3fa3-130">Wartości to `null`</span><span class="sxs-lookup"><span data-stu-id="a3fa3-130">Values is `null`</span></span>|<span data-ttu-id="a3fa3-131">Nie podano wartości dla wymaganego argumentu działania "Wartości".</span><span class="sxs-lookup"><span data-stu-id="a3fa3-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="a3fa3-132">Błąd</span><span class="sxs-lookup"><span data-stu-id="a3fa3-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="a3fa3-133">Projektant ForEach</span><span class="sxs-lookup"><span data-stu-id="a3fa3-133">ForEach Designer</span></span>  
 <span data-ttu-id="a3fa3-134">Projektant działań przykładowej przypomina do projektanta przewidzianych wbudowane <xref:System.Activities.Statements.ForEach%601> działania.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="a3fa3-135">Projektant jest wyświetlany w przyborniku w **przykłady**, **inne niż ogólne działania** kategorii.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="a3fa3-136">Projektant nosi nazwę **ForEachWithBodyFactory** w przyborniku ponieważ ujawnia działania <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, co powoduje działania z odpowiednio skonfigurowanego <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="a3fa3-137">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="a3fa3-137">To run this sample</span></span>  
  
1.  <span data-ttu-id="a3fa3-138">Ustaw projekt wybranych przez użytkownika jako projekt uruchamiania rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="a3fa3-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1.  <span data-ttu-id="a3fa3-139">**CodeTestClient** przedstawia sposób użycia działanie przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="a3fa3-140">**DesignerTestClient** przedstawia sposób użycia działanie w projektancie.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="a3fa3-141">Tworzenie i uruchamianie projektu.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a3fa3-142">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a3fa3-143">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a3fa3-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a3fa3-144">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a3fa3-145">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a3fa3-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
