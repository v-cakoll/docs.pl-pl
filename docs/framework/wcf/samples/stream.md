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
# <a name="stream"></a>Strumień
Próbka Stream pokazuje użycie komunikacji w trybie przesyłania strumieniowego. Usługa udostępnia kilka operacji, które wysyłają i odbierają strumienie. Ten przykład jest hostowany samodzielnie. Zarówno klient, jak i usługa są programami konsolowymi.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Windows Communication Foundation (WCF) może komunikować się w dwóch trybach transferu — buforowane lub przesyłania strumieniowego. W domyślnym buforowanym trybie transferu komunikat musi zostać całkowicie dostarczony, zanim odbiorca będzie mógł ją odczytać. W trybie przesyłania strumieniowego odbiorca może rozpocząć przetwarzanie wiadomości, zanim zostanie całkowicie dostarczona. Tryb przesyłania strumieniowego jest przydatne, gdy informacje, które są przekazywane jest długa i mogą być przetwarzane szeregowo. Tryb przesyłania strumieniowego jest również przydatne, gdy wiadomość jest zbyt duża, aby być całkowicie buforowane.  
  
## <a name="streaming-and-service-contracts"></a>Kontrakty przesyłania strumieniowego i usług  
 Przesyłanie strumieniowe jest czymś, co należy wziąć pod uwagę podczas projektowania umowy serwisowej. Jeśli operacja odbiera lub zwraca duże ilości danych, należy rozważyć przesyłanie strumieniowe tych danych, aby uniknąć wysokiego wykorzystania pamięci z powodu buforowania komunikatów wejściowych lub wyjściowych. Aby przesyłać strumieniowo dane, parametr, który przechowuje te dane, musi być jedynym parametrem w komunikacie. Na przykład jeśli komunikat wejściowy jest ten, który ma być przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie jeśli komunikat wyjściowy ma być przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wyjściowy lub wartość zwracaną. W obu przypadkach parametr lub typ wartości zwracanej `Message`musi `IXmlSerializable`być albo `Stream`, lub . Poniżej znajduje się umowa serwisowa używana w tym przykładzie przesyłania strumieniowego.  
  
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
  
 Operacja `GetStream` odbiera niektóre dane wejściowe jako ciąg, który `Stream`jest buforowany i zwraca , który jest przesyłany strumieniowo. Z drugiej `UploadStream` strony `Stream` przyjmuje (przesyłane strumieniowo) i zwraca `bool` (buforowane). `EchoStream`pobiera i `Stream` zwraca i jest przykładem operacji, której komunikaty wejściowe i wyjściowe są przesyłane strumieniowo. Na koniec `GetReversedStream` nie pobiera żadnych `Stream` danych wejściowych i zwraca (przesyłane strumieniowo).  
  
## <a name="enabling-streamed-transfers"></a>Włączanie transferów przesyłanych strumieniowo  
 Definiowanie kontraktów operacyjnych, jak opisano wcześniej zapewnia przesyłanie strumieniowe na poziomie modelu programowania. Jeśli zatrzymasz się tam, transport nadal buforuje całą zawartość wiadomości. Aby włączyć przesyłanie strumieniowe transportu, wybierz tryb transferu na element powiązania transportu. Element wiązania ma `TransferMode` właściwość, którą `Buffered` `Streamed`można `StreamedRequest`ustawić `StreamedResponse`na , , , lub . Ustawienie trybu transferu `Streamed` w celu umożliwiającego przesyłanie strumieniowe komunikacji w obu kierunkach. Ustawienie trybu transferu `StreamedRequest` `StreamedResponse` lub włącza komunikację strumieniową odpowiednio tylko w żądaniu lub odpowiedzi.  
  
 Udostępnia `basicHttpBinding` `TransferMode` właściwość na powiązanie, `NetTcpBinding` `NetNamedPipeBinding`podobnie jak i . W przypadku innych transportów należy utworzyć niestandardowe powiązanie, aby ustawić tryb transferu.  
  
 Następujący kod konfiguracji z przykładu `TransferMode` pokazuje ustawienie `basicHttpBinding` właściwości do przesyłania strumieniowego na i niestandardowe powiązanie HTTP:  
  
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
  
 Oprócz ustawienia `transferMode` na `Streamed`, poprzedni kod konfiguracji `maxReceivedMessageSize` ustawia na 64MB. Jako mechanizm obronny `maxReceivedMessageSize` umieszcza limit maksymalnego dopuszczalnego rozmiaru wiadomości podczas odbierania. Wartość `maxReceivedMessageSize` domyślna to 64 KB, która jest zwykle zbyt niska dla scenariuszy przesyłania strumieniowego.  
  
## <a name="processing-data-as-it-is-streamed"></a>Przetwarzanie danych w miarę ich przesyłania strumieniowego  
 Operacje `GetStream`i `UploadStream` `EchoStream` wszystkie dotyczą wysyłania danych bezpośrednio z pliku lub zapisywania odebranych danych bezpośrednio do pliku. Jednak w niektórych przypadkach istnieje wymóg wysyłania lub odbierania dużych ilości danych i wykonywania niektórych przetwarzania na fragmentach danych, gdy są wysyłane lub odbierane. Jednym ze sposobów rozwiązania takich scenariuszy jest napisanie strumienia <xref:System.IO.Stream>niestandardowego (klasy, która wywodzi się z ), który przetwarza dane w miarę ich odczytu lub zapisu. Operacja `GetReversedStream` i `ReverseStream` klasa są tego przykładem.  
  
 `GetReversedStream`tworzy i zwraca nowe `ReverseStream`wystąpienie . Rzeczywiste przetwarzanie odbywa się w `ReverseStream` systemie odczytuje z tego obiektu. Implementacja `ReverseStream.Read` odczytuje fragment bajtów z pliku źródłowego, odwraca je, a następnie zwraca odwrócone bajty. Nie powoduje to odwrócenia całej zawartości pliku; odwraca jeden fragment bajtów naraz. Jest to przykład, aby pokazać, jak można wykonać przetwarzanie strumienia, jak zawartość jest odczytywany lub zapisywany z i do strumienia.  
  
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
  
## <a name="running-the-sample"></a>Uruchamianie próbki  
 Aby uruchomić przykład, najpierw skompiluj usługę i klienta, postępając zgodnie ze wskazówkami na końcu tego dokumentu. Następnie uruchom usługę i klienta w dwóch różnych oknach konsoli. Po uruchomieniu klienta czeka na naciśnięcie klawisza ENTER, gdy usługa jest gotowa. Następnie klient wywołuje `GetStream()`metody `UploadStream()` `GetReversedStream()` , a najpierw za pośrednictwem protokołu HTTP, a następnie za pośrednictwem protokołu TCP. Oto przykład danych wyjściowych z usługi, a następnie przykładowe dane wyjściowe z klienta:  
  
 Wyjście usługi:  
  
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
  
 Dane wyjściowe klienta:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
