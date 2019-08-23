---
title: Strumień
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: 9bafdf41f8e608182cc8cff55ac84a4acbd644d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958778"
---
# <a name="stream"></a>Strumień
Przykład strumienia ilustruje użycie komunikacji w trybie transferu strumieniowego. Usługa udostępnia kilka operacji wysyłających i odbierających strumienie. Ten przykład jest samodzielny. Zarówno klient, jak i usługa to programy konsolowe.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Windows Communication Foundation (WCF) może komunikować się w dwóch trybach transferu — buforowane lub przesyłane strumieniowo. W domyślnym trybie transferu buforowanego komunikat musi zostać całkowicie dostarczony, aby odbiorca mógł go odczytać. W trybie transferu strumieniowego odbiorca może zacząć przetwarzać komunikat, zanim zostanie on całkowicie dostarczony. Tryb przesyłania strumieniowego jest przydatny, gdy przesyłane informacje są długie i mogą być przetwarzane sekwencyjnie. Tryb przesyłania strumieniowego jest również przydatny, gdy komunikat jest zbyt duży, aby był całkowicie buforowany.  
  
## <a name="streaming-and-service-contracts"></a>Kontrakty przesyłania strumieniowego i usług  
 Przesyłanie strumieniowe jest brane pod uwagę podczas projektowania kontraktu usługi. Jeśli operacja odbiera lub zwraca duże ilości danych, należy rozważyć przesyłanie strumieniowe tych danych w celu uniknięcia wysokiego użycia pamięci z powodu buforowania komunikatów wejściowych lub wyjściowych. Aby przesłać strumieniowo dane, parametr, który przechowuje te dane, musi być jedynym parametrem w komunikacie. Na przykład jeśli komunikat wejściowy jest przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie, jeśli wiadomość wyjściowa ma być przesyłana strumieniowo, operacja musi mieć dokładnie jeden parametr wyjściowy lub wartość zwracaną. W obu przypadkach parametr lub typ wartości zwracanej musi mieć `Stream`wartość, `Message`, lub `IXmlSerializable`. Poniżej znajduje się kontrakt usługi używany w tym przykładzie przesyłania strumieniowego.  
  
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
  
 Operacja otrzymuje dane wejściowe jako ciąg, który jest buforowany i zwraca obiekt `Stream`, który jest przesyłany strumieniowo. `GetStream` Z drugiej `UploadStream` strony, przyjmuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowana). `EchoStream`przyjmuje i zwraca `Stream` i jest przykładem operacji, której przesyłanie strumieniowe danych wejściowych i wyjściowych odbywa się jednocześnie. `GetReversedStream` Na`Stream` koniec nie przyjmuje danych wejściowych i zwraca (strumieniowo).  
  
## <a name="enabling-streamed-transfers"></a>Włączanie transferu strumieniowego  
 Zdefiniowanie kontraktów operacji, jak opisano wcześniej, zapewnia przesyłanie strumieniowe na poziomie modelu programowania. Jeśli zatrzymasz ten problem, transport nadal buforuje całą zawartość wiadomości. Aby włączyć przesyłanie strumieniowe transportu, wybierz tryb transferu dla elementu powiązania transportu. Element `TransferMode` Binding ma właściwość, która może być ustawiona na `Streamed` `Buffered`,, `StreamedRequest`, lub `StreamedResponse`. Ustawienie trybu transferu w taki `Streamed` sposób, aby włączyć komunikację przesyłania strumieniowego w obu kierunkach. Ustawienie trybu transferu na `StreamedRequest` lub `StreamedResponse` umożliwia komunikację przesyłania strumieniowego tylko odpowiednio do żądania lub odpowiedzi.  
  
 Uwidacznia właściwość dla powiązania jako`NetNamedPipeBinding`i. `NetTcpBinding` `basicHttpBinding` `TransferMode` W przypadku innych transportów należy utworzyć niestandardowe powiązanie, aby ustawić tryb transferu.  
  
 Poniższy kod konfiguracji z przykładu pokazuje ustawienie `TransferMode` właściwości do przesyłania strumieniowego `basicHttpBinding` i niestandardowego powiązania http:  
  
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
  
 Oprócz ustawienia `transferMode` do `Streamed`, `maxReceivedMessageSize` poprzedni kod konfiguracji ustawia do 64 MB. Jako mechanizm obrony należy `maxReceivedMessageSize` umieścić limit na maksymalny dozwolony rozmiar komunikatów odbieranych. Wartość domyślna `maxReceivedMessageSize` to 64 KB, która jest zwykle zbyt niska dla scenariuszy przesyłania strumieniowego.  
  
## <a name="processing-data-as-it-is-streamed"></a>Przetwarzanie danych przesyłanych strumieniowo  
 Operacje `UploadStream` i `GetStream` wszystkie`EchoStream` działania związane z wysyłaniem danych bezpośrednio z pliku lub zapisywaniem danych odebranych bezpośrednio do pliku. Jednak w niektórych przypadkach istnieje wymóg, aby wysyłać lub odbierać duże ilości danych, a także wykonywać przetwarzanie na fragmentach danych w miarę ich wysyłania lub odbierania. Jednym ze sposobów na rozwiązanie takich scenariuszy jest zapisanie niestandardowego strumienia (klasy pochodzącej z <xref:System.IO.Stream>), która przetwarza dane w miarę ich odczytu lub zapisu. Przykładem jest `ReverseStream`operacjaiKlasa `GetReversedStream` .  
  
 `GetReversedStream`tworzy i zwraca nowe wystąpienie `ReverseStream`. Rzeczywiste przetwarzanie odbywa się, gdy system odczytuje z tego `ReverseStream` obiektu. `ReverseStream.Read` Implementacja odczytuje fragmenty bajtów z pliku bazowego, odwraca je, a następnie zwraca odwrócone bajty. Nie powoduje to odwrócenia całej zawartości pliku; powoduje odwrócenie jednego fragmentu bajtów w danym momencie. Jest to przykład pokazujący, jak można wykonać przetwarzanie strumienia, ponieważ zawartość jest odczytywana lub zapisywana z i do strumienia.  
  
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
 Aby uruchomić przykład, należy najpierw skompilować usługę i klienta, postępując zgodnie z instrukcjami na końcu tego dokumentu. Następnie uruchom usługę i klienta w dwóch różnych oknach konsoli. Po uruchomieniu klienta czeka na naciśnięcie klawisza ENTER, gdy usługa jest gotowa. Klient wywołuje metody `GetStream()`, `UploadStream()` a `GetReversedStream()` najpierw za pośrednictwem protokołu HTTP, a następnie za pośrednictwem protokołu TCP. Oto przykładowe dane wyjściowe usługi, a następnie przykładowe dane wyjściowe z klienta:  
  
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
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
