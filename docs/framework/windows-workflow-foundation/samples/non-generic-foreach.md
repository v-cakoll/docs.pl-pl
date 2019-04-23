---
title: Nieogólne działanie ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 353128d1c313be62222e091c084e5b5e37a92b58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303547"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="05c46-102">Nieogólne działanie ForEach</span><span class="sxs-lookup"><span data-stu-id="05c46-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="05c46-103">jest dostarczany w przyborniku jej zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ForEach%601>, co pozwala iteracja <xref:System.Collections.Generic.IEnumerable%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05c46-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="05c46-104"><xref:System.Activities.Statements.ForEach%601> wymaga jego <xref:System.Activities.Statements.ForEach%601.Values%2A> właściwość typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="05c46-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="05c46-105">Użytkownicy to wyklucza z Iterowanie struktur danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejsu (na przykład <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="05c46-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="05c46-106">Wersja nieogólnego <xref:System.Activities.Statements.ForEach%601> pozwala pokonać ten wymóg, kosztem więcej złożoności środowiska wykonawczego dla zapewnienia zgodności z typów wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05c46-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="05c46-107">Ten przykład przedstawia sposób implementowania nieogólnego <xref:System.Activities.Statements.ForEach%601> działanie i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="05c46-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="05c46-108">To działanie może służyć do iterowania po <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="05c46-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="05c46-109">Działanie ForEach</span><span class="sxs-lookup"><span data-stu-id="05c46-109">ForEach Activity</span></span>  
 <span data-ttu-id="05c46-110">C# /VB `foreach` instrukcji wylicza elementów kolekcji, wykonywania osadzonych instrukcji dla każdego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05c46-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="05c46-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Równoważne działania `foreach` są <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="05c46-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="05c46-112"><xref:System.Activities.Statements.ForEach%601> Aktywności zawiera listę wartości i treść.</span><span class="sxs-lookup"><span data-stu-id="05c46-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="05c46-113">W czasie wykonywania jest postanowiliśmy listy, a następnie zostaje wykonana dla każdej wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="05c46-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="05c46-114">W większości przypadków ogólnego wersję działania powinny być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których go będzie używana i oferuje typu sprawdzanie w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="05c46-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="05c46-115">Wersja nieogólnego może służyć do iteracji przez typy, które implementują niepodstawowy <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="05c46-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="05c46-116">Definicja klasy</span><span class="sxs-lookup"><span data-stu-id="05c46-116">Class Definition</span></span>  
 <span data-ttu-id="05c46-117">Poniższy przykład kodu pokazuje definicji nieogólnego `ForEach` działania.</span><span class="sxs-lookup"><span data-stu-id="05c46-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
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
  
 <span data-ttu-id="05c46-118">Treść (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="05c46-118">Body (optional)</span></span>  
 <span data-ttu-id="05c46-119"><xref:System.Activities.ActivityAction> Typu <xref:System.Object>, które jest wykonywane dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05c46-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="05c46-120">Każdego pojedynczego elementu jest przekazywany do treści za pośrednictwem jego `Argument` właściwości.</span><span class="sxs-lookup"><span data-stu-id="05c46-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="05c46-121">Wartości (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="05c46-121">Values (optional)</span></span>  
 <span data-ttu-id="05c46-122">Kolekcja elementów, które są powtarzana.</span><span class="sxs-lookup"><span data-stu-id="05c46-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="05c46-123">Upewnić się, że wszystkie elementy kolekcji są zgodnych typów odbywa się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05c46-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="05c46-124">Przykład Używanie instrukcji ForEach</span><span class="sxs-lookup"><span data-stu-id="05c46-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="05c46-125">Poniższy kod przedstawia sposób użycia działanie ForEach w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05c46-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
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
  
|<span data-ttu-id="05c46-126">Warunek</span><span class="sxs-lookup"><span data-stu-id="05c46-126">Condition</span></span>|<span data-ttu-id="05c46-127">Komunikat</span><span class="sxs-lookup"><span data-stu-id="05c46-127">Message</span></span>|<span data-ttu-id="05c46-128">Ważność</span><span class="sxs-lookup"><span data-stu-id="05c46-128">Severity</span></span>|<span data-ttu-id="05c46-129">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="05c46-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="05c46-130">Wartości `null`</span><span class="sxs-lookup"><span data-stu-id="05c46-130">Values is `null`</span></span>|<span data-ttu-id="05c46-131">Nieprawidłowa wartość argumentu wymagane działania "Wartości".</span><span class="sxs-lookup"><span data-stu-id="05c46-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="05c46-132">Błąd</span><span class="sxs-lookup"><span data-stu-id="05c46-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="05c46-133">Projektant ForEach</span><span class="sxs-lookup"><span data-stu-id="05c46-133">ForEach Designer</span></span>  
 <span data-ttu-id="05c46-134">Projektant działań dla przykładu przypomina projektanta podane dla wbudowanej <xref:System.Activities.Statements.ForEach%601> działania.</span><span class="sxs-lookup"><span data-stu-id="05c46-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="05c46-135">Pojawi się okno projektanta w przyborniku, w **przykłady**, **działania Nieuniwersalne** kategorii.</span><span class="sxs-lookup"><span data-stu-id="05c46-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="05c46-136">Projektant jest o nazwie **ForEachWithBodyFactory** w przyborniku, ponieważ ujawnia działania <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, co powoduje utworzenie działania z prawidłowo skonfigurowane <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="05c46-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="05c46-137">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="05c46-137">To run this sample</span></span>  
  
1. <span data-ttu-id="05c46-138">Ustaw projekt wybranego jako projekt startowy rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="05c46-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1.  <span data-ttu-id="05c46-139">**CodeTestClient** pokazuje, jak użyć działania przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="05c46-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="05c46-140">**DesignerTestClient** pokazuje, jak użyć działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="05c46-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="05c46-141">Skompiluj i uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="05c46-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05c46-142">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="05c46-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="05c46-143">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="05c46-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="05c46-144">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="05c46-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="05c46-145">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="05c46-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
