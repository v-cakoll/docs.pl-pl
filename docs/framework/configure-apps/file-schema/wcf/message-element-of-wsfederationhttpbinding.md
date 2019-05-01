---
title: <message> element <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 79739dd715d7982555e5577c921cb65156af5923
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769879"
---
# <a name="message-element-of-wsfederationhttpbinding"></a>\<komunikat > element \<wsFederationHttpBinding >
Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 \<system.ServiceModel>  
\<powiązania >  
\<wsFederatedBinding>  
\<Powiązanie >  
\<security>  
\<message>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|algorithmSuite|Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Zobacz tabelę "algorithmSuite atrybutu" prawidłowych wartości tego atrybutu. Wartość domyślna to `Basic256`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).|  
|issuedKeyType|Określa typ klucza zostanie wysłane. Prawidłowe wartości są następujące:<br /><br /> -SymmetricKey<br />-PublicKey<br /><br /> Wartość domyślna to `SymmetricKey`. Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.|  
|issuedTokenType|Ciąg, który zawiera identyfikator URI, który określa typ token został wystawiony. Wartość domyślna to `null`.|  
|negotiateServiceCredential|Wartość logiczna, która określa, czy poświadczenia usługi powinny być wymieniane w ramach negocjacji znajduje się poza pasmem. Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite Attribute  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Basic128|Użyj szyfrowania Basic128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.|  
|Basic192|Należy używać szyfrowania Basic192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256|Należy używać szyfrowania Basic256, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256Rsa15|Użyj Basic256 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic192Rsa15|Użyj Basic192 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDes|Należy używać szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic128Rsa15|Użyj Basic128 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDesRsa15|Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic128Sha256|Użyj Basic128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic192Sha256|Użyj Basic192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256Sha256|Użyj Basic256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|TripleDesSha256|TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic128Sha256Rsa15|Użyj Basic128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic192Sha256Rsa15|Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic256Sha256Rsa15|Użyj Basic256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDesSha256Rsa15|TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Określa kolekcję typów oświadczeń dla tego powiązania. Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.|  
|issuer|Określa punkt końcowy, który wystawia token zabezpieczający. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.|  
|issuerMetadata|Określa adres punktu końcowego wystawcy.|  
|[\<tokenRequestParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|Kolekcja parametrów żądania tokenu. Każdy parametr jest elementem XML.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
