---
title: Strumień
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: f22339ca298f053fa636cc37281276051c70f6d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183322"
---
# <a name="stream"></a><span data-ttu-id="2cf4f-102">Strumień</span><span class="sxs-lookup"><span data-stu-id="2cf4f-102">Stream</span></span>
<span data-ttu-id="2cf4f-103">Próbka Stream pokazuje użycie komunikacji w trybie przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="2cf4f-104">Usługa udostępnia kilka operacji, które wysyłają i odbierają strumienie.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="2cf4f-105">Ten przykład jest hostowany samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-105">This sample is self-hosted.</span></span> <span data-ttu-id="2cf4f-106">Zarówno klient, jak i usługa są programami konsolowymi.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cf4f-107">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2cf4f-108">Windows Communication Foundation (WCF) może komunikować się w dwóch trybach transferu — buforowane lub przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="2cf4f-109">W domyślnym buforowanym trybie transferu komunikat musi zostać całkowicie dostarczony, zanim odbiorca będzie mógł ją odczytać.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="2cf4f-110">W trybie przesyłania strumieniowego odbiorca może rozpocząć przetwarzanie wiadomości, zanim zostanie całkowicie dostarczona.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="2cf4f-111">Tryb przesyłania strumieniowego jest przydatne, gdy informacje, które są przekazywane jest długa i mogą być przetwarzane szeregowo.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="2cf4f-112">Tryb przesyłania strumieniowego jest również przydatne, gdy wiadomość jest zbyt duża, aby być całkowicie buforowane.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="2cf4f-113">Kontrakty przesyłania strumieniowego i usług</span><span class="sxs-lookup"><span data-stu-id="2cf4f-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="2cf4f-114">Przesyłanie strumieniowe jest czymś, co należy wziąć pod uwagę podczas projektowania umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="2cf4f-115">Jeśli operacja odbiera lub zwraca duże ilości danych, należy rozważyć przesyłanie strumieniowe tych danych, aby uniknąć wysokiego wykorzystania pamięci z powodu buforowania komunikatów wejściowych lub wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="2cf4f-116">Aby przesyłać strumieniowo dane, parametr, który przechowuje te dane, musi być jedynym parametrem w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="2cf4f-117">Na przykład jeśli komunikat wejściowy jest ten, który ma być przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="2cf4f-118">Podobnie jeśli komunikat wyjściowy ma być przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wyjściowy lub wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="2cf4f-119">W obu przypadkach parametr lub typ wartości zwracanej `Message`musi `IXmlSerializable`być albo `Stream`, lub .</span><span class="sxs-lookup"><span data-stu-id="2cf4f-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="2cf4f-120">Poniżej znajduje się umowa serwisowa używana w tym przykładzie przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-120">The following is the service contract used in this streaming sample.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="2cf4f-121">Operacja `GetStream` odbiera niektóre dane wejściowe jako ciąg, który `Stream`jest buforowany i zwraca , który jest przesyłany strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="2cf4f-122">Z drugiej `UploadStream` strony `Stream` przyjmuje (przesyłane strumieniowo) i zwraca `bool` (buforowane).</span><span class="sxs-lookup"><span data-stu-id="2cf4f-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="2cf4f-123">`EchoStream`pobiera i `Stream` zwraca i jest przykładem operacji, której komunikaty wejściowe i wyjściowe są przesyłane strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="2cf4f-124">Na koniec `GetReversedStream` nie pobiera żadnych `Stream` danych wejściowych i zwraca (przesyłane strumieniowo).</span><span class="sxs-lookup"><span data-stu-id="2cf4f-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="2cf4f-125">Włączanie transferów przesyłanych strumieniowo</span><span class="sxs-lookup"><span data-stu-id="2cf4f-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="2cf4f-126">Definiowanie kontraktów operacyjnych, jak opisano wcześniej zapewnia przesyłanie strumieniowe na poziomie modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="2cf4f-127">Jeśli zatrzymasz się tam, transport nadal buforuje całą zawartość wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="2cf4f-128">Aby włączyć przesyłanie strumieniowe transportu, wybierz tryb transferu na element powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="2cf4f-129">Element wiązania ma `TransferMode` właściwość, którą `Buffered` `Streamed`można `StreamedRequest`ustawić `StreamedResponse`na , , , lub .</span><span class="sxs-lookup"><span data-stu-id="2cf4f-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="2cf4f-130">Ustawienie trybu transferu `Streamed` w celu umożliwiającego przesyłanie strumieniowe komunikacji w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="2cf4f-131">Ustawienie trybu transferu `StreamedRequest` `StreamedResponse` lub włącza komunikację strumieniową odpowiednio tylko w żądaniu lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="2cf4f-132">Udostępnia `basicHttpBinding` `TransferMode` właściwość na powiązanie, `NetTcpBinding` `NetNamedPipeBinding`podobnie jak i .</span><span class="sxs-lookup"><span data-stu-id="2cf4f-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="2cf4f-133">W przypadku innych transportów należy utworzyć niestandardowe powiązanie, aby ustawić tryb transferu.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="2cf4f-134">Następujący kod konfiguracji z przykładu `TransferMode` pokazuje ustawienie `basicHttpBinding` właściwości do przesyłania strumieniowego na i niestandardowe powiązanie HTTP:</span><span class="sxs-lookup"><span data-stu-id="2cf4f-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="2cf4f-135">Oprócz ustawienia `transferMode` na `Streamed`, poprzedni kod konfiguracji `maxReceivedMessageSize` ustawia na 64MB.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="2cf4f-136">Jako mechanizm obronny `maxReceivedMessageSize` umieszcza limit maksymalnego dopuszczalnego rozmiaru wiadomości podczas odbierania.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="2cf4f-137">Wartość `maxReceivedMessageSize` domyślna to 64 KB, która jest zwykle zbyt niska dla scenariuszy przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="2cf4f-138">Przetwarzanie danych w miarę ich przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="2cf4f-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="2cf4f-139">Operacje `GetStream`i `UploadStream` `EchoStream` wszystkie dotyczą wysyłania danych bezpośrednio z pliku lub zapisywania odebranych danych bezpośrednio do pliku.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="2cf4f-140">Jednak w niektórych przypadkach istnieje wymóg wysyłania lub odbierania dużych ilości danych i wykonywania niektórych przetwarzania na fragmentach danych, gdy są wysyłane lub odbierane.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="2cf4f-141">Jednym ze sposobów rozwiązania takich scenariuszy jest napisanie strumienia <xref:System.IO.Stream>niestandardowego (klasy, która wywodzi się z ), który przetwarza dane w miarę ich odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="2cf4f-142">Operacja `GetReversedStream` i `ReverseStream` klasa są tego przykładem.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="2cf4f-143">`GetReversedStream`tworzy i zwraca nowe `ReverseStream`wystąpienie .</span><span class="sxs-lookup"><span data-stu-id="2cf4f-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="2cf4f-144">Rzeczywiste przetwarzanie odbywa się w `ReverseStream` systemie odczytuje z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="2cf4f-145">Implementacja `ReverseStream.Read` odczytuje fragment bajtów z pliku źródłowego, odwraca je, a następnie zwraca odwrócone bajty.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="2cf4f-146">Nie powoduje to odwrócenia całej zawartości pliku; odwraca jeden fragment bajtów naraz.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="2cf4f-147">Jest to przykład, aby pokazać, jak można wykonać przetwarzanie strumienia, jak zawartość jest odczytywany lub zapisywany z i do strumienia.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="2cf4f-148">Uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="2cf4f-148">Running the Sample</span></span>  
 <span data-ttu-id="2cf4f-149">Aby uruchomić przykład, najpierw skompiluj usługę i klienta, postępając zgodnie ze wskazówkami na końcu tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="2cf4f-150">Następnie uruchom usługę i klienta w dwóch różnych oknach konsoli.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="2cf4f-151">Po uruchomieniu klienta czeka na naciśnięcie klawisza ENTER, gdy usługa jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="2cf4f-152">Następnie klient wywołuje `GetStream()`metody `UploadStream()` `GetReversedStream()` , a najpierw za pośrednictwem protokołu HTTP, a następnie za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="2cf4f-153">Oto przykład danych wyjściowych z usługi, a następnie przykładowe dane wyjściowe z klienta:</span><span class="sxs-lookup"><span data-stu-id="2cf4f-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="2cf4f-154">Wyjście usługi:</span><span class="sxs-lookup"><span data-stu-id="2cf4f-154">Service Output:</span></span>  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="2cf4f-155">Dane wyjściowe klienta:</span><span class="sxs-lookup"><span data-stu-id="2cf4f-155">Client Output:</span></span>  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2cf4f-156">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="2cf4f-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2cf4f-157">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2cf4f-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2cf4f-158">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2cf4f-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2cf4f-159">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2cf4f-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cf4f-160">Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2cf4f-161">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2cf4f-162">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-162">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2cf4f-163">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2cf4f-164">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2cf4f-164">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
