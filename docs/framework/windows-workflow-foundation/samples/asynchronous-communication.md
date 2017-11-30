---
title: Komunikacji asynchronicznej
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1b9435342d73fc5cb292ee72781362146604ce9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-communication"></a><span data-ttu-id="9d655-102">Komunikacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="9d655-102">Asynchronous Communication</span></span>
<span data-ttu-id="9d655-103">W tym przykładzie pokazano sposób komunikacji między dwóch różnych [!INCLUDE[wf](../../../../includes/wf-md.md)] usług jest wykonywane asynchronicznie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9d655-103">This sample demonstrates how the communication between two different [!INCLUDE[wf](../../../../includes/wf-md.md)] services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9d655-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="9d655-104">Demonstrates</span></span>  
 <span data-ttu-id="9d655-105">Asynchroniczną komunikację między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="9d655-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9d655-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="9d655-106">Discussion</span></span>  
 <span data-ttu-id="9d655-107">W tym przykładzie pokazano sposób komunikacji między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacji jest wykonywane asynchronicznie za pomocą działania obsługi komunikatów dostarczonych przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d655-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="9d655-108">W tym przykładzie składa się z następujących trzech projektach.</span><span class="sxs-lookup"><span data-stu-id="9d655-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="9d655-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="9d655-109">CreditCheckService</span></span>  
 <span data-ttu-id="9d655-110">Ta usługa odbiera wynik środki danej osoby lub wartość elementu uzyskanie, a następnie decyduje o tym, czy środków znajduje się z osobą.</span><span class="sxs-lookup"><span data-stu-id="9d655-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="9d655-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="9d655-111">RentalApprovalService</span></span>  
 <span data-ttu-id="9d655-112">Ta usługa odbiera aplikacji od osoby, która wymaga certyfikat.</span><span class="sxs-lookup"><span data-stu-id="9d655-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="9d655-113">Ta usługa komunikuje asynchronicznie `CreditCheckService` zdecydować, czy aplikacja kredytowej jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="9d655-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="9d655-114">Klient</span><span class="sxs-lookup"><span data-stu-id="9d655-114">Client</span></span>  
 <span data-ttu-id="9d655-115">Klient komunikuje się synchronicznie z `RentalApprovalService` wiedzieć, czy jest zatwierdzona środków.</span><span class="sxs-lookup"><span data-stu-id="9d655-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9d655-116">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="9d655-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9d655-117">Kliknij prawym przyciskiem myszy **AsynchronousCommunication** rozwiązania i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9d655-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="9d655-118">W **wspólne właściwości**, wybierz pozycję **projekt startowy**i wybierz **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="9d655-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="9d655-119">Przenieś **RentalApprovalService** na pierwszą pozycję na liście, a następnie **CreditCheckService**, a następnie **klienta**.</span><span class="sxs-lookup"><span data-stu-id="9d655-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="9d655-120">Ustaw **Start** akcji we wszystkich trzech projektach.</span><span class="sxs-lookup"><span data-stu-id="9d655-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="9d655-121">Kliknij przycisk **OK**, i naciśnij klawisz F5, aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="9d655-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d655-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9d655-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9d655-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9d655-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9d655-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="9d655-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d655-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9d655-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
