---
title: "Domyślny kontrakt komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1219f2c1a173f454827c7450e66d90a500d87e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="default-message-contract"></a><span data-ttu-id="e39ca-102">Domyślny kontrakt komunikatów</span><span class="sxs-lookup"><span data-stu-id="e39ca-102">Default Message Contract</span></span>
<span data-ttu-id="e39ca-103">Domyślny kontrakt komunikatów w przykładzie pokazano usługi, gdy wiadomość niestandardowe zdefiniowane przez użytkownika jest przekazywany do i z operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e39ca-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="e39ca-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej interfejs Kalkulator jako typu usługi.</span><span class="sxs-lookup"><span data-stu-id="e39ca-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="e39ca-105">Zamiast poszczególnych usług operacji dodawania, odejmowania mnożenia i dzielenia używane w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), w tym przykładzie przekazuje niestandardowy komunikat, który zawiera argumenty operacji i operatora i zwraca wynik operacji arytmetycznych.</span><span class="sxs-lookup"><span data-stu-id="e39ca-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="e39ca-106">Klient znajduje się program konsoli (.exe) i usługi biblioteki (.dll) jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="e39ca-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="e39ca-107">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e39ca-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e39ca-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e39ca-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e39ca-109">W usłudze operacji usługi pojedynczej zdefiniowano akceptuje i zwraca komunikaty niestandardowe typu `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="e39ca-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="e39ca-110">Mimo że w tym przykładzie komunikatów żądań i odpowiedzi są tego samego typu, oczywiście może być inny komunikat kontraktów w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="e39ca-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="e39ca-111">Niestandardowy komunikat `MyMessage` jest zdefiniowany w klasie opatrzoną <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e39ca-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="e39ca-112">Trzeci Konstruktor jest używany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e39ca-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="e39ca-113">Używanie kontraktów komunikatu umożliwia wykonywanie pełnej kontroli nad komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e39ca-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="e39ca-114">W tym przykładzie <xref:System.ServiceModel.MessageHeaderAttribute> atrybut służy do put `Operation` w nagłówku protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e39ca-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="e39ca-115">Argumenty operacji `N1`, `N2` i `Result` wystąpić w treści protokołu SOAP, ponieważ mają one <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybut zastosowany.</span><span class="sxs-lookup"><span data-stu-id="e39ca-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```  
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
  
 <span data-ttu-id="e39ca-116">Klasa implementacji zawiera kod `Calculate` operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e39ca-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="e39ca-117">`CalculateService` Klas uzyskuje argumenty i operatora z komunikatu żądania i tworzy komunikat odpowiedzi, zawierający wynik żądanej operacji, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="e39ca-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="e39ca-118">Wygenerowanego kodu klienta dla klienta został utworzony z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e39ca-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="e39ca-119">Narzędzie automatycznie tworzy typy kontraktu komunikatu w kodzie wygenerowanego klienta, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="e39ca-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="e39ca-120">`/messageContract` Można określić opcji polecenia, aby wymuszenie kontraktów komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e39ca-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="e39ca-121">Następujący przykładowy kod przedstawia klienta przy użyciu `MyMessage` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e39ca-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="e39ca-122">Po uruchomieniu próbki obliczenia są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e39ca-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="e39ca-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="e39ca-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="e39ca-124">W tym momencie przekazanego niestandardowe zdefiniowane przez użytkownika wiadomości między klientem a operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e39ca-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="e39ca-125">Kontrakt komunikatu zdefiniowane, że argumenty i wyniki były w treści wiadomości i że operator w nagłówku wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e39ca-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="e39ca-126">Rejestrowanie komunikatów można skonfigurować do stosowania tej struktury wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e39ca-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e39ca-127">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="e39ca-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e39ca-128">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e39ca-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e39ca-129">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e39ca-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e39ca-130">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e39ca-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e39ca-131">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e39ca-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e39ca-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e39ca-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e39ca-133">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e39ca-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e39ca-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e39ca-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a><span data-ttu-id="e39ca-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e39ca-135">See Also</span></span>
