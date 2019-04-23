---
title: WSDL i zasady
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: caaa54f04bbb10ed3b3dd65b53ace633b88f9126
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151908"
---
# <a name="wsdl-and-policy"></a>WSDL i zasady
W tym temacie omówiono WSDL Windows Communication Foundation (WCF) 1.1, szczegóły implementacji protokołu WS-Policy i WS-PolicyAttachment, a także dodatkowe potwierdzenia WS-Policy i rozszerzenia WSDL 1.1 wprowadzone przez architekturę WCF.  
  
 Usługi WCF implementuje specyfikacji WS-Policy i WS-PolicyAttachment przesłane do W3C z ograniczeniami i wyjaśnienia, opisane w tym dokumencie.  
  
 Ten dokument używa prefiksy i przestrzenie nazw pokazano w poniższej tabeli.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|WSP (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|WSP (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|cdp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>Rozszerzenia WSDL1.1 WCF  
 Usługi WCF używa następujących rozszerzeń WSDL1.1 do opisują wymagania dotyczące sesji kontraktu.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:Boolean, wskazuje, że ta operacja powoduje zainicjowanie sesji usługi WCF. Wartość domyślna to `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:Boolean, wskazuje, że ta operacja kończy sesję WCF. Wartość domyślna to `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:Boolean, wskazuje, że ten kontrakt wymaga elementu session zostać nawiązane.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>Liczba bloków URI protokołu SOAP 1.x HTTP powiązania transportu  
 Usługi WCF używa następujących identyfikatorów URI, aby wskazać transportu do użycia dla elementów rozszerzenia Powiązanie WSDL 1.1, SOAP 1.1 i SOAP 1.2.  
  
|Transport|Identyfikator URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|Usługa MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Nazwane potoki|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Asercji zasad implementowane przez architekturę WCF  
 Oprócz asercji zasad, które wprowadzono w specyfikacji usług sieci Web (WS-*) i wspomniano w innych częściach niniejszego dokumentu, usługi WCF implementuje następujących asercji zasad.  
  
|Potwierdzenie zasad|Zasad tematu|Opis|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania podstawowego HTTP.|  
|http:HttpDigestAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania szyfrowanego protokołu HTTP.|  
|http:HttpNegotiateAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania negocjowania protokołu HTTP.|  
|http:HttpNtlmAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania NTLM HTTP.|  
|msf:Streamed|Punkt końcowy|Punkt końcowy korzysta ramek strumienia komunikatów. Potwierdzenie jest używany przy użyciu protokołu ramek wiadomości podano dla transportu, takich jak TCP i nazwane potoki.|  
|msf:SslTransportSecurity|Punkt końcowy|Punkt końcowy korzysta transport layer security (TLS) za pomocą ramek komunikatu.|  
|msf:WindowsTransportSecurity|Punkt końcowy|Punkt końcowy korzysta zabezpieczeń dostawcy negocjacji SPNEGO () za pomocą ramek komunikatu.|  
|msmq:MsmqBestEffort|Punkt końcowy|Usługa MSMQ gwarancje największej staranności.|  
|msmq:MsmqSession|Punkt końcowy|Gwarantuje usługi MSMQ z sesją.|  
|msmq:MsmqVolatile|Punkt końcowy|MSMQ Volatile.|  
|msmq:Authenticated|Punkt końcowy|Za pomocą transportu MSMQ jest używane uwierzytelnianie.|  
|msmq:WindowsDomain|Punkt końcowy|Usługa MSMQ korzysta z uwierzytelniania Windows domeny.|  
|cdp:CompositeDuplex|Punkt końcowy|Punkt końcowy korzysta z dwóch oddzielnych transportu odwrotna połączeń dla in i out wiadomości.|  
|mssp:RsaToken|Nested|Potwierdzenie tokenu klucza RSA. Wymóg ten jest zazwyczaj spełnione przez klucz RSA serializować bezpośrednio jako część informacji klucza w podpisie zatwierdzania.|  
|mssp:SslContextToken|Nested|Wymaga wykorzystania SecurityContextToken uzyskany przy użyciu binarne uzgadniania TLS przy użyciu protokołu WS-Trust. Zagnieżdżone potwierdzenia obejmują: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|Nested|Określa wymagania, że żądania tokenu zabezpieczającego (RST) żądania komunikatów [WS-Trust] za pomocą powiązania Anuluj [WS-Trust, WS-SC] nie można wysłać do wystawca danego SecurityContextToken. Jeśli ma to potwierdzenie takich komunikatów żądań nie musi być wysyłane do wystawcy. Jeśli ta asercja nie jest obecny, takich komunikatów żądań może otrzymywać wystawcy.|  
|mssp:RequireClientCertificate|Nested|Ten opcjonalny element określa wymagania certyfikatu klienta należy podać w ramach protokołu TLSNEGO. Jeśli ta asercja jest obecna, musi być podana certyfikatu klienta. Jeśli ta asercja nie jest obecny, następnie certyfikat klienta nie jest wymagany. Ta asercja nie mogą być używane poza mssp:SslContextToken.|  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
- [Instrukcje: Eksportowanie niestandardowych plików WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Instrukcje: Import Custom WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
