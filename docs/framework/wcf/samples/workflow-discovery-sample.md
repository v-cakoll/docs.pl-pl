---
title: Odnajdywanie przepływu pracy — przykład
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: eafe031b71836eae8de5ce15cd669459c866e89f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094764"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="5c70d-102">Odnajdywanie przepływu pracy — przykład</span><span class="sxs-lookup"><span data-stu-id="5c70d-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="5c70d-103">Ten przykład pokazuje, jak umożliwić odnajdywanie usługi przepływu pracy oraz sposób tworzenia niestandardowego działania kodu, które wyszukuje określoną usługę.</span><span class="sxs-lookup"><span data-stu-id="5c70d-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5c70d-104">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="5c70d-104">Demonstrates</span></span>  
 <span data-ttu-id="5c70d-105">Odnajdywanie — wyszukiwanie działań i przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="5c70d-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5c70d-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="5c70d-106">Discussion</span></span>  
 <span data-ttu-id="5c70d-107">W pierwszej części przykładu usługa przepływu pracy jest wykrywalna przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5c70d-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="5c70d-108">Konfiguracji można także użyć do odpowiedniego zastosowania usługi przy użyciu niestandardowych metadanych (takich jak zakresy).</span><span class="sxs-lookup"><span data-stu-id="5c70d-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="5c70d-109">Na kliencie przykład używa niestandardowego działania kodu, które używa odnajdywania w celu wyszukania usługi zgodnej z konkretną umową.</span><span class="sxs-lookup"><span data-stu-id="5c70d-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="5c70d-110">Działanie Code generuje identyfikator URI, który jest później używany przez działanie wysyłania.</span><span class="sxs-lookup"><span data-stu-id="5c70d-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c70d-111">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="5c70d-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5c70d-112">Ten przykład korzysta z punktów końcowych HTTP, które muszą mieć odpowiednie listy ACL adresów URL do uruchomienia (zobacz [Konfigurowanie protokołu HTTP i https](../feature-details/configuring-http-and-https.md) , aby uzyskać szczegółowe informacje).</span><span class="sxs-lookup"><span data-stu-id="5c70d-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="5c70d-113">Wykonanie następującego polecenia w wierszu polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="5c70d-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="5c70d-114">Jeśli powłoka nie rozpoznaje formatu zmiennej, należy zastąpić domenę i nazwę użytkownika dla następujących argumentów.</span><span class="sxs-lookup"><span data-stu-id="5c70d-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
     <span data-ttu-id="5c70d-115">**netsh http Add urlacl URL =http://+:8000/ użytkownik =% domena%\\% UserName%**</span><span class="sxs-lookup"><span data-stu-id="5c70d-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c70d-116">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5c70d-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5c70d-117">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="5c70d-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5c70d-118">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c70d-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c70d-119">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5c70d-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
