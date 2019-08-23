---
title: Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 963325604f66ddd4f8470933584b7880c86403bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951556"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
Program Windows Communication Foundation (WCF) jest oparty na współpracy z usługami sieci Web, które obsługują zestaw specyfikacji znanych jako specyfikacje usług sieci Web. Aby uprościć konfigurację usługi pod kątem najlepszych rozwiązań dotyczących współdziałania, w programie WCF wprowadzono trzy <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>powiązania <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>dostarczone przez <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>system:, i. W przypadku współdziałania z organizacją dla rozwoju standardów informacji o strukturze (języka Oasis), WCF obejmuje jedno powiązanie dostarczone przez system: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. W przypadku publikacji metadanych Funkcja WCF obejmuje dwa powiązania dostarczone przez system: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) i [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). W tym temacie wymieniono specyfikacje obsługiwane przez system powiązań interoperacyjności.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protokoły usług sieci Web obsługiwane przez powiązania basicHttpBinding, wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding  
  
### <a name="all-bindings"></a>Wszystkie powiązania  
 Powiązania BasicHttpBinding >, [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)i [ \<WS2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) obsługują następujące protokoły. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
  
> [!NOTE]
> Informacje o powiązaniach używanych do publikowania metadanych znajdują się w sekcji "powiązania metadanych dostarczone przez system" w dalszej części tego tematu.  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding` i`WS2007HttpBinding` używaj transportów http i https.|  
|Obsługa komunikatów|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding` i`ws2007HttpBinding` obsługują mechanizm optymalizacji transmisji wiadomości (MTOM). Domyślnie nieużywane. Aby użyć mechanizmu MTOM, należy `messageEncoding` ustawić atrybut `"Mtom"`na.<br /><br /> Przykład:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadane|WSDL 1.1|[WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> Program WCF używa Web Services Description Language (WSDL) do opisywania usług.|  
|Metadane|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> Funkcja WCF używa specyfikacji WS-Policy wraz z potwierdzeniami specyficznymi dla domeny, aby opisać wymagania i możliwości usługi.|  
|Metadane|WS-Policy 1.5|[WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> Funkcja WCF używa specyfikacji WS-Policy wraz z potwierdzeniami specyficznymi dla domeny, aby opisać wymagania i możliwości usługi.|  
|Metadane|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> Funkcja WCF implementuje usługę WS-PolicyAttachment, aby dołączać wyrażenia zasad w różnych zakresach w Web Services Description Language (WSDL).|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Funkcja WCF implementuje usługę WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Obsługa komunikatów|PROTOKÓŁ SOAP 1,1|[SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Zgodnie z profilem Basic 1,1 `basicHttpBinding` element implementuje protokół komunikatów protokołu SOAP 1,1.|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP programu WSS 1,0|[Zabezpieczenia komunikatów SOAP programu WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Zgodnie z podstawowym profilem zabezpieczeń, `basicHttpBinding` element zabezpieczenia usług w sieci Web implementuje specyfikację Security 1,0 (WSS) protokołu SOAP dotyczącą zabezpieczeń wiadomości dla nazwy użytkownika i hasła oraz zabezpieczeń opartych na X. 509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpieczenia|UsernameToken profilu zabezpieczeń komunikatów SOAP usług WSS 1,0|[UsernameToken profilu zabezpieczeń komunikatów SOAP usług WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpieczenia|Ochrona komunikatów SOAP programu WSS — profil tokenu certyfikatu X. 509 1,0|[Ochrona komunikatów SOAP programu WSS — profil tokenu certyfikatu X. 509 1,0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Obsługa komunikatów|PROTOKÓŁ SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Struktura komunikatów](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym powiązania HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa komunikatów|WS-Addressing 2005/08|[Web Services Addressing 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, Izaimplementować`wsDualHttpBinding` zalecenia WS-Addressing organizacja World Wide Web Consortium (W3C) w celu włączenia asynchronicznych komunikatów, korelacji komunikatów oraz mechanizmów adresów neutralnych transportowo. `ws2007HttpBinding`<br /><br /> Funkcja WCF nie obsługuje szyfrowania nagłówków WS-Addressing, chociaż jest to dozwolone w specyfikacjach WS-*.|  
|Obsługa komunikatów|WS-Addressing 1,0 — metadane|[Metadane usługi WS-addressing 1,0](https://www.w3.org/2007/05/addressing/metadata) Obsługa tego protokołu jest włączana przez ustawienie wersji zasad w ramach zachowania usługi ServiceMetadata — z opcją PolicyVersion ustawioną na 1,2 (wartość domyślna), opis WSDL jest zgodny z protokołem WSDL WS-Addressing, z PolicyVersion ustawionym na 1,5, opis WSDL jest zgodne z metadanymi WS-Addressing.<br /><br /> Funkcja WCF nie obsługuje szyfrowania nagłówków WS-Addressing, chociaż jest to dozwolone w specyfikacjach WS-*.|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP programu WSS 1,0|[Zabezpieczenia komunikatów SOAP programu WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Użyj, `securityMode` gdy atrybut jest ustawiony na wartość "wsSecurityOverHttp" (wartość domyślna), a parametry są `wsSecurity` konfigurowane przy użyciu elementu podrzędnego.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|UsernameToken profilu zabezpieczeń komunikatów SOAP usług WSS 1,1|[UsernameToken profilu zabezpieczeń komunikatów SOAP usług WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Użyj, `wsSecurity` gdy `authenticationMode` atrybut elementu jest ustawiony na "username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Ochrona komunikatów SOAP programu WSS — profil tokenu certyfikatu X. 509 1,1|[Ochrona komunikatów SOAP programu WSS — profil tokenu certyfikatu X. 509 1,1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Użyj do ochrony wiadomości, gdy `wsSecurity` `authenticationMode` atrybut elementu ma wartość "username", "Certificate" lub "none". Ponadto Użyj tej opcji do uwierzytelniania klienta, gdy `wsSecurity` `authenticationMode` atrybut elementu jest ustawiony na "certyfikat".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP usługi WSS — profil tokenów Kerberos 1,1|[Zabezpieczenia komunikatów SOAP usługi WSS — profil tokenów Kerberos 1,1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Użyj do uwierzytelniania i ochrony komunikatów, gdy `wsSecurity` `authenticationMode` atrybut elementu jest ustawiony na "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Użyj, aby zapewnić bezpieczną sesję, gdy `security/@mode` atrybut ma wartość "Message" `message/@establishSecurityContext` , a atrybut jest ustawiony na wartość "true" (domyślnie).|  
|Zabezpieczenia|Usługa WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Używane przez WS-SecureConversation (Zobacz powyżej).|  
|Niezawodna obsługa komunikatów|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Użyj, gdy powiązanie jest skonfigurowane do użycia `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakcje|Protokół WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Używany do komunikacji między menedżerami transakcji. Klienci i usługi WCF zawsze korzystają z lokalnych menedżerów transakcji.|  
|Transakcje|WS-Coordination|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Służy do przepływu kontekstu transakcji, gdy `flowTransactions` atrybut jest ustawiony na wartość "dozwolone" lub "wymagane".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding i ws2007FederationHttpBinding  
 Elementy [WSFederationHttpBinding > i WS2007FederationHttpBinding > są wprowadzane w celu zapewnienia obsługi scenariuszy federacyjnych, w przypadku których firma zewnętrzna wystawia token używany do uwierzytelniania klienta. \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) Oprócz protokołów używanych przez `wsHttpBinding`program `wsFederationHttpBinding` wykorzystuje:  
  
- `WS-Trust`w przypadku wystawiania tokenów.  
  
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
 W poniższych tabelach opisano protokoły obsługiwane przez systemowe powiązania metadanych współdziałania udostępniane przez <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> klasę.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 Powiązanie > mexHttpBinding obsługuje następujące protokoły. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) Aby uzyskać więcej informacji na temat korzystania z tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|Obsługa komunikatów|PROTOKÓŁ SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Struktura komunikatów](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym powiązania HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa komunikatów|WS-Addressing 2005/08|[Web Services Addressing 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Funkcja WCF implementuje usługę WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding > obsługuje następujące protokoły. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Aby uzyskać więcej informacji na temat korzystania z tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protokół|Specyfikacja i użycie|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Zabezpieczenia transportu są włączone.|  
|Obsługa komunikatów|PROTOKÓŁ SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Struktura komunikatów](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym powiązania HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa komunikatów|WS-Addressing 2005/08|[Web Services Addressing 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Funkcja WCF implementuje usługę WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
## <a name="see-also"></a>Zobacz także

- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
