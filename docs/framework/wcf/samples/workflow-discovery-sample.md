---
title: Odnajdywanie przepływu pracy — przykład
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 56437607d6e940b59698641ad3305c525d8f7095
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045395"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="366fc-102">Odnajdywanie przepływu pracy — przykład</span><span class="sxs-lookup"><span data-stu-id="366fc-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="366fc-103">Ten przykład pokazuje, jak umożliwić odnajdywanie usługi przepływu pracy oraz sposób tworzenia niestandardowego działania kodu, które wyszukuje określoną usługę.</span><span class="sxs-lookup"><span data-stu-id="366fc-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="366fc-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="366fc-104">Demonstrates</span></span>  
 <span data-ttu-id="366fc-105">Odnajdywanie — wyszukiwanie działań i przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="366fc-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="366fc-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="366fc-106">Discussion</span></span>  
 <span data-ttu-id="366fc-107">W pierwszej części przykładu usługa przepływu pracy jest wykrywalna przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="366fc-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="366fc-108">Konfiguracji można także użyć do odpowiedniego zastosowania usługi przy użyciu niestandardowych metadanych (takich jak zakresy).</span><span class="sxs-lookup"><span data-stu-id="366fc-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="366fc-109">Na kliencie przykład używa niestandardowego działania kodu, które używa odnajdywania w celu wyszukania usługi zgodnej z konkretną umową.</span><span class="sxs-lookup"><span data-stu-id="366fc-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="366fc-110">Działanie Code generuje identyfikator URI, który jest później używany przez działanie wysyłania.</span><span class="sxs-lookup"><span data-stu-id="366fc-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="366fc-111">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="366fc-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="366fc-112">Ten przykład korzysta z punktów końcowych HTTP, które muszą mieć odpowiednie listy ACL adresów URL do uruchomienia (zobacz [Konfigurowanie protokołu HTTP i https](https://go.microsoft.com/fwlink/?LinkId=70353) , aby uzyskać szczegółowe informacje).</span><span class="sxs-lookup"><span data-stu-id="366fc-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="366fc-113">Wykonanie następującego polecenia w wierszu polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="366fc-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="366fc-114">Zastąp domenę i nazwę użytkownika dla następujących argumentów, jeśli powłoka nie zrozumie formatu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="366fc-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="366fc-115">**netsh http Add urlacl URL =http://+:8000/ użytkownik =% domena%\\ % username%**</span><span class="sxs-lookup"><span data-stu-id="366fc-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="366fc-116">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="366fc-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="366fc-117">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="366fc-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="366fc-118">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="366fc-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="366fc-119">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="366fc-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
