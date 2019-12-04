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
# <a name="stream"></a>Strumień
Przykład strumienia ilustruje użycie komunikacji w trybie transferu strumieniowego. Usługa udostępnia kilka operacji wysyłających i odbierających strumienie. Ten przykład jest samodzielny. Zarówno klient, jak i usługa to programy konsolowe.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Windows Communication Foundation (WCF) może komunikować się w dwóch trybach transferu — buforowane lub przesyłane strumieniowo. W domyślnym trybie transferu buforowanego komunikat musi zostać całkowicie dostarczony, aby odbiorca mógł go odczytać. W trybie transferu strumieniowego odbiorca może zacząć przetwarzać komunikat, zanim zostanie on całkowicie dostarczony. Tryb przesyłania strumieniowego jest przydatny, gdy przesyłane informacje są długie i mogą być przetwarzane sekwencyjnie. Tryb przesyłania strumieniowego jest również przydatny, gdy komunikat jest zbyt duży, aby był całkowicie buforowany.  
  
## <a name="streaming-and-service-contracts"></a>Kontrakty przesyłania strumieniowego i usług  
 Przesyłanie strumieniowe jest brane pod uwagę podczas projektowania kontraktu usługi. Jeśli operacja odbiera lub zwraca duże ilości danych, należy rozważyć przesyłanie strumieniowe tych danych w celu uniknięcia wysokiego użycia pamięci z powodu buforowania komunikatów wejściowych lub wyjściowych. Aby przesłać strumieniowo dane, parametr, który przechowuje te dane, musi być jedynym parametrem w komunikacie. Na przykład jeśli komunikat wejściowy jest przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie, jeśli wiadomość wyjściowa ma być przesyłana strumieniowo, operacja musi mieć dokładnie jeden parametr wyjściowy lub wartość zwracaną. W obu przypadkach parametr lub typ wartości zwracanej musi mieć wartość `Stream`, `Message`lub `IXmlSerializable`. Poniżej znajduje się kontrakt usługi używany w tym przykładzie przesyłania strumieniowego.  
  
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
  
 Operacja `GetStream` otrzymuje dane wejściowe jako ciąg, który jest buforowany i zwraca `Stream`, który jest przesyłany strumieniowo. Z kolei `UploadStream` wykonuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowana). `EchoStream` pobiera i zwraca `Stream` i jest przykładem operacji, której przesyłanie strumieniowe i wyjściowe odbywa się jednocześnie. Na koniec `GetReversedStream` nie pobiera danych wejściowych i zwraca `Stream` (przesyłane strumieniowo).  
  
## <a name="enabling-streamed-transfers"></a>Włączanie transferu strumieniowego  
 Zdefiniowanie kontraktów operacji, jak opisano wcześniej, zapewnia przesyłanie strumieniowe na poziomie modelu programowania. Jeśli zatrzymasz ten problem, transport nadal buforuje całą zawartość wiadomości. Aby włączyć przesyłanie strumieniowe transportu, wybierz tryb transferu dla elementu powiązania transportu. Element Binding ma właściwość `TransferMode`, która może być ustawiona na `Buffered`, `Streamed`, `StreamedRequest`lub `StreamedResponse`. Ustawienie trybu transferu na `Streamed` Włącza komunikację przesyłania strumieniowego w obu kierunkach. Ustawienie trybu transferu na `StreamedRequest` lub `StreamedResponse` Włącza komunikację przesyłania strumieniowego odpowiednio do żądania lub odpowiedzi.  
  
 `basicHttpBinding` uwidacznia Właściwość `TransferMode` w powiązaniu jako `NetTcpBinding` i `NetNamedPipeBinding`. W przypadku innych transportów należy utworzyć niestandardowe powiązanie, aby ustawić tryb transferu.  
  
 Poniższy kod konfiguracji z przykładu przedstawia Ustawianie właściwości `TransferMode` do przesyłania strumieniowego `basicHttpBinding` i niestandardowego powiązania HTTP:  
  
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
  
 Poza ustawieniem `transferMode` na `Streamed`, poprzedni kod konfiguracji ustawia `maxReceivedMessageSize` na 64 MB. Jako mechanizm obrony `maxReceivedMessageSize` umieszcza limit na maksymalny dozwolony rozmiar komunikatów odbieranych przez program. Domyślny `maxReceivedMessageSize` to 64 KB, który jest zwykle zbyt niski dla scenariuszy przesyłania strumieniowego.  
  
## <a name="processing-data-as-it-is-streamed"></a>Przetwarzanie danych przesyłanych strumieniowo  
 Operacje `GetStream`, `UploadStream` i `EchoStream` wszystkie związane z wysyłaniem danych bezpośrednio z pliku lub zapisywanie danych odebranych bezpośrednio do pliku. Jednak w niektórych przypadkach istnieje wymóg, aby wysyłać lub odbierać duże ilości danych, a także wykonywać przetwarzanie na fragmentach danych w miarę ich wysyłania lub odbierania. Jednym ze sposobów na rozwiązanie takich scenariuszy jest zapisanie niestandardowego strumienia (klasy pochodzącej od <xref:System.IO.Stream>), która przetwarza dane w trakcie ich odczytu lub zapisu. Przykładem jest operacja `GetReversedStream` i Klasa `ReverseStream`.  
  
 `GetReversedStream` tworzy i zwraca nowe wystąpienie `ReverseStream`. Rzeczywiste przetwarzanie odbywa się, gdy system odczytuje z tego obiektu `ReverseStream`. Implementacja `ReverseStream.Read` odczytuje fragmenty bajtów z pliku bazowego, odwraca je, a następnie zwraca odwrócone bajty. Nie powoduje to odwrócenia całej zawartości pliku; powoduje odwrócenie jednego fragmentu bajtów w danym momencie. Jest to przykład pokazujący, jak można wykonać przetwarzanie strumienia, ponieważ zawartość jest odczytywana lub zapisywana z i do strumienia.  
  
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
  
## <a name="running-the-sample"></a>Uruchamianie przykładu  
 Aby uruchomić przykład, należy najpierw skompilować usługę i klienta, postępując zgodnie z instrukcjami na końcu tego dokumentu. Następnie uruchom usługę i klienta w dwóch różnych oknach konsoli. Po uruchomieniu klienta czeka na naciśnięcie klawisza ENTER, gdy usługa jest gotowa. Klient następnie wywołuje metody `GetStream()`, `UploadStream()` i `GetReversedStream()` najpierw za pośrednictwem protokołu HTTP, a następnie za pośrednictwem protokołu TCP. Oto przykładowe dane wyjściowe usługi, a następnie przykładowe dane wyjściowe z klienta:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
