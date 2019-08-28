---
title: Komunikacja asynchroniczna
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: b5cf788ce4587dacb5a7642e25cb1b5b1e6f3e3c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044365"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="bf647-102">Komunikacja asynchroniczna</span><span class="sxs-lookup"><span data-stu-id="bf647-102">Asynchronous Communication</span></span>
<span data-ttu-id="bf647-103">W tym przykładzie pokazano, jak komunikacja między dwiema różnymi usługami Windows Workflow Foundation (WF) odbywa się domyślnie asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="bf647-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bf647-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="bf647-104">Demonstrates</span></span>  
 <span data-ttu-id="bf647-105">Asynchroniczna komunikacja [!INCLUDE[wf1](../../../../includes/wf1-md.md)] między usługami.</span><span class="sxs-lookup"><span data-stu-id="bf647-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="bf647-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="bf647-106">Discussion</span></span>  
 <span data-ttu-id="bf647-107">Ten przykład pokazuje, jak komunikacja między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacjami odbywa się asynchronicznie przy użyciu działań dotyczących komunikatów dostarczonych przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf647-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="bf647-108">Ten przykład składa się z trzech następujących projektów.</span><span class="sxs-lookup"><span data-stu-id="bf647-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="bf647-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="bf647-109">CreditCheckService</span></span>  
 <span data-ttu-id="bf647-110">Ta usługa otrzymuje wynik kredytowy określonej osoby lub wartość elementu do pobrania, a następnie decyduje o tym, czy kredyt został udzielony.</span><span class="sxs-lookup"><span data-stu-id="bf647-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="bf647-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="bf647-111">RentalApprovalService</span></span>  
 <span data-ttu-id="bf647-112">Ta usługa otrzymuje aplikację od osoby, która jest w trakcie pewnego kredytu.</span><span class="sxs-lookup"><span data-stu-id="bf647-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="bf647-113">Ta usługa komunikuje się asynchronicznie `CreditCheckService` z, aby określić, czy aplikacja kredytowa jest ważna.</span><span class="sxs-lookup"><span data-stu-id="bf647-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="bf647-114">Klient</span><span class="sxs-lookup"><span data-stu-id="bf647-114">Client</span></span>  
 <span data-ttu-id="bf647-115">Klient komunikuje się synchronicznie z informacją o tym, `RentalApprovalService` czy środki zostały zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="bf647-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf647-116">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="bf647-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bf647-117">Kliknij prawym przyciskiem myszy rozwiązanie **AsynchronousCommunication** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="bf647-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="bf647-118">W obszarze **wspólne właściwości**wybierz pozycję **projekt startowy**, a następnie wybierz opcję **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="bf647-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="bf647-119">Przenieś **RentalApprovalService** do pierwszej pozycji na liście, a następnie **CreditCheckService**, po którym następuje **Klient**.</span><span class="sxs-lookup"><span data-stu-id="bf647-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="bf647-120">Ustaw akcję **startową** dla wszystkich trzech projektów.</span><span class="sxs-lookup"><span data-stu-id="bf647-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="bf647-121">Kliknij przycisk **OK**, a następnie naciśnij klawisz F5, aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="bf647-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf647-122">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bf647-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bf647-123">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="bf647-123">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="bf647-124">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="bf647-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf647-125">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bf647-125">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
