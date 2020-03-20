---
title: Niezawodny dostawca wystawionych tokenów
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 08c6837f45ba1c422cdc3df2c884aa81b50a7f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144750"
---
# <a name="durable-issued-token-provider"></a>Niezawodny dostawca wystawionych tokenów
W tym przykładzie pokazano, jak zaimplementować niestandardowego dostawcy tokenu wystawionego przez klienta niestandardowego.  
  
## <a name="discussion"></a>Dyskusji  
 Dostawca tokenów w programie Windows Communication Foundation (WCF) służy do dostarczania poświadczeń do infrastruktury zabezpieczeń. Dostawca tokenu w ogóle sprawdza obiekt docelowy i wystawia odpowiednie poświadczenia, dzięki czemu infrastruktura zabezpieczeń może zabezpieczyć komunikat. WCF jest dostarczany z dostawcą tokenów CardSpace. Dostawcy tokenów niestandardowych są przydatne w następujących przypadkach:  
  
- Jeśli masz magazyn poświadczeń, z którego nie może działać wbudowany dostawca tokenu.  
  
- Jeśli chcesz podać własny mechanizm niestandardowy do przekształcania poświadczeń od punktu, gdy użytkownik udostępnia szczegóły, gdy klient WCF używa poświadczeń.  
  
- Jeśli budujesz token niestandardowy.  
  
 W tym przykładzie pokazano, jak utworzyć niestandardowego dostawcy tokenów, który buforuje tokeny wystawione przez usługę tokenu zabezpieczającego (STS).  
  
 Podsumowując, w tym przykładzie przedstawiono następujące elementy:  
  
- Jak można skonfigurować klienta za pomocą niestandardowego dostawcy tokenu.  
  
- Jak wystawione tokeny mogą być buforowane i dostarczane do klienta WCF.  
  
- Sposób uwierzytelniania serwera przez klienta przy użyciu certyfikatu X.509 serwera.  
  
 Ten przykład składa się z programu konsoli klienta (Client.exe), programu konsoli usługi tokenu zabezpieczającego (Securitytokenservice.exe) i programu konsoli usługi (Service.exe). Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowany `ICalculator` przez interfejs, który udostępnia operacje matematyczne (dodawanie, odejmowanie, mnożenie i dzielenie). Klient pobiera token zabezpieczający z usługi tokenu zabezpieczającego (STS) i sprawia, że synchroniczne żądania do usługi dla danej operacji matematycznej i odpowiedzi usługi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład udostępnia kontrakt ICalculator przy użyciu [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfiguracja tego powiązania na kliencie jest pokazana w poniższym kodzie.  
  
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
  
 W `security` `wsFederationHttpBinding`elemencie `mode` wartość określa, który tryb zabezpieczeń powinien być używany. W tym przykładzie używane są zabezpieczenia `message` wiadomości, `wsFederationHttpBinding` dlatego element `security` jest `wsFederationHttpBinding`określony wewnątrz elementu . Element `issuer` `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` określa adres i powiązanie dla usługi tokenu zabezpieczającego, który wystawia token zabezpieczający do klienta, dzięki czemu klient może uwierzytelnić się w usłudze Kalkulator.  
  
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
  
 W `security` `wsFederationHttpBinding`elemencie `mode` wartość określa, który tryb zabezpieczeń powinien być używany. W tym przykładzie używane są zabezpieczenia `message` wiadomości, `wsFederationHttpBinding` dlatego element `security` jest `wsFederationHttpBinding`określony wewnątrz elementu . Element `issuerMetadata` `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` określa adres i tożsamość punktu końcowego, który może służyć do pobierania metadanych dla usługi tokenu zabezpieczającego.  
  
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
  
 Element `issuedTokenAuthentication` wewnątrz `serviceCredentials` elementu umożliwia usługi, aby określić ograniczenia tokenów, które umożliwia klientom do przedstawienia podczas uwierzytelniania. Ta konfiguracja określa, że tokeny podpisane certyfikatem, którego nazwa podmiotu jest CN = STS są akceptowane przez usługę.  
  
 Usługa tokenu zabezpieczającego udostępnia pojedynczy punkt końcowy przy użyciu standardowego wsHttpBinding. Usługa tokenu zabezpieczającego odpowiada na żądanie klientów dotyczące tokenów i, pod warunkiem, że klient uwierzytelnia się przy użyciu konta systemu Windows, wystawia token zawierający nazwę użytkownika klienta jako oświadczenie w wystawionym tokenie. W ramach tworzenia tokenu usługa tokenu zabezpieczającego podpisuje token przy użyciu klucza prywatnego skojarzonego z certyfikatem CN=STS. Ponadto tworzy klucz symetryczny i szyfruje go przy użyciu klucza publicznego skojarzonego z certyfikatem CN=localhost. Podczas zwracania tokenu do klienta usługa tokenu zabezpieczającego zwraca również klucz symetryczny. Klient przedstawia wystawiony token do usługi Kalkulator i udowadnia, że zna klucz symetryczny, podpisując wiadomość za pomocą tego klucza.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Niestandardowe poświadczenia klienta i dostawca tokenów  
 Poniższe kroki pokazują, jak opracować niestandardowego dostawcy tokenu, który buforuje wystawione tokeny i zintegrować go z WCF: security.  
  
### <a name="to-develop-a-custom-token-provider"></a>Aby opracować niestandardowego dostawcę tokenów  
  
1. Napisz niestandardowego dostawcy tokenu.  
  
     Przykład implementuje niestandardowego dostawcy tokenu, który zwraca token zabezpieczający pobrany z pamięci podręcznej.  
  
     Aby wykonać to zadanie, dostawca tokenu niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenProvider> wyprowadza <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> klasę i zastępuje metodę. Ta metoda próbuje pobrać token z pamięci podręcznej lub jeśli token nie można znaleźć w pamięci podręcznej, pobiera token od dostawcy źródłowego, a następnie buforuje tego tokenu. W obu przypadkach metoda `SecurityToken`zwraca .  
  
    ```csharp  
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
  
2. Napisz niestandardowy menedżer tokenów zabezpieczających.  
  
     Jest <xref:System.IdentityModel.Selectors.SecurityTokenManager> używany do <xref:System.IdentityModel.Selectors.SecurityTokenProvider> tworzenia dla <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> określonego, który jest `CreateSecurityTokenProvider` przekazywany do niego w metodzie. Menedżer tokenów zabezpieczających jest również używany do tworzenia tokenów uwierzytelniaczy i serializatorów tokenów, ale nie są to objęte tym przykładem. W tym przykładzie niestandardowy menedżer tokenu zabezpieczającego <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> dziedziczy z klasy i zastępuje `CreateSecurityTokenProvider` metodę zwracania dostawcy tokenu niestandardowego, gdy wymagania dotyczące tokenu przekazanego wskazują, że żądany jest wystawiony token.  
  
    ```csharp
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
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. Napisz niestandardowe poświadczenia klienta.  
  
     Klasa poświadczeń klienta jest używana do reprezentowania poświadczeń skonfigurowanych dla serwera proxy klienta i tworzy menedżera tokenu zabezpieczającego, który jest używany do uzyskiwania wystawców uwierzytelniających token, dostawców tokenów i serializatorów tokenów.  
  
    ```csharp
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
        get  
        {  
          return this.cache;  
        }  
        set  
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
  
4. Zaimplementuj pamięć podręczną tokenu. Przykładowa implementacja używa abstrakcyjnej klasy podstawowej, za pomocą której konsumenci danej pamięci podręcznej tokenu współdziałają z pamięcią podręczną.  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     Aby klient używał niestandardowych poświadczeń klienta, przykładowy usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Uruchamianie przykładowej aplikacji  
 Zobacz poniższe instrukcje, aby uruchomić próbkę. Po uruchomieniu przykładu żądanie tokenu zabezpieczającego jest wyświetlane w oknie konsoli usługi tokenu zabezpieczającego. Żądania operacji i odpowiedzi są wyświetlane w oknach konsoli klienta i usługi. Naciśnij klawisz ENTER w dowolnym okienku konsoli, aby wyłączyć aplikację.  
  
## <a name="the-setupcmd-batch-file"></a>Plik wsadowy instalatora.cmd  
 Plik wsadowy Setup.cmd dołączony do tego przykładu umożliwia skonfigurowanie usługi serwera i tokenu zabezpieczającego z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej samodzielnie. Plik wsadowy tworzy dwa certyfikaty zarówno w magazynie certyfikatów CurrentUser/TrustedPeople. Pierwszy certyfikat ma nazwę podmiotu CN = STS i jest używany przez usługę tokenu zabezpieczającego do podpisywania tokenów zabezpieczających, które wystawia klientowi. Drugi certyfikat ma nazwę podmiotu CN = localhost i jest używany przez usługę tokenu zabezpieczającego do szyfrowania klucza tajnego, aby usługa mogła go odszyfrować.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Uruchom plik Setup.cmd, aby utworzyć wymagane certyfikaty.  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md). Upewnij się, że wszystkie projekty w rozwiązaniu są zbudowane (udostępnione, RSTRSTR, usługa, SecurityTokenService i klienta).  
  
3. Upewnij się, że usługi Service.exe i SecurityTokenService.exe są uruchomione z uprawnieniami administratora.  
  
4. Uruchom plik Client.exe.  
  
### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
1. Uruchom cleanup.cmd w folderze próbek po zakończeniu uruchamiania próbki.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
