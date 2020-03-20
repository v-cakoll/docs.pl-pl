---
title: Odnajdywanie przepływu pracy — przykład
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143489"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="956b8-102">Odnajdywanie przepływu pracy — przykład</span><span class="sxs-lookup"><span data-stu-id="956b8-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="956b8-103">W tym przykładzie pokazano, jak sprawić, aby usługa przepływu pracy była wykrywalna i jak tworzyć niestandardowe działanie kodu, które wyszukuje określoną usługę.</span><span class="sxs-lookup"><span data-stu-id="956b8-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="956b8-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="956b8-104">Demonstrates</span></span>  
 <span data-ttu-id="956b8-105">Odnajdowanie Znajdowanie aktywności i użycia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="956b8-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="956b8-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="956b8-106">Discussion</span></span>  
 <span data-ttu-id="956b8-107">W pierwszej części próbki usługa przepływu pracy jest wykrywalna przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="956b8-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="956b8-108">Konfiguracja może również służyć do stosowania usługi odpowiednio z metadanych niestandardowych (takich jak zakresy).</span><span class="sxs-lookup"><span data-stu-id="956b8-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="956b8-109">Na kliencie przykład używa działania kodu niestandardowego, który używa odnajdywania do wyszukiwania usługi pasującej do określonego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="956b8-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="956b8-110">Działanie kodu wyprowadza identyfikator URI, który jest później używany przez działanie wysyłania.</span><span class="sxs-lookup"><span data-stu-id="956b8-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="956b8-111">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="956b8-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="956b8-112">W tym przykładzie użyto punktów końcowych HTTP, które muszą mieć odpowiednie listy ACL URL do uruchomienia (zobacz [Konfigurowanie protokołu HTTP i HTTPS,](../feature-details/configuring-http-and-https.md) aby uzyskać szczegółowe informacje).</span><span class="sxs-lookup"><span data-stu-id="956b8-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="956b8-113">Wykonywanie następującego polecenia w wierszu polecenia z podwyższonym poziomem uprawnień należy dodać odpowiednie listy ACL.</span><span class="sxs-lookup"><span data-stu-id="956b8-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="956b8-114">Jeśli powłoka nie rozumie formatu zmiennej, zastąp domenę i nazwę użytkownika następującymi argumentami.</span><span class="sxs-lookup"><span data-stu-id="956b8-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
     <span data-ttu-id="956b8-115">**netsh http dodaj urlacl url=http://+:8000/ \\użytkownik=%DOMENA% %UserName%**</span><span class="sxs-lookup"><span data-stu-id="956b8-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="956b8-116">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="956b8-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="956b8-117">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="956b8-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="956b8-118">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="956b8-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="956b8-119">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="956b8-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
