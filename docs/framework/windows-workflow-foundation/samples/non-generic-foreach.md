---
title: Nieogólne działanie ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 08dbac3974915f823a4f6e39f35927453a7c4b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142709"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="86d22-102">Nieogólne działanie ForEach</span><span class="sxs-lookup"><span data-stu-id="86d22-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="86d22-103">w swoim zestawie narzędzi znajduje się zestaw <xref:System.Activities.Statements.ForEach%601>działań control flow, <xref:System.Collections.Generic.IEnumerable%601> w tym , który umożliwia iterację poprzez kolekcje.</span><span class="sxs-lookup"><span data-stu-id="86d22-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="86d22-104"><xref:System.Activities.Statements.ForEach%601>wymaga, <xref:System.Activities.Statements.ForEach%601.Values%2A> aby jego <xref:System.Collections.Generic.IEnumerable%601>właściwość była typu.</span><span class="sxs-lookup"><span data-stu-id="86d22-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="86d22-105">Uniemożliwia to użytkownikom iterację struktur danych <xref:System.Collections.Generic.IEnumerable%601> implementujących interfejs <xref:System.Collections.ArrayList>(na przykład ).</span><span class="sxs-lookup"><span data-stu-id="86d22-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="86d22-106">Nierodzyna <xref:System.Activities.Statements.ForEach%601> wersja pokonuje to wymaganie, kosztem większej złożoności w czasie wykonywania w celu zapewnienia zgodności typów wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="86d22-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="86d22-107">W tym przykładzie pokazano, <xref:System.Activities.Statements.ForEach%601> jak zaimplementować działanie niegeneryczne i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="86d22-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="86d22-108">To działanie może służyć do <xref:System.Collections.ArrayList>iteracji przez .</span><span class="sxs-lookup"><span data-stu-id="86d22-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="86d22-109">Aktywność ForEach</span><span class="sxs-lookup"><span data-stu-id="86d22-109">ForEach Activity</span></span>  
 <span data-ttu-id="86d22-110">Instrukcja C#/Visual Basic `foreach` wylicza elementy kolekcji, wykonując osadzoną instrukcję dla każdego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="86d22-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="86d22-111">Równoważne [!INCLUDE[wf1](../../../../includes/wf1-md.md)] działania `foreach` są <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.ParallelForEach%601>i .</span><span class="sxs-lookup"><span data-stu-id="86d22-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="86d22-112">Działanie <xref:System.Activities.Statements.ForEach%601> zawiera listę wartości i treść.</span><span class="sxs-lookup"><span data-stu-id="86d22-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="86d22-113">W czasie wykonywania lista jest iterowana, a treść jest wykonywana dla każdej wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="86d22-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="86d22-114">W większości przypadków ogólna wersja działania powinna być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których będzie używana i zapewnia sprawdzanie typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="86d22-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="86d22-115">Wersja niegeneryczna może służyć do iteracji za pośrednictwem <xref:System.Collections.IEnumerable> typów, które implementują interfejs niegeneryczny.</span><span class="sxs-lookup"><span data-stu-id="86d22-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="86d22-116">Definicja klasy</span><span class="sxs-lookup"><span data-stu-id="86d22-116">Class Definition</span></span>  
 <span data-ttu-id="86d22-117">Poniższy przykład kodu przedstawia definicję `ForEach` działania nierodzego.</span><span class="sxs-lookup"><span data-stu-id="86d22-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
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
  
 <span data-ttu-id="86d22-118">Korpus (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="86d22-118">Body (optional)</span></span>  
 <span data-ttu-id="86d22-119">Typ <xref:System.Activities.ActivityAction> <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="86d22-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="86d22-120">Każdy pojedynczy element jest przekazywany do Body za pośrednictwem jego `Argument` właściwości.</span><span class="sxs-lookup"><span data-stu-id="86d22-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="86d22-121">Wartości (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="86d22-121">Values (optional)</span></span>  
 <span data-ttu-id="86d22-122">Kolekcja elementów, które są iterowane ponad.</span><span class="sxs-lookup"><span data-stu-id="86d22-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="86d22-123">Upewnienie się, że wszystkie elementy kolekcji są zgodne typy odbywa się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="86d22-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="86d22-124">Przykład korzystania z ForEach</span><span class="sxs-lookup"><span data-stu-id="86d22-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="86d22-125">Poniższy kod pokazuje, jak używać ForEach działania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86d22-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
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
  
|<span data-ttu-id="86d22-126">Warunek</span><span class="sxs-lookup"><span data-stu-id="86d22-126">Condition</span></span>|<span data-ttu-id="86d22-127">Komunikat</span><span class="sxs-lookup"><span data-stu-id="86d22-127">Message</span></span>|<span data-ttu-id="86d22-128">Ważność</span><span class="sxs-lookup"><span data-stu-id="86d22-128">Severity</span></span>|<span data-ttu-id="86d22-129">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="86d22-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="86d22-130">Wartości są`null`</span><span class="sxs-lookup"><span data-stu-id="86d22-130">Values is `null`</span></span>|<span data-ttu-id="86d22-131">Wartość wymaganego argumentu działania "Wartości" nie została podana.</span><span class="sxs-lookup"><span data-stu-id="86d22-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="86d22-132">Błąd</span><span class="sxs-lookup"><span data-stu-id="86d22-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="86d22-133">Projektant ForEach</span><span class="sxs-lookup"><span data-stu-id="86d22-133">ForEach Designer</span></span>  
 <span data-ttu-id="86d22-134">Projektant działania dla przykładu jest podobny wygląd do projektanta <xref:System.Activities.Statements.ForEach%601> przewidziane dla wbudowanego działania.</span><span class="sxs-lookup"><span data-stu-id="86d22-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="86d22-135">Projektant pojawi się w przyborniku w **kategorii Przykłady**, **Działania niegeneryczne.**</span><span class="sxs-lookup"><span data-stu-id="86d22-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="86d22-136">Projektant nosi nazwę **ForEachWithBodyFactory** w przyborniku, <xref:System.Activities.Presentation.IActivityTemplateFactory> ponieważ działanie udostępnia w przyborniku, który <xref:System.Activities.ActivityAction>tworzy działanie z prawidłowo skonfigurowanym .</span><span class="sxs-lookup"><span data-stu-id="86d22-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="86d22-137">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="86d22-137">To run this sample</span></span>  
  
1. <span data-ttu-id="86d22-138">Ustaw wybrany projekt jako projekt startowy rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="86d22-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="86d22-139">**CodeTestClient** pokazuje, jak używać działania przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="86d22-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="86d22-140">**DesignerTestClient** pokazuje, jak używać działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="86d22-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="86d22-141">Tworzenie i uruchamianie projektu.</span><span class="sxs-lookup"><span data-stu-id="86d22-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="86d22-142">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="86d22-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="86d22-143">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="86d22-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="86d22-144">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="86d22-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="86d22-145">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="86d22-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
