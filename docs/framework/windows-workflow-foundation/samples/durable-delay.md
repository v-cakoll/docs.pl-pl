---
title: Trwałe opóźnienie
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 2a7692e28d60232913ae5d11a90025e59664c0e5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507636"
---
# <a name="durable-delay"></a><span data-ttu-id="fc414-102">Trwałe opóźnienie</span><span class="sxs-lookup"><span data-stu-id="fc414-102">Durable Delay</span></span>
<span data-ttu-id="fc414-103">Ten przykład pokazuje sposób użycia trwałe opóźnienie z opóźnieniem, która utrzymuje przepływu pracy na trwałe urządzenie podczas opóźnienie.</span><span class="sxs-lookup"><span data-stu-id="fc414-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="fc414-104">Przykładowy przepływ pracy zawiera dwa komunikaty wyjściowe do konsoli, które są oddzielone opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="fc414-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="fc414-105">Po wyzwoleniu opóźnienie przepływu pracy jest zwalniana i oczekuje na 5 sekund magazynu wystąpień przepływu pracy ładowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fc414-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="fc414-106">Szczegóły przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fc414-106">Workflow Details</span></span>  
 <span data-ttu-id="fc414-107">Hosta usługi przepływu pracy obsługuje przepływu pracy i wystąpienia przepływu pracy, ładowanie i zwalnianie nimi zarządza.</span><span class="sxs-lookup"><span data-stu-id="fc414-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="fc414-108">Aby uruchomić wystąpienie definicji przepływu pracy, próbki zestawów serwera proxy, który wysyła wiadomość do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="fc414-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="fc414-109"><xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Właściwość jest ustawiona na `true`, dzięki czemu może utworzyć nowe wystąpienie przepływu pracy, po odebraniu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fc414-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="fc414-110">Poniżej przedstawiono szczegółową listę konfiguracji przez hosta usługi przepływu pracy podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="fc414-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="fc414-111">Tworzy hosta usługi przy użyciu adresu (http://localhost:8080/Client).</span><span class="sxs-lookup"><span data-stu-id="fc414-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="fc414-112">Tworzy punkt końcowy na hoście usługi, aby umożliwić komunikację z <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="fc414-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="fc414-113">Konfiguruje magazyn wystąpienia programu SQL.</span><span class="sxs-lookup"><span data-stu-id="fc414-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="fc414-114">Dodaje zachowanie wystąpienia unload, który określa warunki, w których hosta usługi przepływu pracy należy zwolnić wystąpienia przepływu pracy w magazynie stanów trwałych programu SQL.</span><span class="sxs-lookup"><span data-stu-id="fc414-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="fc414-115">W tym przykładzie zwalnia wystąpienie natychmiast po zakończeniu przepływu pracy przechodzi bezczynności (w przypadku wyzwolenia opóźnienie).</span><span class="sxs-lookup"><span data-stu-id="fc414-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="fc414-116">Tworzy serwer proxy, który wysyła wiadomość do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="fc414-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fc414-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="fc414-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="fc414-118">Konfigurowanie bazy danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="fc414-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="fc414-119">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fc414-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="fc414-120">Przejdź do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] katalogu (C:\Windows\Microsoft.NET\Framework\v4. X\\).</span><span class="sxs-lookup"><span data-stu-id="fc414-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="fc414-121">Edytuj plik WorkflowManagementService.exe.config i dodaj następujące parametry połączenia w ramach <`database`> element.</span><span class="sxs-lookup"><span data-stu-id="fc414-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="fc414-122">Przejdź do katalogu DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="fc414-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="fc414-123">Uruchom plik Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="fc414-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="fc414-124">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] przy użyciu podniesionych uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonę i wybierając polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="fc414-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="fc414-125">Otwórz plik rozwiązania Delay.sln.</span><span class="sxs-lookup"><span data-stu-id="fc414-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="fc414-126">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="fc414-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="fc414-127">Naciśnij klawisze CTRL + F5, aby uruchomić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="fc414-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="fc414-128">Aby odinstalować tego przykładu</span><span class="sxs-lookup"><span data-stu-id="fc414-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="fc414-129">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fc414-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="fc414-130">Przejdź do katalogu DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="fc414-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="fc414-131">Uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="fc414-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc414-132">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fc414-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc414-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fc414-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fc414-134">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="fc414-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc414-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fc414-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`