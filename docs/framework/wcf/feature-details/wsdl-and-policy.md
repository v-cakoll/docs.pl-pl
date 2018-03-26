---
title: WSDL i zasady
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd52e36199fc2412abb003d530dd5614cda8049b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="wsdl-and-policy"></a>WSDL i zasady
W tym temacie omówiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WSDL 1.1, szczegóły implementacji protokołu WS-Policy i WS-PolicyAttachment, a także dodatkowe potwierdzenia WS-Policy i wprowadzone przez rozszerzenia WSDL 1.1 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje specyfikacji WS-Policy i WS-PolicyAttachment przesłane do W3C z ograniczeniami i wyjaśnienia opisanych w tym dokumencie.  
  
 Ten dokument korzysta z prefiksy przestrzeni nazw pokazano w poniższej tabeli.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|WSP (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|WSP (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|Http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|cdp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>Rozszerzenia WSDL1.1 WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] następujące rozszerzenia WSDL1.1 nawiązywał opisano wymagania sesji kontraktu.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 Wskazuje xs:Boolean, ta operacja inicjuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sesji; wartość domyślna wartość to `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 Wskazuje xs:Boolean, ta operacja kończy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sesji; wartość domyślna wartość to `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:Boolean, wskazuje, że ten kontrakt wymaga elementu session określone.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>Liczba bloków URI SOAP 1.x HTTP powiązania transportu  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa następujących identyfikatorów URI w celu wskazania transportu do zastosowania w przypadku elementów rozszerzenia powiązania WSDL 1.1, SOAP 1.1 i SOAP 1.2.  
  
|Transportu|Identyfikator URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|Usługa MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Nazwane potoki|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Potwierdzenia zasad zaimplementowana przez usługi WCF  
 Oprócz potwierdzeń zasad, które wprowadzono w specyfikacji usług sieci Web (WS-*) i jest to wymienione w innych częściach niniejszego dokumentu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje następujących potwierdzeń zasad.  
  
|Potwierdzenia zasad|Zasady podmiotu|Opis|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania podstawowego HTTP.|  
|http:HttpDigestAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania Digest protokołu HTTP.|  
|http:HttpNegotiateAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania negocjowania protokołu HTTP.|  
|http:HttpNtlmAuthentication|Punkt końcowy|Punkt końcowy korzysta z uwierzytelniania NTLM HTTP.|  
|msf:Streamed|Punkt końcowy|Punkt końcowy używa ramek komunikat przesyłany strumieniowo. Potwierdzenie jest używany z protokołem Message Framing podane dla transportu, takie jak protokół TCP i nazwane potoki.|  
|msf:SslTransportSecurity|Punkt końcowy|Punkt końcowy używa transport layer security (TLS) z ramek komunikatu.|  
|msf:WindowsTransportSecurity|Punkt końcowy|Punkt końcowy używa zabezpieczeń dostawcy negocjacji SPNEGO () z ramek komunikatu.|  
|msmq:MsmqBestEffort|Punkt końcowy|Usługa MSMQ optymalnych gwarancji.|  
|MSMQ:MsmqSession|Punkt końcowy|Gwarantuje usługi MSMQ z sesją.|  
|msmq:MsmqVolatile|Punkt końcowy|MSMQ Volatile.|  
|msmq:Authenticated|Punkt końcowy|Uwierzytelnianie jest używane z transportu MSMQ.|  
|msmq:WindowsDomain|Punkt końcowy|Usługa MSMQ korzysta z uwierzytelniania domeny systemu Windows.|  
|cdp:CompositeDuplex|Punkt końcowy|Punkt końcowy korzysta z dwóch oddzielnych odwrotna połączenia transportu dla in i out wiadomości.|  
|Mssp:RsaToken|Zagnieżdżone|Potwierdzenie tokenu klucza RSA. To wymaganie jest zwykle spełniać serializować bezpośrednio jako część klucza informacji w podpisie indosowania klucza RSA.|  
|mssp:SslContextToken|Zagnieżdżone|Wymaga wykorzystania SecurityContextToken uzyskany przy użyciu binarnej uzgadniania TLS przy użyciu protokołu WS-Trust. Zagnieżdżone potwierdzenia obejmują: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|Zagnieżdżone|Określa wymagania, że żądania tokenu zabezpieczającego (RST) żądania komunikatów [WS-Trust] za pomocą tego powiązania Anuluj [WS-Trust, WS-SC] nie można wysłać do wystawca danego SecurityContextToken. Jeśli potwierdzenie, takie komunikaty żądania nie musi być wysyłane do wystawcy. Jeśli potwierdzenie nie jest obecny, takie komunikaty żądania można przesyłane wystawcy.|  
|mssp:RequireClientCertificate|Zagnieżdżone|Ten opcjonalny element określa wymaganie certyfikatu klienta mają zostać podane jako część protokołu TLSNEGO. Jeśli potwierdzenie, należy podać certyfikat klienta. Jeśli potwierdzenie nie jest obecny, następnie certyfikat klienta nie należy podawać. Nie można używać poza mssp:SslContextToken potwierdzenie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 [Instrukcje: eksportowanie niestandardowych informacji w formacie WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Instrukcje: importowanie niestandardowych informacji w formacie WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
