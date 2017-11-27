---
title: Niestandardowe kryteria znajdowania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d49661ff91477f2f53d180a10ae1c9b3b632461f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-find-criteria"></a><span data-ttu-id="56789-102">Niestandardowe kryteria znajdowania</span><span class="sxs-lookup"><span data-stu-id="56789-102">Custom Find Criteria</span></span>
<span data-ttu-id="56789-103">Przykładzie pokazano, jak utworzyć niestandardowy zakres dopasowania przy użyciu logiki i sposobu implementacji usługi odnajdywania niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="56789-103">This sample demonstrates how to create a custom scope match using logic and how to implement a custom discovery service.</span></span> <span data-ttu-id="56789-104">Klienci używają niestandardowy zakres funkcji dopasowywania uściślić i dalsze bazując funkcje Znajdź dostarczane przez system odnajdywania WCF.</span><span class="sxs-lookup"><span data-stu-id="56789-104">Clients use custom scope matching functionality to refine and further build on top of the system-provided find functionality of WCF Discovery.</span></span> <span data-ttu-id="56789-105">Scenariusz, które obejmuje ten przykład jest następujący:</span><span class="sxs-lookup"><span data-stu-id="56789-105">The scenario this sample covers is as follows:</span></span>  
  
1.  <span data-ttu-id="56789-106">Klient szuka usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="56789-106">A client is looking for a calculator service.</span></span>  
  
2.  <span data-ttu-id="56789-107">Aby uściślić wyszukiwanie, klient musi używać niestandardowego zakresu regułę dopasowania.</span><span class="sxs-lookup"><span data-stu-id="56789-107">To refine its search, the client must use a custom scope matching rule.</span></span>  
  
3.  <span data-ttu-id="56789-108">Zgodnie z regułą usługa odpowiada klientowi Jeśli punktu końcowego pasuje do żadnego z zakresów określonych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="56789-108">According to this rule, a service responds back to the client if its endpoint matches any of the scopes specified by the client.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="56789-109">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="56789-109">Demonstrates</span></span>  
  
-   <span data-ttu-id="56789-110">Tworzenie niestandardowych odnajdywania usługi.</span><span class="sxs-lookup"><span data-stu-id="56789-110">Creating a custom discovery service.</span></span>  
  
-   <span data-ttu-id="56789-111">Implementowanie dopasowanie niestandardowy zakres przez algorytm.</span><span class="sxs-lookup"><span data-stu-id="56789-111">Implementing a custom scope match by algorithm.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="56789-112">Omówienie</span><span class="sxs-lookup"><span data-stu-id="56789-112">Discussion</span></span>  
 <span data-ttu-id="56789-113">Dla typu "Lub" spełniających kryteria wyszukiwania klienta.</span><span class="sxs-lookup"><span data-stu-id="56789-113">The client is looking for "OR" type matching criteria.</span></span> <span data-ttu-id="56789-114">Usługa odpowiada ponownie, jeśli zakresy na jego punkty końcowe pasuje do żadnej z zakresów określonych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="56789-114">A service responds back if the scopes on its endpoints match any of the scopes provided by the client.</span></span> <span data-ttu-id="56789-115">W takim przypadku klient jest szuka usługi Kalkulator, które ma jakiekolwiek z zakresów na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="56789-115">In this case, the client is looking for a calculator service that has any of the scopes in the following list:</span></span>  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 <span data-ttu-id="56789-116">W tym celu klienta określa, że usługi do użycia niestandardowego zakresu regułę dopasowania przez przekazywanie dopasowanie niestandardowy zakres przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="56789-116">To accomplish this, the client directs services to use a custom scope matching rule by passing in a custom scope match by URI.</span></span> <span data-ttu-id="56789-117">W celu ułatwienia dopasowywania niestandardowy zakres, usługa musi używać usługi odnajdywania niestandardowych rozumie reguły dopasowania niestandardowy zakres, który implementuje skojarzonej logiki zgodnego.</span><span class="sxs-lookup"><span data-stu-id="56789-117">To facilitate the custom scope matching, the service must use a custom discovery service that understands the custom scope match rule and implements the associated matching logic.</span></span>  
  
 <span data-ttu-id="56789-118">W projekcie klienta Otwórz plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="56789-118">In the client project, open the Program.cs file.</span></span> <span data-ttu-id="56789-119">Należy pamiętać, że `ScopeMatchBy` pole `FindCriteria` obiektu ma ustawioną wartość określonego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="56789-119">Note that the `ScopeMatchBy` field of the `FindCriteria` object is set to a specific URI.</span></span> <span data-ttu-id="56789-120">Ten identyfikator jest wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="56789-120">This identifier is sent to the service.</span></span> <span data-ttu-id="56789-121">Jeśli usługa nie rozpoznaje tej reguły, ignoruje żądanie Znajdź klienta.</span><span class="sxs-lookup"><span data-stu-id="56789-121">If the service does not understand this rule, it ignores the client’s find request.</span></span>  
  
 <span data-ttu-id="56789-122">Otwórz projekt usługi.</span><span class="sxs-lookup"><span data-stu-id="56789-122">Open the service project.</span></span> <span data-ttu-id="56789-123">Trzy pliki są używane do implementowania usługi odnajdywania niestandardowe:</span><span class="sxs-lookup"><span data-stu-id="56789-123">Three files are used to implement the Custom Discovery Service:</span></span>  
  
1.  <span data-ttu-id="56789-124">**AsyncResult.cs**: jest to implementacja `AsyncResult` , co jest wymagane przez metody odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="56789-124">**AsyncResult.cs**: This is the implementation of the `AsyncResult` that is required by Discovery methods.</span></span>  
  
2.  <span data-ttu-id="56789-125">**CustomDiscoveryService.cs**: ten plik implementuje usługę odnajdywania niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="56789-125">**CustomDiscoveryService.cs**: This file implements the custom discovery service.</span></span> <span data-ttu-id="56789-126">Implementacja rozszerza <xref:System.ServiceModel.Discovery.DiscoveryService> klasy i zastępuje metody niezbędne.</span><span class="sxs-lookup"><span data-stu-id="56789-126">The implementation extends the <xref:System.ServiceModel.Discovery.DiscoveryService> class and overrides the necessary methods.</span></span> <span data-ttu-id="56789-127">Należy pamiętać, implementacja <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="56789-127">Note the implementation of the <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> method.</span></span> <span data-ttu-id="56789-128">Metoda sprawdza, czy dopasowanie niestandardowy zakres przez regułę został określony przez klienta.</span><span class="sxs-lookup"><span data-stu-id="56789-128">The method checks to see whether the custom scope match by rule was specified by the client.</span></span> <span data-ttu-id="56789-129">To jest tej samej niestandardowy identyfikator URI, który poprzednio określono klienta.</span><span class="sxs-lookup"><span data-stu-id="56789-129">This is the same custom URI that the client specified previously.</span></span> <span data-ttu-id="56789-130">Jeśli określono niestandardową regułę, implementujący logiki dopasowania "Lub" ścieżkę kodu jest zakończony.</span><span class="sxs-lookup"><span data-stu-id="56789-130">If the custom rule is specified, the code path that implements the "OR" match logic is followed.</span></span>  
  
     <span data-ttu-id="56789-131">Tej niestandardowej logiki przechodzi przez wszystkie zakresy na każdym z punktów końcowych, które w usłudze.</span><span class="sxs-lookup"><span data-stu-id="56789-131">This custom logic goes through all of the scopes on each of the endpoints that the service has.</span></span> <span data-ttu-id="56789-132">Jeśli żadnego punktu końcowego zakresy zgodny z żadną z zakresów dostarczonych przez klienta usługi odnajdywania dodaje tego punktu końcowego do odpowiedzi, który jest wysyłany do klienta.</span><span class="sxs-lookup"><span data-stu-id="56789-132">If any of the endpoint's scopes match any of the scopes provided by the client, the discovery service adds that endpoint to the response that is sent back to the client.</span></span>  
  
3.  <span data-ttu-id="56789-133">**CustomDiscoveryExtension.cs**: ostatni krok w przypadku implementowania usługi odnajdywania jest podłączenie tej implementacji niestandardowego odnajdywanie usługi hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="56789-133">**CustomDiscoveryExtension.cs**: The last step in implementing the discovery service is to connect this implementation of the custom discover service to the service host.</span></span> <span data-ttu-id="56789-134">Klasa pomocnika używany w tym miejscu jest `CustomDiscoveryExtension` klasy.</span><span class="sxs-lookup"><span data-stu-id="56789-134">The helper class used here is the `CustomDiscoveryExtension` class.</span></span> <span data-ttu-id="56789-135">Ta klasa rozszerza <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="56789-135">This class extends the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> class.</span></span> <span data-ttu-id="56789-136">Użytkownik musi przesłonić <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="56789-136">The user must override the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> method.</span></span> <span data-ttu-id="56789-137">W tym przypadku metoda zwraca wystąpienie usługi odnajdywania niestandardowego, który został utworzony przed.</span><span class="sxs-lookup"><span data-stu-id="56789-137">In this case, the method returns an instance of the custom discovery service that was created before.</span></span> <span data-ttu-id="56789-138">`PublishedEndpoints`jest <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zawierający wszystkie punkty końcowe aplikacji, które są dodawane do <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="56789-138">`PublishedEndpoints` is a <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> that contains all of the application endpoints that are added to the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="56789-139">Usługi odnajdywania niestandardowe używa go do wypełnienia listy wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="56789-139">The custom discovery service uses this to populate its internal list.</span></span> <span data-ttu-id="56789-140">Użytkownik może dodać inne metadane punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="56789-140">A user can to add other endpoint metadata as well.</span></span>  
  
 <span data-ttu-id="56789-141">Na koniec Otwórz plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="56789-141">Lastly, open Program.cs.</span></span> <span data-ttu-id="56789-142">Należy pamiętać, że zarówno <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i `CustomDiscoveryExtension` zostaną dodane do hosta.</span><span class="sxs-lookup"><span data-stu-id="56789-142">Note that both the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and `CustomDiscoveryExtension` are added to the host.</span></span> <span data-ttu-id="56789-143">Gdy odbywa się i host ma punkt końcowy służącym do odbierania wiadomości odnajdywania, aplikacja może korzystać z usługi odnajdywania niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="56789-143">Once this is done and the host has an endpoint over which to receive discovery messages, the application can use the custom discovery service.</span></span>  
  
 <span data-ttu-id="56789-144">Sprawdź, czy klient jest w stanie znaleźć usługi bez uprzedniego uzyskania informacji o jego adres.</span><span class="sxs-lookup"><span data-stu-id="56789-144">Observe that the client is able to find the service without knowing its address.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="56789-145">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="56789-145">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="56789-146">Otwórz rozwiązanie, które zawiera projekt.</span><span class="sxs-lookup"><span data-stu-id="56789-146">Open the solution that contains the project.</span></span>  
  
2.  <span data-ttu-id="56789-147">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="56789-147">Build the project.</span></span>  
  
3.  <span data-ttu-id="56789-148">Uruchom aplikację usługi.</span><span class="sxs-lookup"><span data-stu-id="56789-148">Run the service application.</span></span>  
  
4.  <span data-ttu-id="56789-149">Uruchom aplikację klienta.</span><span class="sxs-lookup"><span data-stu-id="56789-149">Run the client application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56789-150">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="56789-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="56789-151">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="56789-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="56789-152">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="56789-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="56789-153">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="56789-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
