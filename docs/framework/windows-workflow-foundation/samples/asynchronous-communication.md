---
title: Komunikacji asynchronicznej
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 9eafeab89aefb181ae016dc0219f9155d9bd2a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515163"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="b0653-102">Komunikacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="b0653-102">Asynchronous Communication</span></span>
<span data-ttu-id="b0653-103">W przykładzie pokazano, jak komunikację między dwóch różnych usług Windows Workflow Foundation (WF) jest wykonywane asynchronicznie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="b0653-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b0653-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="b0653-104">Demonstrates</span></span>  
 <span data-ttu-id="b0653-105">Asynchroniczną komunikację między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="b0653-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b0653-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b0653-106">Discussion</span></span>  
 <span data-ttu-id="b0653-107">W tym przykładzie pokazano sposób komunikacji między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacji jest wykonywane asynchronicznie za pomocą działania obsługi komunikatów dostarczonych przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0653-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="b0653-108">W tym przykładzie składa się z następujących trzech projektach.</span><span class="sxs-lookup"><span data-stu-id="b0653-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="b0653-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="b0653-109">CreditCheckService</span></span>  
 <span data-ttu-id="b0653-110">Ta usługa odbiera wynik środki danej osoby lub wartość elementu uzyskanie, a następnie decyduje o tym, czy środków znajduje się z osobą.</span><span class="sxs-lookup"><span data-stu-id="b0653-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="b0653-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="b0653-111">RentalApprovalService</span></span>  
 <span data-ttu-id="b0653-112">Ta usługa odbiera aplikacji od osoby, która wymaga certyfikat.</span><span class="sxs-lookup"><span data-stu-id="b0653-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="b0653-113">Ta usługa komunikuje asynchronicznie `CreditCheckService` zdecydować, czy aplikacja kredytowej jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b0653-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="b0653-114">Klient</span><span class="sxs-lookup"><span data-stu-id="b0653-114">Client</span></span>  
 <span data-ttu-id="b0653-115">Klient komunikuje się synchronicznie z `RentalApprovalService` wiedzieć, czy jest zatwierdzona środków.</span><span class="sxs-lookup"><span data-stu-id="b0653-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b0653-116">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="b0653-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b0653-117">Kliknij prawym przyciskiem myszy **AsynchronousCommunication** rozwiązania i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b0653-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b0653-118">W **wspólne właściwości**, wybierz pozycję **projekt startowy**i wybierz **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="b0653-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="b0653-119">Przenieś **RentalApprovalService** na pierwszą pozycję na liście, a następnie **CreditCheckService**, a następnie **klienta**.</span><span class="sxs-lookup"><span data-stu-id="b0653-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="b0653-120">Ustaw **Start** akcji we wszystkich trzech projektach.</span><span class="sxs-lookup"><span data-stu-id="b0653-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="b0653-121">Kliknij przycisk **OK**, i naciśnij klawisz F5, aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="b0653-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0653-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b0653-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b0653-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b0653-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b0653-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b0653-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0653-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b0653-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
