---
title: "Powiązanie HTTP w standardzie WS 2007 Federation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3cdba8b43c109b8fbd0a5892bfa4c4c15e1caabf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ws-2007-federation-http-binding"></a>Powiązanie HTTP w standardzie WS 2007 Federation
W tym przykładzie przedstawiono użycie <xref:System.ServiceModel.WS2007FederationHttpBinding>, standard, powiązanie, której można utworzyć scenariuszach obejmujących Federację wersji 1.3 Specyfikacja WS-Trust tej pomocy technicznej.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Próbka składa się z klienta w konsoli programu (Client.exe), program usługi tokenu zabezpieczeń opartych na konsoli (Securitytokenservice.exe) i usługi opartej na konsoli programu (Service.exe). Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie/odpowiedź. Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (`Add`, `Subtract`, `Multiply`, i `Divide`). Klient uzyskuje tokenu zabezpieczającego z zabezpieczeń usługi tokenów (STS) i zgłasza żądania dotyczące synchroniczne do operacji matematycznych danej usługi. Usługa następnie odpowiedzi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.  
  
 Przykład sprawia, że `ICalculator` dostępne za pomocą kontraktu `ws2007FederationHttpBinding` elementu. W poniższym kodzie przedstawiono konfiguracji tego powiązania na kliencie.  
  
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
  
 Na [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` wartość określa, który tryb zabezpieczeń powinny być używane. W tym przykładzie `message` używane są zabezpieczenia, która jest dlaczego [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określono wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<Wystawcy >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element wewnątrz [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Określa adres i powiązanie dla usługi STS, który wystawia token zabezpieczający do klienta, dzięki czemu klient może uwierzytelnianie `ICalculator` usługi.  
  
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
  
 Na [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` wartość określa, który tryb zabezpieczeń powinny być używane. W tym przykładzie `message` używane są zabezpieczenia, która jest dlaczego [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określono wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementu `ws2007FederationHttpBinding` wewnątrz [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Określa adres i tożsamości dla punktu końcowego, który może służyć do pobrania metadane dla usługi STS.  
  
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
  
 [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umożliwia usłudze określić ograniczeń na tokeny umożliwia klientom prezentować podczas uwierzytelniania. Ta konfiguracja Określa, że tokeny podpisane za pomocą certyfikatu, którego podmiot jest CN = STS są akceptowane przez usługę.  
  
 STS udostępnia jeden punkt końcowy przy użyciu standardu <xref:System.ServiceModel.WS2007HttpBinding>. Usługa odpowiada na żądania klientów dotyczące tokenów. Jeśli klient jest uwierzytelniany przy użyciu konta systemu Windows, usługa wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenia. Podczas tworzenia tokenu usługi STS znaki tokenu przy użyciu klucza prywatnego skojarzonego z CN = certyfikat STS. Ponadto tworzy klucza symetrycznego i szyfruje go za pomocą klucza publicznego skojarzonego z CN = localhost certyfikat. Zwracany token do klienta, STS zwraca klucz symetryczny. Klient przedstawia wystawiony token `ICalculator` usługi i okaże się wie klucza symetrycznego, tworząc wiadomości z tego klucza.  
  
 Po uruchomieniu próbki żądania tokenu zabezpieczającego jest wyświetlany w oknie konsoli usługi STS. Operacja żądania i odpowiedzi są wyświetlane w oknach konsoli klienta i usługi. Naciśnij klawisz ENTER w żadnym z okna konsoli można zamknąć aplikacji.  
  
 `Add(100,15.99) = 115.99`  
  
 `Subtract(145,76.54) = 68.46`  
  
 `Multiply(9,81.25) = 731.25`  
  
 `Divide(22,7) = 3.14285714285714`  
  
 `Press <ENTER> to terminate client.`  
  
 Plik pliku Setup.bat uwzględnionych w tym przykładzie umożliwia skonfigurowanie serwera i STS za pomocą odpowiednich certyfikatów do uruchomienia aplikacji siebie. Plik wsadowy tworzy dwa certyfikaty w magazynie LocalMachine/TrustedPeople certyfikatów. Pierwszy certyfikat ma nazwę podmiotu, CN = STS i jest używany przez usługę STS do podpisywania tokenów zabezpieczających, które wystawia klientowi. Drugi certyfikat ma nazwę podmiotu, CN = localhost i jest używany przez usługę STS do szyfrowania klucza w taki sposób, aby usługa może odszyfrować.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Otwórz wiersz polecenia programu Visual Studio z uprawnieniami administratora i uruchom plik pliku Setup.bat do tworzenia wymaganych certyfikatów.  
  
 Ten plik wsadowy używa Certmgr.exe i Makecert.exe, które są dystrybuowane przy użyciu zestawu SDK systemu Windows. Należy jednak uruchomić pliku Setup.bat z w wierszu polecenia programu Visual Studio, aby umożliwić uruchomienie skryptu znaleźć te narzędzia.  
  
1.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Jeśli używasz [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], należy uruchomić Service.exe, Client.exe, i SecurityTokenService.exe z podwyższonym poziomem uprawnień (kliknij prawym przyciskiem myszy plik, a następnie kliknij przycisk **Uruchom jako administrator**).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a>Zobacz też
