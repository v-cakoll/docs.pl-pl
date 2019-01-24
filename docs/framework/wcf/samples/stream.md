---
title: Strumień
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: c16f12e6fb122fbba7dc46abb26859be49c08f74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662598"
---
# <a name="stream"></a>Strumień
Przykładowe Stream zademonstrowano użycie przesyłania strumieniowego komunikacji tryb transferu. Kilka operacji wysyłania i odbierania strumieni, które uwidacznia usługa. W tym przykładzie jest samodzielnie hostowana. Klient i usługa są programy konsoli.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Windows Communication Foundation (WCF) może komunikować się w dwóch trybach transferu — buforowane lub przesyłania strumieniowego. W domyślnym trybie buforowanego transferu wiadomości musi być całkowicie dostarczana przed odbiorca może go odczytać. W trybie przesyłania strumieniowego transferu odbiornika można rozpocząć przetworzyć komunikatu przed przekazaniem całkowicie. Tryb przesyłania strumieniowego jest przydatne, gdy informacje jest przekazywany jest długi i mogą być przetwarzane pojedynczo. Tryb przesyłania strumieniowego jest również przydatne, gdy komunikat jest zbyt duży, aby całkowicie buforowany.  
  
## <a name="streaming-and-service-contracts"></a>Przesyłanie strumieniowe i kontraktów usług  
 Przesyłanie strumieniowe jest coś, co wziąć pod uwagę podczas projektowania kontraktu usługi. Jeśli operacja odbiera lub zwraca dużych ilości danych, należy rozważyć, przesyłanie strumieniowe tych danych w celu uniknięcia wysokiego użycia pamięci z powodu buforowania komunikatów wejściowych lub wyjściowych. Przesyłanie strumieniowe danych parametr, który przechowuje, że dane muszą być jedynym parametrem w komunikacie. Na przykład jeśli komunikat wejściowy jest repliką strumieniowe przesyłanie, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie jeśli komunikat wyjściowy jest przesyłane strumieniowo, operacja musi mieć dokładnie jeden wyjściowy parametru lub wartości zwracanej. Wartość case, parametr lub zwracany typ musi być albo `Stream`, `Message`, lub `IXmlSerializable`. To jest Umowa serwisowa używane w tym przykładzie przesyłania strumieniowego.  
  
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
  
 `GetStream` Operacja odbiera dane wejściowe jako ciąg, który jest buforowana i zwraca `Stream`, który jest przesyłany strumieniowo. Z drugiej strony `UploadStream` przyjmuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowanej). `EchoStream` przyjmuje i zwraca `Stream` jest przykładem operacji, których dane wejściowe i wyjściowe komunikaty są zarówno przesyłane strumieniowo. Na koniec `GetReversedStream` nie dane wejściowe przyjmuje i zwraca `Stream` (przesyłane strumieniowo).  
  
## <a name="enabling-streamed-transfers"></a>Włączanie transfery przesyłane strumieniowo  
 Definiowanie kontraktów operacji, jak opisano wcześniej zapewnia przesyłania strumieniowego na poziomie modelu programowania. Jeśli użytkownik zaprzestanie, transport nadal buforuje zawartość cały komunikat. Aby włączyć transportu przesyłania strumieniowego, wybierz tryb transferu na element powiązania transportu. Element powiązania ma `TransferMode` właściwość, która może być równa `Buffered`, `Streamed`, `StreamedRequest`, lub `StreamedResponse`. Ustawienie trybu transferu `Streamed` umożliwia przesyłanie strumieniowe komunikacji w obu kierunkach. Ustawienie trybu transferu `StreamedRequest` lub `StreamedResponse` umożliwia przesyłanie strumieniowe komunikacji w tylko żądania lub odpowiedzi, odpowiednio.  
  
 `basicHttpBinding` Udostępnia `TransferMode` właściwości powiązania, tak jak `NetTcpBinding` i `NetNamedPipeBinding`. Dla innych transportu należy utworzyć niestandardowego powiązania, aby ustawić tryb transferu.  
  
 W poniższym kodzie konfiguracji z przykładowych pokazano ustawienie `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania protokołu HTTP:  
  
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
  
 Oprócz ustawienia `transferMode` do `Streamed`, poprzednie zestawów konfiguracyjnych w kodzie `maxReceivedMessageSize` 64 MB. W mechanizmie defense `maxReceivedMessageSize` otrzymywać limit maksymalny dozwolony rozmiar wiadomości w miejscach. Wartość domyślna `maxReceivedMessageSize` wynosi 64 KB, który zwykle jest zbyt mała dla przesyłania strumieniowego scenariuszy.  
  
## <a name="processing-data-as-it-is-streamed"></a>Przetwarzanie danych, ponieważ jest ona przesyłana strumieniowo  
 Operacje `GetStream`, `UploadStream` i `EchoStream` wszystko zaradzenia wysyłanie danych bezpośrednio z pliku lub zapisywania odebranych danych bezpośrednio do pliku. Jednak w niektórych przypadkach jest to wymagane do wysyłania lub odbierania dużej ilości danych i wykonywać niektóre przetwarzanie dużych ilości danych w miarę jego wysyłane lub odbierane. Jednym ze sposobów rozwiązania takich scenariuszy jest napisanie niestandardowego strumienia (klasy, która pochodzi od klasy <xref:System.IO.Stream>) przetwarza dane, ponieważ jest to odczytu lub zapisu. `GetReversedStream` Operacji i `ReverseStream` klasy są przykładem.  
  
 `GetReversedStream` Tworzy i zwraca nowe wystąpienie klasy `ReverseStream`. Rzeczywiste przetwarzanie odbywa się zgodnie z system odczytuje przy jego użyciu `ReverseStream` obiektu. `ReverseStream.Read` Implementacji odczytuje fragmentów bajtów z pliku podstawowego, cofa ich, a następnie zwraca bajtów odwróconej. Będą zawartości całego pliku; Odwraca ono jednym fragmencie bajtów w danym momencie. Jest to przykład demonstrujący, jak można wykonać przetwarzania strumienia, ponieważ zawartość jest odczytywanych lub zapisywanych od i do strumienia.  
  
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
  
## <a name="running-the-sample"></a>Działa aplikacja przykładowa  
 Aby uruchomić przykład, twórz usługi i klienta postępując zgodnie z instrukcjami wyświetlanymi na końcu tego dokumentu. Następnie uruchom usługę i klienta w dwóch różnych konsoli systemu windows. Po uruchomieniu klient czeka na naciśnięcie klawisza ENTER, gdy usługa jest gotowa. Klient następnie wywołuje metody `GetStream()`, `UploadStream()` i `GetReversedStream()` najpierw przy użyciu protokołu HTTP, a następnie za pośrednictwem protokołu TCP. Poniżej przedstawiono przykładowe dane wyjściowe z usługi, a po nim przykładowe dane wyjściowe z klienta:  
  
 Dane wyjściowe usługi:  
  
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
  
 Dane wyjściowe z klienta:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a>Zobacz także
