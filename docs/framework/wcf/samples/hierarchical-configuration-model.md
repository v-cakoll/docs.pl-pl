---
title: Hierarchiczny model konfiguracji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbcef9ebe1b4876e429da97b3e217dd32286e4d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="3b49d-102">Hierarchiczny model konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3b49d-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="3b49d-103">W tym przykładzie pokazano, jak wdrożyć hierarchia pliki konfiguracji dla usług.</span><span class="sxs-lookup"><span data-stu-id="3b49d-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="3b49d-104">Pokazuje też, jak powiązania zachowania usługi i zachowania punktu końcowego są dziedziczone z wyższego poziomu w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="3b49d-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="3b49d-105">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="3b49d-105">Sample details</span></span>  
 <span data-ttu-id="3b49d-106">Jedną z funkcji opracowanych dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] ulepszenia w hierarchiczny model konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3b49d-106">One of the features developed for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="3b49d-107">Przykładem modelu hierarchiczna konfiguracji może być zdefiniowana w pliku Machine.config -> Rootweb.config -> pliku Web.config. W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], tych powiązań i zachowania, które są zdefiniowane w górnym poziomów w hierarchii konfiguracji są dodawane do usługi z jawnym konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3b49d-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="3b49d-108">W tym przykładzie pokazano, jak możliwe jest uproszczenie konfiguracji usługi przez jednostki uzależnionej w elementach konfiguracji zdefiniowanych w komputerze lub na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b49d-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="3b49d-109">W tym przykładzie składa się z dziewięciu usług, określonych w trzech poziomach hierarchii.</span><span class="sxs-lookup"><span data-stu-id="3b49d-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="3b49d-110">`Service1`znajduje się w folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="3b49d-110">`Service1` is at the root.</span></span> <span data-ttu-id="3b49d-111">`Service2`i `Service3` dziedziczą domyślne elementy z `Service1`.</span><span class="sxs-lookup"><span data-stu-id="3b49d-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="3b49d-112">`Service4`, `Service5`, `Service6` i `Service7` są definiowane na trzeci poziom hierarchii dziedziczenia domyślne elementy z `Service3`.</span><span class="sxs-lookup"><span data-stu-id="3b49d-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="3b49d-113">Na koniec `Service10` i `Service11` są czwartego poziomu hierarchii.</span><span class="sxs-lookup"><span data-stu-id="3b49d-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="3b49d-114">Wszystkie usługi wdrożenia `IDesc` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3b49d-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="3b49d-115">Poniżej znajduje się definicja `IDesc` interfejs, który zawiera metody ujawnione w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3b49d-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="3b49d-116">`IDesc` Interfejsu jest zdefiniowany w Service1.cs.</span><span class="sxs-lookup"><span data-stu-id="3b49d-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 <span data-ttu-id="3b49d-117">Implementacja metody te przez usługi jest prosta.</span><span class="sxs-lookup"><span data-stu-id="3b49d-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="3b49d-118">`ListEndpoints`wykonuje iterację wszystkie punkty końcowe usługi i zwraca listę wszystkich punktów końcowych, które usługa ma.</span><span class="sxs-lookup"><span data-stu-id="3b49d-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="3b49d-119">`ListServiceBehaviors`wykonuje iterację wszystkie zachowania dodane do usługi i zwraca listę wszystkich zachowań usługi związane z usługą.</span><span class="sxs-lookup"><span data-stu-id="3b49d-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="3b49d-120">`ListEndpointBehaviors`działa w podobny sposób jak `ListServiceBehaviors`, ale zamiast tego zwraca listę zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3b49d-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="3b49d-121">Ta implementacja umożliwia jest ujawniany przez klienta, aby wiedzieć, jak wiele punktów końcowych usługi i które zachowania usługi i zachowania punktu końcowego zostały dodane do usługi.</span><span class="sxs-lookup"><span data-stu-id="3b49d-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="3b49d-122">Klient, który został zaimplementowany jako część próbki dodaje odwołania do usługi do wszystkich usług w rozwiązaniu i zawiera te elementy dla każdego z nich usługi.</span><span class="sxs-lookup"><span data-stu-id="3b49d-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="3b49d-123">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="3b49d-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="3b49d-124">Uruchom klienta</span><span class="sxs-lookup"><span data-stu-id="3b49d-124">To run the client</span></span>  
  
1.  <span data-ttu-id="3b49d-125">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik ConfigHierarchicalModel.sln.</span><span class="sxs-lookup"><span data-stu-id="3b49d-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="3b49d-126">Projekt klienta nie już ustawiono jako projekt rozruchu, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="3b49d-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="3b49d-127">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="3b49d-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="3b49d-128">W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie kliknij przycisk **jednego projektu startowego**.</span><span class="sxs-lookup"><span data-stu-id="3b49d-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="3b49d-129">Z **jednego projektu startowego** listy rozwijanej, wybierz pozycję **klienta**.</span><span class="sxs-lookup"><span data-stu-id="3b49d-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="3b49d-130">Kliknij przycisk **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="3b49d-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="3b49d-131">Aby samodzielnie tworzyć przykładowy, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="3b49d-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="3b49d-132">Aby uruchomić klienta, naciśnij kombinację klawiszy Ctrl + F5.</span><span class="sxs-lookup"><span data-stu-id="3b49d-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b49d-133">Jeśli te kroki nie działają, następnie upewnij się, że środowiska nie został prawidłowo skonfigurowany, wykonując następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="3b49d-133">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="3b49d-134">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3b49d-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="3b49d-135">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3b49d-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="3b49d-136">Aby uruchomić przykład w jednym lub wielu konfiguracji komputera, postępuj zgodnie z instrukcjami [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3b49d-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3b49d-137">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3b49d-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3b49d-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3b49d-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3b49d-139">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="3b49d-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b49d-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3b49d-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="3b49d-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b49d-141">See Also</span></span>  
 [<span data-ttu-id="3b49d-142">Przykłady zarządzania AppFabric</span><span class="sxs-lookup"><span data-stu-id="3b49d-142">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)
