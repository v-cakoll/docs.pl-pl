---
title: <message>elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738997"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a>\<message>elementu\<ws2007FederationHttpBinding>
Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) elementu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`algorithmSuite`|Opcjonalny. Ustawia szyfrowanie wiadomości, sygnaturę i algorytmy zawijania kluczy. Algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasę. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Zapoznaj się z poniższą tabelą, aby poznać możliwe wartości. Wartość domyślna to Basic256.|  
|`issuedKeyType`|Określa typ klucza do wystawienia. Prawidłowe wartości to:<br /><br /> - SymmetricKey<br />-PublicKey<br />- BearerKey<br /><br /> Wartość domyślna to SymmetricKey. Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType> .|  
|`issuedTokenType`|Identyfikator URI, który określa typ tokenu do wystawienia. Wartość domyślna to `null`.|  
|`negotiateServiceCredential`|Wartość określająca, czy poświadczenie usługi powinno być wymieniane jako część negocjacji, czy też jest dostępne poza pasmem. Wartość domyślna to `true` , co oznacza, że poświadczenie usługi jest negocjowane.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Basic128|Użyj szyfrowania Aes128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic192|Użyj szyfrowania Aes192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic256|Użyj szyfrowania AES256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic256Rsa15|Użyj AES256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.|  
|Basic192Rsa15|Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.|  
|TripleDes|Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic128Rsa15|Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.|  
|TripleDesRsa15|Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.|  
|Basic128Sha256|Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic192Sha256|Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic256Sha256|Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|TripleDesSha256|Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic128Sha256Rsa15|Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.|  
|Basic192Sha256Rsa15|Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.|  
|Basic256Sha256Rsa15|Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.|  
|TripleDesSha256Rsa15|Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|Określa kolekcję typów roszczeń dla tego powiązania. Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .|  
|[\<issuer>](issuer.md)|Określa punkt końcowy, który wystawia token zabezpieczający. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .|  
|[\<issuerMetadata>](issuermetadata.md)|Określa adres punktu końcowego wystawcy.|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|Kolekcja parametrów żądania tokenu. Każdy parametr jest elementem XML.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
