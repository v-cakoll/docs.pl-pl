---
title: Odnajdywanie przepływu pracy — przykład
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198026"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="ee53f-102">Odnajdywanie przepływu pracy — przykład</span><span class="sxs-lookup"><span data-stu-id="ee53f-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="ee53f-103">Niniejszy przykład pokazuje, jak stał się wykrywalny usługi przepływu pracy i jak tworzyć działania kodu niestandardowego, wyszukująca określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="ee53f-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ee53f-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="ee53f-104">Demonstrates</span></span>  
 <span data-ttu-id="ee53f-105">Działanie funkcji Znajdź odnajdywania i użycie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ee53f-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ee53f-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="ee53f-106">Discussion</span></span>  
 <span data-ttu-id="ee53f-107">W pierwszej części przykładu, jest wykrywalne usługi przepływu pracy przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ee53f-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="ee53f-108">Konfiguracja może również Zastosuj usługę odpowiednio przy użyciu niestandardowych metadanych (np. zakresy).</span><span class="sxs-lookup"><span data-stu-id="ee53f-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="ee53f-109">Na komputerze klienckim w przykładzie użyto działania kodu niestandardowego, które używa odnajdywania do wyszukiwania usługi dopasowania określonej umowy.</span><span class="sxs-lookup"><span data-stu-id="ee53f-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="ee53f-110">Identyfikator URI, który jest później używany przez działanie wysyłania wyjściem działania kodu.</span><span class="sxs-lookup"><span data-stu-id="ee53f-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee53f-111">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="ee53f-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ee53f-112">W tym przykładzie użyto punktów końcowych HTTP, które musi mieć odpowiednie ACL adresu URL do uruchomienia (zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Aby uzyskać szczegółowe informacje).</span><span class="sxs-lookup"><span data-stu-id="ee53f-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="ee53f-113">Wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, należy dodać odpowiednie listy ACL.</span><span class="sxs-lookup"><span data-stu-id="ee53f-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="ee53f-114">Zastąp Twoja domena i nazwa użytkownika o wprowadzenie następujących argumentów, jeśli powłoki nie rozpoznaje formatu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ee53f-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="ee53f-115">**netsh http Dodaj adres url urlacl =http://+:8000/ użytkownika domeny % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="ee53f-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee53f-116">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ee53f-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee53f-117">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ee53f-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee53f-118">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="ee53f-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee53f-119">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ee53f-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
