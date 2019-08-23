---
title: Domyślny kontrakt komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 0a9b6ddb67f914c2c1c228f3042152ef9582f7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961787"
---
# <a name="default-message-contract"></a><span data-ttu-id="4358e-102">Domyślny kontrakt komunikatów</span><span class="sxs-lookup"><span data-stu-id="4358e-102">Default Message Contract</span></span>
<span data-ttu-id="4358e-103">Domyślny przykład kontraktu komunikatu pokazuje usługę, w której do i z operacji usługi jest przesyłany niestandardowy komunikat zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4358e-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="4358e-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje interfejs kalkulatora jako usługę o określonym typie.</span><span class="sxs-lookup"><span data-stu-id="4358e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="4358e-105">Zamiast poszczególnych operacji usługi do dodawania, odejmowania, mnożenia i dzielenia używanych w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), ten przykład przekazuje komunikat niestandardowy, który zawiera operandy i operator, i zwraca wynik Obliczanie arytmetyczne.</span><span class="sxs-lookup"><span data-stu-id="4358e-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="4358e-106">Klient jest programem konsolowym (. exe), a Biblioteka usług (. dll) jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="4358e-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="4358e-107">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="4358e-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4358e-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4358e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4358e-109">W usłudze jest zdefiniowana jedna operacja usługi, która akceptuje i zwraca niestandardową wiadomość typu `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="4358e-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="4358e-110">Mimo że w tym przykładzie komunikaty żądania i odpowiedzi są tego samego typu, w razie potrzeby mogą oczywiście być różne umowy dotyczące komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4358e-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="4358e-111">Wiadomość `MyMessage` niestandardowa jest definiowana w klasie <xref:System.ServiceModel.MessageHeaderAttribute> z <xref:System.ServiceModel.MessageContractAttribute>adnotacjami i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutami.</span><span class="sxs-lookup"><span data-stu-id="4358e-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="4358e-112">Tylko trzeci Konstruktor jest używany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4358e-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="4358e-113">Używanie kontraktów komunikatów umożliwia pełną kontrolę nad komunikatem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4358e-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="4358e-114">W tym przykładzie <xref:System.ServiceModel.MessageHeaderAttribute> atrybut jest używany do umieszczania `Operation` w nagłówku protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4358e-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="4358e-115">Operandy `N1`i <xref:System.ServiceModel.MessageBodyMemberAttribute> `N2` pojawiająsięwtreściprotokołuSOAP,ponieważmajązastosowaneatrybuty.`Result`</span><span class="sxs-lookup"><span data-stu-id="4358e-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,   
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="4358e-116">Klasa implementacji zawiera kod dla `Calculate` operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4358e-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="4358e-117">`CalculateService` Klasa uzyskuje operandy i operator z komunikatu żądania i tworzy komunikat odpowiedzi, który zawiera wynik żądanego obliczenia, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4358e-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="4358e-118">Wygenerowany kod klienta dla klienta został utworzony za pomocą narzędzia [Svcutil. exe (narzędzie do przesyłania metadanych)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="4358e-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="4358e-119">W razie potrzeby narzędzie automatycznie tworzy w kodzie wygenerowanym klienta typy kontraktów komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4358e-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="4358e-120">Opcja `/messageContract` polecenia może być określona, aby wymusić generowanie kontraktów komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4358e-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="4358e-121">Następujący przykładowy kod demonstruje klienta korzystającego z `MyMessage` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4358e-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage() 
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="4358e-122">Po uruchomieniu przykładu obliczenia są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4358e-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="4358e-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="4358e-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4358e-124">W tym momencie niestandardowe komunikaty zdefiniowane przez użytkownika przechodzą między klientem a operacją usługi.</span><span class="sxs-lookup"><span data-stu-id="4358e-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="4358e-125">Kontrakt komunikatu określił, że operandy i wyniki znajdowały się w treści wiadomości i że operator znajdował się w nagłówku komunikatu.</span><span class="sxs-lookup"><span data-stu-id="4358e-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="4358e-126">Rejestrowanie komunikatów można skonfigurować tak, aby obserwować tę strukturę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4358e-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4358e-127">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="4358e-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4358e-128">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4358e-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4358e-129">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4358e-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4358e-130">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4358e-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4358e-131">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4358e-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4358e-132">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="4358e-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4358e-133">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="4358e-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4358e-134">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4358e-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
