---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: d2111639266612183630231dbd51be55ef9c1ee4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779341"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
W przykładzie pokazano sposób tworzenia powiązania, który jest przeznaczony do obsługi transmisji strumieniowej scenariuszy stosowania transportu HTTP.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Dostępne są następujące kroki, aby utworzyć i skonfigurować nowe powiązanie standardowe.  
  
1.  Utwórz nowe powiązanie standardowe  
  
     Powiązania w standardowych w Windows Communication Foundation (WCF), takie jak basicHttpBinding i netTcpBinding Konfigurowanie transportów podstawowych i stosu kanału do określonych wymagań. W tym przykładzie `WSStreamedHttpBinding` konfiguruje stosu kanału do obsługi przesyłania strumieniowego. Domyślnie WS-Security i niezawodną obsługę komunikatów nie są dodawane do stosu kanału, ponieważ obie funkcje nie są obsługiwane przez przesyłania strumieniowego. Nowe powiązanie jest zaimplementowana w klasie `WSStreamedHttpBinding` który pochodzi od klasy <xref:System.ServiceModel.Channels.Binding>. `WSStreamedHttpBinding` Zawiera następujące elementy powiązania: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, i <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Klasa oferuje `CreateBindingElements()` metodę, aby skonfigurować wynikowy stosu powiązania, jak pokazano w poniższym przykładowym kodzie.  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2.  Dodanie obsługi konfiguracji  
  
     Aby uwidocznić transportu za pomocą konfiguracji próbki implementuje dwóch klas więcej —`WSStreamedHttpBindingConfigurationElement` i `WSStreamedHttpBindingSection`. Klasa `WSStreamedHttpBindingSection` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> który uwidacznia `WSStreamedHttpBinding` systemu konfiguracji usługi WCF. Duża część wykonania jest delegowane do `WSStreamedHttpBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>. Klasa `WSStreamedHttpBindingConfigurationElement` ma właściwości, które odnoszą się do właściwości `WSStreamedHttpBinding`i funkcje, aby mapować każdy element konfiguracji do powiązania.  
  
     Zarejestruj program obsługi przy użyciu systemu konfiguracji, dodając następującą sekcję do pliku konfiguracji usługi.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Program obsługi mogą następnie odwoływać się w sekcji Konfiguracja modelu serviceModel.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano czynności opisane w [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Do uruchomienia przykładu w konfiguracji między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6.  Kiedy wyświetli się okno klienta, wpisz "Przykład.txt". "Kopiuj z przykład.txt" powinien znajdować się w katalogu.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>Usługa WSStreamedHttpBinding próbki  
 Usługa próbki, która używa `WSStreamedHttpBinding` znajduje się w podkatalogu usługi. Implementacja `OperationContract` używa `MemoryStream` można najpierw pobrać wszystkie dane w przychodzącym strumieniu przed zwróceniem `MemoryStream`. Próbka jest hostowana usługa Internet Information Services (IIS).  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>Klient WSStreamedHttpBinding próbki  
 Klient, który służy do interakcji z usługą przy użyciu `WSStreamedHttpBinding` znajduje się w podkatalogu klienta. Ponieważ certyfikat używany w tym przykładzie jest utworzone za pomocą Makecert.exe certyfikat testowy, alert zabezpieczeń zawiera przy próbie uzyskania dostępu do adresu HTTPS w przeglądarce, takich jak https://localhost/servicemodelsamples/service.svc. Aby zezwolić na klienta platformy WCF do pracy z certyfikatem testowym w miejscu, dodano dodatkowy kod klienta dla pomijania alertu zabezpieczeń. Kod i towarzyszące klasy nie są wymagane, podczas korzystania z certyfikatów w środowisku produkcyjnym.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a>Zobacz też
