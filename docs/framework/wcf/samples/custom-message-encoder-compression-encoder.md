---
title: 'Niestandardowy koder komunikatów: Koder kompresji'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: db20ec20579d6fcb0ec202920db0d7781b0676df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600623"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="820f2-102">Niestandardowy koder komunikatów: Koder kompresji</span><span class="sxs-lookup"><span data-stu-id="820f2-102">Custom Message Encoder: Compression Encoder</span></span>

<span data-ttu-id="820f2-103">Ten przykład ilustruje sposób implementacji kodera niestandardowego przy użyciu platformy Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="820f2-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="820f2-104">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="820f2-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="820f2-105">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="820f2-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="820f2-106">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="820f2-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="820f2-107">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="820f2-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a><span data-ttu-id="820f2-108">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="820f2-108">Sample Details</span></span>

<span data-ttu-id="820f2-109">Ten przykład składa się z programu konsolowego klienta (exe), samodzielnego programu obsługi konsoli usług (exe) i biblioteki kodera komunikatów kompresji (. dll).</span><span class="sxs-lookup"><span data-stu-id="820f2-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="820f2-110">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="820f2-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="820f2-111">Kontrakt jest definiowany przez `ISampleServer` interfejs, który ujawnia podstawowe operacje ECHA ciągów ( `Echo` i `BigEcho` ).</span><span class="sxs-lookup"><span data-stu-id="820f2-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="820f2-112">Klient wykonuje synchroniczne żądania do danej operacji i odpowiedzi usługi przez powtarzanie komunikatu z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="820f2-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="820f2-113">Działanie klienta i usługi jest widoczne w oknach konsoli.</span><span class="sxs-lookup"><span data-stu-id="820f2-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="820f2-114">Celem tego przykładu jest pokazanie sposobu pisania kodera niestandardowego i zademonstrowanie wpływu kompresji wiadomości w sieci.</span><span class="sxs-lookup"><span data-stu-id="820f2-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="820f2-115">Można dodać instrumentację do kodera komunikatu kompresji, aby obliczyć rozmiar wiadomości, czas przetwarzania lub oba te elementy.</span><span class="sxs-lookup"><span data-stu-id="820f2-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>

> [!NOTE]
> <span data-ttu-id="820f2-116">W .NET Framework 4 funkcja automatycznej dekompresji została włączona na kliencie WCF, jeśli serwer wysyła skompresowaną odpowiedź (utworzono przy użyciu algorytmu, takiego jak GZip lub Wklęśnięcie).</span><span class="sxs-lookup"><span data-stu-id="820f2-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="820f2-117">Jeśli usługa jest hostowana w sieci Web w programie Internet Information Server (IIS), można skonfigurować usługi IIS do wysyłania skompresowanej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="820f2-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="820f2-118">Tego przykładu można użyć, jeśli wymagane jest kompresowanie i dekompresja zarówno klienta, jak i usługi, albo jeśli usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="820f2-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>

<span data-ttu-id="820f2-119">W przykładzie pokazano, jak skompilować i zintegrować niestandardowy koder komunikatów z aplikacją WCF.</span><span class="sxs-lookup"><span data-stu-id="820f2-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="820f2-120">Biblioteka GZipEncoder. dll jest wdrażana razem z klientem i usługą.</span><span class="sxs-lookup"><span data-stu-id="820f2-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="820f2-121">Ten przykład ilustruje także wpływ kompresowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="820f2-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="820f2-122">Kod w GZipEncoder. dll ilustruje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="820f2-122">The code in GZipEncoder.dll demonstrates the following:</span></span>

- <span data-ttu-id="820f2-123">Kompilowanie kodera niestandardowego i fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="820f2-123">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="820f2-124">Tworzenie elementu powiązania dla kodera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="820f2-124">Developing a binding element for a custom encoder.</span></span>

- <span data-ttu-id="820f2-125">Używanie konfiguracji niestandardowego powiązania do integrowania niestandardowych elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="820f2-125">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="820f2-126">Opracowywanie niestandardowego programu obsługi konfiguracji w celu zezwolenia na konfigurację pliku niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="820f2-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

<span data-ttu-id="820f2-127">Jak wskazano wcześniej, istnieje kilka warstw, które są zaimplementowane w niestandardowym koderie.</span><span class="sxs-lookup"><span data-stu-id="820f2-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="820f2-128">Aby lepiej zilustrować relacje między każdą z tych warstw, uproszczona kolejność zdarzeń dla uruchamiania usługi znajduje się na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="820f2-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>

1. <span data-ttu-id="820f2-129">Serwer zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="820f2-129">The server starts.</span></span>

2. <span data-ttu-id="820f2-130">Informacje o konfiguracji są odczytywane.</span><span class="sxs-lookup"><span data-stu-id="820f2-130">The configuration information is read.</span></span>

    1. <span data-ttu-id="820f2-131">Konfiguracja usługi rejestruje procedurę obsługi konfiguracji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="820f2-131">The service configuration registers the custom configuration handler.</span></span>

    2. <span data-ttu-id="820f2-132">Host usługi został utworzony i otwarty.</span><span class="sxs-lookup"><span data-stu-id="820f2-132">The service host is created and opened.</span></span>

    3. <span data-ttu-id="820f2-133">Niestandardowy element konfiguracji tworzy i zwraca niestandardowy element powiązania.</span><span class="sxs-lookup"><span data-stu-id="820f2-133">The custom configuration element creates and returns the custom binding element.</span></span>

    4. <span data-ttu-id="820f2-134">Niestandardowy element powiązania tworzy i zwraca fabrykę kodera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="820f2-134">The custom binding element creates and returns a message encoder factory.</span></span>

3. <span data-ttu-id="820f2-135">Odebrano komunikat.</span><span class="sxs-lookup"><span data-stu-id="820f2-135">A message is received.</span></span>

4. <span data-ttu-id="820f2-136">Fabryka kodera komunikatów zwraca koder komunikatów służący do odczytu w komunikacie i zapisywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="820f2-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>

5. <span data-ttu-id="820f2-137">Warstwa kodera jest zaimplementowana jako fabryka klas.</span><span class="sxs-lookup"><span data-stu-id="820f2-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="820f2-138">Tylko fabryka klas kodera musi być publicznie uwidoczniona dla kodera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="820f2-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="820f2-139">Obiekt fabryki jest zwracany przez element powiązania po <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ChannelFactory%601> utworzeniu obiektu lub.</span><span class="sxs-lookup"><span data-stu-id="820f2-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="820f2-140">Kodery komunikatów mogą działać w trybie buforowanym lub przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="820f2-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="820f2-141">Ten przykład pokazuje tryb buforowany i tryb przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="820f2-141">This sample demonstrates both buffered mode and streaming mode.</span></span>

<span data-ttu-id="820f2-142">Dla każdego trybu istnieje przyłączona `ReadMessage` i `WriteMessage` metoda klasy abstrakcyjnej `MessageEncoder` .</span><span class="sxs-lookup"><span data-stu-id="820f2-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="820f2-143">Większość pracy z kodowaniem odbywa się w tych metodach.</span><span class="sxs-lookup"><span data-stu-id="820f2-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="820f2-144">Przykład otacza istniejący tekst i binarne kodery komunikatów.</span><span class="sxs-lookup"><span data-stu-id="820f2-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="820f2-145">Pozwala to przykładowi na oddelegowanie odczytu i zapisu komunikacji przewodowej komunikatów do kodera wewnętrznego i umożliwia koderowi kompresji kompresowanie lub kompresowanie wyników.</span><span class="sxs-lookup"><span data-stu-id="820f2-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="820f2-146">Ponieważ nie ma potoku do kodowania komunikatów, jest to jedyny model używany do korzystania z wielu koderów w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="820f2-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="820f2-147">Po przeprowadzeniu dekompresowania komunikatu wynikowy komunikat jest przesyłany do stosu dla stosu kanału do obsłużenia.</span><span class="sxs-lookup"><span data-stu-id="820f2-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="820f2-148">Podczas kompresji uzyskany skompresowany komunikat jest zapisywana bezpośrednio do podanego strumienia.</span><span class="sxs-lookup"><span data-stu-id="820f2-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>

<span data-ttu-id="820f2-149">W tym przykładzie użyto metod pomocnika ( `CompressBuffer` i `DecompressBuffer` ) do wykonania konwersji z buforów na strumienie, aby użyć `GZipStream` klasy.</span><span class="sxs-lookup"><span data-stu-id="820f2-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>

<span data-ttu-id="820f2-150">Buforowane `ReadMessage` i `WriteMessage` klasy wykorzystują `BufferManager` klasę.</span><span class="sxs-lookup"><span data-stu-id="820f2-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="820f2-151">Koder jest dostępny tylko za pomocą fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="820f2-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="820f2-152">Klasa abstrakcyjna `MessageEncoderFactory` zawiera właściwość o nazwie `Encoder` do uzyskiwania dostępu do bieżącego kodera oraz metodę o nazwie `CreateSessionEncoder` do tworzenia kodera, który obsługuje sesje.</span><span class="sxs-lookup"><span data-stu-id="820f2-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="820f2-153">Takiego kodera można użyć w scenariuszu, w którym kanał obsługuje sesje, jest uporządkowany i niezawodny.</span><span class="sxs-lookup"><span data-stu-id="820f2-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="820f2-154">Ten scenariusz umożliwia optymalizację w każdej sesji danych zapisywana w sieci.</span><span class="sxs-lookup"><span data-stu-id="820f2-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="820f2-155">Jeśli nie jest to potrzebne, metoda podstawowa nie powinna być przeciążona.</span><span class="sxs-lookup"><span data-stu-id="820f2-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="820f2-156">`Encoder`Właściwość zapewnia mechanizm uzyskiwania dostępu do kodera bez sesji i domyślna implementacja `CreateSessionEncoder` metody zwraca wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="820f2-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="820f2-157">Ponieważ przykład otacza istniejący koder w celu zapewnienia kompresji, `MessageEncoderFactory` implementacja przyjmuje, `MessageEncoderFactory` że reprezentuje wewnętrzną fabrykę kodera.</span><span class="sxs-lookup"><span data-stu-id="820f2-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>

<span data-ttu-id="820f2-158">Teraz, gdy jest zdefiniowany koder i fabryka kodera, mogą one być używane z klientem i usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="820f2-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="820f2-159">Jednak te kodery muszą zostać dodane do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="820f2-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="820f2-160">Można dziedziczyć klasy z <xref:System.ServiceModel.ServiceHost> klas i <xref:System.ServiceModel.ChannelFactory%601> i zastąpić metody, `OnInitialize` Aby ręcznie dodać tę fabrykę kodera.</span><span class="sxs-lookup"><span data-stu-id="820f2-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="820f2-161">Możesz również uwidocznić fabrykę koderów za pomocą niestandardowego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="820f2-161">You can also expose the encoder factory through a custom binding element.</span></span>

<span data-ttu-id="820f2-162">Aby utworzyć nowy element powiązania niestandardowego, Utwórz klasę z <xref:System.ServiceModel.Channels.BindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="820f2-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="820f2-163">Istnieje jednak kilka typów elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="820f2-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="820f2-164">Aby zapewnić, że element powiązania niestandardowego jest rozpoznawany jako element powiązania kodowania komunikatów, należy również zaimplementować <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="820f2-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="820f2-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement>Uwidacznia metodę tworzenia nowej fabryki kodera komunikatów ( `CreateMessageEncoderFactory` ), która jest zaimplementowana w celu zwrócenia wystąpienia zgodnej fabryki kodera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="820f2-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="820f2-166">Ponadto <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> ma właściwość, która wskazuje na wersję adresowania.</span><span class="sxs-lookup"><span data-stu-id="820f2-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="820f2-167">Ponieważ ten przykład otacza istniejące kodery, implementacja przykładu otacza istniejące elementy powiązania kodera i przyjmuje wewnętrzny element powiązania kodera jako parametr do konstruktora i udostępnia go za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="820f2-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="820f2-168">Poniższy przykładowy kod przedstawia implementację `GZipMessageEncodingBindingElement` klasy.</span><span class="sxs-lookup"><span data-stu-id="820f2-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>

```csharp
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

<span data-ttu-id="820f2-169">Należy zauważyć, że `GZipMessageEncodingBindingElement` Klasa implementuje `IPolicyExportExtension` interfejs, dzięki czemu ten element powiązania można wyeksportować jako zasady w metadanych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="820f2-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>

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

<span data-ttu-id="820f2-170">`GZipMessageEncodingBindingElementImporter`Klasa implementuje `IPolicyImportExtension` interfejs, ta klasa importuje zasady dla `GZipMessageEncodingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="820f2-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="820f2-171">Narzędzie Svcutil. exe może służyć do importowania zasad do pliku konfiguracji, aby obsłużyć `GZipMessageEncodingBindingElement` następujące czynności należy dodać do Svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="820f2-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>

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

<span data-ttu-id="820f2-172">Teraz, gdy istnieje pasujący element powiązania dla kodera kompresji, można go programowo podłączyć do usługi lub klienta przez zbudowanie nowego niestandardowego obiektu powiązania i dodanie do niego elementu niestandardowego powiązania, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="820f2-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

<span data-ttu-id="820f2-173">Chociaż może to być wystarczające dla większości scenariuszy użytkowników, obsługa konfiguracji plików jest niezwykle ważna, jeśli usługa ma być hostowana w Internecie.</span><span class="sxs-lookup"><span data-stu-id="820f2-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="820f2-174">Aby zapewnić obsługę scenariusza hostowanego w sieci Web, należy opracować procedurę obsługi konfiguracji niestandardowej, aby umożliwić konfigurację elementu niestandardowego powiązania w pliku.</span><span class="sxs-lookup"><span data-stu-id="820f2-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>

<span data-ttu-id="820f2-175">Można utworzyć procedurę obsługi konfiguracji dla elementu Binding na górze systemu konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="820f2-175">You can build a configuration handler for the binding element on top of the configuration system.</span></span> <span data-ttu-id="820f2-176">Program obsługi konfiguracji dla elementu Binding musi być pochodną <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="820f2-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="820f2-177"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType>Informuje system konfiguracji typu elementu powiązania, który ma zostać utworzony dla tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="820f2-177">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> informs the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="820f2-178">Wszystkie aspekty `BindingElement` , które można ustawić, powinny być uwidocznione jako właściwości w <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="820f2-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="820f2-179"><xref:System.Configuration.ConfigurationPropertyAttribute>Pomaga w mapowaniu atrybutów elementu konfiguracji do właściwości i ustawiania wartości domyślnych w przypadku braku atrybutów.</span><span class="sxs-lookup"><span data-stu-id="820f2-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="820f2-180">Po załadowaniu wartości z konfiguracji i zastosowaniu ich do właściwości <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> jest wywoływana metoda, która konwertuje właściwości na konkretne wystąpienie elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="820f2-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="820f2-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType>Metoda służy do konwertowania właściwości <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy pochodnej na wartości, które mają być ustawiane dla nowo utworzonego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="820f2-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newly created binding element.</span></span>

<span data-ttu-id="820f2-182">Poniższy przykładowy kod przedstawia implementację programu `GZipMessageEncodingElement` .</span><span class="sxs-lookup"><span data-stu-id="820f2-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>

```csharp
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

<span data-ttu-id="820f2-183">Ta procedura obsługi konfiguracji mapuje do następującej reprezentacji w pliku App. config lub Web. config dla usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="820f2-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

<span data-ttu-id="820f2-184">Aby użyć tego programu obsługi konfiguracji, musi on być zarejestrowany w obrębie [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="820f2-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="820f2-185">Po uruchomieniu serwera programu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="820f2-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="820f2-186">Naciśnij klawisz ENTER w oknie, aby zamknąć serwer.</span><span class="sxs-lookup"><span data-stu-id="820f2-186">Press ENTER in the window to shut down the server.</span></span>

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

<span data-ttu-id="820f2-187">Po uruchomieniu klienta żądania operacji i odpowiedzi są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="820f2-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="820f2-188">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="820f2-188">Press ENTER in the client window to shut down the client.</span></span>

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="820f2-189">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="820f2-189">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="820f2-190">Zainstaluj program ASP.NET 4,0 przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="820f2-190">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="820f2-191">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="820f2-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="820f2-192">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="820f2-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="820f2-193">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="820f2-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="820f2-194">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="820f2-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="820f2-195">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="820f2-195">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="820f2-196">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="820f2-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="820f2-197">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="820f2-197">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
