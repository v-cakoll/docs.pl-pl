---
title: WSStreamedHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6259640bae2b4be4fac73883df8945bf1db7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
Przykład przedstawia sposób tworzenia powiązania, które umożliwia obsługę przesyłania strumieniowego scenariuszy stosowania transportu HTTP.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Dostępne są następujące kroki, aby utworzyć i skonfigurować nowe powiązanie standardowe.  
  
1.  Utwórz nowe powiązanie standardowe  
  
     Standardowe powiązania w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] takie jak basicHttpBinding i netTcpBinding Konfigurowanie transportów podstawowej i stosu kanału dla określonych wymagań. W tym przykładzie `WSStreamedHttpBinding` konfiguruje stosu kanału w celu obsługi przesyłania strumieniowego. Domyślnie WS-Security i niezawodna obsługa komunikatów nie są dodawane do stosu kanału, ponieważ obie funkcje nie są obsługiwane przez przesyłania strumieniowego. Nowe powiązanie jest zaimplementowana w klasie `WSStreamedHttpBinding` która pochodzi z <xref:System.ServiceModel.Channels.Binding>. `WSStreamedHttpBinding` Zawiera następujące elementy powiązania: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, i <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Ta klasa dostarcza `CreateBindingElements()` Metoda konfiguracji wynikowy stosu powiązanie, jak pokazano w poniższym kodzie próbki.  
  
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
  
2.  Dodawanie obsługi konfiguracji  
  
     Do udostępnienia transportu za pomocą konfiguracji próbki implementuje dwie klasy więcej —`WSStreamedHttpBindingConfigurationElement` i `WSStreamedHttpBindingSection`. Klasa `WSStreamedHttpBindingSection` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> który uwidacznia `WSStreamedHttpBinding` do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system konfiguracji. Delegowane do zbiorczego wdrożenia `WSStreamedHttpBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>. Klasa `WSStreamedHttpBindingConfigurationElement` ma właściwości, które odpowiadają właściwości `WSStreamedHttpBinding`i funkcji do mapowania każdego elementu konfiguracji powiązania.  
  
     Zarejestruj program obsługi przy użyciu systemu konfiguracji przez dodanie następujących sekcji w pliku konfiguracji usługi.  
  
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
  
     Program obsługi można odwoływać się następnie z sekcji konfiguracji serviceModel.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano czynności opisane w [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Upewnij się, że wykonano procedurę [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Aby uruchomić przykładowy w konfiguracji między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6.  Po wyświetleniu okna klienta, wpisz "Przykład.txt". "Kopiowania z przykład.txt" powinien znajdować się w katalogu.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>Usługa WSStreamedHttpBinding próbki  
 Usługa próbki, która używa `WSStreamedHttpBinding` znajduje się w podkatalogu usługi. Implementacja `OperationContract` używa `MemoryStream` najpierw pobrać wszystkich danych ze strumienia przychodzącego przed zwróceniem `MemoryStream`. Usługa próbki jest obsługiwana przez Internet Information Services (IIS).  
  
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
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>Przykładowe WSStreamedHttpBinding klienta  
 Klient, który służy do interakcji z usługi przy użyciu `WSStreamedHttpBinding` znajduje się w podkatalogu klienta. Ponieważ certyfikat użyty w tym przykładzie jest certyfikatu testowego utworzone za pomocą Makecert.exe, alert zabezpieczeń wyświetlany, gdy próbują uzyskać dostęp w przeglądarce, takie jak https://localhost/servicemodelsamples/service.svc adres HTTPS. Aby umożliwić [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, aby pracować przy użyciu certyfikatu testowego w miejscu, dodatkowy kod został dodany do klienta dla pomijania alertu zabezpieczeń. Kod i towarzyszące klasy nie są wymagane, podczas korzystania z certyfikatów w środowisku produkcyjnym.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a>Zobacz też
