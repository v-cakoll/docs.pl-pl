---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 619c7e793ff94efffcb72774cf3e367df377a3a3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600896"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding

W przykładzie pokazano, jak utworzyć powiązanie, które jest przeznaczone do obsługi scenariuszy przesyłania strumieniowego, gdy używany jest transport HTTP.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 Poniżej przedstawiono procedurę tworzenia i konfigurowania nowego powiązania standardowego.

1. Tworzenie nowego powiązania standardowego

    Standardowe powiązania w Windows Communication Foundation (WCF), takie jak basicHttpBinding i netTcpBinding, konfigurują podstawowe transporty i stos kanałów dla określonych wymagań. W tym przykładzie `WSStreamedHttpBinding` konfiguruje stos kanałów do obsługi przesyłania strumieniowego. Domyślnie usługa WS-Security i niezawodna obsługa komunikatów nie są dodawane do stosu kanałów, ponieważ obie funkcje nie są obsługiwane przez przesyłanie strumieniowe. Nowe powiązanie jest zaimplementowane w klasie `WSStreamedHttpBinding` , która pochodzi od <xref:System.ServiceModel.Channels.Binding> . `WSStreamedHttpBinding`Zawiera następujące elementy powiązania: <xref:System.ServiceModel.Channels.HttpTransportBindingElement> , <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> , <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , i <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> . Klasa udostępnia `CreateBindingElements()` metodę konfigurowania wynikowego stosu powiązań, jak pokazano w poniższym przykładowym kodzie.

    ```csharp
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

2. Dodawanie obsługi konfiguracji

    Aby uwidocznić transport poprzez konfigurację, przykład implementuje dwie więcej klas — `WSStreamedHttpBindingConfigurationElement` i `WSStreamedHttpBindingSection` . Klasa `WSStreamedHttpBindingSection` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> uwidaczniana `WSStreamedHttpBinding` dla systemu konfiguracji WCF. Zbiorcza implementacja jest delegowana do `WSStreamedHttpBindingConfigurationElement` , który pochodzi od <xref:System.ServiceModel.Configuration.StandardBindingElement> . Klasa `WSStreamedHttpBindingConfigurationElement` ma właściwości, które odpowiadają właściwościom `WSStreamedHttpBinding` , i funkcje do mapowania każdego elementu konfiguracji do powiązania.

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

    Do programu obsługi można odwoływać się z sekcji konfiguracji serviceModel.

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

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że wykonano kroki opisane w [temacie Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

3. Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](iis-server-certificate-installation-instructions.md).

4. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

5. Aby uruchomić przykład w konfiguracji między maszynami, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

6. Po wyświetleniu okna klienta wpisz "Sample. txt". W katalogu powinna znajdować się "kopia przykładowa. txt".

## <a name="the-wsstreamedhttpbinding-sample-service"></a>Przykładowa usługa WSStreamedHttpBinding

Przykładowa usługa, która używa programu, `WSStreamedHttpBinding` znajduje się w podkatalogu usługi. Implementacja programu `OperationContract` używa programu, `MemoryStream` Aby najpierw pobrać wszystkie dane ze strumienia przychodzącego przed zwróceniem `MemoryStream` . Przykładowa usługa jest hostowana przez Internet Information Services (IIS).

```csharp
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

## <a name="the-wsstreamedhttpbinding-sample-client"></a>Przykładowy klient WSStreamedHttpBinding

Klient, który jest używany do współpracy z usługą za pomocą programu, `WSStreamedHttpBinding` znajduje się w podkatalogu klienta. Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym przy użyciu programu Makecert. exe, podczas próby uzyskania dostępu do adresu HTTPS w przeglądarce, takiego jak `https://localhost/servicemodelsamples/service.svc` . Aby umożliwić klientowi WCF współpracuję z certyfikatem testowym, do klienta został dodany dodatkowy kod, aby pominąć alert zabezpieczeń. Kod i towarzysząca Klasa nie są wymagane w przypadku korzystania z certyfikatów produkcyjnych.

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
