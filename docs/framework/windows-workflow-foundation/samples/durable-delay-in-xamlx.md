---
title: "Trwałe opóźnienia w XAMLX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a52f3444b51f91d7076d6bc5a580d6efb6e26eb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="durable-delay-in-xamlx"></a><span data-ttu-id="e8151-102">Trwałe opóźnienia w XAMLX</span><span class="sxs-lookup"><span data-stu-id="e8151-102">Durable Delay in XAMLX</span></span>
<span data-ttu-id="e8151-103">W tym przykładzie przedstawiono sposób użycia trwałe opóźnienia, czyli opóźnienie będzie się powtarzał przepływu pracy na urządzeniu trwałe podczas opóźnienie.</span><span class="sxs-lookup"><span data-stu-id="e8151-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8151-104">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e8151-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8151-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e8151-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e8151-106">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e8151-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8151-107">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e8151-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a><span data-ttu-id="e8151-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e8151-108">Discussion</span></span>  
 <span data-ttu-id="e8151-109">Przykładowy przepływ pracy zawiera dwa komunikaty do pliku lokalnego, oddzielonych opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="e8151-109">The sample workflow contains two messages to a local file that are separated by a delay.</span></span> <span data-ttu-id="e8151-110">Po wyzwoleniu opóźnienie przepływu pracy jest zwalniany i oczekuje na 5 sekund w magazynie wystąpień przepływu pracy przed ładowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8151-110">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
 <span data-ttu-id="e8151-111">Plik .xamlx jest usługi przepływu pracy, który znajduje się w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8151-111">The .xamlx file is a workflow service that is hosted in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="e8151-112">używa Cassini, który korzysta z hosta do hosta usługi przepływu pracy, przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="e8151-112"> uses Cassini that uses a workflow service host to host the workflow.</span></span>  
  
 <span data-ttu-id="e8151-113">Oprócz obsługuje przepływ pracy, hosta usługi przepływu pracy zarządza wystąpienia przepływu pracy, ładowanie i zwalnianie je.</span><span class="sxs-lookup"><span data-stu-id="e8151-113">In addition to hosting the workflow, the workflow service host manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="e8151-114">Aby uruchomić wystąpienie [!INCLUDE[wf](../../../../includes/wf-md.md)] definicji (na hosta usługi przepływu pracy), Ustaw klienta, który wysyła komunikat do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e8151-114">To start an instance of the [!INCLUDE[wf](../../../../includes/wf-md.md)] definition (on the workflow service host), set a client that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="e8151-115">To <xref:System.ServiceModel.Activities.Receive> ma jego <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> ustawioną właściwość `true`, włączenie go w celu utworzenia nowego wystąpienia przepływu pracy po otrzymaniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e8151-115">This <xref:System.ServiceModel.Activities.Receive> has its <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="e8151-116">Podczas inicjowania zwolnienie zachowanie wystąpienia są dodawane do pliku konfiguracji, która określa hosta usługi przepływu pracy, pod którym powinna zwolnić wystąpienie w magazynie trwałości (baza danych).</span><span class="sxs-lookup"><span data-stu-id="e8151-116">During initialization, an unload instance behavior is added to the configuration file that specifies to the workflow service host under which it should unload an instance to the persistence store (database).</span></span> <span data-ttu-id="e8151-117">Dla tego przykładu zwalnia wystąpienie natychmiast po przepływu pracy przechodzi bezczynności (po wyzwoleniu opóźnienia).</span><span class="sxs-lookup"><span data-stu-id="e8151-117">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e8151-118">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="e8151-118">To use this sample</span></span>  
  
1.  <span data-ttu-id="e8151-119">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e8151-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="e8151-120">Przejdź do folderu DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="e8151-120">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="e8151-121">Uruchom Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="e8151-121">Run Setup.cmd.</span></span>  
  
4.  <span data-ttu-id="e8151-122">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako administrator.</span><span class="sxs-lookup"><span data-stu-id="e8151-122">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an administrator.</span></span>  
  
5.  <span data-ttu-id="e8151-123">Otwórz plik rozwiązania DurableDelayXamlx.sln.</span><span class="sxs-lookup"><span data-stu-id="e8151-123">Open the DurableDelayXamlx.sln solution file.</span></span>  
  
6.  <span data-ttu-id="e8151-124">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e8151-124">In **Solution Explorer**, right-click the solution and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="e8151-125">Wybierz **wiele projektów startowych** ustawiono oba projekty **Start**.</span><span class="sxs-lookup"><span data-stu-id="e8151-125">Select **Multiple startup projects** and set both projects to **Start**.</span></span>  
  
8.  <span data-ttu-id="e8151-126">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="e8151-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
9. <span data-ttu-id="e8151-127">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="e8151-127">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="e8151-128">Aby odinstalować tego przykładu</span><span class="sxs-lookup"><span data-stu-id="e8151-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="e8151-129">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e8151-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="e8151-130">Przejdź do folderu DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="e8151-130">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="e8151-131">Uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="e8151-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8151-132">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e8151-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8151-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e8151-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e8151-134">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e8151-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8151-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e8151-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
