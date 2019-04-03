---
title: Transport WS z poświadczeniami komunikatu
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 31c1ed5d4b62c0f0b4c0c149629bb84a7dab6f01
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826213"
---
# <a name="ws-transport-with-message-credential"></a>Transport WS z poświadczeniami komunikatu
Niniejszy przykład pokazuje korzystanie z zabezpieczeń transportu protokołu SSL w połączeniu z poświadczeniami klienta, które są przenoszone w komunikacie. W tym przykładzie użyto `wsHttpBinding` powiązania.  
  
 Domyślnie `wsHttpBinding` powiązania zapewnia komunikację HTTP. Po skonfigurowaniu zabezpieczeń transportu powiązanie obsługuje komunikację HTTPS. Protokół HTTPS oferuje poufność i ochrona integralności wiadomości, które są przesyłane przez sieć. Jednak zestaw mechanizmów uwierzytelniania, które mogą służyć do uwierzytelniania klienta do usługi jest ograniczona do obsługuje transportu HTTPS. Windows Communication Foundation (WCF) oferuje `TransportWithMessageCredential` tryb zabezpieczeń, której celem jest to ograniczenie. Po skonfigurowaniu tego trybu zabezpieczeń zabezpieczeń transportu jest używany, zapewnienie poufności i integralności przesyłanych wiadomości i do wykonywania uwierzytelniania usługi. Jednak uwierzytelnianie klienta odbywa się przez umieszczanie poświadczeń klienta bezpośrednio w wiadomości. Dzięki temu można używać dowolnego typu poświadczeń, który jest obsługiwany przez trybu zabezpieczenia wiadomości do uwierzytelniania klientów przy zachowaniu zalet wydajności tryb zabezpieczeń transport.  
  
 W tym przykładzie `UserName` typ poświadczeń jest używany do uwierzytelniania klienta do usługi.  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora. `wsHttpBinding` Powiązania jest określona i skonfigurowany w plikach konfiguracji aplikacji dla klienta i usługi.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Kod programu, w przykładzie jest niemal identyczny z [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) usługi. Istnieje jedna operacja dodatkowe dostarczone przez kontrakt usługi - `GetCallerIdentity`. Ta operacja zwraca Nazwa tożsamości elementu wywołującego do obiektu wywołującego.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Należy utworzyć certyfikat i przypisz go za pomocą kreatora certyfikatu serwera sieci Web przed kompilowanie i uruchamianie przykładu. Definicja punktu końcowego i definicji powiązania w konfiguracji pliku ustawienia umożliwiające `TransportWithMessageCredential` tryb zabezpieczeń, jak pokazano w poniższym Przykładowa konfiguracja klienta.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Określony adres wykorzystuje schemat https://. Konfiguracja powiązania Ustawia tryb zabezpieczeń `TransportWithMessageCredential`. Taki sam tryb zabezpieczeń należy określić w pliku Web.config tej usługi.  
  
 Ponieważ certyfikat używany w tym przykładzie jest utworzone za pomocą Makecert.exe certyfikat testowy, alert zabezpieczeń jest wyświetlany, gdy próbują uzyskać dostęp przy użyciu protokołu https: adres, takie jak `https://localhost/servicemodelsamples/service.svc`, z poziomu przeglądarki. Aby zezwolić na klienta platformy WCF do pracy z certyfikatem testowym w miejscu, dodano dodatkowy kod klienta dla pomijania alertu zabezpieczeń. Ten kod i towarzyszące klasy, nie jest wymagane, podczas korzystania z certyfikatów w środowisku produkcyjnym.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
