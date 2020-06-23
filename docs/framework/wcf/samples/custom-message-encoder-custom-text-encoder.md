---
title: 'Niestandardowy koder komunikatów: Niestandardowy koder tekstu'
description: Użyj tego przykładu, aby zaimplementować niestandardowy koder komunikatów tekstowych przy użyciu programu WCF. Ten koder obsługuje wszystkie kodowanie znaków obsługiwane przez platformę na potrzeby współdziałania.
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88ddc79e6cc1df654aea851cedb0e60c6fbcd017
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246275"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="3f422-104">Niestandardowy koder komunikatów: Niestandardowy koder tekstu</span><span class="sxs-lookup"><span data-stu-id="3f422-104">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="3f422-105">W tym przykładzie przedstawiono sposób implementacji niestandardowego kodera komunikatów tekstowych przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3f422-105">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="3f422-106">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3f422-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3f422-107">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3f422-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3f422-108">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="3f422-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f422-109">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3f422-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="3f422-110">W programie <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF obsługiwane są tylko kodowania UTF-8, UTF-16 i big-endian.</span><span class="sxs-lookup"><span data-stu-id="3f422-110">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="3f422-111">Koder niestandardowej wiadomości tekstowej w tym przykładzie obsługuje wszystkie kodowania znaków obsługiwane przez platformę, które mogą być wymagane w celu współdziałania.</span><span class="sxs-lookup"><span data-stu-id="3f422-111">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="3f422-112">Przykład składa się z programu konsoli klienta (exe), biblioteki usług (. dll) hostowanej przez Internet Information Services (IIS) i biblioteki kodera wiadomości tekstowych (. dll).</span><span class="sxs-lookup"><span data-stu-id="3f422-112">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="3f422-113">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="3f422-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="3f422-114">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie).</span><span class="sxs-lookup"><span data-stu-id="3f422-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="3f422-115">Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a usługa zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="3f422-115">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="3f422-116">Zarówno klient, jak i usługa używa `CustomTextMessageEncoder` zamiast domyślnego <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="3f422-116">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="3f422-117">Implementacja kodera niestandardowego składa się z fabryki kodera komunikatów, kodera komunikatów, elementu powiązania kodowania komunikatów i programu obsługi konfiguracji, a następnie ilustruje następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="3f422-117">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="3f422-118">Kompilowanie kodera niestandardowego i fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="3f422-118">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="3f422-119">Tworzenie elementu powiązania dla kodera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3f422-119">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="3f422-120">Używanie konfiguracji niestandardowego powiązania do integrowania niestandardowych elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f422-120">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="3f422-121">Opracowywanie niestandardowego programu obsługi konfiguracji w celu zezwolenia na konfigurację pliku niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f422-121">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3f422-122">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="3f422-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3f422-123">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="3f422-123">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="3f422-124">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f422-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="3f422-125">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f422-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="3f422-126">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f422-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="3f422-127">Fabryka koderów komunikatów i koder komunikatów</span><span class="sxs-lookup"><span data-stu-id="3f422-127">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="3f422-128">Po <xref:System.ServiceModel.ServiceHost> otwarciu lub uruchomieniu kanału klienta składnik czasu projektowania `CustomTextMessageBindingElement` tworzy `CustomTextMessageEncoderFactory` .</span><span class="sxs-lookup"><span data-stu-id="3f422-128">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="3f422-129">Fabryka tworzy `CustomTextMessageEncoder` .</span><span class="sxs-lookup"><span data-stu-id="3f422-129">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="3f422-130">Koder komunikatów działa zarówno w trybie przesyłania strumieniowego, jak i w trybie buforowanym.</span><span class="sxs-lookup"><span data-stu-id="3f422-130">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="3f422-131">Używa <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do odczytu i zapisu wiadomości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3f422-131">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="3f422-132">W przeciwieństwie do zoptymalizowanych czytników XML i autorów programu WCF, które obsługują tylko UTF-8, UTF-16 i big-endian Unicode, te czytelnicy i autorzy obsługują wszystkie kodowanie obsługiwane przez platformę.</span><span class="sxs-lookup"><span data-stu-id="3f422-132">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="3f422-133">Poniższy przykład kodu przedstawia CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="3f422-133">The following code example shows the CustomTextMessageEncoder.</span></span>

```csharp
public class CustomTextMessageEncoder : MessageEncoder
{
    private CustomTextMessageEncoderFactory factory;
    private XmlWriterSettings writerSettings;
    private string contentType;

    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)
    {
        this.factory = factory;

        this.writerSettings = new XmlWriterSettings();
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);
        this.contentType = $"{this.factory.MediaType}; charset={this.writerSettings.Encoding.HeaderName}";
    }

    public override string ContentType
    {
        get
        {
            return this.contentType;
        }
    }

    public override string MediaType
    {
        get
        {
            return factory.MediaType;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.factory.MessageVersion;
        }
    }

    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)
    {
        byte[] msgContents = new byte[buffer.Count];
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);
        bufferManager.ReturnBuffer(buffer.Array);

        MemoryStream stream = new MemoryStream(msgContents);
        return ReadMessage(stream, int.MaxValue);
    }

    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)
    {
        XmlReader reader = XmlReader.Create(stream);
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);
    }

    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)
    {
        MemoryStream stream = new MemoryStream();
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();

        byte[] messageBytes = stream.GetBuffer();
        int messageLength = (int)stream.Position;
        stream.Close();

        int totalLength = messageLength + messageOffset;
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);

        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);
        return byteArray;
    }

    public override void WriteMessage(Message message, Stream stream)
    {
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();
    }
}
```

<span data-ttu-id="3f422-134">Poniższy przykład kodu pokazuje, jak utworzyć fabrykę kodera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3f422-134">The following code example shows how to build the message encoder factory.</span></span>

```csharp
public class CustomTextMessageEncoderFactory : MessageEncoderFactory
{
    private MessageEncoder encoder;
    private MessageVersion version;
    private string mediaType;
    private string charSet;

    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,
        MessageVersion version)
    {
        this.version = version;
        this.mediaType = mediaType;
        this.charSet = charSet;
        this.encoder = new CustomTextMessageEncoder(this);
    }

    public override MessageEncoder Encoder
    {
        get
        {
            return this.encoder;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.version;
        }
    }

    internal string MediaType
    {
        get
        {
            return this.mediaType;
        }
    }

    internal string CharSet
    {
        get
        {
            return this.charSet;
        }
    }
}
```

## <a name="message-encoding-binding-element"></a><span data-ttu-id="3f422-135">Element powiązania kodowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="3f422-135">Message Encoding Binding Element</span></span>

<span data-ttu-id="3f422-136">Elementy powiązania umożliwiają konfigurację stosu wykonawczego programu WCF.</span><span class="sxs-lookup"><span data-stu-id="3f422-136">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="3f422-137">Aby użyć niestandardowego kodera komunikatów w aplikacji WCF, wymagany jest element powiązania, który tworzy fabrykę kodera komunikatów z odpowiednimi ustawieniami na odpowiednim poziomie w stosie czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3f422-137">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="3f422-138">`CustomTextMessageBindingElement`Pochodzi z <xref:System.ServiceModel.Channels.BindingElement> klasy bazowej i dziedziczy z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="3f422-138">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="3f422-139">Dzięki temu inne składniki usługi WCF mogą rozpoznać ten element powiązania jako element powiązania kodowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3f422-139">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="3f422-140">Implementacja <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> zwraca wystąpienie zgodnej fabryki kodera komunikatów z odpowiednimi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="3f422-140">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="3f422-141">`CustomTextMessageBindingElement`Uwidacznia ustawienia dla `MessageVersion` , `ContentType` i `Encoding` za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="3f422-141">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="3f422-142">Koder obsługuje zarówno wersje Soap11Addressing, jak i Soap12Addressing1.</span><span class="sxs-lookup"><span data-stu-id="3f422-142">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="3f422-143">Wartość domyślna to Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="3f422-143">The default is Soap11Addressing1.</span></span> <span data-ttu-id="3f422-144">Wartość domyślna `ContentType` to "text/xml".</span><span class="sxs-lookup"><span data-stu-id="3f422-144">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="3f422-145">`Encoding`Właściwość pozwala ustawić wartość kodowania żądanego znaku.</span><span class="sxs-lookup"><span data-stu-id="3f422-145">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="3f422-146">Przykładowy klient i usługa używają kodowania znaków ISO-8859-1 (Latin1), które nie jest obsługiwane przez program <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.</span><span class="sxs-lookup"><span data-stu-id="3f422-146">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="3f422-147">Poniższy kod pokazuje, jak programowo utworzyć powiązanie przy użyciu niestandardowego kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="3f422-147">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="3f422-148">Dodawanie obsługi metadanych do elementu powiązania kodowania komunikatu</span><span class="sxs-lookup"><span data-stu-id="3f422-148">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="3f422-149">Każdy typ pochodzący od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> jest odpowiedzialny za aktualizowanie wersji powiązania protokołu SOAP w dokumencie WSDL wygenerowanym dla usługi.</span><span class="sxs-lookup"><span data-stu-id="3f422-149">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="3f422-150">Jest to realizowane przez implementację `ExportEndpoint` metody w <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsie, a następnie zmodyfikowanie wygenerowanego WSDL.</span><span class="sxs-lookup"><span data-stu-id="3f422-150">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="3f422-151">W tym przykładzie `CustomTextMessageBindingElement` używa logiki eksportu WSDL z `TextMessageEncodingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="3f422-151">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="3f422-152">W tym przykładzie konfiguracja klienta jest konfigurowana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="3f422-152">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="3f422-153">Nie można użyć Svcutil.exe do wygenerowania konfiguracji klienta, ponieważ nie `CustomTextMessageBindingElement` eksportuje potwierdzenia zasad, aby opisać jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="3f422-153">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="3f422-154">Należy zwykle zaimplementować <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejs na elemencie powiązania niestandardowego, aby wyeksportować potwierdzenie zasad niestandardowych, który opisuje zachowanie lub możliwość implementowaną przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f422-154">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="3f422-155">Aby zapoznać się z przykładem sposobu eksportowania potwierdzenia zasad dla elementu niestandardowego powiązania, zapoznaj się z przykładem [transport: UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="3f422-155">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="3f422-156">Procedura obsługi konfiguracji powiązania kodowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="3f422-156">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="3f422-157">W poprzedniej sekcji pokazano, jak programowo używać niestandardowego kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="3f422-157">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="3f422-158">`CustomTextMessageEncodingBindingSection`Implementacja programu obsługi konfiguracji, która pozwala określić użycie niestandardowego kodera komunikatów tekstowych w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3f422-158">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="3f422-159">`CustomTextMessageEncodingBindingSection`Klasa pochodzi od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="3f422-159">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="3f422-160">`BindingElementType`Właściwość informuje system konfiguracji typu elementu powiązania, który ma zostać utworzony dla tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3f422-160">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="3f422-161">Wszystkie ustawienia zdefiniowane przez `CustomTextMessageBindingElement` są udostępniane jako właściwości w `CustomTextMessageEncodingBindingSection` .</span><span class="sxs-lookup"><span data-stu-id="3f422-161">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="3f422-162"><xref:System.Configuration.ConfigurationPropertyAttribute>Pomaga w mapowaniu atrybutów elementu konfiguracji do właściwości i ustawiania wartości domyślnych, jeśli atrybut nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="3f422-162">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="3f422-163">Po załadowaniu wartości z konfiguracji i zastosowaniu ich do właściwości typu <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> Metoda zostaje wywołana, co spowoduje konwersję właściwości w konkretnym wystąpieniu elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f422-163">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="3f422-164">Ta procedura obsługi konfiguracji mapuje do następującej reprezentacji w App.config lub Web.config dla usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="3f422-164">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="3f422-165">Przykład używa kodowania ISO-8859-1.</span><span class="sxs-lookup"><span data-stu-id="3f422-165">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="3f422-166">Aby użyć tego programu obsługi konfiguracji, należy go zarejestrować przy użyciu następującego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3f422-166">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
