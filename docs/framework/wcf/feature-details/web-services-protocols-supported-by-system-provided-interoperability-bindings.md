---
title: Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 80fa0e501f425bd5b917059e90f2811f075db651
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746899"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
Program Windows Communication Foundation (WCF) jest oparty na współpracy z usługami sieci Web, które obsługują zestaw specyfikacji znanych jako specyfikacje usług sieci Web. Aby uprościć konfigurację usługi pod kątem najlepszych rozwiązań dotyczących współdziałania, w programie WCF wprowadzono trzy powiązania dostarczone przez system: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>i <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. W przypadku współdziałania z organizacją w celu rozwoju standardów języka Oasis (Structured Information Standards), WCF obejmuje jedno powiązanie dostarczone przez system: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. W przypadku publikacji metadanych Funkcja WCF obejmuje dwa powiązania dostarczone przez system: [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) i [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). W tym temacie wymieniono specyfikacje obsługiwane przez system powiązań interoperacyjności.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protokoły usług sieci Web obsługiwane przez powiązania basicHttpBinding, wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding  
  
### <a name="all-bindings"></a>Wszystkie powiązania  
 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)i\<powiązania [WS2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) obsługują następujące protokoły.  
  
> [!NOTE]
> Informacje o powiązaniach używanych do publikowania metadanych znajdują się w sekcji "powiązania metadanych dostarczone przez system" w dalszej części tego tematu.  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`i `WS2007HttpBinding` używają transportów HTTP i HTTPS.|  
|Obsługa wiadomości|MTOM|[MTOM](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding`i `ws2007HttpBinding` obsługują mechanizm optymalizacji transmisji wiadomości (MTOM). Domyślnie nieużywane. Aby użyć mechanizmu MTOM, ustaw atrybut `messageEncoding` na `"Mtom"`.<br /><br /> Przykład:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadane|WSDL 1.1|[WSDL 1.1](https://www.w3.org/TR/wsdl/)<br /><br /> Program WCF używa Web Services Description Language (WSDL) do opisywania usług.|  
|Metadane|WS-Policy|[WS-Policy](https://www.w3.org/Submission/WS-Policy/)<br /><br /> Funkcja WCF używa specyfikacji WS-Policy wraz z potwierdzeniami specyficznymi dla domeny, aby opisać wymagania i możliwości usługi.|  
|Metadane|WS-Policy 1.5|[WS-Policy 1.5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> Funkcja WCF używa specyfikacji WS-Policy wraz z potwierdzeniami specyficznymi dla domeny, aby opisać wymagania i możliwości usługi.|  
|Metadane|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> Funkcja WCF implementuje usługę WS-PolicyAttachment, aby dołączać wyrażenia zasad w różnych zakresach w Web Services Description Language (WSDL).|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> Funkcja WCF implementuje usługę WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Obsługa wiadomości|PROTOKÓŁ SOAP 1,1|[SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> Zgodnie z profilem Basic 1,1 element `basicHttpBinding` implementuje protokół komunikatów protokołu SOAP 1,1.|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP programu WSS 1,0|[Zabezpieczenia komunikatów SOAP programu WSS 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Zgodnie z podstawowym profilem zabezpieczeń, element `basicHttpBinding` implementuje specyfikację Security 1,0 zabezpieczenia usług w sieci Web (WSS) protokołu SOAP dotyczącej zabezpieczeń w przypadku nazwy użytkownika/hasła oraz zabezpieczeń opartych na X. 509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpieczenia|UsernameToken profilu zabezpieczeń komunikatów SOAP usług WSS 1,0|[UsernameToken profilu zabezpieczeń komunikatów SOAP usług WSS 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpieczenia|Ochrona komunikatów SOAP programu WSS — profil tokenu certyfikatu X. 509 1,0|[Ochrona komunikatów SOAP programu WSS — profil tokenu certyfikatu X. 509 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Obsługa wiadomości|PROTOKÓŁ SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Struktura komunikatów](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (w tym powiązania HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Obsługa wiadomości|WS-Addressing 2005/08|[Web Services Addressing 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Services Addressing 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`i `wsDualHttpBinding` zaimplementować zalecenia WS-Addressing organizacja World Wide Web Consortium (W3C) w celu włączenia asynchronicznych komunikatów, korelacji komunikatów i mechanizmów adresów neutralnych transportowo.<br /><br /> Funkcja WCF nie obsługuje szyfrowania nagłówków WS-Addressing, chociaż jest to dozwolone w specyfikacjach WS-*.|  
|Obsługa wiadomości|WS-Addressing 1,0 — metadane|[Metadane usługi WS-addressing 1,0](https://www.w3.org/2007/05/addressing/metadata/) Obsługa tego protokołu jest włączana przez ustawienie wersji zasad w ramach zachowania usługi ServiceMetadata — z opcją PolicyVersion ustawioną na 1,2 (wartość domyślna), opis WSDL jest zgodny z protokołem WSDL WS-Addressing, z PolicyVersion ustawionym na 1,5, opis WSDL jest zgodny z metadanymi WS-Addressing.<br /><br /> Funkcja WCF nie obsługuje szyfrowania nagłówków WS-Addressing, chociaż jest to dozwolone w specyfikacjach WS-*.|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP programu WSS 1,0|[Zabezpieczenia komunikatów SOAP programu WSS 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Użyj, gdy atrybut `securityMode` jest ustawiony na wartość "wsSecurityOverHttp" (wartość domyślna), a parametry są konfigurowane przy użyciu `wsSecurity` elementu podrzędnego.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|UsernameToken profilu zabezpieczeń komunikatów SOAP usług WSS 1,1|[UsernameToken profilu zabezpieczeń komunikatów SOAP usług WSS 1,0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Użyj, gdy atrybut `authenticationMode` elementu `wsSecurity` jest ustawiony na wartość "username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Ochrona komunikatów SOAP programu WSS — profil tokenu certyfikatu X. 509 1,1|[Ochrona komunikatów SOAP programu WSS — profil tokenu certyfikatu X. 509 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> Użyj do ochrony wiadomości, gdy atrybut `authenticationMode` elementu `wsSecurity` jest ustawiony na wartość "username", "Certificate" lub "none". Ponadto Użyj tej opcji do uwierzytelniania klienta, gdy atrybut `authenticationMode` elementu `wsSecurity` jest ustawiony na "certyfikat".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP usługi WSS — profil tokenów Kerberos 1,1|[Zabezpieczenia komunikatów SOAP usługi WSS — profil tokenów Kerberos 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> Użyj do uwierzytelniania i ochrony komunikatów, gdy atrybut `authenticationMode` elementu `wsSecurity` jest ustawiony na "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Użyj, aby zapewnić bezpieczną sesję, gdy atrybut `security/@mode` ma wartość "Message", a atrybut `message/@establishSecurityContext` ma wartość "true" (wartość domyślna).|  
|Zabezpieczenia|Usługa WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> Używane przez WS-SecureConversation (Zobacz powyżej).|  
|Niezawodna obsługa komunikatów|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Użyj, gdy powiązanie jest skonfigurowane do używania `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakcje|Protokół WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> Używany do komunikacji między menedżerami transakcji. Klienci i usługi WCF zawsze korzystają z lokalnych menedżerów transakcji.|  
|Transakcje|WS-Coordination|[WS-Coordination](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> Służy do przepływu kontekstu transakcji, gdy atrybut `flowTransactions` jest ustawiony na wartość "dozwolone" lub "wymagane".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding i ws2007FederationHttpBinding  
 [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i [\<elementów >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) , aby zapewnić obsługę scenariuszy federacyjnych, w przypadku których firma trzecia wystawia token używany do uwierzytelniania klienta. Oprócz protokołów używanych przez `wsHttpBinding`, `wsFederationHttpBinding` wykorzystuje:  
  
- `WS-Trust` na potrzeby wystawiania tokenów.  
  
- W przypadku usługi WSS Security Assertions Language (SAML) — profil tokenów 1,0 i 1,1 dla najczęściej wystawionego formatu tokenu.  
  
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
  
## <a name="system-provided-metadata-bindings"></a>Powiązania metadanych dostarczone przez system  
 W poniższych tabelach opisano protokoły obsługiwane przez systemowe powiązania metadanych współdziałania udostępniane przez klasę <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 Powiązanie [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) obsługuje następujące protokoły. Aby uzyskać więcej informacji na temat korzystania z tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Obsługa wiadomości|PROTOKÓŁ SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Struktura komunikatów](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (w tym powiązania HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Obsługa wiadomości|WS-Addressing 2005/08|[Web Services Addressing 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Services Addressing 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> Funkcja WCF implementuje usługę WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) obsługuje następujące protokoły. Aby uzyskać więcej informacji na temat korzystania z tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> Zabezpieczenia transportu są włączone.|  
|Obsługa wiadomości|PROTOKÓŁ SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Struktura komunikatów](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (w tym powiązania HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Obsługa wiadomości|WS-Addressing 2005/08|[Web Services Addressing 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Services Addressing 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> Funkcja WCF implementuje usługę WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
## <a name="see-also"></a>Zobacz także

- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
