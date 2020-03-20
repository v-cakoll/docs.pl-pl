---
title: Powiązanie HTTP w standardzie WS 2007 Federation
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183186"
---
# <a name="ws-2007-federation-http-binding"></a>Powiązanie HTTP w standardzie WS 2007 Federation

W tym przykładzie <xref:System.ServiceModel.WS2007FederationHttpBinding>pokazano użycie , standardowe powiązanie, które można użyć do tworzenia scenariuszy federacyjne, które obsługują wersję 1.3 specyfikacji WS-Trust.

> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Przykład składa się z programu klienckiego opartego na konsoli (*Client.exe*), programu usługi tokenu zabezpieczającego opartego na konsoli *(Securitytokenservice.exe)* i programu usługi opartego na konsoli (*Service.exe*). Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie/odpowiedź. Kontrakt jest definiowany `ICalculator` przez interfejs, który`Add`udostępnia `Subtract` `Multiply`operacje `Divide`matematyczne ( , , , i ). Klient uzyskuje token zabezpieczający z usługi tokenu zabezpieczającego (STS) i sprawia, że synchroniczne żądania do usługi dla danej operacji matematycznej. Następnie usługa odpowiada z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.

Próbka udostępnia `ICalculator` kontrakt przy `ws2007FederationHttpBinding` użyciu elementu. Konfiguracja tego powiązania na kliencie jest pokazana w następującym kodzie:

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

W [ \<>zabezpieczeń ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` wartość określa, który tryb zabezpieczeń ma być używany. W tym `message` przykładzie jest używany zabezpieczeń, dlatego [ \<komunikat>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) jest określony wewnątrz [ \<>zabezpieczeń ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<Wystawca>](../../configure-apps/file-schema/wcf/issuer.md) element wewnątrz [ \<komunikatu>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określa adres i powiązanie dla STS, który wystawia token zabezpieczający do klienta, dzięki czemu klient może uwierzytelnić się w `ICalculator` usłudze.
  
Konfiguracja tego powiązania w usłudze jest wyświetlana w następującym kodzie:

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

W [ \<>zabezpieczeń ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` wartość określa, który tryb zabezpieczeń ma być używany. W tym `message` przykładzie jest używany zabezpieczeń, dlatego [ \<komunikat>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) jest określony wewnątrz [ \<>zabezpieczeń ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<IssuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element `ws2007FederationHttpBinding` wewnątrz [ \<komunikatu>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określa adres i tożsamość punktu końcowego, który może służyć do pobierania metadanych dla STS.

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
  
[ \<IssuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umożliwia usłudze określenie ograniczeń tokenów, które umożliwia klientom prezentowanie podczas uwierzytelniania. Ta konfiguracja określa, że tokeny podpisane certyfikatem, którego nazwa podmiotu jest CN = STS są akceptowane przez usługę.

STS udostępnia pojedynczy punkt końcowy <xref:System.ServiceModel.WS2007HttpBinding>przy użyciu standardowego . Usługa odpowiada na żądania od klientów tokenów. Jeśli klient jest uwierzytelniony przy użyciu konta systemu Windows, usługa wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenie. W ramach tworzenia tokenu STS podpisuje token przy użyciu klucza prywatnego skojarzonego z certyfikatem CN=STS. Ponadto tworzy klucz symetryczny i szyfruje go przy użyciu klucza publicznego skojarzonego z certyfikatem CN=localhost. W powrocie tokenu do klienta STS zwraca również klucz symetryczny. Klient przedstawia wystawiony token do `ICalculator` usługi i udowadnia, że zna klucz symetryczny, podpisując wiadomość za pomocą tego klucza.

Po uruchomieniu przykładu żądanie tokenu zabezpieczającego jest wyświetlane w oknie konsoli STS. Żądania i odpowiedzi operacji są wyświetlane w oknach konsoli klienta i usługi. Naciśnij klawisz ENTER w dowolnym okienku konsoli, aby wyłączyć aplikację.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

Plik *Setup.bat* dołączony do tego przykładu umożliwia skonfigurowanie serwera i systemu STS z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej samodzielnie. Plik wsadowy tworzy dwa certyfikaty w magazynie certyfikatów LocalMachine/TrustedPeople. Pierwszy certyfikat ma nazwę podmiotu CN = STS i jest używany przez STS do podpisywania tokenów zabezpieczających, które wystawia klientowi. Drugi certyfikat ma nazwę podmiotu CN = localhost i jest używany przez STS do szyfrowania klucza w sposób, który usługa może odszyfrować.

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](one-time-setup-procedure-for-the-wcf-samples.md).

2. Otwórz wiersz polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora i uruchom plik Setup.bat, aby utworzyć wymagane certyfikaty.

 Ten plik wsadowy używa *programów Certmgr.exe* i Makecert.exe, które są dystrybuowane za pomocą programu Windows SDK. Jednak należy uruchomić *Setup.bat* z poziomu wiersza polecenia programu Visual Studio, aby włączyć skrypt, aby znaleźć te narzędzia.

1. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](building-the-samples.md).

2. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](running-the-samples.md). Jeśli używasz systemu Windows Vista, należy uruchomić *program Service.exe*, *Client.exe*i *SecurityTokenService.exe* z podwyższonymi uprawnieniami (kliknij prawym przyciskiem myszy pliki, a następnie kliknij polecenie **Uruchom jako administrator**).

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog:
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu:
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
