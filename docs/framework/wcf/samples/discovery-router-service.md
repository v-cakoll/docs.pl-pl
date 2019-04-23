---
title: Usługa routera odnajdywania
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 166f6b9d1055e36f987e6b9a81fe69dc8bd548b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980567"
---
# <a name="discovery-router-service"></a><span data-ttu-id="8b577-102">Usługa routera odnajdywania</span><span class="sxs-lookup"><span data-stu-id="8b577-102">Discovery Router Service</span></span>
<span data-ttu-id="8b577-103">W tym przykładzie przedstawiono sposób przekazywania komunikatów odnajdywania do innego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8b577-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8b577-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="8b577-104">Demonstrates</span></span>  
 <span data-ttu-id="8b577-105">Wykrywanie routingu</span><span class="sxs-lookup"><span data-stu-id="8b577-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8b577-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="8b577-106">Discussion</span></span>  
 <span data-ttu-id="8b577-107">Odnajdywanie routing jest przydatne w sytuacji, w której klient szuka usługi przy użyciu serwera proxy i serwer proxy nie rozpoznaje taką usługę, ale zna innego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="8b577-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="8b577-108">Ten serwer proxy można przekazać pakiet odnajdywania z tego klienta, do drugiego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="8b577-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="8b577-109">Drugi serwer proxy można wyszukać usługę i zwracania odpowiedzi do klienta, oryginalnym.</span><span class="sxs-lookup"><span data-stu-id="8b577-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="8b577-110">W tym przykładzie klient wysyła komunikat do składnika routingu odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="8b577-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="8b577-111">Ta wiadomość jest wysyłana do określonego punktu końcowego na routerze odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="8b577-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="8b577-112">Następnie router przesyła wiadomość na UDP multiemisji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8b577-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="8b577-113">Wiadomości sondy trafia do multiemisji punktu końcowego i usługa nasłuchuje na multiemisji UDP, że adres odpowiada routera odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="8b577-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="8b577-114">Router odnajdywanie umożliwia zbieranie informacji o odpowiedzi i wysyła je z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="8b577-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8b577-115">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="8b577-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8b577-116">Skompiluj przykład.</span><span class="sxs-lookup"><span data-stu-id="8b577-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="8b577-117">Uruchom plik wykonywalny DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="8b577-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="8b577-118">Uruchomić pliku wykonywalnego usługi z katalogu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b577-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="8b577-119">Uruchom ten plik.</span><span class="sxs-lookup"><span data-stu-id="8b577-119">Run the client executable.</span></span> <span data-ttu-id="8b577-120">Należy pamiętać, że klient zlokalizuje usługi.</span><span class="sxs-lookup"><span data-stu-id="8b577-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8b577-121">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8b577-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8b577-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8b577-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8b577-123">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="8b577-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b577-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b577-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
