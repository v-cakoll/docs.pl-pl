---
title: 'Niestandardowy koder komunikatów: niestandardowy Koder tekstu — WCF'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 3d421aa40488deac487418b5ecc83c5dd420fdf4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281682"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="f6b95-102">Niestandardowy koder komunikatów: Niestandardowy koder tekstu</span><span class="sxs-lookup"><span data-stu-id="f6b95-102">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="f6b95-103">W tym przykładzie przedstawiono sposób implementacji niestandardowego kodera komunikatów tekstowych przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f6b95-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="f6b95-104">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f6b95-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f6b95-105">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="f6b95-105">Check for the following (default) directory before continuing.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> <span data-ttu-id="f6b95-106">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6b95-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6b95-107">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f6b95-107">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="f6b95-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF obsługuje tylko kodowania Unicode UTF-8, UTF-16 i big-endian.</span><span class="sxs-lookup"><span data-stu-id="f6b95-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="f6b95-109">Koder niestandardowej wiadomości tekstowej w tym przykładzie obsługuje wszystkie kodowania znaków obsługiwane przez platformę, które mogą być wymagane w celu współdziałania.</span><span class="sxs-lookup"><span data-stu-id="f6b95-109">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="f6b95-110">Przykład składa się z programu konsoli klienta (exe), biblioteki usług (. dll) hostowanej przez Internet Information Services (IIS) i biblioteki kodera wiadomości tekstowych (. dll).</span><span class="sxs-lookup"><span data-stu-id="f6b95-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="f6b95-111">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="f6b95-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="f6b95-112">Kontrakt jest definiowany przez interfejs `ICalculator`, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie).</span><span class="sxs-lookup"><span data-stu-id="f6b95-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="f6b95-113">Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a usługa zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="f6b95-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="f6b95-114">Zarówno klient, jak i usługa używają `CustomTextMessageEncoder` zamiast domyślnej <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f6b95-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="f6b95-115">Implementacja kodera niestandardowego składa się z fabryki kodera komunikatów, kodera komunikatów, elementu powiązania kodowania komunikatów i programu obsługi konfiguracji, a następnie ilustruje następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="f6b95-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="f6b95-116">Kompilowanie kodera niestandardowego i fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="f6b95-116">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="f6b95-117">Tworzenie elementu powiązania dla kodera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f6b95-117">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="f6b95-118">Używanie konfiguracji niestandardowego powiązania do integrowania niestandardowych elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6b95-118">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="f6b95-119">Opracowywanie niestandardowego programu obsługi konfiguracji w celu zezwolenia na konfigurację pliku niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6b95-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f6b95-120">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="f6b95-120">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f6b95-121">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f6b95-121">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="f6b95-122">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6b95-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="f6b95-123">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6b95-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="f6b95-124">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6b95-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="f6b95-125">Fabryka koderów komunikatów i koder komunikatów</span><span class="sxs-lookup"><span data-stu-id="f6b95-125">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="f6b95-126">Gdy zostanie otwarty <xref:System.ServiceModel.ServiceHost> lub kanał klienta, składnik czasu projektowania `CustomTextMessageBindingElement` tworzy `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="f6b95-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="f6b95-127">Fabryka tworzy `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="f6b95-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="f6b95-128">Koder komunikatów działa zarówno w trybie przesyłania strumieniowego, jak i w trybie buforowanym.</span><span class="sxs-lookup"><span data-stu-id="f6b95-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="f6b95-129">Używa <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do odczytu i zapisu wiadomości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f6b95-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="f6b95-130">W przeciwieństwie do zoptymalizowanych czytników XML i autorów programu WCF, które obsługują tylko UTF-8, UTF-16 i big-endian Unicode, te czytelnicy i autorzy obsługują wszystkie kodowanie obsługiwane przez platformę.</span><span class="sxs-lookup"><span data-stu-id="f6b95-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="f6b95-131">Poniższy przykład kodu przedstawia CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="f6b95-131">The following code example shows the CustomTextMessageEncoder.</span></span>

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

<span data-ttu-id="f6b95-132">Poniższy przykład kodu pokazuje, jak utworzyć fabrykę kodera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f6b95-132">The following code example shows how to build the message encoder factory.</span></span>

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

## <a name="message-encoding-binding-element"></a><span data-ttu-id="f6b95-133">Element powiązania kodowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="f6b95-133">Message Encoding Binding Element</span></span>

<span data-ttu-id="f6b95-134">Elementy powiązania umożliwiają konfigurację stosu wykonawczego programu WCF.</span><span class="sxs-lookup"><span data-stu-id="f6b95-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="f6b95-135">Aby użyć niestandardowego kodera komunikatów w aplikacji WCF, wymagany jest element powiązania, który tworzy fabrykę kodera komunikatów z odpowiednimi ustawieniami na odpowiednim poziomie w stosie czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f6b95-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="f6b95-136">`CustomTextMessageBindingElement` pochodzi od klasy bazowej <xref:System.ServiceModel.Channels.BindingElement> i dziedziczy z klasy <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f6b95-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="f6b95-137">Dzięki temu inne składniki usługi WCF mogą rozpoznać ten element powiązania jako element powiązania kodowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f6b95-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="f6b95-138">Implementacja <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> zwraca wystąpienie pasującej fabryki kodera komunikatów z odpowiednimi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="f6b95-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="f6b95-139">`CustomTextMessageBindingElement` uwidacznia ustawienia dla `MessageVersion`, `ContentType`i `Encoding` przez właściwości.</span><span class="sxs-lookup"><span data-stu-id="f6b95-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="f6b95-140">Koder obsługuje zarówno wersje Soap11Addressing, jak i Soap12Addressing1.</span><span class="sxs-lookup"><span data-stu-id="f6b95-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="f6b95-141">Wartość domyślna to Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="f6b95-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="f6b95-142">Wartość domyślna `ContentType` to "text/xml".</span><span class="sxs-lookup"><span data-stu-id="f6b95-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="f6b95-143">Właściwość `Encoding` umożliwia ustawienie wartości żądanego kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="f6b95-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="f6b95-144">Przykładowy klient i usługa używają kodowania znaków ISO-8859-1 (Latin1), które nie jest obsługiwane przez <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.</span><span class="sxs-lookup"><span data-stu-id="f6b95-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="f6b95-145">Poniższy kod pokazuje, jak programowo utworzyć powiązanie przy użyciu niestandardowego kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="f6b95-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="f6b95-146">Dodawanie obsługi metadanych do elementu powiązania kodowania komunikatu</span><span class="sxs-lookup"><span data-stu-id="f6b95-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="f6b95-147">Każdy typ, który pochodzi od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> jest odpowiedzialny za aktualizowanie wersji powiązania protokołu SOAP w dokumencie WSDL wygenerowanym dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f6b95-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="f6b95-148">Jest to realizowane przez implementację metody `ExportEndpoint` w interfejsie <xref:System.ServiceModel.Description.IWsdlExportExtension>, a następnie zmodyfikowanie wygenerowanego WSDL.</span><span class="sxs-lookup"><span data-stu-id="f6b95-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="f6b95-149">W tym przykładzie `CustomTextMessageBindingElement` używa logiki eksportu WSDL z `TextMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="f6b95-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="f6b95-150">W tym przykładzie konfiguracja klienta jest konfigurowana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="f6b95-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="f6b95-151">Nie można użyć Svcutil. exe do wygenerowania konfiguracji klienta, ponieważ `CustomTextMessageBindingElement` nie eksportuje potwierdzenia zasad, aby opisać jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f6b95-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="f6b95-152">Należy zwykle zaimplementować interfejs <xref:System.ServiceModel.Description.IPolicyExportExtension> w elemencie powiązania niestandardowego, aby wyeksportować potwierdzenie zasad niestandardowych, który opisuje zachowanie lub możliwość implementowaną przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6b95-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="f6b95-153">Aby zapoznać się z przykładem sposobu eksportowania potwierdzenia zasad dla elementu niestandardowego powiązania, zapoznaj się z przykładem [transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="f6b95-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="f6b95-154">Procedura obsługi konfiguracji powiązania kodowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="f6b95-154">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="f6b95-155">W poprzedniej sekcji pokazano, jak programowo używać niestandardowego kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="f6b95-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="f6b95-156">`CustomTextMessageEncodingBindingSection` implementuje procedurę obsługi konfiguracji, która pozwala określić użycie niestandardowego kodera komunikatów tekstowych w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f6b95-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="f6b95-157">Klasa `CustomTextMessageEncodingBindingSection` dziedziczy z klasy <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="f6b95-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="f6b95-158">Właściwość `BindingElementType` informuje system konfiguracji typu elementu powiązania, który ma zostać utworzony dla tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f6b95-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="f6b95-159">Wszystkie ustawienia zdefiniowane przez `CustomTextMessageBindingElement` są uwidocznione jako właściwości w `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="f6b95-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="f6b95-160"><xref:System.Configuration.ConfigurationPropertyAttribute> pomaga w mapowaniu atrybutów elementu konfiguracji do właściwości i ustawiania wartości domyślnych, jeśli atrybut nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="f6b95-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="f6b95-161">Po załadowaniu wartości z konfiguracji i zastosowaniu ich do właściwości typu, wywoływana jest metoda <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A>, która konwertuje właściwości na konkretne wystąpienie elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6b95-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="f6b95-162">Ta procedura obsługi konfiguracji mapuje do następującej reprezentacji w pliku App. config lub Web. config dla usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="f6b95-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="f6b95-163">Przykład używa kodowania ISO-8859-1.</span><span class="sxs-lookup"><span data-stu-id="f6b95-163">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="f6b95-164">Aby użyć tego programu obsługi konfiguracji, należy go zarejestrować przy użyciu następującego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f6b95-164">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type=" 
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection, 
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
