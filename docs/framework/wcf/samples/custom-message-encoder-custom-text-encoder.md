---
title: 'Niestandardowy koder komunikatów: Niestandardowy koder tekstu — usługi WCF'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: a1523c854bbae09b2ac5cb0565962b394ec9b70e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003083"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="37556-102">Niestandardowy koder komunikatów: Niestandardowy koder tekstu</span><span class="sxs-lookup"><span data-stu-id="37556-102">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="37556-103">Ten przykład demonstruje sposób implementacji tekst niestandardowy koder komunikatów, za pomocą usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="37556-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="37556-104">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="37556-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37556-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="37556-105">Check for the following (default) directory before continuing.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> <span data-ttu-id="37556-106">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="37556-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37556-107">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="37556-107">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="37556-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> Programu WCF obsługuje tylko kodowania Unicode UTF-8, UTF-16 i big-endian.</span><span class="sxs-lookup"><span data-stu-id="37556-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="37556-109">Koder komunikatów niestandardowego tekstu, w tym przykładzie obsługuje wszystkie kodowania znaków obsługiwanej przez platformę, które mogą być wymagane do współdziałania.</span><span class="sxs-lookup"><span data-stu-id="37556-109">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="37556-110">Przykład składa się z (.exe) klienta konsoli programu service biblioteki (.dll), hostowanej przez Internetowe usługi informacyjne (IIS) i tekst wiadomości kodera biblioteki (.dll).</span><span class="sxs-lookup"><span data-stu-id="37556-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="37556-111">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="37556-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="37556-112">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia).</span><span class="sxs-lookup"><span data-stu-id="37556-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="37556-113">Klient wysyła żądań synchronicznych operacji matematycznych danego i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="37556-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="37556-114">Zarówno klient, jak i usługa używa `CustomTextMessageEncoder` zamiast domyślnego <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="37556-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="37556-115">Implementacji niestandardowego kodera składa się z fabryki kodera komunikatów, kodera komunikatów, komunikatu kodowanie elementu powiązania i obsługi konfiguracji i pokazuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="37556-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="37556-116">Tworzenie niestandardowego kodera, a koder fabryki.</span><span class="sxs-lookup"><span data-stu-id="37556-116">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="37556-117">Tworzenie elementu powiązania dla niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="37556-117">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="37556-118">Za pomocą konfiguracji powiązania niestandardowego do integrowania elementy niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="37556-118">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="37556-119">Tworzenie obsługi niestandardowej konfiguracji, który umożliwia skonfigurowanie pliku elementu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="37556-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37556-120">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="37556-120">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="37556-121">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="37556-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>

    ```
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="37556-122">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37556-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="37556-123">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37556-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="37556-124">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37556-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="37556-125">Fabryki kodera komunikatów i kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="37556-125">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="37556-126">Gdy <xref:System.ServiceModel.ServiceHost> lub klient zostanie otwarty kanał, składnik czasu projektowania `CustomTextMessageBindingElement` tworzy `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="37556-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="37556-127">Tworzy fabrykę `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="37556-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="37556-128">Koder komunikatów działa zarówno w trybie przesyłania strumieniowego i tryb buforowany.</span><span class="sxs-lookup"><span data-stu-id="37556-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="37556-129">Używa ona <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do odczytu i zapisu wiadomości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="37556-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="37556-130">W przeciwieństwie do zoptymalizowane XML czytników i składników zapisywania WCF, które obsługują tylko UTF-8 UTF-16 i big-endian Unicode, te czytników i składników zapisywania kodowanie jest obsługiwane przez wszystkie obsługiwane platformy.</span><span class="sxs-lookup"><span data-stu-id="37556-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="37556-131">Poniższy przykład kodu pokazuje CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="37556-131">The following code example shows the CustomTextMessageEncoder.</span></span>

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

<span data-ttu-id="37556-132">Poniższy przykład kodu pokazuje, jak tworzyć fabryki kodera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="37556-132">The following code example shows how to build the message encoder factory.</span></span>

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

## <a name="message-encoding-binding-element"></a><span data-ttu-id="37556-133">Element powiązania kodowania komunikatu</span><span class="sxs-lookup"><span data-stu-id="37556-133">Message Encoding Binding Element</span></span>

<span data-ttu-id="37556-134">Elementy powiązania umożliwiają konfigurację stos środowiska wykonawczego programu WCF.</span><span class="sxs-lookup"><span data-stu-id="37556-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="37556-135">Aby użyć niestandardowy koder komunikatów w aplikacji WCF, wymagany jest element powiązania tworząca fabryki kodera komunikatów z odpowiednimi ustawieniami na odpowiednim poziomie w stosie czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="37556-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="37556-136">`CustomTextMessageBindingElement` Pochodzi od klasy <xref:System.ServiceModel.Channels.BindingElement> klasy bazowej i dziedziczy <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="37556-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="37556-137">Dzięki temu inne składniki usługi WCF do rozpoznawania tego elementu powiązania jako element powiązania z kodowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="37556-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="37556-138">Implementacja <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> Zwraca wystąpienie pasującego fabryki kodera komunikatów za pomocą odpowiednich ustawień.</span><span class="sxs-lookup"><span data-stu-id="37556-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="37556-139">`CustomTextMessageBindingElement` Udostępnia ustawienia dla `MessageVersion`, `ContentType`, i `Encoding` za pośrednictwem właściwości.</span><span class="sxs-lookup"><span data-stu-id="37556-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="37556-140">Koder obsługuje zarówno Soap11Addressing, jak i Soap12Addressing1 wersji.</span><span class="sxs-lookup"><span data-stu-id="37556-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="37556-141">Wartość domyślna to Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="37556-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="37556-142">Wartość domyślna `ContentType` jest "text/xml".</span><span class="sxs-lookup"><span data-stu-id="37556-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="37556-143">`Encoding` Właściwość można ustawić wartości kodowania żądany znak.</span><span class="sxs-lookup"><span data-stu-id="37556-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="37556-144">Przykładowy klient i usługa używa ISO-8859-1 (Latin1) kodowanie znaków, które nie są obsługiwane przez <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> programu WCF.</span><span class="sxs-lookup"><span data-stu-id="37556-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="37556-145">Poniższy kod pokazuje, jak programowo utworzyć powiązania za pomocą tekst niestandardowy koder komunikatów.</span><span class="sxs-lookup"><span data-stu-id="37556-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="37556-146">Dodanie obsługi metadanych do kodowania, Element powiązania komunikatu</span><span class="sxs-lookup"><span data-stu-id="37556-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="37556-147">Dowolny typ, który pochodzi od klasy <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> jest odpowiedzialny za aktualizowanie wersji powiązania protokołu SOAP w dokumencie WSDL, wygenerowany dla usługi.</span><span class="sxs-lookup"><span data-stu-id="37556-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="37556-148">Polega to na implementowanie `ExportEndpoint` metody <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu, a następnie zmodyfikowanie wygenerowanego pliku WSDL.</span><span class="sxs-lookup"><span data-stu-id="37556-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="37556-149">W tym przykładzie `CustomTextMessageBindingElement` używa logiki eksportu WSDL `TextMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="37556-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="37556-150">W tym przykładzie konfiguracja klienta jest skonfigurowane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="37556-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="37556-151">Nie można użyć Svcutil.exe do generowania konfiguracji klienta, ponieważ `CustomTextMessageBindingElement` nie eksportuje asercję zasad w celu opisania jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="37556-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="37556-152">Ogólnie należy zaimplementować <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejsu na element niestandardowego powiązania, aby wyeksportować asercji zasad niestandardowych, opisujący zachowanie lub możliwości implementowane przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="37556-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="37556-153">Na przykład sposobu eksportowania asercję zasad dla elementu niestandardowego powiązania zobacz [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="37556-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="37556-154">Program obsługi konfiguracji powiązania kodowania komunikatu</span><span class="sxs-lookup"><span data-stu-id="37556-154">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="37556-155">Poprzedniej sekcji pokazano, jak programowo używać tekst niestandardowy koder komunikatów.</span><span class="sxs-lookup"><span data-stu-id="37556-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="37556-156">`CustomTextMessageEncodingBindingSection` Implementuje obsługi konfiguracji, który pozwala określić niestandardowy komunikat koder tekstu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="37556-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="37556-157">`CustomTextMessageEncodingBindingSection` Klasa pochodzi od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="37556-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="37556-158">`BindingElementType` Właściwość informuje system konfiguracji typu elementu powiązania do utworzenia dla tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="37556-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="37556-159">Wszystkie ustawienia zdefiniowane przez `CustomTextMessageBindingElement` są widoczne jako właściwości w `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="37556-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="37556-160"><xref:System.Configuration.ConfigurationPropertyAttribute> Pomaga w mapowania atrybutów elementów konfiguracji do właściwości i ustawianie wartości domyślnych, jeśli ten atrybut nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="37556-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="37556-161">Po wartości z konfiguracji zostaną załadowane i zastosowane do właściwości typu <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> wywoływana jest metoda, która konwertuje właściwości na konkretne wystąpienie elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="37556-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="37556-162">Ta procedura obsługi konfiguracji mapuje następujące reprezentacja w pliku App.config lub Web.config, usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="37556-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="37556-163">W przykładzie użyto kodowania ISO-8859-1.</span><span class="sxs-lookup"><span data-stu-id="37556-163">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="37556-164">Aby użyć tej obsługi konfiguracji, które muszą być zarejestrowane przy użyciu następującego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="37556-164">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type=" 
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection, 
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
