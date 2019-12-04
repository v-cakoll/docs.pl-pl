---
title: Ustawianie właściwości use i style — przykłady WCF
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f92b25144759692c54aa7a1730a9bb85cab4f15f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714437"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="25635-102">Ustawianie właściwości Use i Style</span><span class="sxs-lookup"><span data-stu-id="25635-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="25635-103">Ten przykład ilustruje sposób użycia właściwości use i style na <xref:System.ServiceModel.XmlSerializerFormatAttribute> i <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25635-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="25635-104">Te właściwości wpływają na sposób formatowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="25635-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="25635-105">Domyślnie treść komunikatu jest formatowana stylem ustawionym na <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="25635-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="25635-106">Te ustawienia można określić na poziomie kontraktu usługi lub na poziomie kontraktu operacji.</span><span class="sxs-lookup"><span data-stu-id="25635-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="25635-107">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="25635-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="25635-108">Właściwość Style <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> określa sposób formatowania metadanych WSDL dla usługi.</span><span class="sxs-lookup"><span data-stu-id="25635-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="25635-109">Możliwe wartości to <xref:System.ServiceModel.OperationFormatStyle.Document>i <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="25635-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="25635-110">RPC oznacza, że reprezentacja WSDL komunikatów wymienianych dla operacji zawiera parametry tak, jakby były zdalnego wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="25635-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="25635-111">Poniżej przedstawiono przykład.</span><span class="sxs-lookup"><span data-stu-id="25635-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="25635-112">Ustawienie stylu na <xref:System.ServiceModel.OperationFormatStyle.Document> oznacza, że reprezentacja WSDL zawiera pojedynczy element reprezentujący dokument wymieniany dla operacji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="25635-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="25635-113">Właściwość <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> określa format wiadomości.</span><span class="sxs-lookup"><span data-stu-id="25635-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="25635-114">Możliwe wartości to <xref:System.ServiceModel.OperationFormatUse.Literal> i <xref:System.ServiceModel.OperationFormatUse.Encoded>; wartość domyślna to <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="25635-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="25635-115">Literał oznacza, że komunikat jest wystąpieniem literału schematu w języku WSDL, jak pokazano w poniższym przykładzie dokumentu/literału.</span><span class="sxs-lookup"><span data-stu-id="25635-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="25635-116">Zakodowane oznacza, że schematy w języku WSDL są specyfikacjami abstrakcyjnymi, które są kodowane zgodnie z regułami znalezionymi w sekcji SOAP 1,1 sekcja 5.</span><span class="sxs-lookup"><span data-stu-id="25635-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="25635-117">Poniżej znajduje się przykład RPC/Encoded.</span><span class="sxs-lookup"><span data-stu-id="25635-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="25635-118">Profil WS-I Basic 1,0 zabrania używania <xref:System.ServiceModel.OperationFormatUse.Encoded> i należy go używać tylko wtedy, gdy jest to wymagane przez starsze usługi.</span><span class="sxs-lookup"><span data-stu-id="25635-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="25635-119">Format komunikatu `Encoded` jest dostępny tylko w przypadku korzystania z elementu XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="25635-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="25635-120">Aby umożliwić wyświetlanie wysyłanych i odbieranych komunikatów, ten przykład jest oparty na [śledzeniu i rejestrowaniu komunikatów](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="25635-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="25635-121">Konfiguracja usługi i kod źródłowy zostały zmodyfikowane w celu włączenia śledzenia i rejestrowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="25635-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="25635-122">Ponadto <xref:System.ServiceModel.WSHttpBinding> została skonfigurowana bez zabezpieczeń, dlatego zarejestrowane komunikaty mogą być wyświetlane w nieszyfrowanym formacie.</span><span class="sxs-lookup"><span data-stu-id="25635-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="25635-123">Wynikowe dzienniki śledzenia (System. ServiceModel. e2e i Message. log) powinny być przeglądane przy użyciu [narzędzia Podgląd śledzenia usługi (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="25635-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="25635-124">Ślady są konfigurowane do utworzenia w folderze C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="25635-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="25635-125">Utwórz folder przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="25635-125">Create the folder before running the sample.</span></span> <span data-ttu-id="25635-126">Aby wyświetlić zawartość wiadomości w narzędziu Podgląd śledzenia, wybierz pozycję **komunikaty** w lewym okienku narzędzia.</span><span class="sxs-lookup"><span data-stu-id="25635-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="25635-127">Poniższy kod przedstawia kontrakt usługi z właściwością <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ustawioną na <xref:System.ServiceModel.OperationFormatUse> i format treści wiadomości został zmieniony z domyślnej <xref:System.ServiceModel.OperationFormatStyle> na <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="25635-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="25635-128">Aby zobaczyć różnicę między różnymi ustawieniami <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> i <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A>, zmodyfikuj je w usłudze, ponownie Wygeneruj klienta, uruchom przykład i sprawdź plik c:\logs\Message.Logs za pomocą narzędzia Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="25635-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="25635-129">Zaobserwuj również wpływ na metadane, wyświetlając `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="25635-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="25635-130">Metadane usług są zwykle podzielone na wiele stron.</span><span class="sxs-lookup"><span data-stu-id="25635-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="25635-131">Główna strona WSDL zawiera powiązania WSDL, ale Wyświetl `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0`, aby obserwować definicje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="25635-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="25635-132">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="25635-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="25635-133">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25635-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="25635-134">Utwórz katalog C:\LOGS na potrzeby rejestrowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="25635-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="25635-135">Nadaj użytkownikom uprawnienia do zapisu w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="25635-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="25635-136">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25635-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="25635-137">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25635-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25635-138">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="25635-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="25635-139">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="25635-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="25635-140">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25635-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="25635-141">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="25635-141">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
