---
title: Działań niestandardowych do przełącznika na zakres wartości
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: 785db08ffaf4ca6fe27d6418878c0bbf4ada44fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517072"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="52ce4-102">Działań niestandardowych do przełącznika na zakres wartości</span><span class="sxs-lookup"><span data-stu-id="52ce4-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="52ce4-103">Ten przykład przedstawia sposób tworzenia działań niestandardowych, rozszerzający stosowania <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="52ce4-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="52ce4-104">Konwencjonalne <xref:System.Activities.Statements.Switch%601> instrukcji umożliwia przełączanie oparte na pojedynczej wartości.</span><span class="sxs-lookup"><span data-stu-id="52ce4-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="52ce4-105">Istnieją jednak biznesowych, które scenariuszy, w którym działanie, musisz przełączyć ustalane na podstawie zakresu wartości.</span><span class="sxs-lookup"><span data-stu-id="52ce4-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="52ce4-106">Na przykład działanie może wykonać jedno działanie, gdy jest przełączany na wartość od 1 do 5, innej akcji, gdy wartość jest od 6 do 10 i domyślnego działania dla wszystkich innych wartości.</span><span class="sxs-lookup"><span data-stu-id="52ce4-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="52ce4-107">To niestandardowe działanie umożliwia dokładnie tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="52ce4-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="52ce4-108">Działanie SwitchRange</span><span class="sxs-lookup"><span data-stu-id="52ce4-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="52ce4-109">`SwitchRange` Działania planuje działaniem podrzędnym, gdy wartość wyniku jej wyrażenia znajduje się w zakresie jednej z jego `Cases`.</span><span class="sxs-lookup"><span data-stu-id="52ce4-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="52ce4-110">Następujący przykładowy kod to niestandardowe działanie, które przełączniki ustalane na podstawie zakresu wartości.</span><span class="sxs-lookup"><span data-stu-id="52ce4-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
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
  
|<span data-ttu-id="52ce4-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="52ce4-111">Property</span></span>|<span data-ttu-id="52ce4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="52ce4-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="52ce4-113">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="52ce4-113">Expression</span></span>|<span data-ttu-id="52ce4-114">Jest to wyrażenie, które ma zostać obliczone i porównywana zakresów na liście przypadków.</span><span class="sxs-lookup"><span data-stu-id="52ce4-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="52ce4-115">Wynikiem wyrażenia jest typu T.</span><span class="sxs-lookup"><span data-stu-id="52ce4-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="52ce4-116">Przypadków</span><span class="sxs-lookup"><span data-stu-id="52ce4-116">Cases</span></span>|<span data-ttu-id="52ce4-117">Każdej sprawy składa się z zakresu (od a do) i działania (jednostka).</span><span class="sxs-lookup"><span data-stu-id="52ce4-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="52ce4-118">Wyrażenie jest obliczane i porównywana zakresów.</span><span class="sxs-lookup"><span data-stu-id="52ce4-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="52ce4-119">Jeśli wynikiem wyrażenia jest spoza zakresu przypadków, odpowiadające mu działanie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="52ce4-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="52ce4-120">Domyślny</span><span class="sxs-lookup"><span data-stu-id="52ce4-120">Default</span></span>|<span data-ttu-id="52ce4-121">Działanie, które jest wykonywane, gdy w żadnym przypadku nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="52ce4-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="52ce4-122">Jeśli wartość `null`, nie podjęto żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="52ce4-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="52ce4-123">Klasa CaseRange</span><span class="sxs-lookup"><span data-stu-id="52ce4-123">CaseRange Class</span></span>  
 <span data-ttu-id="52ce4-124">`CaseRange` Klasa reprezentuje zakresem w ramach `SwitchRange` działania.</span><span class="sxs-lookup"><span data-stu-id="52ce4-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="52ce4-125">Każde wystąpienie `CaseRange` zawiera zakres (składający się z `From` i `To`) i `Body` działanie, które jest zaplanowane, jeśli wyrażenie w `SwitchRange` jest obliczane w zakresie.</span><span class="sxs-lookup"><span data-stu-id="52ce4-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="52ce4-126">Poniższy przykład kodu jest definicja `CaseRange` klasy.</span><span class="sxs-lookup"><span data-stu-id="52ce4-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="52ce4-127">Zarówno `SwitchRange` i `CaseRange` klasy, które są zdefiniowane w próbce są klas ogólnych, które mogą pracować z dowolnego typu, który implementuje `IComparable`, takiej jak <xref:System.Activities.Statements.Switch%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="52ce4-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="52ce4-128">Przykładowe zastosowanie</span><span class="sxs-lookup"><span data-stu-id="52ce4-128">Sample Usage</span></span>  
 <span data-ttu-id="52ce4-129">Poniższy przykład kodu pokazuje sposób użycia `SwitchRange` działania.</span><span class="sxs-lookup"><span data-stu-id="52ce4-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="52ce4-130">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="52ce4-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="52ce4-131">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania SwitchRange.sln.</span><span class="sxs-lookup"><span data-stu-id="52ce4-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="52ce4-132">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="52ce4-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="52ce4-133">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="52ce4-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52ce4-134">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="52ce4-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52ce4-135">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="52ce4-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52ce4-136">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="52ce4-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52ce4-137">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="52ce4-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`