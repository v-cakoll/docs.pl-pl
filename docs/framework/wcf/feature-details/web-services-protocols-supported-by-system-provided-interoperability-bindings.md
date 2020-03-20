---
title: Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: a1e67401a09370a46bc7a3e8546c95467bc18b67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184146"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
Windows Communication Foundation (WCF) jest zbudowany do współpracy z usługami sieci Web, które obsługują zestaw specyfikacji znanych jako specyfikacje usług sieci Web. Aby uprościć konfigurację usług w celu uzyskania najlepszych praktyk w zakresie interoperacyjności, WCF wprowadza trzy interoperacyjne powiązania dostarczane przez system: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, i <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. W celu interoperacyjności z organizacją na rzecz rozwoju standardów strukturalnych standardów informacyjnych (OASIS) <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>WCF obejmuje jedno interoperacyjne wiążące dla systemu: . W przypadku publikacji metadanych WCF zawiera dwa interoperacyjne powiązania dostarczone przez system: [ \<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) i [ \<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). W tym temacie wymieniono specyfikacje, które są obsługiwane przez interoperacyjne powiązania dostarczone przez system.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protokoły usług sieci Web obsługiwane przez podstawowe powiązaniahttpbinding, wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding Bindings  
  
### <a name="all-bindings"></a>Wszystkie wiązania  
 [ \<Podstawowe>httpbinowanie ](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)i [ \<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) powiązania obsługują następujące protokoły.  
  
> [!NOTE]
> Aby uzyskać informacje na temat powiązań używanych do publikowania metadanych, zobacz sekcję "Powiązania metadanych dostarczonych przez system" w dalszej części tego tematu.  
  
|Kategoria|Protocol (Protokół)|Specyfikacja i użytkowanie|  
|--------------|--------------|-----------------------------|  
|Transport|Protokół HTTP 1.1|[Protokół HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding``WSHttpBinding`, i `WS2007HttpBinding` użyj transportów HTTP i HTTPS.|  
|Obsługa komunikatów|Mtom|[Mtom](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding``wsHttpBinding`, i `ws2007HttpBinding` obsługuje mechanizm optymalizacji transmisji wiadomości (MTOM). Nie jest używany domyślnie. Aby użyć MTOM, `messageEncoding` ustaw `"Mtom"`atrybut na .<br /><br /> Przykład:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadane|WSDL 1.1|[WSDL 1.1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF używa języka opisu usług sieci Web (WSDL) do opisywania usług.|  
|Metadane|Zasady WS|[Zasady WS](https://www.w3.org/Submission/WS-Policy/)<br /><br /> WCF używa specyfikacji zasad WS wraz z potwierdzeń specyficznych dla domeny do opisania wymagań i możliwości usługi.|  
|Metadane|Zasady WS 1.5|[Zasady WS 1.5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> WCF używa specyfikacji zasad WS wraz z potwierdzeń specyficznych dla domeny do opisania wymagań i możliwości usługi.|  
|Metadane|WS-ZasadyPrzywiązania|[WS-ZasadyPrzywiązania](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF implementuje WS-PolicyAttachment dołączyć wyrażenia zasad w różnych zakresach w języku opisu usług sieci Web (WSDL).|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange do pobierania schematu XML, WSDL i WS-policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategoria|Protocol (Protokół)|Specyfikacja i użytkowanie|  
|--------------|--------------|-----------------------------|  
|Obsługa komunikatów|MYDŁO 1.1|[MYDŁO 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> Zgodnie z profilem podstawowym 1.1 `basicHttpBinding` element implementuje protokół komunikatu SOAP 1.1.|  
|Zabezpieczenia|Bezpieczeństwo wiadomości WSS SOAP 1.0|[Bezpieczeństwo wiadomości WSS SOAP 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Zgodnie z podstawowym profilem zabezpieczeń `basicHttpBinding` element implementuje specyfikację zabezpieczenia WSS (WSS) SOAP Message Security 1.0 dla nazwy użytkownika/hasła i zabezpieczeń opartych na x.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpieczenia|Nazwa użytkownika wiadomości WSS SOAP Nazwa użytkownikaDoken Profil 1.0|[Nazwa użytkownika wiadomości WSS SOAP Nazwa użytkownikaDoken Profil 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpieczenia|WSS SOAP Message Security X.509 Profil tokenu certyfikatu 1.0|[WSS SOAP Message Security X.509 Profil tokenu certyfikatu 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding  
  
|Kategoria|Protocol (Protokół)|Specyfikacja i użytkowanie|  
|--------------|--------------|-----------------------------|  
|Obsługa komunikatów|MYDŁO 1.2|[Podręcznik](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Struktura obsługi wiadomości](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adiunktów (w tym powiązania HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Obsługa komunikatów|Adresowanie WS 2005/08|[Adresowanie usług internetowych 1.0 - Rdzeń](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Adresowanie usług internetowych 1.0 - MYDŁO](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> , `wsHttpBinding` `ws2007HttpBinding`i `wsDualHttpBinding` zaimplementować world wide web consortium (W3C) WS-Adresowanie zalecenia, aby włączyć asynchroniczne wiadomości, korelacji wiadomości i transportu neutralne mechanizmy adresowania.<br /><br /> WCF nie obsługuje szyfrowania nagłówków adresowania WS, chociaż jest to dozwolone przez specyfikacje WS-*.|  
|Obsługa komunikatów|Adresowanie WS 1.0 - Metadane|[Metadane adresowania WS 1.0](https://www.w3.org/2007/05/addressing/metadata/) Obsługa tego protokołu jest włączona przez ustawienie wersji zasad w zachowaniu ServiceMetadata — z policyversion ustawioną na 1.2 (domyślnie), Opis wsdl jest zgodny z WS-Addressing wsdl, z policyversion ustawioną na 1.5, opis wsdl jest zgodny z metadanymi adresowania ws.<br /><br /> WCF nie obsługuje szyfrowania nagłówków adresowania WS, chociaż jest to dozwolone przez specyfikacje WS-*.|  
|Zabezpieczenia|Bezpieczeństwo wiadomości WSS SOAP 1.0|[Bezpieczeństwo wiadomości WSS SOAP 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Użyj, `securityMode` gdy atrybut jest ustawiony na "wsSecurityOverHttp" (domyślnie), `wsSecurity` a parametry są konfigurowane przy użyciu elementu podrzędnego.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Nazwa użytkownika wiadomości WSS SOAP Nazwa użytkownikaDoken Profil 1.1|[Nazwa użytkownika wiadomości WSS SOAP Nazwa użytkownikaDoken Profil 1.0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Użyj, `wsSecurity` gdy `authenticationMode` atrybut elementu jest ustawiony na "Nazwa użytkownika".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpieczenia|WSS SOAP Message Security X.509 Profil tokenu certyfikatu 1.1|[WSS SOAP Message Security X.509 Profil tokenu certyfikatu 1.1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> Służy do ochrony `wsSecurity` wiadomości, `authenticationMode` gdy atrybut elementu jest ustawiony na "Nazwa użytkownika", "Certyfikat" lub "Brak". Ponadto użyj tego do uwierzytelniania `wsSecurity` klienta, `authenticationMode` gdy atrybut elementu jest ustawiony na "Certyfikat".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Profil tokenu zabezpieczeń protokołu Kerberos 1.1 w komunikacie WSS SOAP|[Profil tokenu zabezpieczeń protokołu Kerberos 1.1 w komunikacie WSS SOAP](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> Służy do uwierzytelniania i `wsSecurity` ochrony `authenticationMode` wiadomości, gdy atrybut elementu jest ustawiony na "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|WS-SecureKonwersja|[WS-SecureKonwersja](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Użyj, aby zapewnić bezpieczną sesję, `security/@mode` gdy atrybut jest `message/@establishSecurityContext` ustawiony na "Wiadomość", a atrybut jest ustawiony na "true" (domyślnie).|  
|Zabezpieczenia|WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> Używane przez WS-SecureConversation (patrz wyżej).|  
|Niezawodna obsługa komunikatów|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Użyj, gdy powiązanie jest `reliableSession`skonfigurowane do używania .<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakcje|WS-AtomicTransakcja|[WS-AtomicTransakcja](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> Służy do komunikacji między menedżerami transakcji. Klienci i usługi WCF zawsze używają lokalnych menedżerów transakcji.|  
|Transakcje|Koordynacja WS|[Koordynacja WS](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> Użyj do przepływu kontekstu `flowTransactions` transakcji, gdy atrybut jest ustawiony na "Dozwolone" lub "Wymagane".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding i ws2007FederationHttpBinding  
 Elementy>[ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i [ \<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) są wprowadzane w celu zapewnienia obsługi scenariuszy federacyjnych, w których strona trzecia wystawia token używany do uwierzytelniania klienta. Oprócz protokołów używanych `wsHttpBinding`przez `wsFederationHttpBinding` , dźwignie:  
  
- `WS-Trust`emisji tokenów.  
  
- WSS Security Assertions Markup Language (SAML) Token Profile 1.0 i 1.1 dla najczęściej wystawianego formatu tokenu.  
  
 Przykład:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 Aby uzyskać więcej informacji, zobacz [Federacja](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Powiązania metadanych dostarczonych przez system  
 W poniższych tabelach opisano protokoły obsługiwane przez systemowe interoperacyjne <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> powiązania metadanych udostępniane przez klasę.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 Powiązanie>[ \<mexHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) obsługuje następujące protokoły. Aby uzyskać więcej informacji na temat używania tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protocol (Protokół)|Specyfikacja i użytkowanie|  
|--------------|--------------|-----------------------------|  
|Transport|Protokół HTTP 1.1|[Protokół HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Obsługa komunikatów|MYDŁO 1.2|[Podręcznik](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Struktura obsługi wiadomości](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adiunktów (w tym powiązania HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Obsługa komunikatów|Adresowanie WS 2005/08|[Adresowanie usług internetowych 1.0 - Rdzeń](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Adresowanie usług internetowych 1.0 - MYDŁO](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange do pobierania schematu XML, WSDL i WS-policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding>obsługuje następujące protokoły. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Aby uzyskać więcej informacji na temat używania tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protocol (Protokół)|Specyfikacja i użytkowanie|  
|--------------|--------------|-----------------------------|  
|Transport|Protokół HTTP 1.1|[Protokół HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> Zabezpieczenia transportu jest włączona.|  
|Obsługa komunikatów|MYDŁO 1.2|[Podręcznik](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Struktura obsługi wiadomości](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adiunktów (w tym powiązania HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Obsługa komunikatów|Adresowanie WS 2005/08|[Adresowanie usług internetowych 1.0 - Rdzeń](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Adresowanie usług internetowych 1.0 - MYDŁO](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange do pobierania schematu XML, WSDL i WS-policy.|  
  
## <a name="see-also"></a>Zobacz też

- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<podstawowa>httpbinding](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<>wsDualHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<>wiązania mexhttps](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<>mexHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
