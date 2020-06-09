---
title: Kodowanie MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: cf048e1e6b2e2785accc1bde0336f07e3d84ae5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602542"
---
# <a name="mtom-encoding"></a>Kodowanie MTOM
Ten przykład ilustruje użycie kodowania komunikatów mechanizmu optymalizacji transmisji wiadomości (MTOM) za pomocą WSHttpBinding. MTOM to mechanizm przesyłania dużych załączników binarnych przy użyciu komunikatów protokołu SOAP jako bajtów nieprzetworzonych, co pozwala na mniejsze wiadomości.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Domyślnie WSHttpBinding wysyła i odbiera komunikaty jako zwykły tekst XML. Aby włączyć wysyłanie i otrzymywanie komunikatów mechanizmu MTOM, ustaw `messageEncoding` atrybut w konfiguracji powiązania (jak w poniższym kodzie) lub bezpośrednio na oprawie przy użyciu `MessageEncoding` właściwości. Usługa lub klient mogą teraz wysyłać i odbierać komunikaty mechanizmu MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 Koder MTOM może zoptymalizować tablice bajtów i strumieni. W tym przykładzie operacja używa `Stream` parametru i w związku z tym może być zoptymalizowana.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Umowa wybrana dla tego przykładu przesyła dane binarne do usługi i odbiera liczbę przekazanych bajtów jako wartość zwracaną. Po zainstalowaniu usługi i uruchomieniu klienta program drukuje numer 1000, który wskazuje, że odebrano wszystkie 1000 bajtów. Pozostała część danych wyjściowych zawiera zoptymalizowane i niezoptymalizowane rozmiary komunikatów dla różnych ładunków.  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 Celem używania mechanizmu MTOM jest zoptymalizowanie przesyłania dużych ładunków binarnych. Wysyłanie komunikatu protokołu SOAP przy użyciu mechanizmu MTOM ma zauważalne obciążenie dla małych ładunków binarnych, ale stają się doskonałym oszczędnościem, gdy rośnie w ciągu kilku tysięcy bajtów. Przyczyną tego jest fakt, że zwykły tekst XML koduje dane binarne przy użyciu algorytmu Base64, który wymaga czterech znaków dla każdego z trzech bajtów i zwiększa rozmiar danych o jeden trzeci. MTOM jest w stanie przesłać dane binarne jako nieprzetworzone bajty, co umożliwia zapisanie czasu kodowania/dekodowania i wygenerowanie mniejszych komunikatów. Próg kilku tysięcy bajtów jest mały w porównaniu z współczesnymi dokumentami biznesowymi i fotografiami cyfrowymi.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
