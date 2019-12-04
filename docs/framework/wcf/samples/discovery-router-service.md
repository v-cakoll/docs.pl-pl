---
title: Usługa routera odnajdywania
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 09309b23d2a3cc672811c2f617e6fb81a2b4e021
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712290"
---
# <a name="discovery-router-service"></a><span data-ttu-id="2b052-102">Usługa routera odnajdywania</span><span class="sxs-lookup"><span data-stu-id="2b052-102">Discovery Router Service</span></span>
<span data-ttu-id="2b052-103">Ten przykład pokazuje, jak przekazywać komunikaty wykrywania do innego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2b052-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2b052-104">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="2b052-104">Demonstrates</span></span>  
 <span data-ttu-id="2b052-105">Routing odnajdowania</span><span class="sxs-lookup"><span data-stu-id="2b052-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2b052-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="2b052-106">Discussion</span></span>  
 <span data-ttu-id="2b052-107">Routing odnajdowania jest przydatny w scenariuszu, w którym klient szuka usługi przy użyciu serwera proxy, a serwer proxy nie wie o takiej usłudze, ale wie o innym serwerze proxy.</span><span class="sxs-lookup"><span data-stu-id="2b052-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="2b052-108">Ten serwer proxy może przekazywać pakiet odnajdywania z tego klienta do drugiego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="2b052-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="2b052-109">Drugi serwer proxy może wyszukać usługę i zwrócić odpowiedzi do oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="2b052-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="2b052-110">W tym przykładzie klient wysyła komunikat do składnika routingu odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="2b052-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="2b052-111">Ta wiadomość jest wysyłana do określonego punktu końcowego routera odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="2b052-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="2b052-112">Następnie router przekazuje komunikat do punktu końcowego multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="2b052-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="2b052-113">Komunikat sondy przechodzi do punktu końcowego multiemisji, a usługa nasłuchuje na adresie multiemisji UDP odpowiada na ten router odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="2b052-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="2b052-114">Router odnajdowania zbiera odpowiedzi i wysyła je z powrotem do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="2b052-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2b052-115">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="2b052-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2b052-116">Kompiluj przykład.</span><span class="sxs-lookup"><span data-stu-id="2b052-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="2b052-117">Uruchom plik wykonywalny DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="2b052-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="2b052-118">Uruchom plik wykonywalny usługi z katalogu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2b052-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="2b052-119">Uruchom plik wykonywalny klienta.</span><span class="sxs-lookup"><span data-stu-id="2b052-119">Run the client executable.</span></span> <span data-ttu-id="2b052-120">Należy zauważyć, że klient lokalizuje usługę.</span><span class="sxs-lookup"><span data-stu-id="2b052-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2b052-121">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2b052-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2b052-122">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="2b052-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2b052-123">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b052-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2b052-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2b052-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
