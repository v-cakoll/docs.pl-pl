---
title: Kodowanie MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: f54a22b0004623c8aef8f2788ed7d59f7d777ce7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003012"
---
# <a name="mtom-encoding"></a>Kodowanie MTOM
Niniejszy przykład pokazuje użycie kodowania za pomocą WSHttpBinding komunikatu komunikat transmisji optymalizacji mechanizm (MTOM). MTOM jest mechanizm przekazywania dużych załączników binarnych za pomocą protokołu SOAP wiadomości jako bajtów raw, pozwalając na mniejsze wiadomości.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Domyślnie wysyła WSHttpBinding i odebrane komunikaty w postaci zwykłego tekstu XML. Aby włączyć wysyłanie i odbieranie komunikatów MTOM, ustaw `messageEncoding` atrybut wiązania konfiguracji (jak poniższy przykład kodu) lub bezpośrednio za pomocą powiązania `MessageEncoding` właściwości. Usługi lub klienta mogą teraz wysyłanie i odbieranie wiadomości MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 Koder MTOM można zoptymalizować tablice bajtów i strumieni. W tym przykładzie operacja wykorzystuje `Stream` parametru i mogą być optymalizowane.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Kontrakt wybrana dla tego przykładu przesyła dane binarne do usługi i odbiera liczbę bajtów przekazany jako wartość zwracaną. Gdy usługa jest zainstalowana i klienta, wydrukowaniu liczby 1000, co oznacza, że otrzymano wszystkich 1000 bajtów. W pozostałej części danych wyjściowych Wyświetla listę rozmiarów zoptymalizowanych i niezoptymalizowany wiadomości różnych ładunków.  
  
```  
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
  
 Asysty MTOM ma na celu optymalizacji transmisji w trybie duży binarne ładunki. Trwa wysyłanie komunikatu protokołu SOAP, za pomocą MTOM ma zauważalnego obciążenie dla małych binarne ładunki, ale staje się doskonałe oszczędności, gdy ich rosnąć kilka tysięcy bajtów. Przyczyną jest, czy zwykłego tekstu XML koduje dane binarne, przy użyciu Base64, wymaga czterech znaków dla każdego z trzech bajtów, która zwiększa rozmiar danych o jedną trzecią. MTOM jest w stanie przesyłać danych binarnych jako bajtów raw, co umożliwia zaoszczędzenie czasu kodowania dekodowanie i co jest mniejsze wiadomości. Próg kilka tysięcy bajtów jest mały, w porównaniu do współczesnych firm dokumenty i zdjęcia.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też
