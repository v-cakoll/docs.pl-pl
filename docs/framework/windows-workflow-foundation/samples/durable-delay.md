---
title: "Trwałe opóźnienia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b8afc9de0369a440ba9aa7cdacc4a43066ec2ff
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="durable-delay"></a><span data-ttu-id="8b098-102">Trwałe opóźnienia</span><span class="sxs-lookup"><span data-stu-id="8b098-102">Durable Delay</span></span>
<span data-ttu-id="8b098-103">W tym przykładzie przedstawiono sposób użycia trwałe opóźnienia, czyli opóźnienie będzie się powtarzał przepływu pracy na urządzeniu trwałe podczas opóźnienie.</span><span class="sxs-lookup"><span data-stu-id="8b098-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="8b098-104">Przykładowy przepływ pracy zawiera dwa komunikaty do konsoli, oddzielonych opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="8b098-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="8b098-105">Po wyzwoleniu opóźnienie przepływu pracy jest zwalniany i oczekuje na 5 sekund w magazynie wystąpień przepływu pracy przed ładowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8b098-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="8b098-106">Szczegóły przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8b098-106">Workflow Details</span></span>  
 <span data-ttu-id="8b098-107">Hosta usługi przepływu pracy obsługuje przepływu pracy i wystąpienia przepływu pracy przez ładowanie i zwalnianie nimi zarządza.</span><span class="sxs-lookup"><span data-stu-id="8b098-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="8b098-108">Aby uruchomić wystąpienie definicji przepływu pracy, próbki ustawia serwer proxy, który wysyła komunikat do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="8b098-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="8b098-109"><xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Właściwość jest ustawiona na `true`, włączenie go w celu utworzenia nowego wystąpienia przepływu pracy po otrzymaniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8b098-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="8b098-110">Poniższa lista zawiera szczegóły dotyczące konfiguracji przez hosta usługi przepływu pracy podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="8b098-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="8b098-111">Tworzy hosta usługi przy użyciu adresu (adresem http://localhost: 8080/klienta).</span><span class="sxs-lookup"><span data-stu-id="8b098-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="8b098-112">Tworzy punkt końcowy w celu umożliwienia komunikacji z hosta usługi <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="8b098-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="8b098-113">Skonfigurowanie magazynu wystąpienia SQL.</span><span class="sxs-lookup"><span data-stu-id="8b098-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="8b098-114">Dodaje zachowanie wystąpienia zwolnienie określa warunki, w których hosta usługi przepływu pracy należy zwolnić wystąpienia przepływu pracy w magazynie trwałości SQL.</span><span class="sxs-lookup"><span data-stu-id="8b098-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="8b098-115">Dla tego przykładu zwalnia wystąpienie natychmiast po przepływu pracy przechodzi bezczynności (po wyzwoleniu opóźnienia).</span><span class="sxs-lookup"><span data-stu-id="8b098-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="8b098-116">Tworzy serwera proxy, który wysyła komunikat do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="8b098-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8b098-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="8b098-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="8b098-118">Konfigurowanie bazy danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="8b098-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="8b098-119">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8b098-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="8b098-120">Przejdź do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] katalogu (C:\Windows\Microsoft.NET\Framework\v4. X\\).</span><span class="sxs-lookup"><span data-stu-id="8b098-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="8b098-121">Edytuj plik WorkflowManagementService.exe.config i dodaj następujące parametry połączenia w <`database`> elementu.</span><span class="sxs-lookup"><span data-stu-id="8b098-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="8b098-122">Przejdź do katalogu DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="8b098-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="8b098-123">Uruchom Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="8b098-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="8b098-124">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] przy użyciu podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikony, jak i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="8b098-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="8b098-125">Otwórz plik rozwiązania Delay.sln.</span><span class="sxs-lookup"><span data-stu-id="8b098-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="8b098-126">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8b098-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="8b098-127">Naciśnij klawisze CTRL + F5, aby uruchomić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8b098-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="8b098-128">Aby odinstalować tego przykładu</span><span class="sxs-lookup"><span data-stu-id="8b098-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="8b098-129">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8b098-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="8b098-130">Przejdź do katalogu DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="8b098-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="8b098-131">Uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="8b098-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8b098-132">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8b098-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8b098-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8b098-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8b098-134">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="8b098-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b098-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b098-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`