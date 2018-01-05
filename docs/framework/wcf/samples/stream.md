---
title: "Strumień"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab56dd7938f2c7594627b54b4cb61b4e0f6b28fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="stream"></a><span data-ttu-id="80dbb-102">Strumień</span><span class="sxs-lookup"><span data-stu-id="80dbb-102">Stream</span></span>
<span data-ttu-id="80dbb-103">Przykładowe strumienia zademonstrowano użycie przesyłania strumieniowego komunikacji tryb transferu.</span><span class="sxs-lookup"><span data-stu-id="80dbb-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="80dbb-104">Usługa udostępnia kilka operacji wysyłania i odbierania strumieni.</span><span class="sxs-lookup"><span data-stu-id="80dbb-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="80dbb-105">Ten przykład jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="80dbb-105">This sample is self-hosted.</span></span> <span data-ttu-id="80dbb-106">Klient i usługa są programy konsoli.</span><span class="sxs-lookup"><span data-stu-id="80dbb-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80dbb-107">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="80dbb-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="80dbb-108">może komunikować się w dwóch trybach transfer — buforowany lub przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="80dbb-108"> can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="80dbb-109">W domyślnym trybie buforowanego transferu wiadomości musi być całkowicie dostarczana przed odbiorca może go odczytać.</span><span class="sxs-lookup"><span data-stu-id="80dbb-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="80dbb-110">W trybie przesyłania strumieniowego przesyłania można rozpocząć przetworzyć komunikatu przed przekazaniem całkowicie odbiornika.</span><span class="sxs-lookup"><span data-stu-id="80dbb-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="80dbb-111">Tryb strumieniowy jest przydatne, gdy informacje przekazywane jest obszerne i mogą być przetwarzane pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="80dbb-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="80dbb-112">Tryb strumieniowy jest również przydatne, gdy komunikat jest zbyt duży, aby całkowicie buforowany.</span><span class="sxs-lookup"><span data-stu-id="80dbb-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="80dbb-113">Przesyłania strumieniowego i kontrakty usług</span><span class="sxs-lookup"><span data-stu-id="80dbb-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="80dbb-114">Przesyłanie strumieniowe to element wziąć pod uwagę podczas projektowania kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="80dbb-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="80dbb-115">Jeśli operacja odbiera lub zwraca dużych ilości danych, należy rozważyć przesyłania strumieniowego te dane, aby uniknąć użycia pamięci wysokiej wskutek buforowania komunikatów wejściowych lub wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="80dbb-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="80dbb-116">Strumień danych, parametr, który przechowuje, że dane muszą być tylko parametr w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="80dbb-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="80dbb-117">Na przykład jeśli komunikat wejściowy jest przesyłane strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="80dbb-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="80dbb-118">Podobnie w przypadku komunikatu wyjściowego strumieniowe przesyłanie, operacja musi mieć dokładnie jeden wyjściowy parametru lub wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="80dbb-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="80dbb-119">W przypadku, parametr lub zwracane wartości typu musi być albo `Stream`, `Message`, lub `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="80dbb-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="80dbb-120">Poniżej znajduje się kontraktu usługi, używany w tym przykładzie przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="80dbb-120">The following is the service contract used in this streaming sample.</span></span>  
  
```  
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
  
 <span data-ttu-id="80dbb-121">`GetStream` Operacji odbiera niektórych danych wejściowych jako ciąg znaków, które są buforowane i zwraca `Stream`, który jest przesyłane strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="80dbb-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="80dbb-122">Z drugiej strony `UploadStream` przyjmuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowanej).</span><span class="sxs-lookup"><span data-stu-id="80dbb-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="80dbb-123">`EchoStream`pobiera i zwraca `Stream` jest przykładem operacji których dane wejściowe i komunikaty wyjściowe zarówno strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="80dbb-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="80dbb-124">Na koniec `GetReversedStream` przyjmuje nie dane wejściowe i zwraca `Stream` (przesyłane strumieniowo).</span><span class="sxs-lookup"><span data-stu-id="80dbb-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="80dbb-125">Włączanie przesyłanej strumieniowo transferu</span><span class="sxs-lookup"><span data-stu-id="80dbb-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="80dbb-126">Definiowanie kontraktów operacji, jak opisano wcześniej zapewnia przesyłania strumieniowego na poziomie modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="80dbb-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="80dbb-127">Jeśli zatrzymasz, transportu nadal buforuje zawartość cały komunikat.</span><span class="sxs-lookup"><span data-stu-id="80dbb-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="80dbb-128">Aby włączyć transportu strumieniowego, wybierz tryb transferu w elemencie powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="80dbb-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="80dbb-129">Element powiązania ma `TransferMode` właściwość, która może być ustawiony na `Buffered`, `Streamed`, `StreamedRequest`, lub `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="80dbb-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="80dbb-130">Ustawienie Tryb transferu `Streamed` umożliwia przesyłanie strumieniowe komunikacji w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="80dbb-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="80dbb-131">Ustawienie Tryb transferu `StreamedRequest` lub `StreamedResponse` umożliwia przesyłanie strumieniowe komunikacji w tylko żądania lub odpowiedzi, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="80dbb-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="80dbb-132">`basicHttpBinding` Przedstawia `TransferMode` właściwość powiązanie, tak jak w przypadku `NetTcpBinding` i `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="80dbb-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="80dbb-133">Dla innych transportu należy utworzyć niestandardowego powiązania, aby ustawić tryb transferu.</span><span class="sxs-lookup"><span data-stu-id="80dbb-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="80dbb-134">Poniższy kod konfiguracji z próbki pokazuje ustawienie `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania HTTP:</span><span class="sxs-lookup"><span data-stu-id="80dbb-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="80dbb-135">Oprócz ustawienia `transferMode` do `Streamed`, poprzedniego zestawu kodu konfiguracji `maxReceivedMessageSize` 64 MB.</span><span class="sxs-lookup"><span data-stu-id="80dbb-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="80dbb-136">Jako mechanizm obrony `maxReceivedMessageSize` odbierania zakończenia na maksymalny dozwolony rozmiar wiadomości w miejscach.</span><span class="sxs-lookup"><span data-stu-id="80dbb-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="80dbb-137">Wartość domyślna `maxReceivedMessageSize` wynosi 64 KB, który zazwyczaj jest zbyt stara przesyłania strumieniowego scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="80dbb-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="80dbb-138">Przetwarzanie danych, ponieważ jest ona przesyłana strumieniowo</span><span class="sxs-lookup"><span data-stu-id="80dbb-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="80dbb-139">Operacje `GetStream`, `UploadStream` i `EchoStream` wszystkie postępowania w przypadku wysyłania danych bezpośrednio z pliku lub zapisywanie odebranych danych bezpośrednio w pliku.</span><span class="sxs-lookup"><span data-stu-id="80dbb-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="80dbb-140">Jednak w niektórych przypadkach jest wymagane wysyłanie lub odbieranie dużych ilości danych i wykonać niektóre przetwarzania na fragmenty danych, ponieważ jest on wysyłane lub odbierane.</span><span class="sxs-lookup"><span data-stu-id="80dbb-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="80dbb-141">Jednym ze sposobów rozwiązania takich scenariuszy należy napisać niestandardowych strumieni (klasy, która jest pochodną <xref:System.IO.Stream>) przetwarza dane, ponieważ jest do odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="80dbb-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="80dbb-142">`GetReversedStream` Operacji i `ReverseStream` klasy są na przykład.</span><span class="sxs-lookup"><span data-stu-id="80dbb-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="80dbb-143">`GetReversedStream`Tworzy i zwraca nowe wystąpienie klasy `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="80dbb-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="80dbb-144">Aktualnie przetwarzanego się stanie, jak system odczytuje niż `ReverseStream` obiektu.</span><span class="sxs-lookup"><span data-stu-id="80dbb-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="80dbb-145">`ReverseStream.Read` Implementacji odczytuje fragmentu bajtów z pliku źródłowego, odwraca je, a następnie zwraca odwróconej bajtów.</span><span class="sxs-lookup"><span data-stu-id="80dbb-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="80dbb-146">Będą to zawartości całego pliku; Odwraca ono jednym fragmencie bajtów w czasie.</span><span class="sxs-lookup"><span data-stu-id="80dbb-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="80dbb-147">To jest przykład pokazanie, jak wykonać przetwarzającym strumień zawartości jest w trakcie odczytu lub zapisu z i do strumienia.</span><span class="sxs-lookup"><span data-stu-id="80dbb-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="80dbb-148">Uruchomiona próbki</span><span class="sxs-lookup"><span data-stu-id="80dbb-148">Running the Sample</span></span>  
 <span data-ttu-id="80dbb-149">Aby uruchomić przykład, kompilacji zarówno usługę i klienta przez zgodnie z instrukcjami na końcu tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="80dbb-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="80dbb-150">Następnie uruchom usługę i klienta w dwóch różnych konsoli systemu windows.</span><span class="sxs-lookup"><span data-stu-id="80dbb-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="80dbb-151">Po uruchomieniu klienta oczekuje na można nacisnąć klawisz ENTER, gdy usługa jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="80dbb-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="80dbb-152">Klient następnie wywołuje metody `GetStream()`, `UploadStream()` i `GetReversedStream()` najpierw za pośrednictwem protokołu HTTP, a następnie za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="80dbb-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="80dbb-153">Oto przykładowe dane wyjściowe z usługi następuje przykładowe dane wyjściowe z klienta:</span><span class="sxs-lookup"><span data-stu-id="80dbb-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="80dbb-154">Usługi danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="80dbb-154">Service Output:</span></span>  
  
```  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="80dbb-155">Dane wyjściowe klienta:</span><span class="sxs-lookup"><span data-stu-id="80dbb-155">Client Output:</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="80dbb-156">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="80dbb-156">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="80dbb-157">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80dbb-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="80dbb-158">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80dbb-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="80dbb-159">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80dbb-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80dbb-160">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="80dbb-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="80dbb-161">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="80dbb-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="80dbb-162">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="80dbb-162">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="80dbb-163">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="80dbb-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="80dbb-164">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="80dbb-164">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a><span data-ttu-id="80dbb-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80dbb-165">See Also</span></span>
