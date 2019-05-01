---
title: Ustawianie właściwości Use i Style - przykłady WCF
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 64cf64cf5d53ef0dfb4bc38cf86f91c7acd2e5af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007867"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="a8170-102">Ustawianie właściwości Use i Style</span><span class="sxs-lookup"><span data-stu-id="a8170-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="a8170-103">W tym przykładzie pokazano, jak korzystać z właściwości Use i Style na <xref:System.ServiceModel.XmlSerializerFormatAttribute> i <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a8170-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="a8170-104">Te właściwości mają wpływ na sposób sformatowanych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a8170-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="a8170-105">Domyślnie, treść komunikatu jest sformatowany przy użyciu stylu równa <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="a8170-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="a8170-106">Te ustawienia można określić na poziomie kontraktu usługi lub poziomu kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="a8170-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
>  <span data-ttu-id="a8170-107">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a8170-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a8170-108"><xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Właściwość stylu określa sposób formatowania metadanych WSDL usługi.</span><span class="sxs-lookup"><span data-stu-id="a8170-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="a8170-109">Możliwe wartości to <xref:System.ServiceModel.OperationFormatStyle.Document>, i <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="a8170-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="a8170-110">RPC oznacza, że reprezentacja WSDL komunikatów wymienianych operacji zawiera parametry, tak jakby zdalnego wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="a8170-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="a8170-111">Oto przykład.</span><span class="sxs-lookup"><span data-stu-id="a8170-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="a8170-112">Ustawienie stylu <xref:System.ServiceModel.OperationFormatStyle.Document> oznacza, że reprezentacja WSDL zawiera pojedynczy element, który reprezentuje dokument, który są wymieniane dla danej operacji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a8170-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="a8170-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Właściwość określa format wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a8170-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="a8170-114">Możliwe wartości to <xref:System.ServiceModel.OperationFormatUse.Literal> i <xref:System.ServiceModel.OperationFormatUse.Encoded>; wartość domyślna to <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="a8170-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="a8170-115">Literał oznacza, że komunikat jest literału wystąpienia schematu w formacie WSDL, jak pokazano w następującym dokumencie / literału przykładu.</span><span class="sxs-lookup"><span data-stu-id="a8170-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="a8170-116">Zakodowany oznacza, że schematy w formacie WSDL są abstrakcyjne specyfikacje, które są zakodowane zgodnie z regułami w SOAP 1.1 sekcji 5.</span><span class="sxs-lookup"><span data-stu-id="a8170-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="a8170-117">Oto przykład RPC/zakodowane.</span><span class="sxs-lookup"><span data-stu-id="a8170-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="a8170-118">WS-I Basic 1.0 profilu zabraniają używania <xref:System.ServiceModel.OperationFormatUse.Encoded> i należy używać tylko ją, gdy jest to wymagane przez starszej wersji usługi.</span><span class="sxs-lookup"><span data-stu-id="a8170-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="a8170-119">`Encoded` Format komunikatu jest dostępna tylko, gdy za pomocą elementu XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="a8170-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="a8170-120">Aby umożliwić wyświetlanie komunikatów wysyłanych i odbieranych, ten przykład jest oparty na [śledzenia i rejestrowania komunikatów](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="a8170-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="a8170-121">Aby włączyć i wykorzystywać śledzenie i rejestrowanie komunikatów zostały zmodyfikowane konfiguracji usługi i kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="a8170-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="a8170-122">Ponadto <xref:System.ServiceModel.WSHttpBinding> została skonfigurowana bez bezpieczeństwa dlatego zarejestrowane komunikaty mogą być wyświetlane w postaci niezaszyfrowanej.</span><span class="sxs-lookup"><span data-stu-id="a8170-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="a8170-123">Wynikowy dzienniki śledzenia (System.ServiceModel.e2e i Message.log) powinna być przeglądana przy użyciu [narzędzie śledzenia usług (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a8170-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="a8170-124">Ślady są skonfigurowane do utworzony w folderze C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="a8170-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="a8170-125">Utwórz folder przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="a8170-125">Create the folder before running the sample.</span></span> <span data-ttu-id="a8170-126">Zaznacz, aby wyświetlić zawartość wiadomości za pomocą narzędzia podglądu śledzenia **wiadomości** zarówno po lewej stronie, jak i prawego okienka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="a8170-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="a8170-127">Poniższy kod przedstawia kontraktu usługi o <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> właściwością <xref:System.ServiceModel.OperationFormatUse> i format treści wiadomości, zmienić domyślną opcję <xref:System.ServiceModel.OperationFormatStyle> do <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="a8170-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

```csharp
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

<span data-ttu-id="a8170-128">Aby zobaczyć różnicę między różnymi <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> i <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ustawienia, zmodyfikuj je w usłudze, ponownie wygenerować klienta, uruchom aplikację przykładową i zapoznaj się z plikiem c:\logs\message.logs za pomocą narzędzia przeglądarki danych śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="a8170-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="a8170-129">Również obserwować wpływ na metadane, wyświetlając `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="a8170-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="a8170-130">Metadane dla usług jest zazwyczaj dzielone na wielu stronach.</span><span class="sxs-lookup"><span data-stu-id="a8170-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="a8170-131">Na stronie głównej wsdl zawiera powiązania WSDL, ale wyświetlać `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` do obserwowania definicje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a8170-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8170-132">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="a8170-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a8170-133">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8170-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a8170-134">Utwórz katalog C:\LOGS rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a8170-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="a8170-135">Przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="a8170-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="a8170-136">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8170-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="a8170-137">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8170-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8170-138">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a8170-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8170-139">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a8170-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a8170-140">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="a8170-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8170-141">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a8170-141">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`