---
title: Ustawianie przykładów właściwości Użyj i Styl
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f400c0bc08588afa951ae33f221663b47b37602c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144035"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="144bb-102">Ustawianie właściwości Use i Style</span><span class="sxs-lookup"><span data-stu-id="144bb-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="144bb-103">W tym przykładzie pokazano, jak używać Use <xref:System.ServiceModel.XmlSerializerFormatAttribute> i <xref:System.ServiceModel.DataContractFormatAttribute>Style właściwości na i .</span><span class="sxs-lookup"><span data-stu-id="144bb-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="144bb-104">Te właściwości wpływają na sposób formatowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="144bb-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="144bb-105">Domyślnie treść wiadomości jest sformatowana <xref:System.ServiceModel.OperationFormatStyle.Document>ze stylem ustawionym na .</span><span class="sxs-lookup"><span data-stu-id="144bb-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="144bb-106">Te ustawienia można określić na poziomie umowy serwisowej lub na poziomie kontraktu operacji.</span><span class="sxs-lookup"><span data-stu-id="144bb-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="144bb-107">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="144bb-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="144bb-108">Właściwość <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style określa sposób formatowania metadanych WSDL dla usługi.</span><span class="sxs-lookup"><span data-stu-id="144bb-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="144bb-109">Możliwe wartości <xref:System.ServiceModel.OperationFormatStyle.Document>to <xref:System.ServiceModel.OperationFormatStyle.Rpc>, i .</span><span class="sxs-lookup"><span data-stu-id="144bb-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="144bb-110">RPC oznacza, że reprezentacja WSDL wiadomości wymienianych na operację zawiera parametry tak, jakby było to zdalne wywołanie procedury.</span><span class="sxs-lookup"><span data-stu-id="144bb-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="144bb-111">Poniżej przedstawiono przykład.</span><span class="sxs-lookup"><span data-stu-id="144bb-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="144bb-112">Ustawienie stylu <xref:System.ServiceModel.OperationFormatStyle.Document> oznacza, że reprezentacja WSDL zawiera pojedynczy element, który reprezentuje dokument, który jest wymieniany na operację, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="144bb-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="144bb-113">Właściwość <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> określa format wiadomości.</span><span class="sxs-lookup"><span data-stu-id="144bb-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="144bb-114">Możliwe wartości <xref:System.ServiceModel.OperationFormatUse.Literal> <xref:System.ServiceModel.OperationFormatUse.Encoded>są i ; wartością domyślną jest <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="144bb-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="144bb-115">Literal oznacza, że wiadomość jest dosłownym wystąpieniem schematu w WSDL, jak pokazano w poniższym przykładzie Document/ Literal.</span><span class="sxs-lookup"><span data-stu-id="144bb-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="144bb-116">Zakodowane oznacza, że schematy w WSDL są specyfikacje abstrakcyjne, które są zakodowane zgodnie z regułami znalezionymi w soap 1.1 sekcji 5.</span><span class="sxs-lookup"><span data-stu-id="144bb-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="144bb-117">Poniżej przedstawiono przykład RPC/Encoded.</span><span class="sxs-lookup"><span data-stu-id="144bb-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="144bb-118">Profil podstawowy WS-I 1.0 zabrania <xref:System.ServiceModel.OperationFormatUse.Encoded> używania go i należy go używać tylko wtedy, gdy jest to wymagane przez starsze usługi.</span><span class="sxs-lookup"><span data-stu-id="144bb-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="144bb-119">Format `Encoded` wiadomości jest dostępny tylko w przypadku korzystania z XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="144bb-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="144bb-120">Aby umożliwić wyświetlanie wysyłanych i odbieranych wiadomości, ten przykład jest oparty na [śledzeniu i rejestrowaniu wiadomości.](tracing-and-message-logging.md)</span><span class="sxs-lookup"><span data-stu-id="144bb-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="144bb-121">Konfiguracja usługi i kod źródłowy zostały zmodyfikowane, aby włączyć i korzystać z śledzenia i rejestrowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="144bb-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="144bb-122">Ponadto <xref:System.ServiceModel.WSHttpBinding> został skonfigurowany bez zabezpieczeń, dzięki czemu rejestrowane wiadomości mogą być wyświetlane w formacie niezaszyfrowanym.</span><span class="sxs-lookup"><span data-stu-id="144bb-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="144bb-123">Wynikowe dzienniki śledzenia (System.ServiceModel.e2e i Message.log) powinny być przeglądane za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer.exe).](../service-trace-viewer-tool-svctraceviewer-exe.md)</span><span class="sxs-lookup"><span data-stu-id="144bb-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="144bb-124">Ślady są skonfigurowane do tworzenia w folderze C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="144bb-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="144bb-125">Utwórz folder przed uruchomieniem próbki.</span><span class="sxs-lookup"><span data-stu-id="144bb-125">Create the folder before running the sample.</span></span> <span data-ttu-id="144bb-126">Aby wyświetlić zawartość wiadomości w narzędziu Podgląd śledzenia, wybierz pozycję **Wiadomości** zarówno w lewym, jak i prawym okienku narzędzia.</span><span class="sxs-lookup"><span data-stu-id="144bb-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="144bb-127">Poniższy kod przedstawia umowę <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> serwisową <xref:System.ServiceModel.OperationFormatUse> z właściwością ustawioną na i <xref:System.ServiceModel.OperationFormatStyle> <xref:System.ServiceModel.OperationFormatStyle.Document>format treści wiadomości zmienioną z domyślnej na .</span><span class="sxs-lookup"><span data-stu-id="144bb-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="144bb-128">Aby zobaczyć różnicę między <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> różnymi ustawieniami, zmodyfikuj je w usłudze, ponownie wygeneruj klienta, uruchom próbkę i sprawdź plik c:\logs\message.logs za pomocą narzędzia Podgląd śledzenia usług.</span><span class="sxs-lookup"><span data-stu-id="144bb-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="144bb-129">Obserwuj również wpływ na metadane, przeglądając `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="144bb-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="144bb-130">Metadane dla usług są zazwyczaj podzielone na wiele stron.</span><span class="sxs-lookup"><span data-stu-id="144bb-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="144bb-131">Główna strona wsdl zawiera powiązania WSDL, `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` ale widok do przestrzegania definicji wiadomości.</span><span class="sxs-lookup"><span data-stu-id="144bb-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="144bb-132">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="144bb-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="144bb-133">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="144bb-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="144bb-134">Utwórz katalog C:\LOGS do rejestrowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="144bb-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="144bb-135">Nadaj użytkownikowi uprawnienia do zapisu usługi sieciowej dla tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="144bb-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="144bb-136">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="144bb-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="144bb-137">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="144bb-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="144bb-138">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="144bb-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="144bb-139">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="144bb-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="144bb-140">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="144bb-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="144bb-141">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="144bb-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
