---
title: Protokoły transakcyjne wersja 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a19329b56bb569a04195b38877a42d635996ff1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184372"
---
# <a name="transaction-protocols-version-10"></a>Protokoły transakcyjne wersja 1.0
Windows Communication Foundation (WCF) wersja 1 implementuje wersję 1.0 protokołów WS-Atomic Transaction i WS-Coordination. Aby uzyskać więcej informacji na temat wersji 1.1, zobacz [Protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Specyfikacja/dokument|Link|  
|-----------------------------|----------|  
|Koordynacja WS|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|WS-AtomicTransakcja|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 Interoperacyjność tych specyfikacji protokołu jest wymagana na dwóch poziomach: między aplikacjami i między menedżerami transakcji (patrz poniższy rysunek). Specyfikacje opisują bardzo szczegółowo formaty wiadomości i wymiany wiadomości dla obu poziomów interoperacyjności. Niektóre zabezpieczenia, niezawodność i kodowania dla wymiany aplikacji do aplikacji mają zastosowanie, jak to zrobić dla regularnej wymiany aplikacji. Jednak pomyślna interoperacyjność między menedżerami transakcji wymaga porozumienia w sprawie określonego powiązania, ponieważ zwykle nie jest skonfigurowany przez użytkownika.  
  
 W tym temacie opisano skład specyfikacji transakcji WS-Atomic (WS-AT) z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji. Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-Coordination, w tym IBM, IONA, Sun Microsystems i innymi.  
  
 Poniższy rysunek przedstawia interoperacyjność między dwoma menedżerami transakcji, Menedżer transakcji 1 i Menedżer transakcji 2, i dwie aplikacje, Application 1 i Application 2:  
  
 ![Zrzut ekranu przedstawiający interakcję między menedżerami transakcji.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Należy wziąć pod uwagę typowy scenariusz WS-Koordynacja/WS-Atomic transaction z jednym inicjatorem (I) i jeden uczestnik (P). Zarówno inicjator, jak i uczestnik mają menedżerów transakcji (odpowiednio ITM i PTM). Zatwierdzanie dwufazowe jest określane jako 2PC w tym temacie.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Odpowiedź na wiadomość aplikacji|  
|2. CreateCoordinationContextResponse|13. Zatwierdzenie (zakończenie)|  
|3. Zarejestruj się (Zakończenie)|14. Przygotowanie (2PC)|  
|4. RegisterResponse|15. Przygotowanie (2PC)|  
|5. Komunikat aplikacji|16. Przygotowane (2PC)|  
|6. CreateCoordinationContext z kontekstem|17. Przygotowane (2PC)|  
|7. Zarejestruj się (trwały)|18. Popełnione (Zakończenie)|  
|8. RegisterResponse|19. Zatwierdzenie (2PC)|  
|9. CreateCoordinationContextResponse|20. Zatwierdzenie (2PC)|  
|10. Zarejestruj się (trwały)|21. Popełnione (2PC)|  
|11. RejestracjaOdpowiedzialność|22. Popełnione (2PC)|  
  
 W tym dokumencie opisano skład specyfikacji WS-AtomicTransaction z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji. Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-Coordination.  
  
 Rysunek i tabela ilustrują cztery klasy wiadomości z punktu widzenia zabezpieczeń:  
  
- Komunikaty aktywacji (CreateCoordinationContext i CreateCoordinationContextResponse).  
  
- Komunikaty rejestracyjne (Zarejestruj się i ZarejestrujOdpowiedzialność)  
  
- Komunikaty protokołu (Przygotowanie, Wycofywanie, Zatwierdzanie, Przerwane i tak dalej).  
  
- Komunikaty aplikacji.  
  
 Pierwsze trzy klasy wiadomości są uważane za komunikaty Menedżera transakcji, a ich konfiguracja powiązania jest opisana w "Application Message Exchange" w dalszej części tego tematu. Czwarta klasa wiadomości jest aplikacją do komunikatów aplikacji i jest opisana w sekcji "Przykłady wiadomości" w dalszej części tego tematu. W tej sekcji opisano powiązania protokołu używane dla każdej z tych klas przez WCF.  
  
 W całym tym dokumencie używane są następujące obszary nazw XML i skojarzone z nimi prefiksy.  
  
|Prefiks|Identyfikator URI obszaru nazw|  
|------------|-------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|Wsa|http://www.w3.org/2004/08/addressing|  
|wscoor|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|wsat|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|t|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|o|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|Xsd|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a>Powiązania menedżera transakcji  
 R1001: Menedżerowie transakcji muszą używać protokołu SOAP 1.1 i WS-Addressing 2004/08 dla wymiany komunikatów WS-Atomic i WS-Coordination.  
  
 Komunikaty aplikacji nie są ograniczone do tych powiązań i są opisane później.  
  
### <a name="transaction-manager-https-binding"></a>Powiązanie HTTPS menedżera transakcji  
 Powiązanie HTTPS menedżera transakcji opiera się wyłącznie na zabezpieczeniach transportu, aby osiągnąć bezpieczeństwo i ustanowić zaufanie między każdą parą nadawca-odbiorca w drzewie transakcji.  
  
#### <a name="https-transport-configuration"></a>Konfiguracja transportu HTTPS  
 Certyfikaty X.509 są używane do ustanawiania tożsamości Menedżera transakcji. Uwierzytelnianie klient/serwer jest wymagane, a autoryzacja klient/serwer pozostaje jako szczegóły implementacji:  
  
- R1111: Certyfikaty X.509 prezentowane za jego przewodowo muszą mieć nazwę podmiotu odpowiadającą w pełni kwalifikowanej nazwie domeny (FQDN) komputera źródłowego.  
  
- B1112: System DNS musi działać między każdą parą nadawca-odbiorca w systemie, aby sprawdzanie nazwy podmiotu X.509 zakończyło się pomyślnie.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Konfiguracja wiązania aktywacji i rejestracji  
 WCF wymaga żądania/odpowiedzi powiązania dupleksu z korelacji za pośrednictwem protokołu HTTPS. (Aby uzyskać więcej informacji na temat korelacji i opisów wzorców wymiany komunikatów żądania/odpowiedzi, zobacz WS-Atomic Transaction, sekcja 8.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfiguracja wiązania protokołu 2PC  
 WCF obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS. Korelacja między wiadomościami pozostaje jako szczegóły implementacji.  
  
 B2131: Implementacje `wsa:ReferenceParameters` muszą obsługiwać zgodnie z opisem w WS-Addressing, aby osiągnąć korelację komunikatów 2PC WCF.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Mieszane powiązanie zabezpieczeń menedżera transakcji  
 Jest to powiązanie alternatywne (tryb mieszany), który używa zabezpieczeń transportu w połączeniu z modelem tokenu wystawionego przez ws-koordynacji dla celów ustanowienia tożsamości.  Aktywacja i rejestracja są tylko elementy, które różnią się między dwoma powiązaniami.  
  
#### <a name="https-transport-configuration"></a>Konfiguracja transportu HTTPS  
 Certyfikaty X.509 są używane do ustanawiania tożsamości Menedżera transakcji. Uwierzytelnianie klient/serwer jest wymagane, a autoryzacja klient/serwer pozostaje jako szczegóły implementacji.  
  
#### <a name="activation-message-binding-configuration"></a>Konfiguracja wiązania komunikatu aktywacji  
 Komunikaty aktywacji zwykle nie uczestniczą w współdziałania, ponieważ zazwyczaj występują między aplikacją a jej lokalnym Menedżerem transakcji.  
  
 B1221: WCF używa dupleksu powiązania HTTPS (opisane w [protokołach wiadomości)](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)dla komunikatów aktywacji. Żądania i odpowiedz wiadomości są skorelowane przy użyciu WS-Addressing 2004/08.  
  
 Specyfikacja transakcji WS-Atomic, sekcja 8, opisuje dalsze szczegóły dotyczące korelacji i wzorców wymiany komunikatów.  
  
- R1222: Po otrzymaniu `CreateCoordinationContext`, koordynator musi `SecurityContextToken` wydać z `STx`powiązanym kluczem tajemnicy . Ten token jest `t:IssuedTokens` zwracany wewnątrz nagłówka zgodnie ze specyfikacją WS-Trust.  
  
- R1223: Jeśli aktywacja występuje w `t:IssuedTokens` istniejącym `SecurityContextToken` kontekście koordynacji, nagłówek `CreateCoordinationContext` z skojarzonym z istniejącym kontekstem musi przepływać w wiadomości.  
  
 Nowy `t:IssuedTokens` nagłówek powinien zostać wygenerowany do `wscoor:CreateCoordinationContextResponse` dołączania do wiadomości wychodzącej.  
  
#### <a name="registration-message-binding-configuration"></a>Konfiguracja powiązania wiadomości rejestracji  
 B1231: WCF używa powiązania HTTPS dwustronnego (opisanego w [protokołach wiadomości).](../../../../docs/framework/wcf/feature-details/messaging-protocols.md) Żądania i odpowiedz wiadomości są skorelowane przy użyciu WS-Addressing 2004/08.  
  
 WS-AtomicTransaction, Sekcja 8, opisuje dalsze szczegóły dotyczące korelacji i opisy wzorców wymiany komunikatów.  
  
 R1232: `wscoor:Register` Wiadomości wychodzące `IssuedTokenOverTransport` muszą korzystać z trybu uwierzytelniania opisanego w [protokołach zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 Element `wsse:Timestamp` musi być podpisany `SecurityContextToken STx` przy użyciu wystawione. Ten podpis jest dowodem posiadania tokenu skojarzonego z określoną transakcją i jest używany do uwierzytelniania uczestnika rejestrowania w transakcji. Komunikat RegistrationResponse jest wysyłany z powrotem za pośrednictwem protokołu HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfiguracja wiązania protokołu 2PC  
 WCF obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS. Korelacja między wiadomościami pozostaje jako szczegóły implementacji.  
  
 B2131: Implementacje `wsa:ReferenceParameters` muszą obsługiwać zgodnie z opisem w WS-Addressing, aby osiągnąć korelację komunikatów 2PC WCF.  
  
## <a name="application-message-exchange"></a>Wymiana komunikatów aplikacji  
 Aplikacje mogą używać dowolnego szczególnego powiązania dla komunikatów aplikacji do aplikacji, o ile powiązanie spełnia następujące wymagania dotyczące zabezpieczeń:  
  
- R2001: Komunikaty aplikacji do aplikacji `t:IssuedTokens` muszą przepływać nagłówek wraz z `CoordinationContext` nagłówkiem wiadomości.  
  
- R2002: Należy zapewnić `t:IssuedToken` integralność i poufność.  
  
 Nagłówek `CoordinationContext` zawiera `wscoor:Identifier`plik . Podczas gdy `xsd:AnyURI` definicja pozwala na użycie zarówno bezwzględnych, jak `wscoor:Identifiers`i względnych identyfikatorów URI, WCF obsługuje tylko , które są bezwzględnymi identyfikatorami URI.  
  
 Jeśli `wscoor:Identifier` jest `wscoor:CoordinationContext` względny identyfikator URI, błędy zostaną zwrócone z transakcyjnych usług WCF.  
  
## <a name="message-examples"></a>Przykłady wiadomości  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>CreateCoordinationContext Wiadomości żądania/odpowiedzi  
 Następujące komunikaty wykonaj wzorzec żądania/odpowiedzi.  
  
#### <a name="createcoordinationcontext"></a>CreateCoordinationContext  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a>CreateCoordinationContextResponse  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a>Komunikaty rejestracyjne  
 Następujące komunikaty są komunikaty rejestracyjne.  
  
#### <a name="register"></a>Zarejestruj  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a>Zarejestruj odpowiedź  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a>Komunikaty protokołu zatwierdzania dwufazowego  
 Poniższy komunikat odnosi się do protokołu zatwierdzania dwufazowego (2PC).  
  
#### <a name="commit"></a>Zatwierdzenie  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a>Komunikaty aplikacji  
 Następujące komunikaty są komunikaty aplikacji.  
  
#### <a name="application-message-request"></a>Żądanie komunikatu aplikacji  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken
          wssu:Id="IA_Certificate"
          ValueType="...#X509v3"
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->
    <e:EncryptedData Id="encrypted_body"
           Type="http://www.w3.org/2001/04/xmlenc#Content"
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
