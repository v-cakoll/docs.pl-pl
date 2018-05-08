---
title: WSDL i zasady
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: 330a48989e9d6ca3cee0d11bf4b3fce38a25fa3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wsdl-and-policy"></a>WSDL i zasady
W tym temacie omówiono usługi Windows Communication Foundation (WCF), WSDL 1.1, szczegóły implementacji protokołu WS-Policy i WS-PolicyAttachment, a także dodatkowe potwierdzenia WS-Policy i rozszerzenia WSDL 1.1 wprowadzone przez WCF.  
  
 Usługi WCF implementuje specyfikacji WS-Policy i WS-PolicyAttachment przesłane do W3C z ograniczeniami i wyjaśnienia opisanych w tym dokumencie.  
  
 Ten dokument korzysta z prefiksy przestrzeni nazw pokazano w poniższej tabeli.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|WSP (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|WSP (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|Http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|Mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|punkt dystrybucji|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>Rozszerzenia WSDL1.1 WCF  
 Do opisania wymagania sesji kontraktu usługi WCF używa następujące rozszerzenia WSDL1.1.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:Boolean, wskazuje, że ta operacja inicjuje sesję WCF; Wartość domyślna to `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:Boolean, wskazuje, że ta operacja kończy sesję WCF; Wartość domyślna to `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:Boolean, wskazuje, że ten kontrakt wymaga elementu session określone.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>Liczba bloków URI SOAP 1.x HTTP powiązania transportu  
 WCF używa następujących identyfikatorów URI w celu wskazania transportu do zastosowania w przypadku elementów rozszerzenia powiązania WSDL 1.1, SOAP 1.1 i SOAP 1.2.  
  
|Transportu|Identyfikator URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|Usługa MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Nazwane potoki|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Potwierdzenia zasad zaimplementowana przez usługi WCF  
 Oprócz potwierdzeń zasad, które wprowadzono w specyfikacji usług sieci Web (WS-*) i wspomniano w innych częściach niniejszego dokumentu, WCF implementuje następujących potwierdzeń zasad.  
  
|Potwierdzenia zasad|Zasady podmiotu|Opis|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania podstawowego HTTP.|  
|http:HttpDigestAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania Digest protokołu HTTP.|  
|http:HttpNegotiateAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania negocjowania protokołu HTTP.|  
|http:HttpNtlmAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania NTLM HTTP.|  
|msf:Streamed|Punkt końcowy|Punkt końcowy używa ramek komunikat przesyłany strumieniowo. Potwierdzenie jest używany z protokołem Message Framing podane dla transportu, takie jak protokół TCP i nazwane potoki.|  
|msf:SslTransportSecurity|Punkt końcowy|Punkt końcowy używa transport layer security (TLS) z ramek komunikatu.|  
|MSF:WindowsTransportSecurity|Punkt końcowy|Punkt końcowy używa zabezpieczeń dostawcy negocjacji SPNEGO () z ramek komunikatu.|  
|msmq:MsmqBestEffort|Punkt końcowy|Usługa MSMQ optymalnych gwarancji.|  
|MSMQ:MsmqSession|Punkt końcowy|Gwarantuje usługi MSMQ z sesją.|  
|msmq:MsmqVolatile|Punkt końcowy|Volatile usługi MSMQ.|  
|msmq:Authenticated|Punkt końcowy|Uwierzytelnianie jest używane z transportu MSMQ.|  
|msmq:WindowsDomain|Punkt końcowy|Usługa MSMQ korzysta z uwierzytelniania domeny systemu Windows.|  
|cdp:CompositeDuplex|Punkt końcowy|Punkt końcowy korzysta z dwóch oddzielnych odwrotna połączenia transportu dla in i out wiadomości.|  
|Mssp:RsaToken|Zagnieżdżone|Potwierdzenie tokenu klucza RSA. To wymaganie jest zwykle spełniać serializować bezpośrednio jako część klucza informacji w podpisie indosowania klucza RSA.|  
|Mssp:SslContextToken|Zagnieżdżone|Wymaga wykorzystania SecurityContextToken uzyskany przy użyciu binarnej uzgadniania TLS przy użyciu protokołu WS-Trust. Zagnieżdżone potwierdzenia obejmują: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|Zagnieżdżone|Określa wymagania, że żądania tokenu zabezpieczającego (RST) żądania komunikatów [WS-Trust] za pomocą tego powiązania Anuluj [WS-Trust, WS-SC] nie można wysłać do wystawca danego SecurityContextToken. Jeśli potwierdzenie, takie komunikaty żądania nie musi być wysyłane do wystawcy. Jeśli potwierdzenie nie jest obecny, takie komunikaty żądania można przesyłane wystawcy.|  
|Mssp:RequireClientCertificate|Zagnieżdżone|Ten opcjonalny element określa wymaganie certyfikatu klienta mają zostać podane jako część protokołu TLSNEGO. Jeśli potwierdzenie, należy podać certyfikat klienta. Jeśli potwierdzenie nie jest obecny, następnie certyfikat klienta nie należy podawać. Nie można używać poza mssp:SslContextToken potwierdzenie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 [Instrukcje: eksportowanie niestandardowych informacji w formacie WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Instrukcje: importowanie niestandardowych informacji w formacie WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
