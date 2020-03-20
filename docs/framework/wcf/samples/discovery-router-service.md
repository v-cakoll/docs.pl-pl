---
title: Usługa routera odnajdywania
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 149dd69cdd1972465f4b7cb48ab657492d3f21d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183725"
---
# <a name="discovery-router-service"></a><span data-ttu-id="c6f33-102">Usługa routera odnajdywania</span><span class="sxs-lookup"><span data-stu-id="c6f33-102">Discovery Router Service</span></span>
<span data-ttu-id="c6f33-103">W tym przykładzie pokazano, jak przekazywać dalej komunikaty odnajdywania do innego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c6f33-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c6f33-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="c6f33-104">Demonstrates</span></span>  
 <span data-ttu-id="c6f33-105">Routing odnajdowania</span><span class="sxs-lookup"><span data-stu-id="c6f33-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c6f33-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="c6f33-106">Discussion</span></span>  
 <span data-ttu-id="c6f33-107">Routing odnajdowania jest przydatne w scenariuszu, w którym klient szuka usługi przy użyciu serwera proxy i serwer proxy nie jest świadomy takiej usługi, ale zna inny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="c6f33-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="c6f33-108">Ten serwer proxy może przesłać dalej pakiet odnajdywania z tego klienta do drugiego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="c6f33-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="c6f33-109">Drugi serwer proxy może wyszukać usługę i zwrócić odpowiedzi do oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="c6f33-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="c6f33-110">W tym przykładzie klient wysyła wiadomość do składnika routingu odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="c6f33-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="c6f33-111">Ten komunikat jest wysyłany do określonego punktu końcowego na routerze odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="c6f33-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="c6f33-112">Następnie router przekazuje wiadomość do punktu końcowego multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="c6f33-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="c6f33-113">Komunikat sondy wychodzi do punktu końcowego multiemisji, a usługa nasłuchująca na adresie multiemisji UDP odpowiada na ten router odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="c6f33-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="c6f33-114">Router odnajdywania zbiera odpowiedzi i wysyła je z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="c6f33-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c6f33-115">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c6f33-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c6f33-116">Skompiluj przykład.</span><span class="sxs-lookup"><span data-stu-id="c6f33-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="c6f33-117">Uruchom plik wykonywalny DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="c6f33-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="c6f33-118">Uruchom plik wykonywalny usługi z katalogu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c6f33-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="c6f33-119">Uruchom plik wykonywalny klienta.</span><span class="sxs-lookup"><span data-stu-id="c6f33-119">Run the client executable.</span></span> <span data-ttu-id="c6f33-120">Należy zauważyć, że klient lokalizuje usługę.</span><span class="sxs-lookup"><span data-stu-id="c6f33-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c6f33-121">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c6f33-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6f33-122">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c6f33-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c6f33-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c6f33-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6f33-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c6f33-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
