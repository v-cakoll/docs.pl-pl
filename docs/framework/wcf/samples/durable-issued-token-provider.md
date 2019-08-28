---
title: Niezawodny dostawca wystawionych tokenów
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 70c7237329d1ae5f6ecde2231a66bca53e220634
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045018"
---
# <a name="durable-issued-token-provider"></a>Niezawodny dostawca wystawionych tokenów
Ten przykład pokazuje, jak zaimplementować niestandardowego dostawcę tokenów wystawionych przez klienta.  
  
## <a name="discussion"></a>Dyskusji  
 Dostawca tokenu w Windows Communication Foundation (WCF) służy do dostarczania poświadczeń do infrastruktury zabezpieczeń. Dostawca tokenu ogólnie bada cel i wystawia odpowiednie poświadczenia, aby infrastruktura zabezpieczeń mogła zabezpieczyć komunikat. Usługa WCF jest dostarczana z dostawcą tokenu programu CardSpace. Dostawcy tokenów niestandardowych są przydatne w następujących przypadkach:  
  
- Jeśli masz magazyn poświadczeń, którego nie może używać dostawca wbudowanego tokenu.  
  
- Jeśli chcesz zapewnić własny niestandardowy mechanizm przekształcania poświadczeń z punktu, gdy użytkownik poda szczegółowe informacje o tym, kiedy klient WCF używa tych poświadczeń.  
  
- W przypadku kompilowania niestandardowego tokenu.  
  
 Ten przykład pokazuje, jak utworzyć niestandardowego dostawcę tokenów, który przechowuje w pamięci podręcznej tokeny wystawione przez usługę tokenu zabezpieczającego (STS).  
  
 Podsumowując, ten przykład ilustruje następujące elementy:  
  
- Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.  
  
- Sposób, w jaki wystawione tokeny mogą być buforowane i udostępniane klientowi programu WCF.  
  
- Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X. 509 serwera.  
  
 Ten przykład składa się z programu konsolowego klienta (Client. exe), programu usługi tokenu zabezpieczającego (SecurityTokenService. exe) i programu konsoli usług (Service. exe). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie). Klient pobiera token zabezpieczający z usługi tokenu zabezpieczającego (STS) i wysyła synchroniczne żądania do usługi dla danej operacji matematycznej i usługi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład uwidacznia kontrakt ICalculator przy użyciu [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfiguracja tego powiązania na kliencie jest pokazana w poniższym kodzie.  
  
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
  
 `security` Dla elementu,`mode`wartość określa, który tryb zabezpieczeń ma być używany. `wsFederationHttpBinding` W tym przykładzie zabezpieczenia komunikatów są używane, `message` co oznacza, że `wsFederationHttpBinding` element jest `wsFederationHttpBinding`określony `security` w elemencie elementu. Element wewnątrz elementuokreśla`wsFederationHttpBinding` adres i powiązanie dla usługi tokenów zabezpieczających, która wystawia token zabezpieczający dla klienta, aby klient mógł uwierzytelnić się na Kalkulator `message` `issuer` `wsFederationHttpBinding` usługi.  
  
 Konfiguracja tego powiązania w usłudze jest pokazana w poniższym kodzie.  
  
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
  
 `security` Dla elementu,`mode`wartość określa, który tryb zabezpieczeń ma być używany. `wsFederationHttpBinding` W tym przykładzie zabezpieczenia komunikatów są używane, `message` co oznacza, że `wsFederationHttpBinding` element jest `wsFederationHttpBinding`określony `security` w elemencie elementu. Element wewnątrz elementuokreśla`wsFederationHttpBinding` adres i tożsamość punktu końcowego, którego można użyć do pobrania metadanych usługi tokenu zabezpieczającego. `message` `issuerMetadata` `wsFederationHttpBinding`  
  
 Zachowanie usługi jest pokazane w poniższym kodzie.  
  
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
  
 `issuedTokenAuthentication` Element`serviceCredentials` wewnątrz elementu pozwala usłudze określić ograniczenia dotyczące tokenów, które umożliwiają klientom prezentowanie podczas uwierzytelniania. Ta konfiguracja określa, że tokeny podpisane przez certyfikat, którego nazwa podmiotu to CN = STS, są akceptowane przez usługę.  
  
 Usługa token zabezpieczający ujawnia pojedynczy punkt końcowy przy użyciu standardowej wsHttpBinding. Usługa tokenu zabezpieczającego odpowiada na żądanie od klientów tokenów i, pod warunkiem, że klient uwierzytelnia się przy użyciu konta systemu Windows, wystawia token, który zawiera nazwę użytkownika klienta jako zastrzeżenie w wystawionym tokenie. W ramach tworzenia tokenu usługa tokenu zabezpieczającego podpisuje token przy użyciu klucza prywatnego skojarzonego z certyfikatem CN = STS. Ponadto tworzy klucz symetryczny i szyfruje go przy użyciu klucza publicznego skojarzonego z certyfikatem CN = localhost. W programie zwracającym token do klienta usługa tokenu zabezpieczającego zwraca również klucz symetryczny. Klient przedstawia wystawiony token usłudze Kalkulator i potwierdza, że zna klucz symetryczny, podpisując komunikat przy użyciu tego klucza.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Niestandardowe poświadczenia klienta i dostawca tokenów  
 W poniższych krokach przedstawiono sposób tworzenia niestandardowego dostawcy tokenów, który buforuje wystawione tokeny i integruje go z programem WCF: zabezpieczenia.  
  
#### <a name="to-develop-a-custom-token-provider"></a>Aby opracować niestandardowego dostawcę tokenów  
  
1. Napisz niestandardowego dostawcę tokenów.  
  
     Przykład implementuje niestandardowego dostawcę tokenów, który zwraca token zabezpieczający pobrany z pamięci podręcznej.  
  
     Aby wykonać to zadanie, dostawca niestandardowego tokenu dziedziczy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasę i <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> zastępuje metodę. Ta metoda próbuje uzyskać token z pamięci podręcznej lub jeśli nie można znaleźć tokenu w pamięci podręcznej, program pobierze token z bazowego dostawcy, a następnie buforuje ten token. W obu przypadkach Metoda zwraca `SecurityToken`.  
  
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
  
2. Napisz niestandardowego menedżera tokenów zabezpieczających.  
  
     Służy do tworzenia elementu <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla konkretnego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , który jest przesyłany do niego w `CreateSecurityTokenProvider` metodzie. <xref:System.IdentityModel.Selectors.SecurityTokenManager> Menedżer tokenów zabezpieczających jest również używany do tworzenia wystawców tokenów i serializatorów tokenów, ale nie są one objęte tym przykładem. W tym przykładzie niestandardowy Menedżer tokenów zabezpieczających dziedziczy z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i `CreateSecurityTokenProvider` przesłania metodę w celu zwrócenia niestandardowego dostawcy tokenów, gdy spełnione wymagania tokenu wskazują, że zażądano wystawionego tokenu.  
  
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
  
3. Napisz niestandardowe poświadczenie klienta.  
  
     Klasa poświadczeń klienta służy do reprezentowania poświadczeń skonfigurowanych dla serwera proxy klienta i tworzy Menedżera tokenów zabezpieczających, który służy do uzyskiwania wystawców tokenów, dostawców tokenów i serializatorów tokenów.  
  
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
  
4. Zaimplementuj pamięć podręczną tokenów. Przykładowa implementacja używa abstrakcyjnej klasy bazowej, za pośrednictwem której konsumenci danej pamięci podręcznej tokenu pracują z pamięcią podręczną.  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     Aby klient korzystał z niestandardowego poświadczenia klienta, przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Uruchamianie przykładu  
 Zapoznaj się z poniższymi instrukcjami, aby uruchomić przykład. Po uruchomieniu przykładu żądanie tokenu zabezpieczającego jest wyświetlane w oknie konsoli usługi tokenu zabezpieczającego. Żądania operacji i odpowiedzi są wyświetlane w oknach konsoli klienta i usługi. Naciśnij klawisz ENTER w dowolnym systemie Windows Console, aby zamknąć aplikację.  
  
## <a name="the-setupcmd-batch-file"></a>Plik wsadowy Setup. cmd  
 Plik wsadowy Setup. cmd dołączony do tego przykładu umożliwia skonfigurowanie serwera i usługi tokenu zabezpieczającego za pomocą odpowiednich certyfikatów do uruchamiania aplikacji samohostowanej. Plik wsadowy tworzy dwa certyfikaty zarówno w magazynie certyfikatów CurrentUser/TrustedPeople. Pierwszy certyfikat ma nazwę podmiotu CN = STS i jest używany przez usługę tokenu zabezpieczającego do podpisywania tokenów zabezpieczających, które wystąpiły dla klienta. Drugi certyfikat ma nazwę podmiotu CN = localhost i jest używany przez usługę tokenu zabezpieczającego do szyfrowania klucza tajnego, aby usługa mogła je odszyfrować.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Uruchom plik Setup. cmd, aby utworzyć wymagane certyfikaty.  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Upewnij się, że wszystkie projekty w rozwiązaniu zostały skompilowane (Shared, RSTRSTR, Service, SecurityTokenService i Client).  
  
3. Upewnij się, że program Service. exe i SecurityTokenService. exe są uruchamiane z uprawnieniami administratora.  
  
4. Uruchom plik Client. exe.  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
1. Uruchom polecenie Oczyść. cmd w folderze Samples po zakończeniu uruchamiania przykładu.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
