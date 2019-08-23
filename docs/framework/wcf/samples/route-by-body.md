---
title: Trasa według treści
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 4266068bb53e5ae90a05cc6537df2ab9b65b6b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965512"
---
# <a name="route-by-body"></a><span data-ttu-id="6b014-102">Trasa według treści</span><span class="sxs-lookup"><span data-stu-id="6b014-102">Route by Body</span></span>
<span data-ttu-id="6b014-103">Ten przykład pokazuje, jak wdrożyć usługę akceptującą obiekty komunikatów z dowolną akcją SOAP.</span><span class="sxs-lookup"><span data-stu-id="6b014-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="6b014-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="6b014-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="6b014-105">Usługa implementuje pojedynczą `Calculate` operację, która <xref:System.ServiceModel.Channels.Message> akceptuje parametr <xref:System.ServiceModel.Channels.Message> żądania i zwraca odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="6b014-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="6b014-106">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="6b014-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b014-107">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6b014-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6b014-108">Przykład ilustruje wysyłanie komunikatów na podstawie zawartości treści.</span><span class="sxs-lookup"><span data-stu-id="6b014-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="6b014-109">Wbudowany mechanizm wysyłania komunikatów modelu usługi Windows Communication Foundation (WCF) jest oparty na akcjach komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6b014-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="6b014-110">Istnieje jednak wiele istniejących usług sieci Web, które definiują wszystkie operacje z akcją = "".</span><span class="sxs-lookup"><span data-stu-id="6b014-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="6b014-111">Nie można utworzyć usługi opartej na języku WSDL, która ciągle wysyła komunikaty żądania na podstawie informacji o akcjach.</span><span class="sxs-lookup"><span data-stu-id="6b014-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="6b014-112">Ten przykład pokazuje kontrakt usługi oparty na języku WSDL (WSDL jest zawarty w plik Service. WSDL, który jest dołączony do przykładu).</span><span class="sxs-lookup"><span data-stu-id="6b014-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="6b014-113">Kontrakt usługi jest kalkulatorem podobnym do użytego w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="6b014-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="6b014-114">Jest to `[OperationContract]` jednak `Action=""` wartość określana dla wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="6b014-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
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
  
 <span data-ttu-id="6b014-115">W przypadku kontraktu usługa wymaga niestandardowego zachowania `DispatchByBodyBehavior` wysyłania, aby umożliwić wysyłanie komunikatów między operacjami.</span><span class="sxs-lookup"><span data-stu-id="6b014-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="6b014-116">To zachowanie wysyłania inicjuje `DispatchByBodyElementOperationSelector` selektor operacji niestandardowych z tabelą nazw operacji, które są poprzedzone przez QName odpowiednich elementów otoki.</span><span class="sxs-lookup"><span data-stu-id="6b014-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="6b014-117">`DispatchByBodyElementOperationSelector`sprawdza tag początkowy pierwszego elementu podrzędnego treści i wybiera operację przy użyciu wcześniej wymienionej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6b014-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="6b014-118">Klient korzysta z wygenerowanego automatycznie serwera proxy z poziomu WSDL wyeksportowanego przez usługę za pomocą [narzędzia Svcutil. exe](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6b014-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="6b014-119">Fakt, że akcje wszystkich operacji są puste nie ma wpływu na kod klienta, z wyjątkiem parametrów akcji w automatycznie generowanym serwerze proxy.</span><span class="sxs-lookup"><span data-stu-id="6b014-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="6b014-120">Kod klienta wykonuje kilka obliczeń.</span><span class="sxs-lookup"><span data-stu-id="6b014-120">The client code performs several calculations.</span></span> <span data-ttu-id="6b014-121">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="6b014-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6b014-122">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="6b014-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6b014-123">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="6b014-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6b014-124">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b014-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6b014-125">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b014-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6b014-126">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b014-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6b014-127">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6b014-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b014-128">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="6b014-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6b014-129">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6b014-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b014-130">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b014-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
