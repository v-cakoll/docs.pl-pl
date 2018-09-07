---
title: Komunikacji asynchronicznej
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e85f7efb0de1326ceb5091c305b20f34809eab57
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047090"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="2495d-102">Komunikacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="2495d-102">Asynchronous Communication</span></span>
<span data-ttu-id="2495d-103">Niniejszy przykład pokazuje, jak komunikacja między dwoma różnymi usługami Windows Workflow Foundation (WF) są wykonywane asynchronicznie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="2495d-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2495d-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="2495d-104">Demonstrates</span></span>  
 <span data-ttu-id="2495d-105">Komunikacji asynchronicznej między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="2495d-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2495d-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="2495d-106">Discussion</span></span>  
 <span data-ttu-id="2495d-107">Ten przykład pokazuje, jak komunikacja między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacje są wykonywane asynchronicznie przy użyciu działań dotyczących komunikatów dostarczane przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2495d-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="2495d-108">W tym przykładzie składa się z następujących trzech projektach.</span><span class="sxs-lookup"><span data-stu-id="2495d-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="2495d-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="2495d-109">CreditCheckService</span></span>  
 <span data-ttu-id="2495d-110">Ta usługa odbiera wynik środki konkretnej osoby lub wartość elementu można uzyskać i następnie decyduje, czy kredytu znajduje się z osobą.</span><span class="sxs-lookup"><span data-stu-id="2495d-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="2495d-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="2495d-111">RentalApprovalService</span></span>  
 <span data-ttu-id="2495d-112">Ta usługa odbiera aplikacji z osoba będąca wymagające niektóre środki.</span><span class="sxs-lookup"><span data-stu-id="2495d-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="2495d-113">Ta usługa komunikuje asynchronicznie `CreditCheckService` zdecydować, czy wniosku o kredyt jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2495d-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="2495d-114">Klient</span><span class="sxs-lookup"><span data-stu-id="2495d-114">Client</span></span>  
 <span data-ttu-id="2495d-115">Klient komunikuje się synchronicznie przy użyciu `RentalApprovalService` wiedzieć, czy jest zatwierdzony środków.</span><span class="sxs-lookup"><span data-stu-id="2495d-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2495d-116">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="2495d-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2495d-117">Kliknij prawym przyciskiem myszy **AsynchronousCommunication** rozwiązań i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2495d-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2495d-118">W **wspólne właściwości**, wybierz opcję **projekt startowy**i wybierz **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="2495d-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="2495d-119">Przenieś **RentalApprovalService** na pierwszą pozycję na liście, a następnie **CreditCheckService**, a następnie **klienta**.</span><span class="sxs-lookup"><span data-stu-id="2495d-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="2495d-120">Ustaw **Start** akcję na wszystkich trzech projektach.</span><span class="sxs-lookup"><span data-stu-id="2495d-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="2495d-121">Kliknij przycisk **OK**, i naciśnij klawisz F5, aby uruchomić próbki.</span><span class="sxs-lookup"><span data-stu-id="2495d-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2495d-122">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2495d-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2495d-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2495d-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2495d-124">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2495d-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2495d-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2495d-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
