---
title: Komunikacja asynchroniczna
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142879"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="e22e1-102">Komunikacja asynchroniczna</span><span class="sxs-lookup"><span data-stu-id="e22e1-102">Asynchronous Communication</span></span>
<span data-ttu-id="e22e1-103">W tym przykładzie pokazano, jak komunikacja między dwoma różnymi usługami Windows Workflow Foundation (WF) jest domyślnie wykonywana asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="e22e1-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e22e1-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="e22e1-104">Demonstrates</span></span>  
 <span data-ttu-id="e22e1-105">Komunikacja asynchronizacjowa między usługami. [!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e22e1-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e22e1-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="e22e1-106">Discussion</span></span>  
 <span data-ttu-id="e22e1-107">W tym przykładzie [!INCLUDE[wf1](../../../../includes/wf1-md.md)] pokazano, jak komunikacja między aplikacjami odbywa się asynchronicznie przy użyciu działań obsługi wiadomości dostarczonych przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e22e1-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="e22e1-108">Ten przykład składa się z następujących trzech projektów.</span><span class="sxs-lookup"><span data-stu-id="e22e1-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="e22e1-109">Usługa CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="e22e1-109">CreditCheckService</span></span>  
 <span data-ttu-id="e22e1-110">Usługa ta otrzymuje ocenę kredytową konkretnej osoby lub wartość przedmiotu do nabycia, a następnie decyduje, czy kredyt jest przyznawany osobie.</span><span class="sxs-lookup"><span data-stu-id="e22e1-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="e22e1-111">RentalApprovalService (Usługa zdatna do wypożyczania)</span><span class="sxs-lookup"><span data-stu-id="e22e1-111">RentalApprovalService</span></span>  
 <span data-ttu-id="e22e1-112">Usługa ta otrzymuje wniosek od osoby, która potrzebuje jakiegoś kredytu.</span><span class="sxs-lookup"><span data-stu-id="e22e1-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="e22e1-113">Ta usługa komunikuje się asynchronicznie `CreditCheckService` z, aby zdecydować, czy wniosek o kredyt jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e22e1-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="e22e1-114">Klient</span><span class="sxs-lookup"><span data-stu-id="e22e1-114">Client</span></span>  
 <span data-ttu-id="e22e1-115">Klient komunikuje się synchronicznie `RentalApprovalService` z, aby wiedzieć, czy kredyt został zatwierdzony.</span><span class="sxs-lookup"><span data-stu-id="e22e1-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e22e1-116">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="e22e1-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e22e1-117">Kliknij prawym przyciskiem myszy rozwiązanie **komunikacji asynchroniiowej** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e22e1-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="e22e1-118">W **obszarze Właściwości wspólne**wybierz pozycję Projekt **uruchamiania**i wybierz pozycję Wiele projektów **uruchamiania**.</span><span class="sxs-lookup"><span data-stu-id="e22e1-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="e22e1-119">Przenieś **RentalApprovalService** na pierwszą pozycję na liście, a następnie **CreditCheckService**, a następnie **klient**.</span><span class="sxs-lookup"><span data-stu-id="e22e1-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="e22e1-120">Ustaw akcję **Start** dla wszystkich trzech projektów.</span><span class="sxs-lookup"><span data-stu-id="e22e1-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="e22e1-121">Kliknij **przycisk OK**i naciśnij klawisz F5, aby uruchomić próbkę.</span><span class="sxs-lookup"><span data-stu-id="e22e1-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e22e1-122">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e22e1-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e22e1-123">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="e22e1-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e22e1-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e22e1-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e22e1-125">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e22e1-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
