---
title: "Odnajdywanie usługi działającej w trybie unikatowego identyfikatora URI nasłuchiwania — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 82f47fb0b789e41c332ebae2cfeaeb350ff0fddd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="1551a-102">Odnajdywanie usługi działającej w trybie unikatowego identyfikatora URI nasłuchiwania — przykład</span><span class="sxs-lookup"><span data-stu-id="1551a-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="1551a-103">W tym przykładzie pokazano, jak odnajdywanie usługi, która ma <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> ustawioną właściwość <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span><span class="sxs-lookup"><span data-stu-id="1551a-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="1551a-104">Gdy <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Description.ListenUriMode.Unique>, zapewniony ListenUri być unikatowy, ustawiając portu unikatowa lub ścieżka, które mają być unikatowe przez dołączenie identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="1551a-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="1551a-105">Funkcje usługi</span><span class="sxs-lookup"><span data-stu-id="1551a-105">Features on the Service</span></span>  
 <span data-ttu-id="1551a-106"><xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Ma ustawioną wartość właściwości <xref:System.ServiceModel.Description.ListenUriMode.Unique> dla punktu końcowego TCP.</span><span class="sxs-lookup"><span data-stu-id="1551a-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="1551a-107">Usługa jest przeprowadzane wykrywalny przez <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1551a-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="1551a-108">Funkcje na kliencie</span><span class="sxs-lookup"><span data-stu-id="1551a-108">Features on the Client</span></span>  
 <span data-ttu-id="1551a-109">Ten klient nawiąże połączenie z usługą przy użyciu prawidłowego `Via.Uri` przy użyciu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1551a-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="1551a-110"><xref:System.ServiceModel.Discovery.FindResponse> Która jest zwracana z metody następnie zostanie zapytany o Określa, czy zawiera prawidłową <xref:System.ServiceModel.Endpoint.ListenUri%2A> i czy jest ona inna niż `Address.Uri`.</span><span class="sxs-lookup"><span data-stu-id="1551a-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="1551a-111">Odpowiednie informacje są następnie przekazywane do `InvokeCalculatorService` metody.</span><span class="sxs-lookup"><span data-stu-id="1551a-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="1551a-112">W `InvokeCalculatorService` metody, <xref:System.ServiceModel.Endpoint.ListenUri%2A> przekazany przez wywołującego, a następnie `ClientViaBehavior` z prawidłowym `Via.Uri` zostanie dodany do punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="1551a-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="1551a-113">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="1551a-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="1551a-114">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz UniqueListenUriMode.sln.</span><span class="sxs-lookup"><span data-stu-id="1551a-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="1551a-115">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="1551a-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1551a-116">Uruchamianie aplikacji usługi, która jest generowana w folderze \service\bin\debug [katalogu podstawowego rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="1551a-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="1551a-117">Uruchom aplikację klienta, generowany w folderze \Client\bin\debug [katalogu podstawowego rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="1551a-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="1551a-118">Klient lokalizuje uruchomionej usługi i zapisuje konsoli metadanych opublikowanych przez punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="1551a-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1551a-119">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1551a-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1551a-120">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="1551a-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1551a-121">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="1551a-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1551a-122">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1551a-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="1551a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1551a-123">See Also</span></span>
