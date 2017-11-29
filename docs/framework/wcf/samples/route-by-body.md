---
title: "Trasa według treści"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: efbf38d562b120308abc6fc4514a9d17ef608b51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="route-by-body"></a><span data-ttu-id="94ccd-102">Trasa według treści</span><span class="sxs-lookup"><span data-stu-id="94ccd-102">Route by Body</span></span>
<span data-ttu-id="94ccd-103">W tym przykładzie pokazano, jak wdrożyć usługi, która akceptuje obiekty komunikatów z dowolną akcję SOAP.</span><span class="sxs-lookup"><span data-stu-id="94ccd-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="94ccd-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="94ccd-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="94ccd-105">Usługa implementuje pojedynczy `Calculate` operacja, która akceptuje <xref:System.ServiceModel.Channels.Message> żądań parametrów i zwraca <xref:System.ServiceModel.Channels.Message> odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="94ccd-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="94ccd-106">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="94ccd-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94ccd-107">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="94ccd-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="94ccd-108">W przykładzie pokazano wysyłania wiadomości na podstawie zawartości treści.</span><span class="sxs-lookup"><span data-stu-id="94ccd-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="94ccd-109">Wbudowane [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanizmu wysyłania wiadomości modelu usługi jest oparta na komunikat akcji.</span><span class="sxs-lookup"><span data-stu-id="94ccd-109">The built-in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="94ccd-110">Istnieją jednak wielu istniejących usług sieci Web, definiujące wszystkich ich operacji z wartością Action = "".</span><span class="sxs-lookup"><span data-stu-id="94ccd-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="94ccd-111">Nie jest możliwe kompilacji usługi oparte na WSDL, który przechowuje wysyła komunikaty żądań informacje o akcji.</span><span class="sxs-lookup"><span data-stu-id="94ccd-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="94ccd-112">W przykładzie pokazano umowy serwisowej, która jest oparta na WSDL (WSDL znajduje się w Service.wsdl dołączonego przykładu).</span><span class="sxs-lookup"><span data-stu-id="94ccd-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="94ccd-113">Kontrakt usługi jest Kalkulator, podobnie jak używaną w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="94ccd-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="94ccd-114">Jednak `[OperationContract]` Określa `Action=""` dla wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="94ccd-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="94ccd-115">Biorąc pod uwagę kontrakt, usługa wymaga zachowania wysyłania niestandardowych `DispatchByBodyBehavior` wiadomości wysyłanych między operacjami.</span><span class="sxs-lookup"><span data-stu-id="94ccd-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="94ccd-116">To zachowanie wysyłania inicjuje `DispatchByBodyElementOperationSelector` selektor operacji niestandardowych z tabelą nazw operacji, wyznaczaną przez QName otoki odpowiednich elementów.</span><span class="sxs-lookup"><span data-stu-id="94ccd-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="94ccd-117">`DispatchByBodyElementOperationSelector`przegląda tagu początkowego pierwszego elementu podrzędnego treści i wybiera operację, używając w tabeli powyżej.</span><span class="sxs-lookup"><span data-stu-id="94ccd-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="94ccd-118">Klient korzysta z serwera proxy automatycznie generowanej z WSDL wyeksportowane za pomocą usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="94ccd-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="94ccd-119">Fakt, że akcje wszystkie operacje są puste nie ma wpływu na kod klienta, z wyjątkiem parametry akcji w obiekcie pośredniczącym wygenerowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="94ccd-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="94ccd-120">Kod klienta wykonuje kilka obliczeń.</span><span class="sxs-lookup"><span data-stu-id="94ccd-120">The client code performs several calculations.</span></span> <span data-ttu-id="94ccd-121">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="94ccd-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="94ccd-122">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="94ccd-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94ccd-123">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="94ccd-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="94ccd-124">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94ccd-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="94ccd-125">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94ccd-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="94ccd-126">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94ccd-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94ccd-127">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="94ccd-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94ccd-128">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="94ccd-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94ccd-129">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="94ccd-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94ccd-130">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="94ccd-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a><span data-ttu-id="94ccd-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94ccd-131">See Also</span></span>
