---
title: Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 0539f2144c85fe20a440f8b99425936025a186c0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192918"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
Windows Communication Foundation (WCF) został opracowany pod kątem współdziałania z usługami sieci Web, które obsługują zestaw specyfikacji znane jako specyfikacji usług sieci Web. Aby uprościć konfigurację usługi najlepsze rozwiązania dotyczące współdziałania, WCF wprowadza trzy interoperacyjne powiązania dostarczane przez system: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, i <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Współdziałanie z organizacji pod kątem obsługi standardów zawodowego of Structured Information Standards (OASIS), usługi WCF zawiera jedno interoperacyjne powiązanie dostarczane przez system: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. W przypadku publikacji metadanych WCF obejmuje dwa interoperacyjne powiązania dostarczane przez system: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) i [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Ten temat zawiera specyfikacje, które obsługują interoperacyjne powiązania dostarczane przez system.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Web Services protokoły obsługiwane przez wiązania basicHttpBinding, wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding  
  
### <a name="all-bindings"></a>Wszystkie powiązania  
 [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), i [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) obsługę powiązań następujące protokoły.  
  
> [!NOTE]
>  Dla informacji na temat powiązania, używany do publikowania metadanych zobacz sekcję "System-Provided metadanych powiązania" w dalszej części tego tematu.  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`, i `WS2007HttpBinding` użyj transportu HTTP i HTTPS.|  
|Obsługa wiadomości|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`, i `ws2007HttpBinding` obsługi komunikatów transmisji optymalizacji mechanizm (MTOM). Nie jest używane domyślnie. Aby użyć MTOM, ustaw `messageEncoding` atrybutu `"Mtom"`.<br /><br /> Przykład:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadane|WSDL 1.1|[WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> Usługi WCF używa usługi sieci Web Services Description Language (WSDL) do opisu usługi.|  
|Metadane|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> Usługi WCF używa specyfikacji WS-Policy wraz z potwierdzenia specyficznego dla domeny, aby opisują wymagania dotyczące usługi i możliwości.|  
|Metadane|WS-Policy 1.5|[WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> Usługi WCF używa specyfikacji WS-Policy wraz z potwierdzenia specyficznego dla domeny, aby opisują wymagania dotyczące usługi i możliwości.|  
|Metadane|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> Usługi WCF implementuje usługi WS-PolicyAttachment, aby dołączyć wyrażenia zasad w różnych zakresach w sieci Web Services Description Language (WSDL).|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Obsługa wiadomości|PROTOKOŁU SOAP 1.1|[PROTOKOŁU SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Zgodnie z Basic Profile 1.1 `basicHttpBinding` element implementuje protokół wiadomości SOAP 1.1.|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP programu WSS 1.0|[Zabezpieczenia komunikatów SOAP programu WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Zgodnie z profilu podstawowego zabezpieczeń `basicHttpBinding` element implementuje Specyfikacja zabezpieczeń wiadomości SOAP zabezpieczeń usług sieci Web (WSS) 1.0, nazwa użytkownika/hasło i zabezpieczenia oparte na X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpieczenia|Profil UsernameToken zabezpieczeń komunikatu protokołu SOAP programu WSS 1.0|[Profil UsernameToken zabezpieczeń komunikatu protokołu SOAP programu WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpieczenia|Grupie WSS protokołu SOAP wiadomości zabezpieczeń X.509 tokenu profilu certyfikatu 1.0|[Grupie WSS protokołu SOAP wiadomości zabezpieczeń X.509 tokenu profilu certyfikatu 1.0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Obsługa wiadomości|PROTOKOŁU SOAP 1.2|[Podstawowe informacje](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Narzędzia obsługi wiadomości](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym wiązania HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa wiadomości|WS-Addressing 2005/08|[Eliminowanie Core 1.0 - usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Eliminowanie 1.0 - protokołu SOAP usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`, I `wsDualHttpBinding` wykonania World Wide Web Consortium (W3C) protokołu WS-Addressing zalecenia umożliwiające asynchroniczne przesyłanie komunikatów, korelacja komunikatów i mechanizmów adresowania niezależny od transportu.<br /><br /> Usługi WCF nie obsługuje szyfrowania nagłówków WS-Addressing, mimo że jest to dozwolone przez WS-* specyfikacji.|  
|Obsługa wiadomości|WS-Addressing 1.0 — metadanych|[Metadane usługi WS-Addressing 1.0](https://www.w3.org/2007/05/addressing/metadata) włączona jest obsługa tego protokołu, przez ustawienie wersji zasad w zachowanie ServiceMetadata - policyversion równa 1.2 (ustawienie domyślne), opis wsdl jest zgodne z WS-Addressing wsdl, za pomocą policyversion zestawu do wersji 1.5, opis wsdl jest zgodne z metadanymi ws-addressing.<br /><br /> Usługi WCF nie obsługuje szyfrowania nagłówków WS-Addressing, mimo że jest to dozwolone przez WS-* specyfikacji.|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP programu WSS 1.0|[Zabezpieczenia komunikatów SOAP programu WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Zastosowania `securityMode` atrybut jest ustawiony na "wsSecurityOverHttp" (wartość domyślna), a parametry są skonfigurowane przy użyciu `wsSecurity` elementu podrzędnego.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Grupie WSS SOAP 1.1 profilu UsernameToken zabezpieczeń komunikatów|[Profil UsernameToken zabezpieczeń komunikatu protokołu SOAP programu WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Zastosowania `wsSecurity` elementu `authenticationMode` atrybut jest ustawiony na "Nazwa_użytkownika".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Grupie WSS protokołu SOAP wiadomości zabezpieczeń X.509 tokenu profilu certyfikatu 1.1|[Grupie WSS protokołu SOAP wiadomości zabezpieczeń X.509 tokenu profilu certyfikatu 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Używany do ochrony wiadomości gdy `wsSecurity` elementu `authenticationMode` atrybutu jest równa "Nazwa_użytkownika", "Certificate" lub "None". Ponadto, użyj tego do uwierzytelniania klienta podczas `wsSecurity` elementu `authenticationMode` "Certificate" ma ustawioną wartość atrybutu.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Profil tokenu protokołu Kerberos zabezpieczeń wiadomości WSS SOAP 1.1|[Profil tokenu protokołu Kerberos zabezpieczeń wiadomości WSS SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Na użytek uwierzytelniania i komunikat ochrony podczas `wsSecurity` elementu `authenticationMode` atrybut jest ustawiony na "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Służy do zapewnienia bezpiecznej sesji przy `security/@mode` "Message" ma ustawioną wartość atrybutu i `message/@establishSecurityContext` atrybut jest ustawiony na wartość "prawda" (wartość domyślna).|  
|Zabezpieczenia|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Używane przez usługi WS-SecureConversation (zobacz powyżej).|  
|Niezawodna obsługa komunikatów|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Podczas wiązania jest skonfigurowany do używania `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakcje|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Na użytek komunikacji między menedżerowie transakcji. Klienci WCF i usług zawsze używaj menedżerowie transakcji lokalnej.|  
|Transakcje|WS-Coordination|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Służy do przepływu kontekstu transakcji po `flowTransactions` atrybut jest ustawiony na "Dozwolone" lub "Required".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding i ws2007FederationHttpBinding  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementy zostały wprowadzone w celu zapewnienia obsługi scenariuszach obejmujących Federację, gdzie trzecią Strona wystawia token używany do uwierzytelniania klienta. Oprócz protokoły używane przez `wsHttpBinding`, `wsFederationHttpBinding` wykorzystuje:  
  
-   `WS-Trust` wydawania tokenów.  
  
-   WSS zabezpieczeń potwierdzenia Markup Language (SAML) tokenu profilu 1.0 i 1.1 dla większości powszechnie wystawiony format tokenu.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Federacji](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Powiązania dostarczane przez system metadanych  
 W poniższych tabelach opisano protokoły obsługiwane przez usługi powiązania dostarczane przez system metadanych interoperacyjne udostępnianych przez <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> klasy.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<MexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) powiązanie obsługuje następujące protokoły. Aby uzyskać więcej informacji o korzystaniu z tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|Obsługa wiadomości|PROTOKOŁU SOAP 1.2|[Podstawowe informacje](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Narzędzia obsługi wiadomości](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym wiązania HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa wiadomości|WS-Addressing 2005/08|[Eliminowanie Core 1.0 - usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Eliminowanie 1.0 - protokołu SOAP usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) obsługuje następujące protokoły. Aby uzyskać więcej informacji o korzystaniu z tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Zabezpieczenia transportu jest włączona.|  
|Obsługa wiadomości|PROTOKOŁU SOAP 1.2|[Podstawowe informacje](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Narzędzia obsługi wiadomości](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym wiązania HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa wiadomości|WS-Addressing 2005/08|[Eliminowanie Core 1.0 - usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Eliminowanie 1.0 - protokołu SOAP usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
 [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)  
 [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)  
 [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)  
 [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
