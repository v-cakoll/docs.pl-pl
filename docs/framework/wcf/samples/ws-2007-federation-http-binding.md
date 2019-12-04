---
title: Powiązanie HTTP w standardzie WS 2007 Federation
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 2f924bdcbf9082d9d43e02d82c9d00c32ebcaacf
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714975"
---
# <a name="ws-2007-federation-http-binding"></a>Powiązanie HTTP w standardzie WS 2007 Federation

Ten przykład ilustruje użycie <xref:System.ServiceModel.WS2007FederationHttpBinding>, standardowego powiązania, którego można użyć do kompilowania scenariuszy federacyjnych, które obsługują wersję 1,3 specyfikacji WS-Trust.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Przykład składa się z programu klienckiego opartego na konsoli (*Client. exe*), programu usługi tokenu zabezpieczającego opartego na konsoli (*SecurityTokenService. exe*) i programu usług opartego na konsoli (*Service. exe*). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądania/odpowiedzi. Umowa jest definiowana przez interfejs `ICalculator`, który uwidacznia operacje matematyczne (`Add`, `Subtract`, `Multiply`i `Divide`). Klient uzyskuje token zabezpieczający z usługi tokenu zabezpieczającego (STS) i wysyła synchroniczne żądania do usługi dla danej operacji matematycznej. Następnie usługa wysyła odpowiedzi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.

Przykład umożliwia udostępnienie `ICalculator` kontraktu przy użyciu elementu `ws2007FederationHttpBinding`. Konfiguracja tego powiązania na kliencie jest pokazana w poniższym kodzie:

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

Na [> zabezpieczeń\<](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)wartość `security` określa tryb zabezpieczeń, który ma być używany. W tym przykładzie użyto `message` zabezpieczeń, co oznacza, że [> komunikat\<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) został określony w [\<> zabezpieczeń](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [\<wystawca >](../../configure-apps/file-schema/wcf/issuer.md) element wewnątrz [wiadomości\<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określa adres i powiązanie dla usługi STS, która wystawia token zabezpieczający dla klienta, aby klient mógł uwierzytelnić się w usłudze `ICalculator`.
  
Konfiguracja tego powiązania w usłudze jest pokazana w poniższym kodzie:

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

Na [> zabezpieczeń\<](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)wartość `security` określa tryb zabezpieczeń, który ma być używany. W tym przykładzie użyto `message` zabezpieczeń, co oznacza, że [> komunikat\<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) został określony w [\<> zabezpieczeń](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [\<issuerMetadata >](../../configure-apps/file-schema/wcf/issuermetadata.md) element `ws2007FederationHttpBinding` w [\<komunikat >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określa adres i tożsamość punktu końcowego, którego można użyć do pobrania metadanych dla usługi STS.

Zachowanie usługi jest pokazane w następującym kodzie:

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
  
[\<issuedTokenAuthentication >](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umożliwia usłudze określenie ograniczeń dotyczących tokenów, które umożliwiają klientom prezentowanie podczas uwierzytelniania. Ta konfiguracja określa, że tokeny podpisane przez certyfikat, którego nazwa podmiotu to CN = STS, są akceptowane przez usługę.

Usługa STS udostępnia jeden punkt końcowy przy użyciu standardowej <xref:System.ServiceModel.WS2007HttpBinding>. Usługa odpowiada na żądania od klientów tokenów. Jeśli klient jest uwierzytelniany przy użyciu konta systemu Windows, usługa wystawia token, który zawiera nazwę użytkownika klienta jako rolę żądania. W ramach tworzenia tokenu usługa STS podpisuje token przy użyciu klucza prywatnego skojarzonego z certyfikatem usługi STS. Ponadto tworzy klucz symetryczny i szyfruje go przy użyciu klucza publicznego skojarzonego z certyfikatem CN = localhost. W przypadku zwracania tokenu do klienta usługa STS zwraca również klucz symetryczny. Klient przedstawia wystawiony token usłudze `ICalculator` i potwierdza, że zna klucz symetryczny, podpisując komunikat przy użyciu tego klucza.

Po uruchomieniu przykładu żądanie tokenu zabezpieczającego jest wyświetlane w oknie konsoli STS. Żądania i odpowiedzi operacji są wyświetlane w oknach konsoli klienta i usługi. Naciśnij klawisz ENTER w dowolnym systemie Windows Console, aby zamknąć aplikację.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

Plik *Setup. bat* dołączony do tego przykładu umożliwia skonfigurowanie serwera i usługi STS z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej. Plik wsadowy tworzy dwa certyfikaty w magazynie certyfikatów LocalMachine/TrustedPeople. Pierwszy certyfikat ma nazwę podmiotu CN = STS i jest używany przez usługę STS do podpisywania tokenów zabezpieczających, które wystąpiły dla klienta. Drugi certyfikat ma nazwę podmiotu CN = localhost i jest używany przez usługę STS do szyfrowania klucza w sposób, w jaki usługa może odszyfrować.

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora i uruchom plik Setup. bat, aby utworzyć wymagane certyfikaty.

 Ten plik wsadowy używa *certmgr. exe* i Makecert. exe, które są dystrybuowane z Windows SDK. Należy jednak uruchomić *Setup. bat* z poziomu wiersza polecenia programu Visual Studio, aby umożliwić skryptowi znalezienie tych narzędzi.

1. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

2. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md). Jeśli używasz [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], musisz uruchomić program *Service. exe*, *Client. exe*i *SecurityTokenService. exe* z podniesionymi uprawnieniami (kliknij pliki prawym przyciskiem myszy, a następnie kliknij polecenie **Uruchom jako administrator**).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny):
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu:
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
