---
title: Działanie niestandardowe do przełączania na zakres wartości
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: cfaf4318b1557a9fc217de8254e164243ea54569
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133246"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="7d5d5-102">Działanie niestandardowe do przełączania na zakres wartości</span><span class="sxs-lookup"><span data-stu-id="7d5d5-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="7d5d5-103">W tym przykładzie pokazano, jak utworzyć niestandardowe działanie, która rozszerza użytkowania <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="7d5d5-104">Konwencjonalne <xref:System.Activities.Statements.Switch%601> instrukcji umożliwia przełączanie oparte na pojedynczej wartości.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="7d5d5-105">Istnieją jednak biznesowych, które scenariusze, w którym działanie, musisz przełączyć na podstawie zakresu wartości.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="7d5d5-106">Na przykład działanie może być wykonywany jedną akcję, gdy przełączany na wartość od 1 do 5, innej akcji, gdy wartość jest równa od 6 do 10 i domyślna akcja dla wszystkich pozostałych wartości.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="7d5d5-107">To niestandardowe działanie umożliwia dokładnie tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="7d5d5-108">Działanie SwitchRange</span><span class="sxs-lookup"><span data-stu-id="7d5d5-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="7d5d5-109">`SwitchRange` Działania planuje działania podrzędnego, gdy wartość wyniku jej wyrażenia jest uwzględnione w zakresie jednej z jego `Cases`.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="7d5d5-110">Poniższy przykład kodu jest niestandardowe działanie, które przełączniki na podstawie zakresu wartości.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|<span data-ttu-id="7d5d5-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7d5d5-111">Property</span></span>|<span data-ttu-id="7d5d5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7d5d5-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="7d5d5-113">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7d5d5-113">Expression</span></span>|<span data-ttu-id="7d5d5-114">To wyrażenie, które ma zostać obliczone i porównywana zakresów na liście przypadków.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="7d5d5-115">Wynikiem wyrażenia jest typu T.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="7d5d5-116">Przypadków</span><span class="sxs-lookup"><span data-stu-id="7d5d5-116">Cases</span></span>|<span data-ttu-id="7d5d5-117">Każdy przypadek składa się z zakresu (od a do) i działania (treść).</span><span class="sxs-lookup"><span data-stu-id="7d5d5-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="7d5d5-118">Wyrażenie jest obliczane i porównywana z zakresów.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="7d5d5-119">Jeśli wynikiem wyrażenia jest w zakresie przypadkach, odpowiadające mu działanie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="7d5d5-120">Domyślny</span><span class="sxs-lookup"><span data-stu-id="7d5d5-120">Default</span></span>|<span data-ttu-id="7d5d5-121">Działanie, które jest wykonywany, gdy żaden przypadek nie jest dopasowany.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="7d5d5-122">Po ustawieniu `null`, nie podjęto żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="7d5d5-123">Klasa CaseRange</span><span class="sxs-lookup"><span data-stu-id="7d5d5-123">CaseRange Class</span></span>  
 <span data-ttu-id="7d5d5-124">`CaseRange` Klasa reprezentuje zakres, w ramach `SwitchRange` działania.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="7d5d5-125">Każde wystąpienie `CaseRange` zawiera zakres (składające się z `From` i `To`) i `Body` działania, które jest zaplanowane, jeśli wyrażenie w `SwitchRange` jest szacowana w ramach zakresu.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="7d5d5-126">Poniższy przykład kodu jest definicja `CaseRange` klasy.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="7d5d5-127">Zarówno `SwitchRange` i `CaseRange` klasy, które są zdefiniowane w przykładzie są klas ogólnych, które można pracować z dowolnego typu, który implementuje `IComparable`, takiej jak <xref:System.Activities.Statements.Switch%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="7d5d5-128">Przykładowe zastosowanie</span><span class="sxs-lookup"><span data-stu-id="7d5d5-128">Sample Usage</span></span>  
 <span data-ttu-id="7d5d5-129">Poniższy przykład kodu demonstruje sposób używania `SwitchRange` działania.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7d5d5-130">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="7d5d5-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="7d5d5-131">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania SwitchRange.sln.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7d5d5-132">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7d5d5-133">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d5d5-134">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7d5d5-135">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7d5d5-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7d5d5-136">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d5d5-137">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7d5d5-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`