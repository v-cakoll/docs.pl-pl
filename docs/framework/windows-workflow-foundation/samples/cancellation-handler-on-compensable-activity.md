---
title: "Obsługa anulowania w działaniu Compensable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 64d594711a805f75e1d76e59579032b0dc73dc93
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="7f8cc-102">Obsługa anulowania w działaniu Compensable</span><span class="sxs-lookup"><span data-stu-id="7f8cc-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="7f8cc-103">W tym przykładzie przedstawiono użycie obsługi anulowania z <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="7f8cc-104">Ten przykład zawiera dwa scenariusze, które przedstawiają sposób używania <xref:System.Activities.Statements.CompensableActivity> anulowania. Pierwszy scenariusz zawiera compensable działania głównego, który zawiera trzy podrzędne działania compensable.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="7f8cc-105">Dwa działania podrzędne zakończyć ich jednostki działanie pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="7f8cc-106">Po uruchomieniu trzeci treści działania podrzędne napotkał wyjątek, który jest obsługiwany przez anulowanie trzeci przetwarzania działania, po czym zostanie wywołany anulowania działania głównego.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="7f8cc-107">Logikę działania głównego, w tym przykładzie jest odpowiednio innych działań podrzędnych dwóch wykonanych wcześniej.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
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
  
 <span data-ttu-id="7f8cc-108">Drugi scenariusz zademonstrowano wykonywanie <xref:System.Activities.Statements.TryCatch> równolegle z <xref:System.Activities.Statements.Delay>, która kończy się przed <xref:System.Activities.Statements.TryCatch> gałęzi.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="7f8cc-109">Warunek zakończenia ma ustawioną wartość `true` po zakończeniu pierwszej gałęzi, co powoduje innej gałęzi do anulowania.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7f8cc-110">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="7f8cc-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7f8cc-111">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz CompensationCancellation.sln.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="7f8cc-112">Tworzyć przykładowy kod, naciskając klawisze CTRL + SHIFT + B lub wybierz polecenie "Kompiluj rozwiązanie" z menu kompilacji...</span><span class="sxs-lookup"><span data-stu-id="7f8cc-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="7f8cc-113">Uruchom próbkę naciskając klawisz F5 lub wybierz polecenie "Rozpocznij debugowanie" z menu Debugowanie.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="7f8cc-114">Może również naciśnij klawisze Ctrl + F5 lub wybierz opcję "Uruchom bez debugowania" z menu Debugowanie.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f8cc-115">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7f8cc-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7f8cc-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7f8cc-117">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7f8cc-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7f8cc-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`