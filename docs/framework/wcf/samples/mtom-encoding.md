---
title: Kodowanie MTOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 46984ea1ac08aa1128a4f32144285f590eafb6c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mtom-encoding"></a>Kodowanie MTOM
W przykładzie pokazano, użyj kodowania z WSHttpBinding wiadomości mechanizmu optymalizacji transmisji wiadomości (MTOM). MTOM jest mechanizm przekazywania dużych załączników binarnych z komunikatami SOAP raw bajtów, co pozwala na mniejsze wiadomości.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Domyślnie wysyła WSHttpBinding i odebranych komunikatów jako zwykły tekst XML. Aby włączyć wysyłanie i odbieranie komunikatów MTOM, ustaw `messageEncoding` atrybut w konfiguracji powiązania (jak poniższy przykład kodu) lub bezpośrednio za pomocą powiązania `MessageEncoding` właściwości. Usługi lub klienta można teraz wysyłać i odbierać komunikaty MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 Koder MTOM zoptymalizować tablice bajtów i strumieni. W tym przykładzie używa operacji `Stream` parametru i mogą być optymalizowane.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```  
  
 Kontrakt wybrany dla tego przykładu przesyła dane binarne do usługi i odbiera liczba bajtów przekazany jako wartości zwracane. Gdy usługa jest zainstalowana i uruchomieniu klienta, Wyświetla ilość 1000, co oznacza, że otrzymano wszystkich 1000 bajtów. W pozostałej części dane wyjściowe wyświetla listę komunikatów wersją zoptymalizowaną a niezoptymalizowaną rozmiarów różnych ładunków.  
  
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
  
 Cel przy użyciu mechanizmu MTOM jest optymalizacji transmisji dużych ładunków binarne. Wysyłanie wiadomości SOAP przy użyciu mechanizmu MTOM mają zauważalne narzut dla małych ładunków binarne, ale staje się doskonałe oszczędności, gdy ich wraz z upływem kilku tysięcy bajtów. Przyczyną tego jest czy zwykłego tekstu XML koduje dane binarne przy użyciu Base64, który wymaga cztery znaki co trzy bajtów i zwiększa rozmiar danych, jedna trzecia. MTOM jest w stanie przesyłać dane binarne jako nieprzetworzone bajtów, oszczędzając czas kodowanie dekodowania i co jest mniejszy wiadomości. Próg kilku tysięcy bajtów jest małe w stosunku do bieżącej firm dokumenty i zdjęcia.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też
