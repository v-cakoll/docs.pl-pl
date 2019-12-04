---
title: Strumień
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: d4166ac0258001b3e4eb0b8ece0f5163863359a4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716660"
---
# <a name="stream"></a><span data-ttu-id="a62fe-102">Strumień</span><span class="sxs-lookup"><span data-stu-id="a62fe-102">Stream</span></span>
<span data-ttu-id="a62fe-103">Przykład strumienia ilustruje użycie komunikacji w trybie transferu strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="a62fe-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="a62fe-104">Usługa udostępnia kilka operacji wysyłających i odbierających strumienie.</span><span class="sxs-lookup"><span data-stu-id="a62fe-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="a62fe-105">Ten przykład jest samodzielny.</span><span class="sxs-lookup"><span data-stu-id="a62fe-105">This sample is self-hosted.</span></span> <span data-ttu-id="a62fe-106">Zarówno klient, jak i usługa to programy konsolowe.</span><span class="sxs-lookup"><span data-stu-id="a62fe-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a62fe-107">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a62fe-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a62fe-108">Windows Communication Foundation (WCF) może komunikować się w dwóch trybach transferu — buforowane lub przesyłane strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="a62fe-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="a62fe-109">W domyślnym trybie transferu buforowanego komunikat musi zostać całkowicie dostarczony, aby odbiorca mógł go odczytać.</span><span class="sxs-lookup"><span data-stu-id="a62fe-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="a62fe-110">W trybie transferu strumieniowego odbiorca może zacząć przetwarzać komunikat, zanim zostanie on całkowicie dostarczony.</span><span class="sxs-lookup"><span data-stu-id="a62fe-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="a62fe-111">Tryb przesyłania strumieniowego jest przydatny, gdy przesyłane informacje są długie i mogą być przetwarzane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="a62fe-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="a62fe-112">Tryb przesyłania strumieniowego jest również przydatny, gdy komunikat jest zbyt duży, aby był całkowicie buforowany.</span><span class="sxs-lookup"><span data-stu-id="a62fe-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="a62fe-113">Kontrakty przesyłania strumieniowego i usług</span><span class="sxs-lookup"><span data-stu-id="a62fe-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="a62fe-114">Przesyłanie strumieniowe jest brane pod uwagę podczas projektowania kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="a62fe-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="a62fe-115">Jeśli operacja odbiera lub zwraca duże ilości danych, należy rozważyć przesyłanie strumieniowe tych danych w celu uniknięcia wysokiego użycia pamięci z powodu buforowania komunikatów wejściowych lub wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a62fe-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="a62fe-116">Aby przesłać strumieniowo dane, parametr, który przechowuje te dane, musi być jedynym parametrem w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="a62fe-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="a62fe-117">Na przykład jeśli komunikat wejściowy jest przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="a62fe-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="a62fe-118">Podobnie, jeśli wiadomość wyjściowa ma być przesyłana strumieniowo, operacja musi mieć dokładnie jeden parametr wyjściowy lub wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="a62fe-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="a62fe-119">W obu przypadkach parametr lub typ wartości zwracanej musi mieć wartość `Stream`, `Message`lub `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="a62fe-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="a62fe-120">Poniżej znajduje się kontrakt usługi używany w tym przykładzie przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="a62fe-120">The following is the service contract used in this streaming sample.</span></span>  
  
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
  
 <span data-ttu-id="a62fe-121">Operacja `GetStream` otrzymuje dane wejściowe jako ciąg, który jest buforowany i zwraca `Stream`, który jest przesyłany strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="a62fe-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="a62fe-122">Z kolei `UploadStream` wykonuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowana).</span><span class="sxs-lookup"><span data-stu-id="a62fe-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="a62fe-123">`EchoStream` pobiera i zwraca `Stream` i jest przykładem operacji, której przesyłanie strumieniowe i wyjściowe odbywa się jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a62fe-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="a62fe-124">Na koniec `GetReversedStream` nie pobiera danych wejściowych i zwraca `Stream` (przesyłane strumieniowo).</span><span class="sxs-lookup"><span data-stu-id="a62fe-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="a62fe-125">Włączanie transferu strumieniowego</span><span class="sxs-lookup"><span data-stu-id="a62fe-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="a62fe-126">Zdefiniowanie kontraktów operacji, jak opisano wcześniej, zapewnia przesyłanie strumieniowe na poziomie modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="a62fe-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="a62fe-127">Jeśli zatrzymasz ten problem, transport nadal buforuje całą zawartość wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a62fe-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="a62fe-128">Aby włączyć przesyłanie strumieniowe transportu, wybierz tryb transferu dla elementu powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="a62fe-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="a62fe-129">Element Binding ma właściwość `TransferMode`, która może być ustawiona na `Buffered`, `Streamed`, `StreamedRequest`lub `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="a62fe-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="a62fe-130">Ustawienie trybu transferu na `Streamed` Włącza komunikację przesyłania strumieniowego w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="a62fe-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="a62fe-131">Ustawienie trybu transferu na `StreamedRequest` lub `StreamedResponse` Włącza komunikację przesyłania strumieniowego odpowiednio do żądania lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a62fe-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="a62fe-132">`basicHttpBinding` uwidacznia Właściwość `TransferMode` w powiązaniu jako `NetTcpBinding` i `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="a62fe-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="a62fe-133">W przypadku innych transportów należy utworzyć niestandardowe powiązanie, aby ustawić tryb transferu.</span><span class="sxs-lookup"><span data-stu-id="a62fe-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="a62fe-134">Poniższy kod konfiguracji z przykładu przedstawia Ustawianie właściwości `TransferMode` do przesyłania strumieniowego `basicHttpBinding` i niestandardowego powiązania HTTP:</span><span class="sxs-lookup"><span data-stu-id="a62fe-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="a62fe-135">Poza ustawieniem `transferMode` na `Streamed`, poprzedni kod konfiguracji ustawia `maxReceivedMessageSize` na 64 MB.</span><span class="sxs-lookup"><span data-stu-id="a62fe-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="a62fe-136">Jako mechanizm obrony `maxReceivedMessageSize` umieszcza limit na maksymalny dozwolony rozmiar komunikatów odbieranych przez program.</span><span class="sxs-lookup"><span data-stu-id="a62fe-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="a62fe-137">Domyślny `maxReceivedMessageSize` to 64 KB, który jest zwykle zbyt niski dla scenariuszy przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="a62fe-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="a62fe-138">Przetwarzanie danych przesyłanych strumieniowo</span><span class="sxs-lookup"><span data-stu-id="a62fe-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="a62fe-139">Operacje `GetStream`, `UploadStream` i `EchoStream` wszystkie związane z wysyłaniem danych bezpośrednio z pliku lub zapisywanie danych odebranych bezpośrednio do pliku.</span><span class="sxs-lookup"><span data-stu-id="a62fe-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="a62fe-140">Jednak w niektórych przypadkach istnieje wymóg, aby wysyłać lub odbierać duże ilości danych, a także wykonywać przetwarzanie na fragmentach danych w miarę ich wysyłania lub odbierania.</span><span class="sxs-lookup"><span data-stu-id="a62fe-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="a62fe-141">Jednym ze sposobów na rozwiązanie takich scenariuszy jest zapisanie niestandardowego strumienia (klasy pochodzącej od <xref:System.IO.Stream>), która przetwarza dane w trakcie ich odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="a62fe-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="a62fe-142">Przykładem jest operacja `GetReversedStream` i Klasa `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="a62fe-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="a62fe-143">`GetReversedStream` tworzy i zwraca nowe wystąpienie `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="a62fe-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="a62fe-144">Rzeczywiste przetwarzanie odbywa się, gdy system odczytuje z tego obiektu `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="a62fe-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="a62fe-145">Implementacja `ReverseStream.Read` odczytuje fragmenty bajtów z pliku bazowego, odwraca je, a następnie zwraca odwrócone bajty.</span><span class="sxs-lookup"><span data-stu-id="a62fe-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="a62fe-146">Nie powoduje to odwrócenia całej zawartości pliku; powoduje odwrócenie jednego fragmentu bajtów w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="a62fe-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="a62fe-147">Jest to przykład pokazujący, jak można wykonać przetwarzanie strumienia, ponieważ zawartość jest odczytywana lub zapisywana z i do strumienia.</span><span class="sxs-lookup"><span data-stu-id="a62fe-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="a62fe-148">Uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="a62fe-148">Running the Sample</span></span>  
 <span data-ttu-id="a62fe-149">Aby uruchomić przykład, należy najpierw skompilować usługę i klienta, postępując zgodnie z instrukcjami na końcu tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a62fe-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="a62fe-150">Następnie uruchom usługę i klienta w dwóch różnych oknach konsoli.</span><span class="sxs-lookup"><span data-stu-id="a62fe-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="a62fe-151">Po uruchomieniu klienta czeka na naciśnięcie klawisza ENTER, gdy usługa jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="a62fe-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="a62fe-152">Klient następnie wywołuje metody `GetStream()`, `UploadStream()` i `GetReversedStream()` najpierw za pośrednictwem protokołu HTTP, a następnie za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="a62fe-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="a62fe-153">Oto przykładowe dane wyjściowe usługi, a następnie przykładowe dane wyjściowe z klienta:</span><span class="sxs-lookup"><span data-stu-id="a62fe-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="a62fe-154">Dane wyjściowe usługi:</span><span class="sxs-lookup"><span data-stu-id="a62fe-154">Service Output:</span></span>  
  
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
  
 <span data-ttu-id="a62fe-155">Dane wyjściowe klienta:</span><span class="sxs-lookup"><span data-stu-id="a62fe-155">Client Output:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a62fe-156">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a62fe-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a62fe-157">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a62fe-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a62fe-158">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a62fe-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a62fe-159">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a62fe-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a62fe-160">Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="a62fe-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a62fe-161">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a62fe-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a62fe-162">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a62fe-162">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="a62fe-163">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a62fe-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a62fe-164">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a62fe-164">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
