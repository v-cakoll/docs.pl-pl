---
title: "Ustawianie właściwości Use i Style"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 21409597b8fe27992c08bbe76f56e78013156c46
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="7456f-102">Ustawianie właściwości Use i Style</span><span class="sxs-lookup"><span data-stu-id="7456f-102">Setting the Use and Style Properties</span></span>
<span data-ttu-id="7456f-103">W tym przykładzie przedstawiono sposób użycia właściwości Use i Style na <xref:System.ServiceModel.XmlSerializerFormatAttribute> i <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7456f-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="7456f-104">Te właściwości mają wpływ na sposób sformatowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7456f-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="7456f-105">Domyślnie treść komunikatu jest sformatowany przy użyciu stylu ustawioną <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="7456f-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="7456f-106">Te ustawienia można określić w poziomie kontrakt usługi lub na poziomie kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="7456f-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7456f-107">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7456f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7456f-108"><xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Właściwości stylu określa, jak metadanych WSDL usługi jest sformatowany.</span><span class="sxs-lookup"><span data-stu-id="7456f-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="7456f-109">Możliwe wartości to <xref:System.ServiceModel.OperationFormatStyle.Document>, i <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="7456f-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="7456f-110">RPC oznacza, że reprezentacja wiadomości wymieniane operacji WSDL zawiera parametry, tak jakby był on zdalne wywołanie procedury.</span><span class="sxs-lookup"><span data-stu-id="7456f-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="7456f-111">Poniżej przedstawiono przykład.</span><span class="sxs-lookup"><span data-stu-id="7456f-111">The following is an example.</span></span>  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 <span data-ttu-id="7456f-112">Ustawienie stylu <xref:System.ServiceModel.OperationFormatStyle.Document> oznacza, że reprezentacja WSDL zawiera pojedynczy element, który reprezentuje dokumentu, które są wymieniane dla danej operacji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7456f-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <span data-ttu-id="7456f-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Właściwość określa format komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7456f-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="7456f-114">Możliwe wartości to <xref:System.ServiceModel.OperationFormatUse.Literal> i <xref:System.ServiceModel.OperationFormatUse.Encoded>; wartość domyślna to <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="7456f-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="7456f-115">Literał oznacza, że wiadomości jest literału wystąpienie schematu w formacie WSDL, jak pokazano w następującym dokumencie / literału przykład.</span><span class="sxs-lookup"><span data-stu-id="7456f-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 <span data-ttu-id="7456f-116">Zakodowany oznacza, że schematy w formacie WSDL są specyfikacje abstrakcyjna, które są zakodowane zgodnie z regułami w SOAP 1.1 sekcji 5.</span><span class="sxs-lookup"><span data-stu-id="7456f-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="7456f-117">Poniżej przedstawiono przykład RPC/Encoded.</span><span class="sxs-lookup"><span data-stu-id="7456f-117">The following is an RPC/Encoded example.</span></span>  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 <span data-ttu-id="7456f-118">WS-I podstawowe 1.0 profilu zabrania stosowania <xref:System.ServiceModel.OperationFormatUse.Encoded> i należy używać tylko gdy wymagane przez starszej wersji usługi.</span><span class="sxs-lookup"><span data-stu-id="7456f-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="7456f-119">`Encoded` Format komunikatu jest dostępna tylko, gdy użycie XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="7456f-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>  
  
 <span data-ttu-id="7456f-120">Aby umożliwić wyświetlanie wiadomości wysyłanych i odbieranych, w tym przykładzie jest oparta na [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="7456f-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span> <span data-ttu-id="7456f-121">Konfiguracji usługi i kod źródłowy został zmodyfikowany w celu włączenia i wykorzystania śledzenie i rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7456f-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="7456f-122">Ponadto <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> został skonfigurowany bez zabezpieczeń, dlatego zarejestrowane komunikaty, które można wyświetlić w niezaszyfrowanej postaci.</span><span class="sxs-lookup"><span data-stu-id="7456f-122">In addition, the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="7456f-123">Wynikowy dzienniki śledzenia (System.ServiceModel.e2e i Message.log) powinien wyświetlać przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7456f-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="7456f-124">Dane śledzenia są skonfigurowane do utworzenia w folderze C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="7456f-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="7456f-125">Przed uruchomieniem próbki, należy utworzyć folder.</span><span class="sxs-lookup"><span data-stu-id="7456f-125">Create the folder before running the sample.</span></span> <span data-ttu-id="7456f-126">Zaznacz, aby wyświetlić zawartość wiadomości w narzędziu Podgląd śledzenia **wiadomości** zarówno lewego i prawego okienka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="7456f-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>  
  
 <span data-ttu-id="7456f-127">Poniższy kod przedstawia kontraktu usługi o <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ustawioną właściwość <xref:System.ServiceModel.OperationFormatUse> i zmienić formatu treści wiadomości z domyślnego <xref:System.ServiceModel.OperationFormatStyle> do <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="7456f-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,   
                                 Use = OperationFormatUse.Encoded)]  
public interface IUseAndStyleCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="7456f-128">Różnice między różnymi <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> i <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ustawienia, zmodyfikuj je w usłudze, ponownie wygenerować klienta uruchomić przykładowy i zapoznaj się z plikiem c:\logs\message.logs za pomocą narzędzia podglądu śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="7456f-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="7456f-129">Wyświetlając http://localhost/ServiceModelSamples/service.svc?wsdl również obserwować wpływ na metadanych.</span><span class="sxs-lookup"><span data-stu-id="7456f-129">Also observe the impact on the metadata by viewing http://localhost/ServiceModelSamples/service.svc?wsdl.</span></span> <span data-ttu-id="7456f-130">Metadane dla usługi jest zwykle podzielony na wiele stron.</span><span class="sxs-lookup"><span data-stu-id="7456f-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="7456f-131">Na stronie głównej wsdl zawiera powiązania WSDL, ale wyświetlać http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 obserwować definicje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7456f-131">The main wsdl page contains the WSDL bindings, but view http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 to observe the message definitions.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7456f-132">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="7456f-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7456f-133">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7456f-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7456f-134">Utwórz katalog C:\LOGS rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7456f-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="7456f-135">Przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="7456f-135">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="7456f-136">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7456f-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="7456f-137">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7456f-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7456f-138">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7456f-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7456f-139">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7456f-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7456f-140">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="7456f-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7456f-141">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7456f-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a><span data-ttu-id="7456f-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7456f-142">See Also</span></span>
