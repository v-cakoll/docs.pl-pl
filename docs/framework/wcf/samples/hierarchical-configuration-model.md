---
title: Hierarchiczny model konfiguracji
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 8ca9b01eb022e2e2ab940866a6230e8227ceb2dc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499344"
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="978b4-102">Hierarchiczny model konfiguracji</span><span class="sxs-lookup"><span data-stu-id="978b4-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="978b4-103">Ten przykład demonstruje sposób implementacji hierarchii plików konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="978b4-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="978b4-104">Pokazuje również, jak powiązania, zachowań usługi i zachowań punktu końcowego są dziedziczone z poziomu w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="978b4-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="978b4-105">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="978b4-105">Sample details</span></span>  
 <span data-ttu-id="978b4-106">Jedna z funkcji opracowanych dla usług WCF w [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] jest poprawę hierarchiczny model konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="978b4-106">One of the features developed for WCF in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="978b4-107">Przykładem hierarchiczny model konfiguracji jest zdefiniowana w pliku Machine.config -> Rootweb.config -> pliku Web.config. W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], te powiązania i zachowań, które są zdefiniowane w wyższe poziomy w hierarchii konfiguracji, które są dodawane do usługi bez jawnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="978b4-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="978b4-108">Ten przykład pokazuje, jak można uproszczenie konfiguracji usługi, opierając się na elementy konfiguracji, zdefiniowanych na komputerze lub na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="978b4-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="978b4-109">W tym przykładzie składa się z dziewięciu usługi, zdefiniowane w trzech poziomów hierarchii.</span><span class="sxs-lookup"><span data-stu-id="978b4-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="978b4-110">`Service1` jest w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="978b4-110">`Service1` is at the root.</span></span> <span data-ttu-id="978b4-111">`Service2` i `Service3` dziedziczą domyślne elementy z `Service1`.</span><span class="sxs-lookup"><span data-stu-id="978b4-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="978b4-112">`Service4`, `Service5`, `Service6` i `Service7` są definiowane na trzeci poziom w hierarchii dziedziczenia domyślne elementy z `Service3`.</span><span class="sxs-lookup"><span data-stu-id="978b4-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="978b4-113">Na koniec `Service10` i `Service11` znajdują się na czwartego poziomu w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="978b4-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="978b4-114">Wszystkie usługi implementują `IDesc` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="978b4-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="978b4-115">Poniżej przedstawiono definicję `IDesc` interfejs, który zawiera metody, dostępne w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="978b4-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="978b4-116">`IDesc` Interfejsu jest zdefiniowany w plikach Service1.cs.</span><span class="sxs-lookup"><span data-stu-id="978b4-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="978b4-117">Implementacja metody te przez usługi jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="978b4-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="978b4-118">`ListEndpoints` wykonuje iterację przez wszystkie punkty końcowe usługi i zwraca listę wszystkich punktów końcowych, które usługa ma.</span><span class="sxs-lookup"><span data-stu-id="978b4-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="978b4-119">`ListServiceBehaviors` wykonuje iterację przez wszystkie zachowania, które są dodawane do usługi i zwraca listę wszystkich zachowań usługi związane z usługą.</span><span class="sxs-lookup"><span data-stu-id="978b4-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="978b4-120">`ListEndpointBehaviors` zachowuje się w podobny sposób jak `ListServiceBehaviors`, ale zamiast tego zwraca listę zachowań punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="978b4-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="978b4-121">Ta implementacja umożliwia, jest ujawniany przez klienta, aby wiedzieć, ile punktów końcowych usługi i które zachowania usług i zachowań punktu końcowego zostały dodane do usługi.</span><span class="sxs-lookup"><span data-stu-id="978b4-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="978b4-122">Klient, który został zaimplementowany jako części przykładu dodaje odwołanie usługi do wszystkich usług w rozwiązaniu i pokazuje te elementy, dla każdej z nich usługi.</span><span class="sxs-lookup"><span data-stu-id="978b4-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="978b4-123">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="978b4-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="978b4-124">Aby uruchomić klienta</span><span class="sxs-lookup"><span data-stu-id="978b4-124">To run the client</span></span>  
  
1.  <span data-ttu-id="978b4-125">Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik ConfigHierarchicalModel.sln.</span><span class="sxs-lookup"><span data-stu-id="978b4-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="978b4-126">Projekt klienta nie już skonfigurowano jako projekt startowy, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="978b4-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="978b4-127">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="978b4-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="978b4-128">W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie kliknij przycisk **pojedynczy projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="978b4-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="978b4-129">Z **pojedynczy projekt startowy** listę rozwijaną, wybierz opcję **klienta**.</span><span class="sxs-lookup"><span data-stu-id="978b4-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="978b4-130">Kliknij przycisk **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="978b4-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="978b4-131">Aby stworzyć próbkę, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="978b4-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="978b4-132">Aby uruchomić klienta, naciśnij kombinację klawiszy Ctrl + F5.</span><span class="sxs-lookup"><span data-stu-id="978b4-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="978b4-133">Jeśli te kroki nie działa, upewnij się, czy środowiska prawidłowo skonfigurowano, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="978b4-133">If these steps do not work, make sure that your environment has been properly set up, using the following steps:</span></span>  
>   
> 1.  <span data-ttu-id="978b4-134">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="978b4-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="978b4-135">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="978b4-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="978b4-136">Do uruchomienia przykładu w jednej lub wielu konfiguracji komputera, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="978b4-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="978b4-137">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="978b4-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="978b4-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="978b4-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="978b4-139">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="978b4-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="978b4-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="978b4-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="978b4-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="978b4-141">See Also</span></span>  
 [<span data-ttu-id="978b4-142">Przykładami dotyczącymi zarządzania AppFabric</span><span class="sxs-lookup"><span data-stu-id="978b4-142">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
