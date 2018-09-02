---
title: Procedura obsługi anulowania w działaniu kompensacyjnym
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: 2f32d10e22be7fdd1e84229a214409df06efa918
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442710"
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="e8a98-102">Procedura obsługi anulowania w działaniu kompensacyjnym</span><span class="sxs-lookup"><span data-stu-id="e8a98-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="e8a98-103">Niniejszy przykład pokazuje użycie obsługi anulowania w <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="e8a98-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="e8a98-104">Ten przykład zawiera dwa scenariusze, które pokazują użycie <xref:System.Activities.Statements.CompensableActivity> anulowania. Pierwszy scenariusz zawiera działanie kompensacyjne głównego, zawierający trzy czynności kompensacyjne podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e8a98-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="e8a98-105">Dwa działania podrzędne zakończyć ich jednostki działanie pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e8a98-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="e8a98-106">Po uruchomieniu trzeci treści działania podrzędne napotka wyjątek, który jest obsługiwany przez anulowanie trzeci przetwarzania działania, po upływie którego jest wyzwalane anulowania działania głównego.</span><span class="sxs-lookup"><span data-stu-id="e8a98-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="e8a98-107">Logikę działania głównego, w tym przykładzie jest kompensacji inne działania podrzędne dwóch wykonanych wcześniej.</span><span class="sxs-lookup"><span data-stu-id="e8a98-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 <span data-ttu-id="e8a98-108">Drugi scenariusz pokazuje wykonywania <xref:System.Activities.Statements.TryCatch> równolegle z <xref:System.Activities.Statements.Delay>, który zakończy się przed <xref:System.Activities.Statements.TryCatch> gałęzi.</span><span class="sxs-lookup"><span data-stu-id="e8a98-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="e8a98-109">Warunek zakończenia jest ustawiony na `true` po zakończeniu pierwszej gałęzi, powodując innej gałęzi zostaną anulowane.</span><span class="sxs-lookup"><span data-stu-id="e8a98-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8a98-110">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="e8a98-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e8a98-111">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz CompensationCancellation.sln.</span><span class="sxs-lookup"><span data-stu-id="e8a98-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="e8a98-112">Stworzyć próbkę, naciskając klawisze CTRL + SHIFT + B lub menu kompilacja wybierz polecenie "Kompiluj rozwiązanie"...</span><span class="sxs-lookup"><span data-stu-id="e8a98-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="e8a98-113">Uruchom aplikację przykładową, naciskając klawisz F5 lub wybierz pozycję "Uruchom debugowanie" z menu Debugowanie.</span><span class="sxs-lookup"><span data-stu-id="e8a98-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="e8a98-114">Może też naciśnij klawisze Ctrl + F5 lub wybierz pozycję "Rozpocznij bez debugowania" z menu Debugowanie.</span><span class="sxs-lookup"><span data-stu-id="e8a98-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8a98-115">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e8a98-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8a98-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e8a98-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e8a98-117">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e8a98-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8a98-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e8a98-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`