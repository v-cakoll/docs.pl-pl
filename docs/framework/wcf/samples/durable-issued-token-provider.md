---
title: "Niezawodny dostawca wystawionych tokenów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f5662089990ee2775d8e2399e2d5e7770bbf4364
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="durable-issued-token-provider"></a>Niezawodny dostawca wystawionych tokenów
W tym przykładzie pokazano, jak do zaimplementowania niestandardowego klienta, dostawca wystawionych tokenów.  
  
## <a name="discussion"></a>Omówienie  
 Dostawca tokenu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] umożliwia podanie poświadczeń w celu zabezpieczenia infrastruktury. Dostawca tokenu ogólnie sprawdza obiektu docelowego i problemów odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć komunikatu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]jest dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu. Tokenów niestandardowi są przydatne w następujących przypadkach:  
  
-   Jeśli masz Magazyn poświadczeń, które wbudowanego dostawcy tokenów nie może pracować z.  
  
-   Jeśli chcesz udostępnić własny niestandardowy mechanizm do przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje o tym, kiedy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta używa poświadczeń.  
  
-   Jeśli tworzysz niestandardowy token.  
  
 Ten przykład przedstawia sposób tworzenia niestandardowego dostawcę tokenów, który buforuje tokenów wystawionych przez zabezpieczenia tokenu usługi (STS).  
  
 Krótko mówiąc, w tym przykładzie przedstawiono poniżej:  
  
-   Jak można skonfigurować klienta z niestandardowego dostawcy tokenu.  
  
-   Jak wystawione tokeny mogą być buforowane i przekazane do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.  
  
-   Jak serwer jest uwierzytelniany przez klienta przy użyciu certyfikat X.509.  
  
 W tym przykładzie składa się z konsoli programu klienckiego (Client.exe), program konsoli usługi tokenu zabezpieczeń (Securitytokenservice.exe) i program konsoli usługi (Service.exe). Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia). Klient pobiera zabezpieczeń token z zabezpieczeń usługi tokenów (STS) i zgłasza żądania dotyczące synchroniczne usługi dla operacji matematycznych danego i odpowiedzi usługi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład przedstawia, za pomocą kontraktu ICalculator [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). W poniższym kodzie przedstawiono konfiguracji tego powiązania na kliencie.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows" 
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 Na `security` elementu `wsFederationHttpBinding`, `mode` wartość konfiguruje tryb zabezpieczeń, którym powinien być używany. W tym przykładzie zabezpieczeń wiadomości jest używany, która jest dlaczego `message` elementu `wsFederationHttpBinding` określono wewnątrz `security` elementu `wsFederationHttpBinding`. `issuer` Elementu `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` Określa adres i powiązanie dla usługi tokenu zabezpieczającego, który wystawia token zabezpieczający do klienta, dzięki czemu klient może uwierzytelnić się Kalkulator Usługa.  
  
 Konfiguracji tego powiązania usługi przedstawiono w poniższym kodzie.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser" 
                                    storeName="TrustedPeople" 
                                    x509FindType="FindBySubjectDistinguishedName" 
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 Na `security` elementu `wsFederationHttpBinding`, `mode` wartość konfiguruje tryb zabezpieczeń, którym powinien być używany. W tym przykładzie zabezpieczeń wiadomości jest używany, która jest dlaczego `message` elementu `wsFederationHttpBinding` określono wewnątrz `security` elementu `wsFederationHttpBinding`. `issuerMetadata` Elementu `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` Określa adres i tożsamości dla punktu końcowego, który może służyć do pobierania metadanych dla usługi tokenu zabezpieczającego.  
  
 Zachowanie usługi przedstawiono w poniższym kodzie.  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine" 
              storeName="TrustedPeople" 
              x509FindType="FindBySubjectDistinguishedName" 
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine" 
                        storeName="My" 
                        x509FindType="FindBySubjectDistinguishedName" 
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 `issuedTokenAuthentication` Element wewnątrz `serviceCredentials` element umożliwia usługę, aby określić ograniczeń na tokeny umożliwia klientom prezentować podczas uwierzytelniania. Ta konfiguracja Określa, że tokeny podpisane za pomocą certyfikatu, którego podmiot jest CN = STS są akceptowane przez usługę.  
  
 Usługa tokenu zabezpieczającego przedstawia przy użyciu standardowych wsHttpBinding jeden punkt końcowy. Usługi tokenu zabezpieczającego odpowiada na żądania od klientów tokenów i pod warunkiem klienta jest uwierzytelniany przy użyciu konta systemu Windows, wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenia w wystawionego tokenu. Podczas tworzenia tokenu znaki usługi tokenu zabezpieczeń tokenu przy użyciu klucza prywatnego skojarzonego z CN = certyfikat STS. Ponadto tworzy klucza symetrycznego i szyfruje go za pomocą klucza publicznego skojarzonego z CN = localhost certyfikat. Zwracany token do klienta, usługę tokenu zabezpieczającego zwraca klucz symetryczny. Klient prezentuje wystawionego tokenu z usługą Kalkulator i okaże się wie klucza symetrycznego, tworząc wiadomości z tego klucza.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Niestandardowe poświadczenia i dostawcy tokenów  
 Poniższe kroki pokazują, jak utworzyć niestandardowego dostawcę tokenów, że pamięci podręcznych wystawionych tokenów i ich integracji z programem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: zabezpieczeń.  
  
#### <a name="to-develop-a-custom-token-provider"></a>Aby utworzyć niestandardowego dostawcę tokenów  
  
1.  Pisanie niestandardowych dostawcy tokenu.  
  
     Przykład implementuje niestandardowego dostawcę tokenów, który zwraca token zabezpieczający pobierane z pamięci podręcznej.  
  
     Aby wykonać to zadanie, pochodzi niestandardowego dostawcy tokenu <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody. Ta metoda próbuje pobrać tokenu z pamięci podręcznej, lub Jeśli token nie można znaleźć w pamięci podręcznej, pobiera token z podstawowym dostawcy, a następnie buforuje tokenu. W obu przypadkach metoda zwraca `SecurityToken`.  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2.  Zapis Menedżer tokenów zabezpieczających niestandardowych.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla określonego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody. Menedżer tokenów zabezpieczających jest również używane do utworzenia wystawcy uwierzytelnienia tokenu i serializatorów tokenu, ale te nie są objęte w tym przykładzie. W tym przykładzie Menedżer tokenów zabezpieczających niestandardowych dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądanej metody do zwracania niestandardowego dostawcy tokenu podczas przekazany wymagania tokenu wskazują, że wystawionego tokenu.  
  
    ```  
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3.  Wpisz poświadczenia niestandardowego klienta.  
  
     Klasa poświadczeń klienta jest używana do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy Menedżer tokenów, który jest używany do uzyskania wystawcy uwierzytelnienia tokenu, dostawcy tokenów i serializatorów tokenu zabezpieczeń.  
  
    ```  
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        Get  
        {  
          return this.cache;  
        }  
        Set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4.  Implementuje pamięci podręcznej tokenu. Przykładowe zastosowanie używa abstrakcyjna klasa podstawowa, za pomocą którego interakcji użytkowników danego pamięci podręcznej tokenu z pamięci podręcznej.  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     Dla klienta do używania poświadczeń klienta niestandardowych próbka usuwa domyślną klasę poświadczeń klienta i udostępnia nową klasę poświadczeń klienta.  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
 Zobacz poniższe instrukcje do uruchomienia przykładu. Po uruchomieniu próbki żądania tokenu zabezpieczającego jest wyświetlany w oknie konsoli usługi tokenu zabezpieczającego. Operacja żądania i odpowiedzi są wyświetlane w oknie konsoli klienta i usługi. Naciśnij klawisz ENTER w żadnym z okna konsoli można zamknąć aplikacji.  
  
## <a name="the-setupcmd-batch-file"></a>Plik wsadowy Setup.cmd  
 Plik wsadowy Setup.cmd uwzględnionych w tym przykładzie umożliwia skonfigurowanie serwera i usługi tokenu zabezpieczającego z odpowiednich certyfikatów do uruchomienia aplikacji siebie. Plik wsadowy tworzy dwa certyfikaty zarówno w CurrentUser/TrustedPeople magazynie certyfikatów. Pierwszy certyfikat ma nazwę podmiotu, CN = STS i jest używany przez usługę tokenu zabezpieczającego do podpisywania tokenów zabezpieczających, które wystawia klientowi. Drugi certyfikat ma nazwę podmiotu, CN = localhost i jest używany przez usługę tokenu zabezpieczającego można zaszyfrować klucza tajnego, aby można go odszyfrować usługi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Uruchom plik Setup.cmd do tworzenia wymaganych certyfikatów.  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Upewnij się, że skompilowano wszystkie projekty w rozwiązaniu (Shared, RSTRSTR usługi, SecurityTokenService i klienta).  
  
3.  Upewnij się, że Service.exe i SecurityTokenService.exe są uruchomione z uprawnieniami administratora.  
  
4.  Uruchom Client.exe.  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
1.  Uruchamianie Cleanup.cmd w folderze Przykłady po ukończeniu działania próbki.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a>Zobacz też
