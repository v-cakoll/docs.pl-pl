---
title: Emulowanie fundamentalne za pewien czas działania
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 37c64c2b8dc03d58f9c2802edef644fe4888e87d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514716"
---
# <a name="emulating-breaking-in-a-while-activity"></a><span data-ttu-id="a5bef-102">Emulowanie fundamentalne za pewien czas działania</span><span class="sxs-lookup"><span data-stu-id="a5bef-102">Emulating breaking in a While activity</span></span>
<span data-ttu-id="a5bef-103">W przykładzie pokazano sposób podziału pętli mechanizmu z następujących działań: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, i <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="a5bef-103">This sample demonstrates how to break the looping mechanism of the following activities: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
 <span data-ttu-id="a5bef-104">Jest to przydatne, ponieważ Windows Workflow Foundation (WF) nie zawiera żadnych działań, aby przerwać wykonywanie tych pętle.</span><span class="sxs-lookup"><span data-stu-id="a5bef-104">This is useful because Windows Workflow Foundation (WF) does not include any activity to break the execution of these loops.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="a5bef-105">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="a5bef-105">Scenario</span></span>  
 <span data-ttu-id="a5bef-106">Przykład znajduje pierwszy niezawodnej dostawcy z listy dostawców (wystąpienia `Vendor` klasy).</span><span class="sxs-lookup"><span data-stu-id="a5bef-106">The sample finds the first reliable vendor from a list of vendors (instances of the `Vendor` class).</span></span> <span data-ttu-id="a5bef-107">Każdy dostawca ma `ID`, `Name` i określająca sposób niezawodny dostawca jest wartość liczbowa niezawodności.</span><span class="sxs-lookup"><span data-stu-id="a5bef-107">Each vendor has an `ID`, a `Name` and a numeric reliability value that determines how dependable the vendor is.</span></span> <span data-ttu-id="a5bef-108">Przykład tworzy niestandardowe działanie o nazwie `FindReliableVendor` który odbiera dwóch parametrów wejściowych (lista dostawców i wartość minimalna niezawodność) i zwraca pierwszy dostawca listy, która spełnia podane kryteria.</span><span class="sxs-lookup"><span data-stu-id="a5bef-108">The sample creates a custom activity called `FindReliableVendor` that receives two input parameters (a list of vendors and a minimum reliability value) and returns the first vendor of the list that matches the supplied criteria.</span></span>  
  
## <a name="breaking-a-loop"></a><span data-ttu-id="a5bef-109">Fundamentalne pętli</span><span class="sxs-lookup"><span data-stu-id="a5bef-109">Breaking a Loop</span></span>  
 <span data-ttu-id="a5bef-110">Windows Workflow Foundation (WF) nie zawiera działania, aby przerwać pętlę.</span><span class="sxs-lookup"><span data-stu-id="a5bef-110">Windows Workflow Foundation (WF) does not include an activity to break a loop.</span></span> <span data-ttu-id="a5bef-111">Przykładowy kod, który umożliwia zrealizowanie fundamentalne pętli przy użyciu <xref:System.Activities.Statements.If> działania i kilku zmiennych.</span><span class="sxs-lookup"><span data-stu-id="a5bef-111">The code sample accomplishes breaking a loop by using an <xref:System.Activities.Statements.If> activity and several variables.</span></span> <span data-ttu-id="a5bef-112">W przykładzie <xref:System.Activities.Statements.While> działanie zostało przerwane po `reliableVendor` zmiennej jest przypisywana wartość innych niż `null`.</span><span class="sxs-lookup"><span data-stu-id="a5bef-112">In the sample, the <xref:System.Activities.Statements.While> activity is broken once the `reliableVendor` variable is assigned a value other than `null`.</span></span>  
  
 <span data-ttu-id="a5bef-113">W poniższym przykładzie kodu pokazano, jak próbki dzieli chwilę pętli.</span><span class="sxs-lookup"><span data-stu-id="a5bef-113">The following code example demonstrates how the sample breaks a while loop.</span></span>  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a5bef-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="a5bef-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="a5bef-115">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania EmulatingBreakInWhile.sln.</span><span class="sxs-lookup"><span data-stu-id="a5bef-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EmulatingBreakInWhile.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a5bef-116">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a5bef-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a5bef-117">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="a5bef-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a5bef-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a5bef-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a5bef-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a5bef-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a5bef-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a5bef-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5bef-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a5bef-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`