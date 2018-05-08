---
title: Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 728dba65a99d71a52551b16e5f1822104ed40ea7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoły usług sieci Web obsługiwane przez wiązania współdziałania udostępnione przez system
Windows Communication Foundation (WCF) jest oparty na potrzeby współdziałania z usługami sieci Web, które obsługuje zestaw specyfikacji znany jako specyfikacje usług sieci Web. Aby uprościć konfigurację usługi współdziałanie najlepsze rozwiązania, WCF wprowadzono trzy interoperacyjne powiązania dostarczane przez system: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, i <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Współdziałanie z organizacji standardów przejścia z Structured Information Standards (OASIS), WCF zawiera jeden interoperacyjne powiązanie dostarczane przez system: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. W przypadku publikacji metadanych WCF obejmuje dwa interoperacyjne powiązania dostarczane przez system: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) i [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). W tym temacie wymieniono specyfikacje obsługujących powiązania interoperacyjne dostarczane przez system.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Web Services protokoły obsługiwane przez wiązania klasy basicHttpBinding lub wsHttpBinding, ws2007HttpBinding, a wsDualHttpBinding  
  
### <a name="all-bindings"></a>Wszystkie powiązania  
 [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), i [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) powiązania pomocy technicznej następujące protokoły.  
  
> [!NOTE]
>  Informacje używane do publikowania metadanych powiązania zobacz sekcję "System-Provided metadanych powiązania" w dalszej części tego tematu.  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`, i `WS2007HttpBinding` użyj transportu HTTP i HTTPS.|  
|Obsługa wiadomości|MTOM|[MTOM](http://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`, i `ws2007HttpBinding` obsługuje mechanizmu optymalizacji transmisji wiadomości (MTOM). Nie jest używany domyślnie. Aby używać mechanizmu MTOM, ustaw `messageEncoding` atrybutu `"Mtom"`.<br /><br /> Przykład:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadane|WSDL 1.1|[WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> Do opisania usług WCF używa usługi sieci Web Services Description Language (WSDL).|  
|Metadane|WS-Policy|[WS-Policy](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> Usługi WCF używa specyfikacji WS-Policy wraz z potwierdzeniami specyficznego dla domeny do opisu usługi wymagań i możliwości.|  
|Metadane|WS-Policy 1.5|[WS-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> Usługi WCF używa specyfikacji WS-Policy wraz z potwierdzeniami specyficznego dla domeny do opisu usługi wymagań i możliwości.|  
|Metadane|WS-PolicyAttachment|[WS-PolicyAttachment](http://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> Usługi WCF implementuje usługi WS-PolicyAttachment do podłączenia zasad wyrażenia w różnych zakresów w sieci Web Services Description Language (WSDL).|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, można pobrać schematu XML, WSDL i WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Obsługa wiadomości|SOAP 1.1|[SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Zgodnie z Basic Profile 1.1 `basicHttpBinding` element implementuje ten protokół wiadomości SOAP 1.1.|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP WSS 1.0|[Zabezpieczenia komunikatów SOAP WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Zgodnie z Basic Profile zabezpieczeń `basicHttpBinding` element implementuje Specyfikacja zabezpieczenia komunikatów SOAP zabezpieczeń usług sieci Web (WSS) 1.0, nazwa użytkownika/hasło i zabezpieczenia na poziomie X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpieczenia|Profil UsernameToken zabezpieczeń wiadomości SOAP WSS 1.0|[Profil UsernameToken zabezpieczeń wiadomości SOAP WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpieczenia|WSS SOAP komunikatów zabezpieczeń X.509 tokenu profil certyfikatu 1.0|[WSS SOAP komunikatów zabezpieczeń X.509 tokenu profil certyfikatu 1.0](http://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding i wsDualHttpBinding  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Obsługa wiadomości|SOAP 1.2|[Elementarz](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Narzędzia obsługi wiadomości](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym powiązanie HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa wiadomości|Protokół WS-Addressing 2005/08|[Usługi sieci Web adresowanie 1.0 — podstawowe](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Usługi sieci Web adresowanie 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`, I `wsDualHttpBinding` implementacji protokołu WS-Addressing sieci World Wide Web konsorcjum W3C zalecenie, aby umożliwić asynchroniczną obsługę wiadomości, korelacja komunikatów i mechanizmów adresowania niezależny od transportu.<br /><br /> Usługi WCF nie obsługuje szyfrowania nagłówków WS-Addressing, mimo że jest to dozwolone przez WS-* specyfikacji.|  
|Obsługa wiadomości|Protokół WS-Addressing 1.0 - metadanych|[Protokół WS-Addressing metadanych 1.0](http://www.w3.org/2007/05/addressing/metadata) włączona jest obsługa protokołu przez ustawienie wersji zasad w zachowaniu ServiceMetadata - policyversion ustawioną 1.2 (ustawienie domyślne), opis wsdl jest zgodne z protokołu WS-Addressing wsdl z policyversion ustawioną w wersji 1.5, opis wsdl jest zgodne z metadanymi ws-addressing.<br /><br /> Usługi WCF nie obsługuje szyfrowania nagłówków WS-Addressing, mimo że jest to dozwolone przez WS-* specyfikacji.|  
|Zabezpieczenia|Zabezpieczenia komunikatów SOAP WSS 1.0|[Zabezpieczenia komunikatów SOAP WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Używany, gdy `securityMode` atrybutu jest ustawiona na "wsSecurityOverHttp" (ustawienie domyślne), a parametry są skonfigurowane przy użyciu `wsSecurity` element podrzędny.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Profil UsernameToken zabezpieczeń wiadomości programu WSS SOAP 1.1|[Profil UsernameToken zabezpieczeń wiadomości SOAP WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Używany, gdy `wsSecurity` elementu `authenticationMode` atrybut jest ustawiony na "Nazwa_użytkownika".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpieczenia|WSS SOAP komunikatów zabezpieczeń X.509 tokenu profil certyfikatu 1.1|[WSS SOAP komunikatów zabezpieczeń X.509 tokenu profil certyfikatu 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Używany do ochrony wiadomości gdy `wsSecurity` elementu `authenticationMode` ustawiono atrybut "Nazwa_użytkownika", "Certyfikatu" lub "None". Ponadto użyć do uwierzytelniania klienta podczas `wsSecurity` elementu `authenticationMode` atrybut ma wartość "Certyfikat".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|Profil Token protokołu Kerberos zabezpieczeń wiadomości programu WSS SOAP 1.1|[Profil Token protokołu Kerberos zabezpieczeń wiadomości programu WSS SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Używany do uwierzytelniania i komunikat ochrony po `wsSecurity` elementu `authenticationMode` atrybut ma wartość "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpieczenia|WS-SecureConversation|[WS-SecureConversation](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Służy do zapewnienia bezpiecznej sesji podczas `security/@mode` atrybut jest ustawiony na "Komunikat" i `message/@establishSecurityContext` atrybut ma ustawioną wartość "prawda" (ustawienie domyślne).|  
|Zabezpieczenia|WS-Trust|[WS-Trust](http://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Używane przez usługi WS-SecureConversation (zobacz powyżej).|  
|Niezawodna obsługa komunikatów|WS-ReliableMessaging.|[WS-ReliableMessaging](http://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Użyj, jeśli powiązanie jest skonfigurowane do używania `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakcje|WS-AtomicTransaction|[WS-AtomicTransaction](http://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Używany do komunikacji między menedżerami transakcji. Klienci WCF i usług zawsze używać menedżerowie transakcji lokalnej.|  
|Transakcje|WS-Coordination|[WS-Coordination](http://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Użyj przepływ kontekstu transakcji po `flowTransactions` atrybut jest ustawiony na "Dozwolone" lub "Wymagane".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding i ws2007FederationHttpBinding  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementy są wprowadzane zapewnia obsługę scenariuszach obejmujących Federację, gdzie innej Strona wystawia token używany do uwierzytelniania klienta. Oprócz protokołach używanych przez `wsHttpBinding`, `wsFederationHttpBinding` wykorzystuje:  
  
-   `WS-Trust` do wydawania tokenów.  
  
-   WSS zabezpieczeń potwierdzenia Markup Language (SAML) profilu Token 1.0 i 1.1 dla większości wystawiony często format tokenu.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [federacyjnego](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Powiązania dostarczane przez system metadanych  
 W poniższych tabelach opisano protokoły obsługiwane przez wiązania dostarczane przez system interoperacyjne metadanych udostępnianych przez <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> klasy.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<MexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) powiązanie obsługuje następujące protokoły. Aby uzyskać więcej informacji na temat używania tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)|  
|Obsługa wiadomości|SOAP 1.2|[Elementarz](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Narzędzia obsługi wiadomości](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym powiązanie HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa wiadomości|Protokół WS-Addressing 2005/08|[Usługi sieci Web adresowanie 1.0 — podstawowe](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Usługi sieci Web adresowanie 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, można pobrać schematu XML, WSDL i WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) obsługuje następujące protokoły. Aby uzyskać więcej informacji na temat używania tego powiązania, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategoria|Protokół|Specyfikacja i użycia|  
|--------------|--------------|-----------------------------|  
|Transportu|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Zabezpieczenia transportu jest włączone.|  
|Obsługa wiadomości|SOAP 1.2|[Elementarz](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Narzędzia obsługi wiadomości](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (w tym powiązanie HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Obsługa wiadomości|Protokół WS-Addressing 2005/08|[Usługi sieci Web adresowanie 1.0 — podstawowe](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Usługi sieci Web adresowanie 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadane|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, można pobrać schematu XML, WSDL i WS-Policy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
 [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)  
 [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)  
 [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)  
 [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
