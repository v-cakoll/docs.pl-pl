---
title: "Niestandardowy koder komunikatów: Niestandardowy koder tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54e2b87a9e104ea61c32b06ffc604fc864283f3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="c7621-102">Niestandardowy koder komunikatów: Niestandardowy koder tekstu</span><span class="sxs-lookup"><span data-stu-id="c7621-102">Custom Message Encoder: Custom Text Encoder</span></span>
<span data-ttu-id="c7621-103">W tym przykładzie pokazano, jak zaimplementować tekst niestandardowy koder komunikatów, przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7621-103">This sample demonstrates how to implement a custom text message encoder using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c7621-104">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c7621-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7621-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c7621-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c7621-106">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="c7621-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7621-107">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c7621-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <span data-ttu-id="c7621-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje tylko kodowania UTF-8, UTF-16 i Big Endean Unicode.</span><span class="sxs-lookup"><span data-stu-id="c7621-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only the UTF-8, UTF-16 and Big Endean Unicode encodings.</span></span> <span data-ttu-id="c7621-109">Tekst niestandardowy koder komunikatów w tym przykładzie obsługuje wszystkie obsługiwane platformy kodowanie znaków, które mogą być wymagane ze względu na współdziałanie.</span><span class="sxs-lookup"><span data-stu-id="c7621-109">The custom text message encoder in this sample supports all platform-supported character encoding that may be required for interoperability.</span></span> <span data-ttu-id="c7621-110">Próbka składa się z konsoli programu klienckiego (.exe), Usługa biblioteki (.dll), obsługiwane przez usługi Internet Information Services (IIS) i tekst biblioteki kodera wiadomości (.dll).</span><span class="sxs-lookup"><span data-stu-id="c7621-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS) and a text message encoder library (.dll).</span></span> <span data-ttu-id="c7621-111">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="c7621-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c7621-112">Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia).</span><span class="sxs-lookup"><span data-stu-id="c7621-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="c7621-113">Klient wysyła żądań synchronicznych operacji matematycznych danego i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="c7621-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="c7621-114">Zarówno klient, jak i usługa używa `CustomTextMessageEncoder` zamiast domyślnej <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="c7621-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>  
  
 <span data-ttu-id="c7621-115">Implementacji niestandardowego kodera składa się z fabryki kodera wiadomości, kodera wiadomości, kodowanie elementu powiązania i konfiguracji obsługi wiadomości i pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="c7621-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>  
  
-   <span data-ttu-id="c7621-116">Tworzenie niestandardowego kodera i fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="c7621-116">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="c7621-117">Tworzenie elementu powiązania dla niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="c7621-117">Creating a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="c7621-118">Za pomocą konfiguracji powiązania niestandardowego do integracji elementy niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c7621-118">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="c7621-119">Tworzenie konfiguracji niestandardowej obsługi umożliwia konfigurację pliku element niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c7621-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7621-120">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="c7621-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c7621-121">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c7621-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="c7621-122">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7621-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="c7621-123">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7621-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c7621-124">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7621-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="c7621-125">Fabryka kodera wiadomości i koder komunikatów</span><span class="sxs-lookup"><span data-stu-id="c7621-125">Message Encoder Factory and the Message Encoder</span></span>  
 <span data-ttu-id="c7621-126">Gdy <xref:System.ServiceModel.ServiceHost> lub klient otworzyć kanału, składnik czasu projektowania `CustomTextMessageBindingElement` tworzy `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="c7621-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="c7621-127">Tworzy fabrykę `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="c7621-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="c7621-128">Koder komunikatów działa zarówno w trybie przesyłania strumieniowego i tryb buforowany.</span><span class="sxs-lookup"><span data-stu-id="c7621-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="c7621-129">Używa <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do odczytu i zapisu wiadomości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c7621-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="c7621-130">Zamiast zoptymalizowane czytników XML i autorzy z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługują tylko UTF-8, UTF-16, jak i Unicode Big-Endean tych czytników i zapisywania obsługuje wszystkie obsługiwane platformy kodowania.</span><span class="sxs-lookup"><span data-stu-id="c7621-130">As opposed to the optimized XML readers and writers of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that support only UTF-8, UTF-16 and Big-Endean Unicode these readers and writers support all platform supported encoding.</span></span>  
  
 <span data-ttu-id="c7621-131">Poniższy przykład kodu pokazuje CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="c7621-131">The following code example shows the CustomTextMessageEncoder.</span></span>  
  
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
        this.contentType = string.Format("{0}; charset={1}",   
            this.factory.MediaType, this.writerSettings.Encoding.HeaderName);  
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
  
 <span data-ttu-id="c7621-132">W poniższym przykładzie przedstawiono sposób zbudować fabryki kodera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7621-132">The following code example shows how to build the message encoder factory.</span></span>  
  
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
  
## <a name="message-encoding-binding-element"></a><span data-ttu-id="c7621-133">Element powiązania kodowania komunikatu</span><span class="sxs-lookup"><span data-stu-id="c7621-133">Message Encoding Binding Element</span></span>  
 <span data-ttu-id="c7621-134">Elementy można konfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c7621-134">The binding elements allow the configuration of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] run-time stack.</span></span> <span data-ttu-id="c7621-135">Aby użyć niestandardowy koder komunikatów w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikację, wymagany jest element powiązania tworzącą fabryki kodera wiadomości z odpowiednimi ustawieniami na odpowiednim poziomie w stosie czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c7621-135">To use the custom message encoder in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>  
  
 <span data-ttu-id="c7621-136">`CustomTextMessageBindingElement` Pochodną <xref:System.ServiceModel.Channels.BindingElement> klasa podstawowa i dziedziczy <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="c7621-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="c7621-137">Dzięki temu innych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składniki rozpoznanie tego elementu powiązania jako powiązanie element kodowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c7621-137">This allows other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="c7621-138">Implementacja <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> Zwraca wystąpienie klasy pasującej fabryki kodera wiadomości z odpowiednimi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="c7621-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>  
  
 <span data-ttu-id="c7621-139">`CustomTextMessageBindingElement` Udostępnia ustawienia dla `MessageVersion`, `ContentType`, i `Encoding` za pośrednictwem właściwości.</span><span class="sxs-lookup"><span data-stu-id="c7621-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="c7621-140">Koder obsługuje zarówno Soap11Addressing i Soap12Addressing1 wersji.</span><span class="sxs-lookup"><span data-stu-id="c7621-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="c7621-141">Wartość domyślna to Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="c7621-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="c7621-142">Wartość domyślna `ContentType` jest "text/xml".</span><span class="sxs-lookup"><span data-stu-id="c7621-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="c7621-143">`Encoding` Właściwości można ustawić kodowanie znaków żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="c7621-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="c7621-144">Przykładowe klient i usługa używa kodowania znaków ISO 8859-1 (Latin1), który nie jest obsługiwany przez <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7621-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="c7621-145">Poniższy kod przedstawia sposób programowo Utwórz powiązanie, używając tekst niestandardowy koder komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c7621-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="c7621-146">Dodawanie obsługi metadanych do kodowania, Element wiązania komunikatu</span><span class="sxs-lookup"><span data-stu-id="c7621-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>  
 <span data-ttu-id="c7621-147">Dowolnego typu, która jest pochodną <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> jest odpowiedzialny za aktualizowanie wersji powiązania SOAP w dokumencie WSDL wygenerowany dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c7621-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="c7621-148">W tym celu implementowania `ExportEndpoint` metody w <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejs, a następnie modyfikując wygenerowanego WSDL.</span><span class="sxs-lookup"><span data-stu-id="c7621-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="c7621-149">W tym przykładzie `CustomTextMessageBindingElement` używa logiki eksportu WSDL `TextMessageEncodingBinidngElement`.</span><span class="sxs-lookup"><span data-stu-id="c7621-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBinidngElement`.</span></span>  
  
 <span data-ttu-id="c7621-150">Dla tego przykładu Konfiguracja klienta jest skonfigurowane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="c7621-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="c7621-151">Nie można użyć Svcutil.exe do wygenerowania konfiguracji klienta, ponieważ `CustomTextMessageBindingElement` nie eksportuje potwierdzenia zasad, opisujący zachowanie.</span><span class="sxs-lookup"><span data-stu-id="c7621-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="c7621-152">Ogólnie należy zaimplementować <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejsu na element niestandardowego powiązania, aby wyeksportować potwierdzenia zasad niestandardowych, opisujący zachowanie lub możliwości implementowane przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="c7621-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="c7621-153">Na przykład sposobu eksportowania potwierdzenia zasad dla elementu niestandardowego powiązania zobacz [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="c7621-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="c7621-154">Program obsługi konfiguracji powiązania Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="c7621-154">Message Encoding Binding Configuration Handler</span></span>  
 <span data-ttu-id="c7621-155">Poprzedniej sekcji pokazano, jak używać tekstu niestandardowego kodera wiadomości programowo.</span><span class="sxs-lookup"><span data-stu-id="c7621-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="c7621-156">`CustomTextMessageEncodingBindingSection` Implementuje obsługi konfiguracji, która pozwala określić niestandardowy komunikat koder tekstu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c7621-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="c7621-157">`CustomTextMessageEncodingBindingSection` Pochodną klasy <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="c7621-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="c7621-158">`BindingElementType` Właściwości informuje system konfiguracji typu elementu powiązania, aby utworzyć dla tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="c7621-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>  
  
 <span data-ttu-id="c7621-159">Wszystkie ustawienia zdefiniowane przez `CustomTextMessageBindingElement` są widoczne jako właściwości w `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="c7621-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="c7621-160"><xref:System.Configuration.ConfigurationPropertyAttribute> Pomaga w Mapowanie atrybutów elementów konfiguracji do właściwości i ustawianie wartości domyślnych, jeśli nie ustawiono atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c7621-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="c7621-161">Po wartości z konfiguracji są ładowane i stosowane do właściwości typu <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda jest wywoływana, który konwertuje na konkretne wystąpienie elementu powiązania właściwości.</span><span class="sxs-lookup"><span data-stu-id="c7621-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>  
  
 <span data-ttu-id="c7621-162">Ten program obsługi konfiguracji mapuje następujące reprezentacja w pliku App.config lub Web.config dla usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="c7621-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 <span data-ttu-id="c7621-163">W przykładzie zastosowano kodowanie ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="c7621-163">The sample uses the ISO-8859-1 encoding.</span></span>  
  
 <span data-ttu-id="c7621-164">Aby użyć tej obsługi konfiguracji, które muszą być zarejestrowane przy użyciu następującego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c7621-164">To use this configuration handler it must be registered using the following configuration element.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7621-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7621-165">See Also</span></span>
