---
title: Protokoły transakcyjne wersja 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: cb12e2dc60771856b0abaf6cb40e24398ce93513
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585736"
---
# <a name="transaction-protocols-version-10"></a>Protokoły transakcyjne wersja 1.0
Windows Communication Foundation (WCF) w wersji 1 implementuje wersji 1.0 protokołów WS-Atomic Transaction i WS-koordynacji. Aby uzyskać więcej informacji o wersji 1.1, zobacz [protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|WS-Coordination|<http://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|WS-AtomicTransaction|<http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 Współdziałanie w specyfikacji protokołu jest wymagany na dwóch poziomach: między aplikacjami i między menedżerowie transakcji (patrz poniższy rysunek). Specyfikacje opisano szczegółowo formaty wiadomości i wiadomości programu exchange na obu poziomach współdziałania. Niektóre bezpieczeństwa, niezawodności i kodowania dla aplikacji do aplikacji programu exchange mają zastosowanie jak w przypadku regularnego aplikacji programu exchange. Pomyślne współdziałanie menedżerowie transakcji wymaga jednak umowy w określonym powiązaniu, ponieważ zwykle nie jest skonfigurowany przez użytkownika.  
  
 W tym temacie opisuje kompozycję specyfikacji WS-Atomic Transaction (WS-AT) z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerowie transakcji. Podejście opisane w niniejszym dokumencie zostały pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacji m.in. IBM IONA, Sun Microsystems i inne.  
  
 Współdziałanie między dwa menedżerowie transakcji transakcji Menedżera 1 i 2 Menedżera transakcji, a dwie aplikacje, aplikacja 1 i 2 aplikacji przedstawiono na poniższym rysunku:  
  
 ![Zrzut ekranu pokazujący menedżerów interakcji między transakcji.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Należy rozważyć typowy scenariusz protokołu WS-koordynacji/WS-Atomic Transaction za pomocą jednego inicjatora (I) i jednego uczestnika (P). Inicjator i uczestnika, który ma menedżerowie transakcji (ITM i PTM, odpowiednio). Dwufazowego, jest nazywana 2PC, w tym temacie.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Odpowiedź komunikatu aplikacji|  
|2. CreateCoordinationContextResponse|13. Zatwierdź (zakończenie)|  
|3. Rejestr (zakończenie)|14. Przygotowywanie (2PC)|  
|4. RegisterResponse|15. Przygotowywanie (2PC)|  
|5. Komunikatu aplikacji|16. Przygotowany (2PC)|  
|6. CreateCoordinationContext z kontekstem|17. Przygotowany (2PC)|  
|7. Rejestr (trwałość)|18. Zatwierdzone (zakończenie)|  
|8. RegisterResponse|19. Zatwierdzania (2PC)|  
|9. CreateCoordinationContextResponse|20. Zatwierdzania (2PC)|  
|10. Rejestr (trwałość)|21. Zatwierdzone (2PC)|  
|11. RegisterResponse|22. Zatwierdzone (2PC)|  
  
 Ten dokument opisuje kompozycję specyfikacji WS-AtomicTransaction z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerowie transakcji. Podejście opisane w tym dokumencie został przetestowany z innymi implementacjami WS-AT i WS-koordynacji.  
  
 Ilustracja i tabela przedstawiają cztery klasy wiadomości z punktu widzenia zabezpieczeń:  
  
- Aktywacja wiadomości (CreateCoordinationContext CreateCoordinationContextResponse).  
  
- Rejestracja wiadomości (Zarejestruj się i RegisterResponse)  
  
- Komunikaty protokołu (przygotowywanie, wycofywanie, zatwierdzania, Aborted i tak dalej).  
  
- Komunikaty aplikacji.  
  
 Pierwszej klasy trzy wiadomości są traktowane jako komunikaty Menedżera transakcji, a ich konfiguracja powiązania jest opisana w "Aplikacji wiadomości programu Exchange" w dalszej części tego tematu. Czwarty klasę wiadomości jest komunikatów aplikacji i zostało opisane w sekcji "Przykłady komunikatu" w dalszej części tego tematu. W tej sekcji opisano powiązania protokołu używany dla każdej z tych klas przez usługę WCF.  
  
 Następujące obszary nazw XML i skojarzone prefiksy są używane w tym dokumencie.  
  
|Prefiks|Identyfikator URI Namespace|  
|------------|-------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|wsa|http://www.w3.org/2004/08/addressing|  
|wscoor|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|wsat|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|t|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|o|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|xsd|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a>Menedżer transakcji powiązania  
 R1001: Menedżerowie transakcji, należy użyć protokołu SOAP 1.1 i WS-Addressing 2004/08 dla protokołu WS-Atomic Transaction i wymiany wiadomości WS-koordynacji.  
  
 Komunikaty aplikacji nie są ograniczone do tych powiązań i są opisane w dalszej części.  
  
### <a name="transaction-manager-https-binding"></a>Menedżer transakcji HTTPS powiązania  
 Powiązanie HTTPS Menedżera transakcji opiera się wyłącznie na zabezpieczenia transportu do osiągnięcia zabezpieczeń i ustanowienia relacji zaufania między sąsiednimi odbiorcy nadawcy w drzewie transakcji.  
  
#### <a name="https-transport-configuration"></a>Konfiguracja transportu HTTPS  
 Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji. Wymagane jest uwierzytelnienie klienta/serwera i klienta/serwera autoryzacji zostanie pozostawiony jako szczegół implementacji:  
  
- R1111: Certyfikaty X.509 przedstawione przez sieć musi mieć nazwę podmiotu, który pasuje do w pełni kwalifikowana nazwa domeny (FQDN) komputera źródłowego.  
  
- B1112: DNS musi działać każda para odbiorcy nadawcy w systemie kontroli nazwy podmiotu X.509 zakończyło się sukcesem.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Aktywacja i powiązań konfiguracji rejestracji  
 Usługi WCF wymaga dwukierunkowego powiązania żądanie/nietypizowana odpowiedź z korelacją za pośrednictwem protokołu HTTPS. (Aby uzyskać więcej informacji na temat korelacji i opisy wzorców żądanie/nietypizowana odpowiedź wiadomości programu exchange, zobacz WS-Atomic Transaction, sekcja 8).  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfiguracja powiązania protokołu 2PC  
 Usługi WCF obsługuje wiadomości jednokierunkowe (datagram) przy użyciu protokołu HTTPS. Korelacja między wiadomości zostanie pozostawiony jako szczegółowo opisuje implementacja.  
  
 B2131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing do osiągnięcia korelacji wiadomości 2PC firmy WCF.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Menedżer transakcji mieszane powiązanie zabezpieczeń  
 Jest to alternatywny (tryb mieszany) powiązanie zabezpieczenia transportu używana w połączeniu z modelem usługi WS-koordynacji wystawionego tokenu potrzeby określania tożsamości.  Aktywacja i rejestracja są tylko elementy, które różnią się między dwa powiązania.  
  
#### <a name="https-transport-configuration"></a>Konfiguracja transportu HTTPS  
 Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji. Wymagane jest uwierzytelnienie klienta/serwera i klienta/serwera autoryzacji zostanie pozostawiony jako szczegółowo opisuje implementacja.  
  
#### <a name="activation-message-binding-configuration"></a>Konfiguracja powiązania komunikatów aktywacji  
 Komunikaty o aktywacji zwykle nie uczestniczą w współdziałanie ponieważ występują najczęściej między aplikacją a swój lokalny Menedżer transakcji.  
  
 B1221: Dwukierunkowego powiązania HTTPS korzysta z usługi WCF (opisanego w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla wiadomości aktywacji. Skorelowane żądanie i odpowiedź przy użyciu usługi WS-Addressing 2004/08.  
  
 Specyfikacja WS-Atomic Transaction, sekcja 8 opisano dalsze szczegółowe informacje dotyczące korelacji i wzorców wymiany komunikatów.  
  
- R1222: Odebrane `CreateCoordinationContext`, należy wygenerować koordynator `SecurityContextToken` z skojarzony klucz tajny `STx`. Ten token jest zwracany w `t:IssuedTokens` nagłówka następujące specyfikację WS-Trust.  
  
- R1223: Jeśli aktywacja odbywa się w ramach istniejącego kontekstu koordynacji, `t:IssuedTokens` nagłówek o `SecurityContextToken` skojarzony z istniejącym kontekście musi przepływać ze `CreateCoordinationContext` wiadomości.  
  
 Nowy `t:IssuedTokens` musi zostać wygenerowany nagłówek do dołączania do wychodzącej `wscoor:CreateCoordinationContextResponse` wiadomości.  
  
#### <a name="registration-message-binding-configuration"></a>Konfiguracja powiązania komunikat rejestracji  
 B1231: Dwukierunkowego powiązania HTTPS korzysta z usługi WCF (opisanego w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). Skorelowane żądanie i odpowiedź przy użyciu usługi WS-Addressing 2004/08.  
  
 WS-AtomicTransaction, 8 sekcji, w tym artykule opisano dalsze szczegółowe informacje o korelacji i opisy wzorców wiadomości programu exchange.  
  
 R1232: Wychodzące `wscoor:Register` wiadomości należy użyć `IssuedTokenOverTransport` tryb uwierzytelniania opisanego w [protokołów zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 `wsse:Timestamp` Element musi być podpisany przy użyciu `SecurityContextToken STx` wydane. Ta sygnatura jest dowód przesyłany tokenu skojarzone z danej transakcji i jest używany do uwierzytelniania uczestnik rejestrowanie w transakcji. RegistrationResponse wiadomości jest ponownie przy użyciu protokołu HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfiguracja powiązania protokołu 2PC  
 Usługi WCF obsługuje wiadomości jednokierunkowe (datagram) przy użyciu protokołu HTTPS. Korelacja między wiadomości zostanie pozostawiony jako szczegółowo opisuje implementacja.  
  
 B2131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing do osiągnięcia korelacji wiadomości 2PC firmy WCF.  
  
## <a name="application-message-exchange"></a>Wymiana komunikatów w aplikacji  
 Aplikacje są bezpłatne korzystanie z dowolnego określonego powiązania dla wiadomości w aplikacji do aplikacji, tak długo, jak wiązanie spełnia następujące wymagania dotyczące zabezpieczeń:  
  
- R2001: Komunikaty aplikacji do aplikacji musi przepływać `t:IssuedTokens` nagłówka wraz z `CoordinationContext` w nagłówku komunikatu.  
  
- R2002: Integralności i poufności `t:IssuedToken` musi zostać podana.  
  
 `CoordinationContext` Nagłówek zawiera `wscoor:Identifier`. Podczas gdy definicja `xsd:AnyURI` umożliwia korzystanie z identyfikatorów URI względne i bezwzględne WCF obsługuje tylko `wscoor:Identifiers`, które są bezwzględne identyfikatorów URI.  
  
 Jeśli `wscoor:Identifier` z `wscoor:CoordinationContext` jest względny identyfikator URI, błędy, które zostaną zwrócone z transakcji usługi WCF.  
  
## <a name="message-examples"></a>Przykłady komunikatów  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Komunikatów żądań/odpowiedzi CreateCoordinationContext  
 Następujące komunikaty wykonaj wzorzec żądań/odpowiedzi.  
  
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
  
### <a name="registration-messages"></a>Rejestracja wiadomości  
 Następujące komunikaty są komunikatów rejestracji.  
  
#### <a name="register"></a>Rejestruj  
  
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
  
#### <a name="register-response"></a>Rejestrowanie odpowiedzi  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a>Dwóch faza zatwierdzania protokołu komunikatów  
 Następujący komunikat o odnosi się do Protokół dwufazowego (2PC).  
  
#### <a name="commit"></a>Zatwierdzenia  
  
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
 Następujące komunikaty są komunikatów aplikacji.  
  
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
