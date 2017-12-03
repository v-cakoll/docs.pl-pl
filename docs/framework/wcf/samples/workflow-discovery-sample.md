---
title: "Odnajdywanie przepływu pracy — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bba400a4476ffd2589af1d5e7d3e0ca5661102f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="d7e78-102">Odnajdywanie przepływu pracy — przykład</span><span class="sxs-lookup"><span data-stu-id="d7e78-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="d7e78-103">W przykładzie pokazano sposób stał się wykrywalny usługi przepływu pracy i tworzenia działania niestandardowego kodu, która wyszukuje określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="d7e78-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d7e78-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="d7e78-104">Demonstrates</span></span>  
 <span data-ttu-id="d7e78-105">Działanie funkcji odnajdywania Znajdź i użycie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d7e78-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d7e78-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="d7e78-106">Discussion</span></span>  
 <span data-ttu-id="d7e78-107">W pierwszej części próbki jest tworzone wykrywalny usługi przepływu pracy za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d7e78-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="d7e78-108">Konfiguracja można również zastosować usługa odpowiednio o niestandardowych metadanych (np. zakresy).</span><span class="sxs-lookup"><span data-stu-id="d7e78-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="d7e78-109">Na komputerze klienckim w przykładzie użyto działania kodu niestandardowego, używający odnajdywania do wyszukiwania dopasowania określonej kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="d7e78-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="d7e78-110">Działanie kodu generuje identyfikator URI, który jest później używany przez działanie wysyłania.</span><span class="sxs-lookup"><span data-stu-id="d7e78-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d7e78-111">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="d7e78-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d7e78-112">W przykładzie użyto punktów końcowych HTTP, które wymaga prawidłowego adresu URL listy kontroli dostępu do uruchomienia (zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje).</span><span class="sxs-lookup"><span data-stu-id="d7e78-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="d7e78-113">Wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, należy dodać odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="d7e78-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="d7e78-114">Zastąp użytkownika domena i nazwa użytkownika dla następujących argumentów Jeśli powłoki nie rozpoznaje formatu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d7e78-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="d7e78-115">**netsh http Dodaj adres url urlacl = http: / / +: 8000 / użytkownika domeny % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="d7e78-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7e78-116">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d7e78-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d7e78-117">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d7e78-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d7e78-118">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d7e78-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d7e78-119">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d7e78-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
