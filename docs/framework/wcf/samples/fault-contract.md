---
title: Kontrakt błędu
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 914ac85d0aaecfaec84eeacc12461bd3c7023e54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961410"
---
# <a name="fault-contract"></a><span data-ttu-id="2fbbc-102">Kontrakt błędu</span><span class="sxs-lookup"><span data-stu-id="2fbbc-102">Fault Contract</span></span>
<span data-ttu-id="2fbbc-103">Przykładowa umowa dotycząca błędu demonstruje sposób komunikacji z klientem informacji o błędach z usługi.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="2fbbc-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), z dodatkowym kodem dodanym do usługi w celu przekonwertowania wewnętrznego wyjątku na błąd.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="2fbbc-105">Klient próbuje wykonać dzielenie przez zero w celu wymuszenia błędu w usłudze.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fbbc-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2fbbc-107">Kontrakt kalkulatora został zmodyfikowany w taki sposób, <xref:System.ServiceModel.FaultContractAttribute> aby zawierał element, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="2fbbc-108">Ten <xref:System.ServiceModel.FaultContractAttribute> atrybut wskazuje `Divide` , że operacja może zwrócić błąd typu `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="2fbbc-109">Błąd może być dowolnego typu, który może być serializowany.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="2fbbc-110">W tym przypadku `MathFault` jest to kontrakt danych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2fbbc-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 <span data-ttu-id="2fbbc-111">`Divide` Metoda<xref:System.ServiceModel.FaultException%601> zgłasza wyjątek, gdy wystąpi wyjątek dzielenia przez zero, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="2fbbc-112">Ten wyjątek powoduje, że błąd jest wysyłany do klienta.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-112">This exception results in a fault being sent to the client.</span></span>  
  
```csharp
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 <span data-ttu-id="2fbbc-113">Kod klienta wymusza błąd, żądając dzielenia przez zero.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="2fbbc-114">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2fbbc-115">Zobaczysz, że dzielenie przez zero zostanie zgłoszone jako błąd.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="2fbbc-116">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="2fbbc-117">Klient wykonuje to poprzez przechwycenie odpowiedniego `FaultException<MathFault>` wyjątku:</span><span class="sxs-lookup"><span data-stu-id="2fbbc-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="2fbbc-118">Domyślnie szczegóły nieoczekiwanych wyjątków nie są wysyłane do klienta, aby zapobiec szczegółom implementacji usługi z ucieczki bezpiecznej granicy usługi.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="2fbbc-119">`FaultContract`zapewnia sposób opisywania błędów w kontrakcie i oznaczania niektórych typów wyjątków zgodnie z potrzebami do przesyłania danych do klienta.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="2fbbc-120">`FaultException<T>`zapewnia mechanizm czasu wykonywania do wysyłania błędów do odbiorców.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="2fbbc-121">Jednak podczas debugowania warto zobaczyć wewnętrzne szczegóły błędu usługi.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="2fbbc-122">Aby wyłączyć wcześniej opisane bezpieczne zachowanie, można wskazać, że szczegóły każdego nieobsługiwanego wyjątku na serwerze powinny być dołączone do błędu wysyłanego do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="2fbbc-123">Jest to realizowane przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>. `true`</span><span class="sxs-lookup"><span data-stu-id="2fbbc-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="2fbbc-124">Można ustawić ją w kodzie lub w konfiguracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="2fbbc-125">Ponadto zachowanie musi być skojarzone z usługą przez ustawienie `behaviorConfiguration` atrybutu usługi w pliku konfiguracji na "CalculatorServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="2fbbc-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="2fbbc-126">Aby przechwytywać takie błędy na kliencie, należy przechwycić nieogólne <xref:System.ServiceModel.FaultException> .</span><span class="sxs-lookup"><span data-stu-id="2fbbc-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="2fbbc-127">Takie zachowanie powinno być używane tylko do celów debugowania i nigdy nie powinno być włączone w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2fbbc-128">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="2fbbc-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2fbbc-129">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fbbc-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2fbbc-130">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fbbc-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2fbbc-131">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fbbc-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2fbbc-132">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2fbbc-133">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="2fbbc-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2fbbc-134">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fbbc-135">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2fbbc-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
