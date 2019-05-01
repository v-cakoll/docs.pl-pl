---
title: Trasa według treści
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: b8a3f7785d7d59d8ad85d6dddde7fd6a04a12d63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787559"
---
# <a name="route-by-body"></a><span data-ttu-id="c2f07-102">Trasa według treści</span><span class="sxs-lookup"><span data-stu-id="c2f07-102">Route by Body</span></span>
<span data-ttu-id="c2f07-103">Ten przykład demonstruje sposób implementacji to usługa, która akceptuje obiekty wiadomości z dowolnego akcją SOAP.</span><span class="sxs-lookup"><span data-stu-id="c2f07-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="c2f07-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="c2f07-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="c2f07-105">Usługa implementuje jedną `Calculate` operacji, który akceptuje <xref:System.ServiceModel.Channels.Message> żądań parametrów i zwraca <xref:System.ServiceModel.Channels.Message> odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c2f07-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="c2f07-106">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="c2f07-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2f07-107">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c2f07-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c2f07-108">W przykładzie pokazano wysyłania komunikatów na podstawie zawartości treści.</span><span class="sxs-lookup"><span data-stu-id="c2f07-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="c2f07-109">Wbudowany komunikat modelu usługi Windows Communication Foundation (WCF): wysyłania mechanizm opiera się na komunikat akcji.</span><span class="sxs-lookup"><span data-stu-id="c2f07-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="c2f07-110">Istnieją jednak wiele istniejących usług sieci Web, które definiują wszystkie operacje przy użyciu akcji = "".</span><span class="sxs-lookup"><span data-stu-id="c2f07-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="c2f07-111">Nie jest możliwe tworzenie usługi języka WSDL, który przechowuje wysyła komunikaty żądań informacji o akcji.</span><span class="sxs-lookup"><span data-stu-id="c2f07-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="c2f07-112">Niniejszy przykład pokazuje kontraktu usługi, który jest oparty na języku WSDL (WSDL jest zawarty w Service.wsdl, który jest dołączony do przykładu).</span><span class="sxs-lookup"><span data-stu-id="c2f07-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="c2f07-113">Umowa serwisowa jest Kalkulator, podobnie jak komentarzowi użytemu w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c2f07-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="c2f07-114">Jednak `[OperationContract]` Określa `Action=""` dla wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="c2f07-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
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
  
 <span data-ttu-id="c2f07-115">Biorąc pod uwagę kontrakt, usługa wymaga zachowania wysyłania niestandardowych `DispatchByBodyBehavior` wiadomości wysyłanych między operacjami.</span><span class="sxs-lookup"><span data-stu-id="c2f07-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="c2f07-116">To zachowanie wysyłania inicjuje `DispatchByBodyElementOperationSelector` selektor operacji niestandardowego za pomocą tabeli nazw operacji opartych na kluczach QName otoki odpowiednich elementów.</span><span class="sxs-lookup"><span data-stu-id="c2f07-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="c2f07-117">`DispatchByBodyElementOperationSelector` analizuje tagu początkowego pierwszego elementu podrzędnego treści i wybiera tej operacji z użyciem w tabeli powyżej.</span><span class="sxs-lookup"><span data-stu-id="c2f07-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="c2f07-118">Klient korzysta z serwera proxy, wygenerowany automatycznie z danych WSDL wyeksportowane za pomocą usługi [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c2f07-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="c2f07-119">Fakt, że akcje wszystkie operacje są puste nie ma wpływu na kod klienta, z wyjątkiem parametry akcji na serwerze proxy generowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c2f07-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="c2f07-120">Kod klienta wykonuje kilka obliczeń.</span><span class="sxs-lookup"><span data-stu-id="c2f07-120">The client code performs several calculations.</span></span> <span data-ttu-id="c2f07-121">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c2f07-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c2f07-122">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c2f07-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2f07-123">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="c2f07-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c2f07-124">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2f07-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c2f07-125">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2f07-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c2f07-126">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2f07-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2f07-127">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c2f07-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2f07-128">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c2f07-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c2f07-129">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c2f07-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2f07-130">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2f07-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
