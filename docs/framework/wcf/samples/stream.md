---
title: Strumień
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: 96b77d0135a4dac1dcb8406a1b9a1372d0c4a35d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508218"
---
# <a name="stream"></a>Strumień
Przykładowe strumienia zademonstrowano użycie przesyłania strumieniowego komunikacji tryb transferu. Usługa udostępnia kilka operacji wysyłania i odbierania strumieni. Ten przykład jest samodzielnie hostowana. Klient i usługa są programy konsoli.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Windows Communication Foundation (WCF) może komunikować się w dwóch trybach transfer — buforowany lub przesyłania strumieniowego. W domyślnym trybie buforowanego transferu wiadomości musi być całkowicie dostarczana przed odbiorca może go odczytać. W trybie przesyłania strumieniowego przesyłania można rozpocząć przetworzyć komunikatu przed przekazaniem całkowicie odbiornika. Tryb strumieniowy jest przydatne, gdy informacje przekazywane jest obszerne i mogą być przetwarzane pojedynczo. Tryb strumieniowy jest również przydatne, gdy komunikat jest zbyt duży, aby całkowicie buforowany.  
  
## <a name="streaming-and-service-contracts"></a>Przesyłania strumieniowego i kontrakty usług  
 Przesyłanie strumieniowe to element wziąć pod uwagę podczas projektowania kontrakt usługi. Jeśli operacja odbiera lub zwraca dużych ilości danych, należy rozważyć przesyłania strumieniowego te dane, aby uniknąć użycia pamięci wysokiej wskutek buforowania komunikatów wejściowych lub wyjściowych. Strumień danych, parametr, który przechowuje, że dane muszą być tylko parametr w komunikacie. Na przykład jeśli komunikat wejściowy jest przesyłane strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie w przypadku komunikatu wyjściowego strumieniowe przesyłanie, operacja musi mieć dokładnie jeden wyjściowy parametru lub wartości zwracanej. W przypadku, parametr lub zwracane wartości typu musi być albo `Stream`, `Message`, lub `IXmlSerializable`. Poniżej znajduje się kontraktu usługi, używany w tym przykładzie przesyłania strumieniowego.  
  
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
  
 `GetStream` Operacji odbiera niektórych danych wejściowych jako ciąg znaków, które są buforowane i zwraca `Stream`, który jest przesyłane strumieniowo. Z drugiej strony `UploadStream` przyjmuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowanej). `EchoStream` pobiera i zwraca `Stream` jest przykładem operacji których dane wejściowe i komunikaty wyjściowe zarówno strumieniowo. Na koniec `GetReversedStream` przyjmuje nie dane wejściowe i zwraca `Stream` (przesyłane strumieniowo).  
  
## <a name="enabling-streamed-transfers"></a>Włączanie przesyłanej strumieniowo transferu  
 Definiowanie kontraktów operacji, jak opisano wcześniej zapewnia przesyłania strumieniowego na poziomie modelu programowania. Jeśli zatrzymasz, transportu nadal buforuje zawartość cały komunikat. Aby włączyć transportu strumieniowego, wybierz tryb transferu w elemencie powiązania transportu. Element powiązania ma `TransferMode` właściwość, która może być ustawiony na `Buffered`, `Streamed`, `StreamedRequest`, lub `StreamedResponse`. Ustawienie Tryb transferu `Streamed` umożliwia przesyłanie strumieniowe komunikacji w obu kierunkach. Ustawienie Tryb transferu `StreamedRequest` lub `StreamedResponse` umożliwia przesyłanie strumieniowe komunikacji w tylko żądania lub odpowiedzi, odpowiednio.  
  
 `basicHttpBinding` Przedstawia `TransferMode` właściwość powiązanie, tak jak w przypadku `NetTcpBinding` i `NetNamedPipeBinding`. Dla innych transportu należy utworzyć niestandardowego powiązania, aby ustawić tryb transferu.  
  
 Poniższy kod konfiguracji z próbki pokazuje ustawienie `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania HTTP:  
  
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
  
 Oprócz ustawienia `transferMode` do `Streamed`, poprzedniego zestawu kodu konfiguracji `maxReceivedMessageSize` 64 MB. Jako mechanizm obrony `maxReceivedMessageSize` odbierania zakończenia na maksymalny dozwolony rozmiar wiadomości w miejscach. Wartość domyślna `maxReceivedMessageSize` wynosi 64 KB, który zazwyczaj jest zbyt stara przesyłania strumieniowego scenariuszy.  
  
## <a name="processing-data-as-it-is-streamed"></a>Przetwarzanie danych, ponieważ jest ona przesyłana strumieniowo  
 Operacje `GetStream`, `UploadStream` i `EchoStream` wszystkie postępowania w przypadku wysyłania danych bezpośrednio z pliku lub zapisywanie odebranych danych bezpośrednio w pliku. Jednak w niektórych przypadkach jest wymagane wysyłanie lub odbieranie dużych ilości danych i wykonać niektóre przetwarzania na fragmenty danych, ponieważ jest on wysyłane lub odbierane. Jednym ze sposobów rozwiązania takich scenariuszy należy napisać niestandardowych strumieni (klasy, która jest pochodną <xref:System.IO.Stream>) przetwarza dane, ponieważ jest do odczytu lub zapisu. `GetReversedStream` Operacji i `ReverseStream` klasy są na przykład.  
  
 `GetReversedStream` Tworzy i zwraca nowe wystąpienie klasy `ReverseStream`. Aktualnie przetwarzanego się stanie, jak system odczytuje niż `ReverseStream` obiektu. `ReverseStream.Read` Implementacji odczytuje fragmentu bajtów z pliku źródłowego, odwraca je, a następnie zwraca odwróconej bajtów. Będą to zawartości całego pliku; Odwraca ono jednym fragmencie bajtów w czasie. To jest przykład pokazanie, jak wykonać przetwarzającym strumień zawartości jest w trakcie odczytu lub zapisu z i do strumienia.  
  
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
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
 Aby uruchomić przykład, kompilacji zarówno usługę i klienta przez zgodnie z instrukcjami na końcu tego dokumentu. Następnie uruchom usługę i klienta w dwóch różnych konsoli systemu windows. Po uruchomieniu klienta oczekuje na można nacisnąć klawisz ENTER, gdy usługa jest gotowa. Klient następnie wywołuje metody `GetStream()`, `UploadStream()` i `GetReversedStream()` najpierw za pośrednictwem protokołu HTTP, a następnie za pośrednictwem protokołu TCP. Oto przykładowe dane wyjściowe z usługi następuje przykładowe dane wyjściowe z klienta:  
  
 Usługi danych wyjściowych:  
  
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
  
 Dane wyjściowe klienta:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a>Zobacz też
