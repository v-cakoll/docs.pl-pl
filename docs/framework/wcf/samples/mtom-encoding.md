---
title: Kodowanie MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144386"
---
# <a name="mtom-encoding"></a>Kodowanie MTOM
W tym przykładzie pokazano użycie kodowania komunikatów mechanizmu optymalizacji transmisji wiadomości (MTOM) za pomocą funkcji WSHttpBinding. MTOM jest mechanizmem przesyłania dużych załączników binarnych z wiadomościami SOAP jako nieprzetworzonymi bajtami, co pozwala na mniejsze wiadomości.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Domyślnie plik WSHttpBinding wysyła i odbiera wiadomości jako zwykły tekst XML. Aby włączyć wysyłanie i odbieranie komunikatów MTOM, ustaw `messageEncoding` atrybut w konfiguracji powiązania (jak w poniższym `MessageEncoding` przykładowym kodzie) lub bezpośrednio na powiązanie przy użyciu właściwości. Usługa lub klient może teraz wysyłać i odbierać wiadomości MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 Koder MTOM może optymalizować tablice bajtów i strumieni. W tym przykładzie operacja `Stream` używa parametru i dlatego można zoptymalizować.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Kontrakt wybrany dla tego przykładu przesyła dane binarne do usługi i odbiera liczbę bajtów przekazanych jako wartość zwracaną. Po zainstalowaniu usługi i uruchomieniu klienta, drukuje liczbę 1000, co oznacza, że wszystkie 1000 bajtów zostały odebrane. Pozostała część danych wyjściowych zawiera zoptymalizowane i niestyptowane rozmiary komunikatów dla różnych ładunków.  
  
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
  
 Celem wykorzystania MTOM jest optymalizacja transmisji dużych ładunków binarnych. Wysyłanie wiadomości SOAP przy użyciu MTOM ma zauważalne obciążenie dla małych ładunków binarnych, ale staje się wielką oszczędnością, gdy rosną one ponad kilka tysięcy bajtów. Powodem tego jest to, że normalny tekst XML koduje dane binarne przy użyciu Base64, który wymaga czterech znaków na każde trzy bajty i zwiększa rozmiar danych o jedną trzecią. MTOM jest w stanie przesyłać dane binarne jako nieprzetworzone bajty, oszczędzając czas kodowania/dekodowania, a wynikowe jest mniejsze. Próg kilku tysięcy bajtów jest niewielki w porównaniu do dzisiejszych dokumentów biznesowych i fotografii cyfrowych.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
