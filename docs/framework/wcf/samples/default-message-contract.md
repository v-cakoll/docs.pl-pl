---
title: Domyślny kontrakt komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 46b69697616ad7983daed16f8a180a4da7f61a16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183769"
---
# <a name="default-message-contract"></a><span data-ttu-id="c3afc-102">Domyślny kontrakt komunikatów</span><span class="sxs-lookup"><span data-stu-id="c3afc-102">Default Message Contract</span></span>
<span data-ttu-id="c3afc-103">Przykład domyślnej umowy wiadomości pokazuje usługę, w której niestandardowa wiadomość zdefiniowana przez użytkownika jest przekazywana do i z operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="c3afc-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="c3afc-104">Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje interfejs kalkulatora jako wpisaną usługę.</span><span class="sxs-lookup"><span data-stu-id="c3afc-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="c3afc-105">Zamiast poszczególnych operacji usługi dodawania, odejmowania, mnożenia i dzielenia używanego w [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md)w tym przykładzie przekazuje niestandardowy komunikat zawierający zarówno argumenty, jak i operator i zwraca wynik obliczeń arytmetycznych.</span><span class="sxs-lookup"><span data-stu-id="c3afc-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="c3afc-106">Klient jest programem konsoli (exe), a biblioteka usług (dll) jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="c3afc-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="c3afc-107">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c3afc-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3afc-108">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c3afc-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c3afc-109">W usłudze zdefiniowano pojedynczą operację usługi, która akceptuje `MyMessage`i zwraca niestandardowe wiadomości typu .</span><span class="sxs-lookup"><span data-stu-id="c3afc-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="c3afc-110">Chociaż w tym przykładzie wiadomości żądania i odpowiedzi są tego samego typu, mogą one oczywiście być różne kontrakty wiadomości, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="c3afc-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="c3afc-111">Wiadomość `MyMessage` niestandardowa jest zdefiniowana w <xref:System.ServiceModel.MessageContractAttribute>klasie <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> z adnotacjami i atrybutami.</span><span class="sxs-lookup"><span data-stu-id="c3afc-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="c3afc-112">Tylko trzeci konstruktor jest używany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c3afc-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="c3afc-113">Za pomocą kontraktów wiadomości pozwala na wykonywanie pełnej kontroli nad komunikatem SOAP.</span><span class="sxs-lookup"><span data-stu-id="c3afc-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="c3afc-114">W tym przykładzie <xref:System.ServiceModel.MessageHeaderAttribute> atrybut jest `Operation` używany do umieszczenia w nagłówku SOAP.</span><span class="sxs-lookup"><span data-stu-id="c3afc-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="c3afc-115">`N1`Argumenty `N2` i pojawiają się `Result` w treści SOAP, ponieważ <xref:System.ServiceModel.MessageBodyMemberAttribute> mają zastosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="c3afc-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="c3afc-116">Klasa implementacji zawiera kod `Calculate` dla operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="c3afc-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="c3afc-117">Klasa `CalculateService` uzyskuje operands i operator z komunikatu żądania i tworzy komunikat odpowiedzi, który zawiera wynik żądanego obliczenia, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c3afc-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c3afc-118">Wygenerowany kod klienta dla klienta został utworzony za pomocą narzędzia [ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="c3afc-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="c3afc-119">Narzędzie automatycznie tworzy typy kontraktów wiadomości w wygenerowanym kodzie klienta, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="c3afc-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="c3afc-120">Opcja `/messageContract` polecenia może być określona, aby wymusić generowanie kontraktów wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c3afc-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="c3afc-121">Poniższy przykładowy kod pokazuje `MyMessage` klienta przy użyciu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c3afc-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
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
  
 <span data-ttu-id="c3afc-122">Po uruchomieniu próbki obliczenia są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c3afc-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="c3afc-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c3afc-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="c3afc-124">W tym momencie niestandardowe komunikaty zdefiniowane przez użytkownika zostały przekazane między klientem a operacją usługi.</span><span class="sxs-lookup"><span data-stu-id="c3afc-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="c3afc-125">Kontrakt wiadomości zdefiniowane, że argumenty i wyniki były w treści wiadomości i że operator był w nagłówku wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c3afc-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="c3afc-126">Rejestrowanie wiadomości można skonfigurować tak, aby obserwować tę strukturę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c3afc-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3afc-127">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c3afc-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c3afc-128">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3afc-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c3afc-129">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3afc-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c3afc-130">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3afc-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c3afc-131">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c3afc-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3afc-132">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c3afc-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c3afc-133">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c3afc-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3afc-134">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c3afc-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
