---
title: "Niestandardowy koder komunikatów: Koder kompresji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c3c59a574d2206de7722958f676a721b51fbc2d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="b5d8f-102">Niestandardowy koder komunikatów: Koder kompresji</span><span class="sxs-lookup"><span data-stu-id="b5d8f-102">Custom Message Encoder: Compression Encoder</span></span>
<span data-ttu-id="b5d8f-103">W tym przykładzie pokazano, jak zaimplementować przy użyciu niestandardowego kodera [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] platformy.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-103">This sample demonstrates how to implement a custom encoder using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] platform.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5d8f-104">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5d8f-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b5d8f-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b5d8f-106">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5d8f-107">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a><span data-ttu-id="b5d8f-108">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="b5d8f-108">Sample Details</span></span>  
 <span data-ttu-id="b5d8f-109">W tym przykładzie składa się z konsoli program kliencki (.exe), (.exe) hostowanie Samoobsługowe konsoli programu i kompresji biblioteki kodera wiadomości (.dll).</span><span class="sxs-lookup"><span data-stu-id="b5d8f-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="b5d8f-110">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="b5d8f-111">Kontrakt jest definiowana za pomocą `ISampleServer` interfejsu, który ujawnia podstawowe ciągu wyświetlania operacji (`Echo` i `BigEcho`).</span><span class="sxs-lookup"><span data-stu-id="b5d8f-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="b5d8f-112">Klient wysyła żądań synchronicznych operacji i odpowiedzi usługi powtarzając wiadomość do klienta.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="b5d8f-113">Aktywność klienta i usługi jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="b5d8f-114">Celem tego przykładu jest pokazują, jak zapisać niestandardowego kodera i Wykaż wpływ kompresji wiadomości w sieci.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="b5d8f-115">Możesz dodać Instrumentacji do kodera wiadomości kompresji do obliczenia rozmiaru wiadomości i czas przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5d8f-116">W .NET Framework 4, został włączony na automatycznej dekompresji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, jeśli serwer wysyła odpowiedź skompresowane (utworzone przy użyciu algorytmu, takich jak GZip i Deflate).</span><span class="sxs-lookup"><span data-stu-id="b5d8f-116">In the .NET Framework 4, automatic decompression has been enabled on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="b5d8f-117">W przypadku usługi sieci Web hostowanych w Internet Information Server (IIS), usługi IIS można skonfigurować do wysyłania skompresowane odpowiedzi usługi.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="b5d8f-118">Można w tym przykładzie, jeśli wymagane jest przeprowadzenie kompresji i dekompresji zarówno klient, jak i usługi lub usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>  
  
 <span data-ttu-id="b5d8f-119">Przykład pokazuje, jak kompilacji i integracji niestandardowy koder komunikatów do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-119">The sample demonstrates how to build and integrate a custom message encoder into a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="b5d8f-120">Biblioteka GZipEncoder.dll jest wdrażana z zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="b5d8f-121">W przykładzie pokazano także wpływ kompresowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="b5d8f-122">Kod w GZipEncoder.dll przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="b5d8f-122">The code in GZipEncoder.dll demonstrates the following:</span></span>  
  
-   <span data-ttu-id="b5d8f-123">Tworzenie niestandardowego kodera i fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-123">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="b5d8f-124">Tworzenie elementu powiązania dla niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-124">Developing a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="b5d8f-125">Za pomocą konfiguracji powiązania niestandardowego do integracji elementy niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-125">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="b5d8f-126">Tworzenie konfiguracji niestandardowej obsługi umożliwia konfigurację pliku element niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
 <span data-ttu-id="b5d8f-127">Jak wcześniej wspomniano, istnieje kilka warstwy, które zostały wdrożone w niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="b5d8f-128">Aby lepiej zilustrować relacji między każdym z tych warstw, uproszczone kolejność zdarzeń do uruchamiania usługi jest na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="b5d8f-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>  
  
1.  <span data-ttu-id="b5d8f-129">Serwer zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-129">The server starts.</span></span>  
  
2.  <span data-ttu-id="b5d8f-130">Informacje o konfiguracji jest do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-130">The configuration information is read.</span></span>  
  
    1.  <span data-ttu-id="b5d8f-131">Konfiguracja usługi rejestruje obsługi konfiguracji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-131">The service configuration registers the custom configuration handler.</span></span>  
  
    2.  <span data-ttu-id="b5d8f-132">Host usługi jest utworzony i otwarty.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-132">The service host is created and opened.</span></span>  
  
    3.  <span data-ttu-id="b5d8f-133">Element konfiguracji niestandardowej tworzy i zwraca element niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-133">The custom configuration element creates and returns the custom binding element.</span></span>  
  
    4.  <span data-ttu-id="b5d8f-134">Element niestandardowego powiązania tworzy i zwraca fabrykę kodera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-134">The custom binding element creates and returns a message encoder factory.</span></span>  
  
3.  <span data-ttu-id="b5d8f-135">Wiadomość zostanie odebrana.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-135">A message is received.</span></span>  
  
4.  <span data-ttu-id="b5d8f-136">Fabryka kodera wiadomości zwraca kodera wiadomości za odczytywanie wiadomości i zapisywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>  
  
5.  <span data-ttu-id="b5d8f-137">Warstwa koder jest implementowany jako fabrykę klas.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="b5d8f-138">Fabryka klas kodera musi być publicznie wystawiony dla niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="b5d8f-139">Obiekt fabryki jest zwracany przez element powiązania podczas <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601> tworzony jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="b5d8f-140">Kodery komunikat może działać w trybie buforowanego lub przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="b5d8f-141">W przykładzie pokazano, zarówno w trybie buforowanego, jak i w trybie przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-141">This sample demonstrates both buffered mode and streaming mode.</span></span>  
  
 <span data-ttu-id="b5d8f-142">Dla każdego trybu istnieje towarzyszącego `ReadMessage` i `WriteMessage` metoda abstrakcyjna `MessageEncoder` klasy.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="b5d8f-143">Większość pracy kodowania odbywa się w tych metod.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="b5d8f-144">Przykład opakowuje istniejący tekst i kodery komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="b5d8f-145">To pozwala na przykład, aby delegować do odczytywania i zapisywania reprezentacja przesyłania wiadomości do kodera wewnętrzny oraz umożliwia koder kompresji, które mają być kompresowane lub dekompresja wyniki.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="b5d8f-146">Ponieważ nie ma żadnych potoku dla kodowania wiadomości, jest tylko modelu przy użyciu wielu koderów w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5d8f-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="b5d8f-147">Po komunikat został zdekompresowany, komunikat wynikowy jest przekazywany w górę stosu stosu kanału do obsługi.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="b5d8f-148">Podczas kompresji wynikowy skompresowany wiadomości są zapisywane bezpośrednio do dostarczonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>  
  
 <span data-ttu-id="b5d8f-149">W przykładzie użyto metody pomocnicze (`CompressBuffer` i `DecompressBuffer`) aby dokonać konwersji z buforów do strumieni, aby użyć `GZipStream` klasy.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>  
  
 <span data-ttu-id="b5d8f-150">Buforowane `ReadMessage` i `WriteMessage` klasy należy korzystać z `BufferManager` klasy.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="b5d8f-151">Koder jest dostępna tylko za pośrednictwem fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="b5d8f-152">Abstract `MessageEncoderFactory` klasy zawiera właściwości o nazwie `Encoder` do uzyskiwania dostępu do bieżącego kodera i metodę o nazwie `CreateSessionEncoder` umożliwiający utworzenie kodera, który obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="b5d8f-153">Takie kodera służy w sytuacji, gdy kanał obsługuje sesji, porządkowania i niezawodności.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="b5d8f-154">Ten scenariusz umożliwia optymalizacji w każdej sesji zapisanych do przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="b5d8f-155">Jeśli jest to niepożądane, nie można przeciążać metodę podstawową.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="b5d8f-156">`Encoder` Właściwość udostępnia mechanizm do uzyskiwania dostępu do kodera bez sesji i domyślną implementację elementu `CreateSessionEncoder` metoda zwraca wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="b5d8f-157">Ponieważ próbki opakowuje kodera istniejących zapewnienie kompresji, `MessageEncoderFactory` akceptuje implementacji `MessageEncoderFactory` reprezentujący fabryki wewnętrzny kodera.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>  
  
 <span data-ttu-id="b5d8f-158">Teraz, gdy zdefiniowano koder i fabryki kodera, można ich używać z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-158">Now that the encoder and encoder factory are defined, they can be used with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and service.</span></span> <span data-ttu-id="b5d8f-159">Jednak te kodery należy dodać do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="b5d8f-160">Mogą dziedziczyć klasy z <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.ChannelFactory%601> klasy i zastąpienie `OnInitialize` metod, aby ręcznie dodać tej fabryki kodera.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="b5d8f-161">Można również ujawniać fabryki kodera przez element niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-161">You can also expose the encoder factory through a custom binding element.</span></span>  
  
 <span data-ttu-id="b5d8f-162">Aby utworzyć nowy element niestandardowego powiązania, pochodzi z klasy <xref:System.ServiceModel.Channels.BindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="b5d8f-163">Istnieje jednak kilka typów elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="b5d8f-164">Aby upewnić się, że element niestandardowego powiązania jest rozpoznawana jako powiązanie element kodowania komunikatu, również należy zaimplementować <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="b5d8f-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Udostępnia metodę tworzenia fabrykę kodera wiadomości (`CreateMessageEncoderFactory`), którego jest stosowana do zwrócenia wystąpienia pasującej fabryki kodera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="b5d8f-166">Ponadto <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> ma właściwość, aby wskazać wersja adresowania.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="b5d8f-167">Ponieważ w tym przykładzie opakowuje istniejące kodery, przykładowe zastosowanie również opakowuje koder istniejących elementów wiązania i przyjmuje kodera wewnętrznego powiązania elementu jako parametr do konstruktora i uwidacznia go za pośrednictwem właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="b5d8f-168">Następujący przykładowy kod przedstawia implementację `GZipMessageEncodingBindingElement` klasy.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>  
  
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
  
 <span data-ttu-id="b5d8f-169">Należy pamiętać, że `GZipMessageEncodingBindingElement` klasa implementuje `IPolicyExportExtension` interfejsu, tak aby ten element powiązania mogą być eksportowane jako zasady w metadanych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b5d8f-170">`GZipMessageEncodingBindingElementImporter` Klasa implementuje `IPolicyImportExtension` interfejsu, ta klasa zaimportowanie zasad dla `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="b5d8f-171">Narzędzia svcutil.exe umożliwia importowanie zasad do pliku konfiguracji, aby obsłużyć `GZipMessageEncodingBindingElement`, dodaje do Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>  
  
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
  
 <span data-ttu-id="b5d8f-172">Teraz, brak pasującego elementu powiązania dla koder kompresji, jego mogą być programowane dołączane do usługi lub klienta tworząc nowy obiekt niestandardowego powiązania i Dodawanie elementu niestandardowego powiązania, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="b5d8f-173">Może to być wystarczające w większości scenariuszy użytkownika, Obsługa konfiguracji plików jest krytyczne, jeśli usługa ma być hostowana w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="b5d8f-174">Na potrzeby scenariusza hostowanych w sieci Web, należy utworzyć programu obsługi niestandardowej konfiguracji umożliwia element niestandardowego powiązania, będzie można skonfigurować w pliku.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>  
  
 <span data-ttu-id="b5d8f-175">Można utworzyć modułu obsługi konfiguracji element powiązania na udostępnione przez system konfiguracji [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5d8f-175">You can build a configuration handler for the binding element on top of the configuration system provided by the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="b5d8f-176">Obsługa konfiguracji dla elementu powiązania musi pochodzić od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="b5d8f-177">`BindingElementType` Właściwość jest używana do informuje system konfiguracji typu elementu powiązania, aby utworzyć dla tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-177">The `BindingElementType` property is used to inform the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="b5d8f-178">Wszystkie aspekty `BindingElement` które może być zestaw powinny zostać ujawnione jako właściwości <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="b5d8f-179"><xref:System.Configuration.ConfigurationPropertyAttribute> Jest używany jako pomoc w Mapowanie atrybutów elementów konfiguracji do właściwości i ustawianie wartości domyślnych, jeśli brakuje atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> is used to assist in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="b5d8f-180">Po wartości z konfiguracji są ładowane i stosowane do właściwości, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda jest wywoływana, który konwertuje na konkretne wystąpienie elementu powiązania właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="b5d8f-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Metoda jest używana do konwertowania właściwości na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pochodnej klasy na wartości, należy ustawić w elemencie powiązania newlycreated.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newlycreated binding element.</span></span>  
  
 <span data-ttu-id="b5d8f-182">Następujący przykładowy kod przedstawia implementację `GZipMessageEncodingElement`.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>  
  
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
  
 <span data-ttu-id="b5d8f-183">Ten program obsługi konfiguracji mapuje następujące reprezentacja w pliku App.config lub Web.config dla usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 <span data-ttu-id="b5d8f-184">Aby korzystać z tej obsługi konfiguracji, musi być zarejestrowana w ramach [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="b5d8f-185">Po uruchomieniu serwera operację żądania i odpowiedzi są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="b5d8f-186">Naciśnij klawisz ENTER w oknie, aby zamknąć serwera.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-186">Press ENTER in the window to shut down the server.</span></span>  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 <span data-ttu-id="b5d8f-187">Po uruchomieniu klienta operacji żądania i odpowiedzi są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="b5d8f-188">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-188">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b5d8f-189">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="b5d8f-189">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b5d8f-190">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="b5d8f-190">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="b5d8f-191">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b5d8f-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="b5d8f-192">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b5d8f-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="b5d8f-193">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b5d8f-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5d8f-194">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5d8f-195">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b5d8f-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b5d8f-196">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5d8f-197">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b5d8f-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a><span data-ttu-id="b5d8f-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5d8f-198">See Also</span></span>
