---
title: "Usługa routera odnajdywania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 66ff9d760ee59ef7a08f38826437b29077bc68d5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-router-service"></a><span data-ttu-id="152ae-102">Usługa routera odnajdywania</span><span class="sxs-lookup"><span data-stu-id="152ae-102">Discovery Router Service</span></span>
<span data-ttu-id="152ae-103">W tym przykładzie przedstawiono sposób przekazywania komunikatów odnajdywania do innego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="152ae-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="152ae-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="152ae-104">Demonstrates</span></span>  
 <span data-ttu-id="152ae-105">Routing odnajdywania</span><span class="sxs-lookup"><span data-stu-id="152ae-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="152ae-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="152ae-106">Discussion</span></span>  
 <span data-ttu-id="152ae-107">Routing odnajdywania jest przydatne w sytuacji, w którym potrzebuje usługi przy użyciu serwera proxy klienta i serwera proxy nie rozpoznaje takiej usługi, ale zna innego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="152ae-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="152ae-108">Ten serwer proxy można przekazywać pakiet odnajdywania z klienta do drugiego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="152ae-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="152ae-109">Drugi serwer proxy można wyszukać usługę i zwracać odpowiedzi do klienta oryginalnym.</span><span class="sxs-lookup"><span data-stu-id="152ae-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="152ae-110">W tym przykładzie klient wysyła komunikat do odnajdywania składnik routingu.</span><span class="sxs-lookup"><span data-stu-id="152ae-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="152ae-111">Ten komunikat jest wysyłane do określonego punktu końcowego na routerze odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="152ae-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="152ae-112">Router następnie przesyła komunikat do UDP multiemisji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="152ae-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="152ae-113">Wiadomości sondy trafia do multiemisji punktu końcowego i usługa Nasłuchiwanie multiemisji UDP się, że adres odpowiada routera odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="152ae-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="152ae-114">Router odnajdywania zbiera odpowiedzi i wysyła je z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="152ae-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="152ae-115">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="152ae-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="152ae-116">Tworzenie przykładowej.</span><span class="sxs-lookup"><span data-stu-id="152ae-116">Build the sample.</span></span>  
  
2.  <span data-ttu-id="152ae-117">Uruchom plik wykonywalny DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="152ae-117">Run the DiscoveryRouter executable.</span></span>  
  
3.  <span data-ttu-id="152ae-118">Uruchom plik wykonywalny usługi z katalogu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="152ae-118">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="152ae-119">Uruchom plik wykonywalny klienta.</span><span class="sxs-lookup"><span data-stu-id="152ae-119">Run the client executable.</span></span> <span data-ttu-id="152ae-120">Należy pamiętać, że klient lokalizuje usługę.</span><span class="sxs-lookup"><span data-stu-id="152ae-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="152ae-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="152ae-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="152ae-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="152ae-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="152ae-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="152ae-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="152ae-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="152ae-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
