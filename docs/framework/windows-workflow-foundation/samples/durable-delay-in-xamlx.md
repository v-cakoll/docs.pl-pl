---
title: Trwałe opóźnienie w XAMLX
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1eef9211c67d190ecb5f329c481fa2e3d1763353
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594111"
---
# <a name="durable-delay-in-xamlx"></a><span data-ttu-id="0fb9f-102">Trwałe opóźnienie w XAMLX</span><span class="sxs-lookup"><span data-stu-id="0fb9f-102">Durable Delay in XAMLX</span></span>
<span data-ttu-id="0fb9f-103">Ten przykład pokazuje sposób użycia trwałe opóźnienie z opóźnieniem, która utrzymuje przepływu pracy na trwałe urządzenie podczas opóźnienie.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0fb9f-104">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0fb9f-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0fb9f-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0fb9f-106">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0fb9f-107">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a><span data-ttu-id="0fb9f-108">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="0fb9f-108">Discussion</span></span>  
 <span data-ttu-id="0fb9f-109">Przykładowy przepływ pracy zawiera dwa komunikaty do pliku lokalnego, oddzielonych opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-109">The sample workflow contains two messages to a local file that are separated by a delay.</span></span> <span data-ttu-id="0fb9f-110">Po wyzwoleniu opóźnienie przepływu pracy jest zwalniana i oczekuje na 5 sekund magazynu wystąpień przepływu pracy ładowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-110">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
 <span data-ttu-id="0fb9f-111">Plik .xamlx jest usługi przepływu pracy, który znajduje się w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-111">The .xamlx file is a workflow service that is hosted in Visual Studio.</span></span> <span data-ttu-id="0fb9f-112">Visual Studio używa Cassini, który używa usługi przepływu pracy do hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-112">Visual Studio uses Cassini that uses a workflow service host to host the workflow.</span></span>  
  
 <span data-ttu-id="0fb9f-113">Oprócz hostowania przepływu pracy, hosta usługi przepływu pracy zarządza wystąpienia przepływu pracy, ładowanie i zwalnianie je.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-113">In addition to hosting the workflow, the workflow service host manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="0fb9f-114">Aby uruchomić wystąpienie programu Windows Workflow Foundation (WF) definicji (na hosta usługi przepływu pracy), należy ustawić klienta, która wysyła komunikat do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-114">To start an instance of the Windows Workflow Foundation (WF) definition (on the workflow service host), set a client that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="0fb9f-115">To <xref:System.ServiceModel.Activities.Receive> ma jego <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> właściwością `true`, dzięki czemu może utworzyć nowe wystąpienie przepływu pracy, po odebraniu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-115">This <xref:System.ServiceModel.Activities.Receive> has its <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="0fb9f-116">Podczas inicjowania zachowanie wystąpienia zwolnienie jest dodawany do pliku konfiguracji, który określa hosta usługi przepływu pracy w ramach której powinna zwolnić wystąpienia w trwałości sklepie najbardziej (baza danych).</span><span class="sxs-lookup"><span data-stu-id="0fb9f-116">During initialization, an unload instance behavior is added to the configuration file that specifies to the workflow service host under which it should unload an instance to the persistence store (database).</span></span> <span data-ttu-id="0fb9f-117">W tym przykładzie zwalnia wystąpienie natychmiast po zakończeniu przepływu pracy przechodzi bezczynności (w przypadku wyzwolenia opóźnienie).</span><span class="sxs-lookup"><span data-stu-id="0fb9f-117">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0fb9f-118">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="0fb9f-118">To use this sample</span></span>  
  
1.  <span data-ttu-id="0fb9f-119">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="0fb9f-120">Przejdź do folderu DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-120">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="0fb9f-121">Uruchom plik Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-121">Run Setup.cmd.</span></span>  
  
4.  <span data-ttu-id="0fb9f-122">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako administrator.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-122">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an administrator.</span></span>  
  
5.  <span data-ttu-id="0fb9f-123">Otwórz plik rozwiązania DurableDelayXamlx.sln.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-123">Open the DurableDelayXamlx.sln solution file.</span></span>  
  
6.  <span data-ttu-id="0fb9f-124">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-124">In **Solution Explorer**, right-click the solution and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="0fb9f-125">Wybierz **wiele projektów startowych** i ustaw oba projekty **Start**.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-125">Select **Multiple startup projects** and set both projects to **Start**.</span></span>  
  
8.  <span data-ttu-id="0fb9f-126">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
9. <span data-ttu-id="0fb9f-127">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-127">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="0fb9f-128">Aby odinstalować tego przykładu</span><span class="sxs-lookup"><span data-stu-id="0fb9f-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="0fb9f-129">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="0fb9f-130">Przejdź do folderu DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-130">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="0fb9f-131">Uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0fb9f-132">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0fb9f-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0fb9f-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0fb9f-134">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0fb9f-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0fb9f-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
