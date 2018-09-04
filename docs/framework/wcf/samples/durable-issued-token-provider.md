---
title: Niezawodny dostawca wystawionych tokenów
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 7def23a00e42e134d8c0b9bd911710917681ad31
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504594"
---
# <a name="durable-issued-token-provider"></a>Niezawodny dostawca wystawionych tokenów
Ten przykład demonstruje sposób implementacji niestandardowego klienta, dostawca wystawionych tokenów.  
  
## <a name="discussion"></a>Dyskusja  
 Dostawca tokenu w Windows Communication Foundation (WCF) umożliwia podanie poświadczeń w celu infrastruktura zabezpieczeń. Dostawcy tokenu, który sprawdza ogólnie rzecz biorąc, element docelowy i problemy odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć wiadomości. Usługi WCF jest dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu. Niestandardowego dostawcy tokenów są przydatne w następujących przypadkach:  
  
-   Jeśli masz Magazyn poświadczeń, który wbudowanego dostawcy tokenu nie może działać z.  
  
-   Jeśli chcesz udostępnić własny niestandardowy mechanizm przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje, na kiedy klient WCF przy użyciu poświadczeń.  
  
-   Jeśli tworzysz niestandardowy token.  
  
 Niniejszy przykład pokazuje sposób tworzenia niestandardowego dostawcy tokenu, który buforuje tokeny wystawione przez Usługa tokenu zabezpieczającego (STS).  
  
 Aby podsumować, w przykładzie pokazano poniżej:  
  
-   Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.  
  
-   W jaki sposób wystawione tokeny mogą być buforowane i dostarczane do klienta platformy WCF.  
  
-   Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 serwera.  
  
 W tym przykładzie składa się z konsoli programu klienckiego (Client.exe), program konsoli usługi tokenu zabezpieczeń (Securitytokenservice.exe) i program konsoli usługi (Service.exe). Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia). Klient pobiera zabezpieczeń token z Usługa tokenu zabezpieczającego (STS) i sprawia, że żądań synchronicznych usługi dla operacji matematycznych danego i odpowiedzi usługi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład przedstawia przy użyciu umowy ICalculator [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfiguracji tego powiązania na kliencie jest wyświetlany w poniższym kodzie.  
  
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
  
 Na `security` elementu `wsFederationHttpBinding`, `mode` wartość Określa tryb zabezpieczeń, którym powinny być używane. W tym przykładzie zabezpieczeń wiadomości jest używany, co jest dlaczego `message` elementu `wsFederationHttpBinding` jest określona wewnątrz `security` elementu `wsFederationHttpBinding`. `issuer` Elementu `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` Określa adres i powiązanie dla usługi tokenu zabezpieczającego, która wystawia token zabezpieczający do klienta, tak aby klient mógł uwierzytelniać się w kalkulatorze Usługa.  
  
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
  
 Na `security` elementu `wsFederationHttpBinding`, `mode` wartość Określa tryb zabezpieczeń, którym powinny być używane. W tym przykładzie zabezpieczeń wiadomości jest używany, co jest dlaczego `message` elementu `wsFederationHttpBinding` jest określona wewnątrz `security` elementu `wsFederationHttpBinding`. `issuerMetadata` Elementu `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` Określa adres i tożsamości dla punktu końcowego, który może służyć do pobierania metadanych dla usługi tokenu zabezpieczającego.  
  
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
  
 `issuedTokenAuthentication` Element wewnątrz `serviceCredentials` element umożliwia usłudze określanie ograniczeń na tokeny zezwala na klientów przedstawić podczas uwierzytelniania. Ta konfiguracja Określa, że tokeny podpisane przy użyciu certyfikatu, którego nazwa podmiotu jest CN = usługi STS są akceptowane przez usługę.  
  
 Usługa tokenu zabezpieczającego przedstawia jeden punkt końcowy przy użyciu standardowych wsHttpBinding. Usługa tokenu zabezpieczającego odpowiada na żądania od klientów tokenów, a pod warunkiem klient jest uwierzytelniany przy użyciu konta Windows, wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenia w wystawionych tokenów. Jako część tworzenia tokenu, znaki usługę tokenu zabezpieczającego tokenu przy użyciu klucza prywatnego skojarzonego z CN = certyfikatu usługi STS. Ponadto tworzy klucz symetryczny i szyfruje za pomocą klucza publicznego skojarzonego z CN = localhost certyfikat. Zwracany token do klienta, w usługę tokenu zabezpieczającego zwraca klucz symetryczny. Klient przedstawia wystawiony token usługi Kalkulator i upoważnienie wie klucz symetryczny, tworząc wiadomości za pomocą tego klucza.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Poświadczenia klienta oraz dostawcy tokenu  
 Poniższe kroki pokazują jak utworzyć niestandardowego dostawcę tokenów, pamięci podręcznych wystawionych tokenów i zintegrować ją z usługą WCF: zabezpieczeń.  
  
#### <a name="to-develop-a-custom-token-provider"></a>Tworzenie niestandardowego dostawcy tokenów  
  
1.  Pisania niestandardowego dostawcy tokenów.  
  
     Przykład implementuje niestandardowego dostawcę tokenów, który zwraca token zabezpieczający pobrane z pamięci podręcznej.  
  
     Aby wykonać to zadanie, pochodzi niestandardowego dostawcy tokenów <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody. Ta metoda próbuje pobrać tokenu z pamięci podręcznej, lub Jeśli token nie zostanie znaleziony w pamięci podręcznej, pobiera token z źródłowego dostawcy, a następnie buforuje tego tokenu. W obu przypadkach metoda zwraca `SecurityToken`.  
  
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
  
2.  Napisz Menedżer tokenów zabezpieczeń niestandardowych.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla określonego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody. Menedżer tokenów zabezpieczeń umożliwia również tworzenie wystawców uwierzytelnienia tokenu i serializatorów tokenu, ale te nie są objęte tego przykładu. W tym przykładzie Menedżer tokenów zabezpieczeń niestandardowe dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądana jest metoda, aby zwrócić niestandardowego dostawcy tokenów gdy przekazany wymagania tokenu wskazują, że wystawiony token.  
  
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
  
     Klasa poświadczeń klienta jest używany do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy bezpieczeństwo Menedżer tokenów, który jest używany do uzyskiwania wystawców uwierzytelnienia tokenu, dostawcy tokenów i tokenów serializatory.  
  
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
  
4.  Implementowanie pamięci podręcznej tokenu. W przykładowej implementacji użyto abstrakcyjna klasa bazowa, za pomocą którego odbiorców tokenu pamięć podręczna wchodzić w interakcje z pamięcią podręczną.  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     Klienta można użyć poświadczeń klienta niestandardowe przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Działa aplikacja przykładowa  
 Zobacz następujące instrukcje do uruchomienia przykładu. Po uruchomieniu przykładu, żądania tokenu zabezpieczeń są wyświetlane w oknie konsoli usługi tokenu zabezpieczającego. Operacja żądania i odpowiedzi są wyświetlane w oknach konsoli klienta i usługi. Naciśnij klawisz ENTER w żadnym z okna konsoli do zamykania aplikacji.  
  
## <a name="the-setupcmd-batch-file"></a>Plik wsadowy plik Setup.cmd  
 Plik wsadowy plik Setup.cmd, które są dołączone do tego przykładu umożliwia skonfigurowanie serwera i Usługa tokenu zabezpieczającego z certyfikatami odpowiednie do uruchamiania aplikacji samodzielnie hostowany. Plik wsadowy tworzy dwa certyfikaty, że zarówno w CurrentUser/TrustedPeople magazynu certyfikatów. Pierwszy certyfikat ma nazwę podmiotu, CN = usługi STS i jest używany przez usługę tokenu zabezpieczającego do podpisywania tokenów zabezpieczających, które generuje dla klienta. Drugi certyfikat ma nazwę podmiotu, CN = localhost i jest używany przez usługę tokenu zabezpieczającego do szyfrowania klucza tajnego, dzięki czemu usługa może go odszyfrować.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Uruchom plik Setup.cmd plik do tworzenia wymaganych certyfikatów.  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Upewnij się, że wszystkie projekty w rozwiązaniu są kompilowane (udostępnione, RSTRSTR, usługi, SecurityTokenService i klienta).  
  
3.  Upewnij się, że Service.exe i SecurityTokenService.exe są uruchomione z uprawnieniami administratora.  
  
4.  Uruchom Client.exe.  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
1.  Uruchom Cleanup.cmd w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a>Zobacz też
