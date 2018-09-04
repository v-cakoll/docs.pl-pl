---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 181910db3f1dd6da892f6ae2ddcbf7bd5859ff17
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525424"
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="7a87d-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="7a87d-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="7a87d-103">Ten przykład pokazuje, jak wstawianie niestandardowych metadanych XML metadanych odnajdywania dla punktu końcowego wykrywalny udostępnianych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="7a87d-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="7a87d-104">Przykład następnie pokazano, jak wyszukać usługę klienta i wyodrębniania danych z tego niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="7a87d-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="7a87d-105">W tym przykładzie składa się z dwóch projektów, usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="7a87d-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="7a87d-106">Usługa</span><span class="sxs-lookup"><span data-stu-id="7a87d-106">Service</span></span>  
 <span data-ttu-id="7a87d-107">W `main` metody przykład pokazuje, że obiekt typu <xref:System.Xml.Linq.XElement> jest wypełniana przy użyciu żądane pola i jest dodawany do <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7a87d-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="7a87d-108">To <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> zostanie dodany do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7a87d-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="7a87d-109">Po odnalezieniu tego punktu końcowego metadanych odnajdywania zawiera danych niestandardowych, który został dodany tutaj.</span><span class="sxs-lookup"><span data-stu-id="7a87d-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="7a87d-110">Klient</span><span class="sxs-lookup"><span data-stu-id="7a87d-110">Client</span></span>  
 <span data-ttu-id="7a87d-111">Przedstawia przykładowe <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody wywoływane na <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span><span class="sxs-lookup"><span data-stu-id="7a87d-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="7a87d-112">Wartość wynikowa <xref:System.ServiceModel.Discovery.FindResponse> następnie zostaje przesłane zapytanie dla elementów XML odpowiednie i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="7a87d-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="7a87d-113">Elementy te są następnie drukowane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a87d-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7a87d-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="7a87d-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="7a87d-115">Załaduj projekt rozwiązanie w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="7a87d-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="7a87d-116">Pierwsze uruchomienie aplikacji usługi generowane w \service\bin\debug [katalog podstawowy rozwiązania] i następnie uruchom aplikację klienta, wygenerowane w \Client\bin\debug [katalog podstawowy rozwiązania]</span><span class="sxs-lookup"><span data-stu-id="7a87d-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="7a87d-117">Należy pamiętać, że usługa przejściu do trybu online klienta lokalizuje usługę i wyświetla metadane, opublikowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7a87d-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7a87d-118">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7a87d-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7a87d-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7a87d-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7a87d-120">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="7a87d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a87d-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7a87d-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="7a87d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a87d-122">See Also</span></span>
