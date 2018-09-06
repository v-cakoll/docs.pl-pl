---
title: Kontrakt błędu
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 5b3348f31d239d6bf7e64852ba02010115062669
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724922"
---
# <a name="fault-contract"></a><span data-ttu-id="fde04-102">Kontrakt błędu</span><span class="sxs-lookup"><span data-stu-id="fde04-102">Fault Contract</span></span>
<span data-ttu-id="fde04-103">Przykładowe kontrakt błędu pokazuje, jak komunikować informacje o błędzie z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="fde04-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="fde04-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), za pomocą dodatkowy kod dodany do usługi, aby przekonwertować wyjątek wewnętrzny błąd.</span><span class="sxs-lookup"><span data-stu-id="fde04-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="fde04-105">Klient próbuje wykonać dzielenie przez zero, aby wymusić warunek błędu usługi.</span><span class="sxs-lookup"><span data-stu-id="fde04-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fde04-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fde04-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fde04-107">Kontrakt Kalkulator została zmodyfikowana, aby uwzględnić <xref:System.ServiceModel.FaultContractAttribute> jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fde04-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="fde04-108"><xref:System.ServiceModel.FaultContractAttribute> Atrybut wskazuje, że `Divide` operacja może zwrócić błąd typu `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="fde04-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="fde04-109">Awarii może być dowolnego typu, który może być serializowany.</span><span class="sxs-lookup"><span data-stu-id="fde04-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="fde04-110">W tym przypadku `MathFault` jest kontraktu danych, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fde04-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```  
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
  
 <span data-ttu-id="fde04-111">`Divide` Metoda zgłasza wyjątek <xref:System.ServiceModel.FaultException%601> występuje wyjątek podczas dzielenia przez zero wyjątek, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fde04-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="fde04-112">Ten wyjątek powoduje błąd, są wysyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="fde04-112">This exception results in a fault being sent to the client.</span></span>  
  
```  
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
  
 <span data-ttu-id="fde04-113">Kod klienta powoduje błąd przez zażądanie dzielenia przez zero.</span><span class="sxs-lookup"><span data-stu-id="fde04-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="fde04-114">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="fde04-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fde04-115">Zobaczysz dzielenia przez zero, które zgłaszają się jako błąd.</span><span class="sxs-lookup"><span data-stu-id="fde04-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="fde04-116">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="fde04-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="fde04-117">Klient robi to przez odpowiednie `FaultException<MathFault>` wyjątek:</span><span class="sxs-lookup"><span data-stu-id="fde04-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="fde04-118">Domyślnie szczegółowe informacje o nieoczekiwane wyjątki nie są wysyłane do klienta zapobiegające szczegółowe informacje o implementacji usługi ucieczce granicę bezpiecznej usługi.</span><span class="sxs-lookup"><span data-stu-id="fde04-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="fde04-119">`FaultContract` zapewnia sposób opisania usterek w umowie i oznaczania niektórych rodzajów wyjątków zgodnie z potrzebami w celu przesłania go do klienta.</span><span class="sxs-lookup"><span data-stu-id="fde04-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="fde04-120">`FaultException<T>` udostępnia mechanizm środowiska wykonawczego wysyłanie błędów do odbiorców.</span><span class="sxs-lookup"><span data-stu-id="fde04-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="fde04-121">Jest przydatne podczas debugowania, zobacz szczegóły wewnętrznego błędu usługi.</span><span class="sxs-lookup"><span data-stu-id="fde04-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="fde04-122">Aby wyłączyć to zachowanie bezpiecznych opisany wcześniej, można wskazać, że należy uwzględnić szczegółowe informacje o każdym nieobsługiwany wyjątek na serwerze w domenach błędów, które są wysyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="fde04-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="fde04-123">Jest to realizowane przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> do `true`.</span><span class="sxs-lookup"><span data-stu-id="fde04-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="fde04-124">Można ustawić go w kodzie lub w konfiguracji, jak pokazano w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fde04-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="fde04-125">Ponadto zachowanie musi być skojarzony z usługą, ustawiając `behaviorConfiguration` atrybut usługi w pliku konfiguracji "CalculatorServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="fde04-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="fde04-126">Aby wykryć takie błędy na kliencie, inną niż ogólna <xref:System.ServiceModel.FaultException> musi być przechwycony.</span><span class="sxs-lookup"><span data-stu-id="fde04-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="fde04-127">To zachowanie można stosować tylko na potrzeby debugowania i nigdy nie powinna być włączona w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="fde04-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fde04-128">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="fde04-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fde04-129">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fde04-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fde04-130">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fde04-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="fde04-131">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fde04-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fde04-132">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fde04-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fde04-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fde04-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fde04-134">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="fde04-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fde04-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fde04-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="fde04-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fde04-136">See Also</span></span>
