---
title: Powiązanie HTTP w standardzie WS 2007 Federation
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 550a88552658864e3eedb70463e676ad6f9a2511
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324945"
---
# <a name="ws-2007-federation-http-binding"></a>Powiązanie HTTP w standardzie WS 2007 Federation
Ten przykład demonstruje użycie <xref:System.ServiceModel.WS2007FederationHttpBinding>, standard, powiązanie, której można tworzyć scenariuszach obejmujących Federację obsługi wersji 1.3 specyfikację protokołu WS-Trust.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Przykład składa się z programu klienckiego z konsoli (Client.exe), program usługi tokenu zabezpieczeń opartych na konsoli (Securitytokenservice.exe) i usługa oparta na konsoli programu (Service.exe). Usługa implementuje kontraktu, który definiuje wzorzec komunikacji żądanie/nietypizowana odpowiedź. Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (`Add`, `Subtract`, `Multiply`, i `Divide`). Klient uzyskuje token zabezpieczający z Usługa tokenu zabezpieczającego (STS) i sprawia, że do usługi w przypadku operacji matematycznych danego żądań synchronicznych. Usługa następnie odpowiedzi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.  
  
 Przykład sprawia, że `ICalculator` dostępne za pośrednictwem umowy `ws2007FederationHttpBinding` elementu. Konfiguracji tego powiązania na kliencie jest wyświetlany w poniższym kodzie.  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Endpoint address and binding for Security Token Service -->  
          <issuer address ="http://localhost:8000/sts/windows"   
                  binding ="ws2007HttpBinding" />                
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 Na [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` wartość Określa tryb zabezpieczeń, którym powinny być używane. W tym przykładzie `message` zabezpieczeń jest używany, co jest dlaczego [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) jest określona wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<Issuer >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element wewnątrz [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Określa adres i powiązanie dla usługi STS, która wystawia token zabezpieczający do klienta, tak aby klient może uwierzytelnianie `ICalculator` usługi.  
  
 Konfiguracji tego powiązania usługi przedstawiono w poniższym kodzie.  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Metadata address for Security Token Service -->  
          <issuerMetadata address ="http://localhost:8000/sts/mex" >  
            <identity>  
              <certificateReference storeLocation ="CurrentUser"   
                                    storeName="TrustedPeople"   
                                    x509FindType ="FindBySubjectDistinguishedName"   
                                    findValue ="CN=STS" />  
            </identity>  
          </issuerMetadata>  
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 Na [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` wartość Określa tryb zabezpieczeń, którym powinny być używane. W tym przykładzie `message` zabezpieczeń jest używany, co jest dlaczego [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) jest określona wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementu `ws2007FederationHttpBinding` wewnątrz [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Określa adres i tożsamości dla punktu końcowego, który może służyć do pobrania metadane dla usługi STS.  
  
 Zachowanie usługi przedstawiono w poniższym kodzie.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name ="ServiceBehaviour" >  
      <serviceDebug includeExceptionDetailInFaults ="true"/>  
      <serviceMetadata httpGetEnabled ="true"/>  
      <serviceCredentials>  
        <issuedTokenAuthentication>  
          <knownCertificates>  
            <add storeLocation ="LocalMachine"  
                 storeName="TrustedPeople"  
                 x509FindType="FindBySubjectDistinguishedName"  
                 findValue="CN=STS" />  
          </knownCertificates>  
        </issuedTokenAuthentication>  
        <serviceCertificate storeLocation ="LocalMachine"  
                            storeName ="My"  
                            x509FindType ="FindBySubjectDistinguishedName"  
                            findValue ="CN=localhost"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umożliwia usłudze określanie ograniczeń na tokeny zezwala na klientów przedstawić podczas uwierzytelniania. Ta konfiguracja Określa, że tokeny podpisane przy użyciu certyfikatu, którego nazwa podmiotu jest CN = usługi STS są akceptowane przez usługę.  
  
 Usługi STS sprawia, że jeden punkt końcowy jest dostępny za pomocą standardowych <xref:System.ServiceModel.WS2007HttpBinding>. Usługa odpowiada na żądania klientów dotyczące tokenów. Jeśli klient jest uwierzytelniany przy użyciu konta Windows, usługę wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenia. Jako część tworzenia tokenu usługi STS podpisuje token przy użyciu klucza prywatnego skojarzonego z CN = certyfikatu usługi STS. Ponadto tworzy klucz symetryczny i szyfruje za pomocą klucza publicznego skojarzonego z CN = localhost certyfikat. Zwracany token do klienta, w STS zwraca klucz symetryczny. Klient przedstawia wystawiony token `ICalculator` usług i upoważnienie wie klucz symetryczny, tworząc wiadomości za pomocą tego klucza.  
  
 Po uruchomieniu przykładu, żądania tokenu zabezpieczeń są wyświetlane w oknie konsoli usługi STS. Operacja żądania i odpowiedzi są wyświetlane w oknach konsoli klienta i usługi. Naciśnij klawisz ENTER w żadnym z okna konsoli do zamykania aplikacji.  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Plik Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera i usługę STS przy użyciu odpowiednich certyfikatów do uruchamiania aplikacji samodzielnie hostowanej. Plik wsadowy tworzy dwa certyfikaty w magazynie LocalMachine/TrustedPeople certyfikatów. Pierwszy certyfikat ma nazwę podmiotu, CN = usługi STS i jest używany przez usługę STS do podpisywania tokenów zabezpieczających, które generuje dla klienta. Drugi certyfikat ma nazwę podmiotu, CN = localhost i jest używany przez usługę STS do szyfrowania klucza w taki sposób, że usługa może odszyfrować.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora i uruchom plik Setup.bat jest, aby utworzyć wymagane certyfikaty.  
  
 Ten plik wsadowy używa Certmgr.exe i Makecert.exe, które są dystrybuowane za pomocą zestawu Windows SDK. Należy jednak uruchomić Setup.bat z, w wierszu polecenia programu Visual Studio, aby włączyć skryptów znaleźć te narzędzia.  
  
1. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Jeśli używasz [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], należy uruchomić Service.exe, Client.exe, i SecurityTokenService.exe z podwyższonym poziomem uprawnień (kliknij prawym przyciskiem myszy pliki, a następnie kliknij przycisk **Uruchom jako administrator**).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
