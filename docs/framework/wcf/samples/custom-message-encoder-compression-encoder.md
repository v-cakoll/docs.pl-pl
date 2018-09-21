---
title: 'Niestandardowy koder komunikatów: Koder kompresji'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: b70875e385fa32256476f6d1ae53e8cc1f5ff9de
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46471778"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="7066c-102">Niestandardowy koder komunikatów: Koder kompresji</span><span class="sxs-lookup"><span data-stu-id="7066c-102">Custom Message Encoder: Compression Encoder</span></span>
<span data-ttu-id="7066c-103">Ten przykład demonstruje sposób implementacji niestandardowego kodera, za pomocą platformy Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7066c-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7066c-104">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7066c-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7066c-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7066c-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7066c-106">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="7066c-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7066c-107">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7066c-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a><span data-ttu-id="7066c-108">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="7066c-108">Sample Details</span></span>  
 <span data-ttu-id="7066c-109">W tym przykładzie składa się z (.exe) klienta konsoli programu, (.exe) usługa hostowana samodzielnie konsoli programu i kompresji komunikat kodera biblioteki (.dll).</span><span class="sxs-lookup"><span data-stu-id="7066c-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="7066c-110">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="7066c-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="7066c-111">Kontrakt jest definiowany przez `ISampleServer` interfejs, który ujawnia podstawowe parametry wyświetlania operacji (`Echo` i `BigEcho`).</span><span class="sxs-lookup"><span data-stu-id="7066c-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="7066c-112">Klient wysyła żądań synchronicznych do danej operacji i odpowiedzi usługi przez powtórzenie komunikatu do klienta.</span><span class="sxs-lookup"><span data-stu-id="7066c-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="7066c-113">Aktywność klienta i usługi jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7066c-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="7066c-114">Zamiarem tego przykładu jest pokazują, jak napisać niestandardowy koder i demonstrować wpływ kompresji wiadomości na łączu.</span><span class="sxs-lookup"><span data-stu-id="7066c-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="7066c-115">Można dodać Instrumentację do kodera komunikatów kompresji, do obliczenia rozmiaru dla wiadomości i/lub czas przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="7066c-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7066c-116">W programie .NET Framework 4 dekompresja automatyczna jest ma włączone klienta WCF, jeśli serwer wysyła odpowiedź skompresowany (utworzonych za pomocą algorytmu, takich jak GZip lub Deflate).</span><span class="sxs-lookup"><span data-stu-id="7066c-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="7066c-117">W przypadku usługi sieci Web hostowanych w Internet Information Server (IIS), usługi IIS można skonfigurować do wysyłania skompresowane odpowiedzi usługi.</span><span class="sxs-lookup"><span data-stu-id="7066c-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="7066c-118">Można w tym przykładzie, jeśli wymagane jest celu kompresja i Dekompresja zarówno klient, jak i usługi lub usługi jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="7066c-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>  
  
 <span data-ttu-id="7066c-119">W przykładzie pokazano sposób tworzenia i zintegrować niestandardowy koder komunikatów aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="7066c-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="7066c-120">Biblioteka GZipEncoder.dll jest wdrażana przy użyciu zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="7066c-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="7066c-121">Niniejszy przykład pokazuje także wpływ kompresowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7066c-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="7066c-122">Kod w GZipEncoder.dll pokazuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7066c-122">The code in GZipEncoder.dll demonstrates the following:</span></span>  
  
-   <span data-ttu-id="7066c-123">Tworzenie niestandardowego kodera, a koder fabryki.</span><span class="sxs-lookup"><span data-stu-id="7066c-123">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="7066c-124">Tworzenie elementu powiązania dla niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="7066c-124">Developing a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="7066c-125">Za pomocą konfiguracji powiązania niestandardowego do integrowania elementy niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7066c-125">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="7066c-126">Tworzenie obsługi niestandardowej konfiguracji, który umożliwia skonfigurowanie pliku elementu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7066c-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
 <span data-ttu-id="7066c-127">Jak wcześniej wspomniano, istnieje kilka warstw, które są implementowane w niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="7066c-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="7066c-128">Aby lepiej zilustrować relacji między każdym z tych warstw, uproszczone kolejności zdarzeń dla uruchamiania usługi jest na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="7066c-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>  
  
1.  <span data-ttu-id="7066c-129">Serwer jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="7066c-129">The server starts.</span></span>  
  
2.  <span data-ttu-id="7066c-130">Informacje o konfiguracji jest do odczytu.</span><span class="sxs-lookup"><span data-stu-id="7066c-130">The configuration information is read.</span></span>  
  
    1.  <span data-ttu-id="7066c-131">Konfiguracja usługi rejestruje obsługi konfiguracji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="7066c-131">The service configuration registers the custom configuration handler.</span></span>  
  
    2.  <span data-ttu-id="7066c-132">Host usługi zostanie utworzony i otwarty.</span><span class="sxs-lookup"><span data-stu-id="7066c-132">The service host is created and opened.</span></span>  
  
    3.  <span data-ttu-id="7066c-133">Niestandardowy element konfiguracji, tworzy i zwraca element niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7066c-133">The custom configuration element creates and returns the custom binding element.</span></span>  
  
    4.  <span data-ttu-id="7066c-134">Element niestandardowego powiązania, tworzy i zwraca fabrykę koder komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7066c-134">The custom binding element creates and returns a message encoder factory.</span></span>  
  
3.  <span data-ttu-id="7066c-135">Wiadomość zostaje odebrana.</span><span class="sxs-lookup"><span data-stu-id="7066c-135">A message is received.</span></span>  
  
4.  <span data-ttu-id="7066c-136">Fabryki kodera komunikatów zwraca kodera komunikatów do odczytu w komunikacie i wypisywanie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7066c-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>  
  
5.  <span data-ttu-id="7066c-137">Warstwa kodera jest implementowany jako fabrykę klas.</span><span class="sxs-lookup"><span data-stu-id="7066c-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="7066c-138">Fabryka klas kodera musi być publicznie udostępniany dla niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="7066c-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="7066c-139">Obiekt fabryki jest zwracany przez element powiązania podczas <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601> obiekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="7066c-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="7066c-140">Kodery komunikat może działać w tryb buforowany lub przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="7066c-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="7066c-141">Niniejszy przykład pokazuje, zarówno w trybie buforowanego, jak i w trybie przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="7066c-141">This sample demonstrates both buffered mode and streaming mode.</span></span>  
  
 <span data-ttu-id="7066c-142">Dla każdego trybu istnieje towarzyszący `ReadMessage` i `WriteMessage` metody abstrakcyjnej `MessageEncoder` klasy.</span><span class="sxs-lookup"><span data-stu-id="7066c-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="7066c-143">Większość pracy kodowania odbywa się w tych metodach.</span><span class="sxs-lookup"><span data-stu-id="7066c-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="7066c-144">Przykład opakowuje istniejący tekst i koderów komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="7066c-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="7066c-145">Zezwala na przykład delegować odczytu i zapisu o komunikacji sieciowej reprezentacji w postaci wiadomości do wewnętrznego kodera i umożliwia koder kompresji kompresji lub dekompresji wyniki.</span><span class="sxs-lookup"><span data-stu-id="7066c-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="7066c-146">Ponieważ nie ma żadnych potoku na potrzeby kodowania komunikatu, jest tylko model dla programu WCF za pomocą koderów wielu.</span><span class="sxs-lookup"><span data-stu-id="7066c-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="7066c-147">Gdy komunikat został zdekompresowany, wynikowy wiadomości są przekazywane stosu stosu kanału do obsługi.</span><span class="sxs-lookup"><span data-stu-id="7066c-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="7066c-148">Podczas kompresji wynikowy skompresowany wiadomości są zapisywane bezpośrednio z podanego strumienia.</span><span class="sxs-lookup"><span data-stu-id="7066c-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>  
  
 <span data-ttu-id="7066c-149">W tym przykładzie użyto metody pomocnika (`CompressBuffer` i `DecompressBuffer`) do wykonywania konwersji z buforów do strumieni, aby użyć `GZipStream` klasy.</span><span class="sxs-lookup"><span data-stu-id="7066c-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>  
  
 <span data-ttu-id="7066c-150">Buforowane `ReadMessage` i `WriteMessage` wprowadzić klasy użytkowania `BufferManager` klasy.</span><span class="sxs-lookup"><span data-stu-id="7066c-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="7066c-151">Koder jest dostępna wyłącznie za pośrednictwem fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="7066c-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="7066c-152">Abstrakcyjna `MessageEncoderFactory` klasy zawiera właściwości o nazwie `Encoder` do uzyskiwania dostępu do bieżącego encoder i metodę o nazwie `CreateSessionEncoder` dla tworzenia koder, który obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="7066c-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="7066c-153">Takie koder może służyć w sytuacji, gdy kanał obsługuje sesji, porządkowania i jest niezawodne.</span><span class="sxs-lookup"><span data-stu-id="7066c-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="7066c-154">Ten scenariusz umożliwia optymalizacji w każdej sesji dane zapisywane podczas transmisji.</span><span class="sxs-lookup"><span data-stu-id="7066c-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="7066c-155">Jeśli jest to niepożądane, nie być przeciążone metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="7066c-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="7066c-156">`Encoder` Właściwość udostępnia mechanizm do uzyskiwania dostępu do mniej sesji kodera i domyślną implementację elementu `CreateSessionEncoder` metoda zwraca wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="7066c-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="7066c-157">Ponieważ próbki opakowuje istniejących koder zapewnienie kompresji, `MessageEncoderFactory` akceptuje implementacji `MessageEncoderFactory` reprezentujący fabryki wewnętrzny kodera.</span><span class="sxs-lookup"><span data-stu-id="7066c-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>  
  
 <span data-ttu-id="7066c-158">Skoro zdefiniowano encoder i fabryki kodera służy za pomocą klienta WCF i usługi.</span><span class="sxs-lookup"><span data-stu-id="7066c-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="7066c-159">Jednak te koderów należy dodać do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="7066c-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="7066c-160">Utworzeniu klasy pochodnej klasy z <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.ChannelFactory%601> klasy i zastąpienie `OnInitialize` metody, aby ręcznie dodać tę fabrykę kodera.</span><span class="sxs-lookup"><span data-stu-id="7066c-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="7066c-161">Należy również udostępnić fabryki kodera za pośrednictwem elementu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7066c-161">You can also expose the encoder factory through a custom binding element.</span></span>  
  
 <span data-ttu-id="7066c-162">Aby utworzyć nowy element niestandardowego powiązania, należy wyprowadzić klasę z <xref:System.ServiceModel.Channels.BindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="7066c-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="7066c-163">Istnieje jednak kilka typów elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="7066c-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="7066c-164">Aby upewnić się, że element niestandardowego powiązania jest rozpoznawany jako element powiązania kodowania komunikatu, należy także zaimplementować <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7066c-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="7066c-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Udostępnia metodę tworzenia nowej fabryki koder komunikatu (`CreateMessageEncoderFactory`), które jest implementowane w celu zwrócenia wystąpienia pasującego fabryki kodera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7066c-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="7066c-166">Ponadto <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> nie ma właściwości, aby wskazać, wersja adresowania.</span><span class="sxs-lookup"><span data-stu-id="7066c-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="7066c-167">Ponieważ w tym przykładzie opakowuje istniejących koderów, w przykładowej implementacji również opakowuje kodera istniejących elementów wiązania przyjmuje kodera wewnętrzny element powiązania jako parametr do konstruktora i udostępnia go za pośrednictwem właściwości.</span><span class="sxs-lookup"><span data-stu-id="7066c-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="7066c-168">Następujący przykładowy kod przedstawia implementację `GZipMessageEncodingBindingElement` klasy.</span><span class="sxs-lookup"><span data-stu-id="7066c-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>  
  
```  
public sealed class GZipMessageEncodingBindingElement   
                        : MessageEncodingBindingElement //BindingElement  
                        , IPolicyExportExtension  
{  
  
    //We use an inner binding element to store information   
    //required for the inner encoder.  
    MessageEncodingBindingElement innerBindingElement;  
  
        //By default, use the default text encoder as the inner encoder.  
        public GZipMessageEncodingBindingElement()  
            : this(new TextMessageEncodingBindingElement()) { }  
  
    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)  
    {  
        this.innerBindingElement = messageEncoderBindingElement;  
    }  
  
    public MessageEncodingBindingElement InnerMessageEncodingBindingElement  
    {  
        get { return innerBindingElement; }  
        set { innerBindingElement = value; }  
    }  
  
    //Main entry point into the encoder binding element.   
    // Called by WCF to get the factory that creates the  
    //message encoder.  
    public override MessageEncoderFactory CreateMessageEncoderFactory()  
    {  
        return new   
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get { return innerBindingElement.MessageVersion; }  
        set { innerBindingElement.MessageVersion = value; }  
    }  
  
    public override BindingElement Clone()  
    {  
        return new   
        GZipMessageEncodingBindingElement(this.innerBindingElement);  
    }  
  
    public override T GetProperty<T>(BindingContext context)  
    {  
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))  
        {  
            return innerBindingElement.GetProperty<T>(context);  
        }  
        else   
        {  
            return base.GetProperty<T>(context);  
        }  
    }  
  
    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelFactory<TChannel>();  
    }  
  
    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelListener<TChannel>();  
    }  
  
    public override bool CanBuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.CanBuildInnerChannelListener<TChannel>();  
    }  
  
    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)  
    {  
        if (policyContext == null)  
        {  
            throw new ArgumentNullException("policyContext");  
        }  
       XmlDocument document = new XmlDocument();  
       policyContext.GetBindingAssertions().Add(document.CreateElement(  
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,  
            GZipMessageEncodingPolicyConstants.GZipEncodingName,  
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));  
    }  
}  
```  
  
 <span data-ttu-id="7066c-169">Należy pamiętać, że `GZipMessageEncodingBindingElement` klasy implementuje `IPolicyExportExtension` interfejsu, tak aby ten element powiązania można wyeksportować jako zasady w metadanych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7066c-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">  
    <wsp:ExactlyOne>  
      <wsp:All>  
        <gzip:text xmlns:gzip=  
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />   
       <wsaw:UsingAddressing />   
     </wsp:All>  
   </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="7066c-170">`GZipMessageEncodingBindingElementImporter` Klasy implementuje `IPolicyImportExtension` interfejsu, ta klasa zaimportowanie zasad dla `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="7066c-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="7066c-171">Narzędzia svcutil.exe może służyć do zaimportowania zasady do pliku konfiguracji, aby obsłużyć `GZipMessageEncodingBindingElement`, dodaje do Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="7066c-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="gzipMessageEncoding"   
          type=  
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </bindingElementExtensions>  
    </extensions>  
    <client>  
      <metadata>  
        <policyImporters>  
          <remove type=  
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
          <extension type=  
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7066c-172">Teraz, czy jest pasujący element powiązania dla koder kompresji, jego mogą być programowo dołączane do usługi lub klienta tworząc nowy obiekt niestandardowego powiązania i Dodawanie elementu niestandardowego powiązania, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7066c-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 <span data-ttu-id="7066c-173">Chociaż może to być wystarczające w większości scenariuszy użytkowników, obsługa plik konfiguracyjny ma krytyczne znaczenie, jeśli usługa ma być hostowane w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7066c-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="7066c-174">Aby zapewnić obsługę scenariusza hostingu w sieci Web, możesz tworzyć obsługi niestandardowej konfiguracji, aby zezwolić na element niestandardowego powiązania umożliwiać konfigurację w pliku.</span><span class="sxs-lookup"><span data-stu-id="7066c-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>  
  
 <span data-ttu-id="7066c-175">Można utworzyć program obsługi konfiguracji dla elementu powiązania na podstawie dostarczonych przez system konfiguracji [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7066c-175">You can build a configuration handler for the binding element on top of the configuration system provided by the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="7066c-176">Obsługa konfiguracji element powiązania musi pochodzić od klasy <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="7066c-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="7066c-177">`BindingElementType` Właściwość jest używana w celu poinformowania systemu konfiguracji typu elementu powiązania do utworzenia dla tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7066c-177">The `BindingElementType` property is used to inform the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="7066c-178">Wszystkie aspekty `BindingElement` , może być zestaw powinny zostać ujawnione jako właściwości na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7066c-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="7066c-179"><xref:System.Configuration.ConfigurationPropertyAttribute> Jest używany jako pomoc w mapowania atrybutów elementów konfiguracji do właściwości i ustawianie wartości domyślnych, jeśli atrybuty są spełnione.</span><span class="sxs-lookup"><span data-stu-id="7066c-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> is used to assist in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="7066c-180">Po wartości z konfiguracji zostaną załadowane i zastosowane do właściwości, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> wywoływana jest metoda, która konwertuje właściwości na konkretne wystąpienie elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="7066c-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="7066c-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Metoda jest używana do konwersji właściwości na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy pochodnej na wartości, które ma być ustawiony na element powiązania newlycreated.</span><span class="sxs-lookup"><span data-stu-id="7066c-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newlycreated binding element.</span></span>  
  
 <span data-ttu-id="7066c-182">Następujący przykładowy kod przedstawia implementację `GZipMessageEncodingElement`.</span><span class="sxs-lookup"><span data-stu-id="7066c-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>  
  
```  
public class GZipMessageEncodingElement : BindingElementExtensionElement  
{  
    public GZipMessageEncodingElement()  
    {  
    }  
  
//Called by the WCF to discover the type of binding element this   
//config section enables  
    public override Type BindingElementType  
    {  
        get { return typeof(GZipMessageEncodingBindingElement); }  
    }  
  
    //The only property we need to configure for our binding element is   
    //the type of inner encoder to use. Here, we support text and  
    //binary.  
    [ConfigurationProperty("innerMessageEncoding",   
                         DefaultValue = "textMessageEncoding")]  
    public string InnerMessageEncoding  
    {  
        get { return (string)base["innerMessageEncoding"]; }  
        set { base["innerMessageEncoding"] = value; }  
    }  
  
    //Called by the WCF to apply the configuration settings (the   
    //property above) to the binding element  
    public override void ApplyConfiguration(BindingElement bindingElement)  
    {  
        GZipMessageEncodingBindingElement binding =   
                (GZipMessageEncodingBindingElement)bindingElement;  
        PropertyInformationCollection propertyInfo =   
                    this.ElementInformation.Properties;  
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=   
                                     PropertyValueOrigin.Default)  
        {  
            switch (this.InnerMessageEncoding)  
            {  
                case "textMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                      new TextMessageEncodingBindingElement();  
                    break;  
                case "binaryMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                         new BinaryMessageEncodingBindingElement();  
                    break;  
            }  
        }  
    }  
  
    //Called by the WCF to create the binding element  
    protected override BindingElement CreateBindingElement()  
    {  
        GZipMessageEncodingBindingElement bindingElement =   
                new GZipMessageEncodingBindingElement();  
        this.ApplyConfiguration(bindingElement);  
        return bindingElement;  
    }  
}   
```  
  
 <span data-ttu-id="7066c-183">Ta procedura obsługi konfiguracji mapuje następujące reprezentacja w pliku App.config lub Web.config, usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="7066c-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 <span data-ttu-id="7066c-184">Aby korzystać z tej obsługi konfiguracji, musi być zarejestrowana w ramach [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="7066c-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
       <add   
           name="gzipMessageEncoding"   
           type=  
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,  
           GZipEncoder, Version=1.0.0.0, Culture=neutral,   
           PublicKeyToken=null" />  
      </bindingElementExtensions>  
</extensions>  
```  
  
 <span data-ttu-id="7066c-185">Po uruchomieniu serwera, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7066c-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="7066c-186">Naciśnij klawisz ENTER w oknie do zamykania serwera.</span><span class="sxs-lookup"><span data-stu-id="7066c-186">Press ENTER in the window to shut down the server.</span></span>  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 <span data-ttu-id="7066c-187">Po uruchomieniu klienta, operacji żądań i odpowiedzi są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7066c-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="7066c-188">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="7066c-188">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7066c-189">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="7066c-189">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7066c-190">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="7066c-190">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="7066c-191">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7066c-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="7066c-192">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7066c-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="7066c-193">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7066c-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7066c-194">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7066c-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7066c-195">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7066c-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7066c-196">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="7066c-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7066c-197">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7066c-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a><span data-ttu-id="7066c-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7066c-198">See Also</span></span>
