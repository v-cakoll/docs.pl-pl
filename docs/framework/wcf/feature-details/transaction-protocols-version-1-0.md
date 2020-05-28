---
title: Protokoły transakcyjne wersja 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: 6063c643be4c60e9830a020d10ac9fbcd236dac2
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144776"
---
# <a name="transaction-protocols-version-10"></a>Protokoły transakcyjne wersja 1.0
Windows Communication Foundation (WCF) w wersji 1 implementuje wersję 1,0 transakcji WS-i protokołów koordynacyjnych WS-AT. Aby uzyskać więcej informacji na temat wersji 1,1, zobacz [Protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Specyfikacja/dokument|Link|  
|-----------------------------|----------|  
|Usługa WS-koordynacja|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|Protokół WS-AtomicTransaction|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 Współdziałanie z tymi specyfikacjami protokołu jest wymagane na dwóch poziomach: między aplikacjami i menedżerami transakcji (patrz poniższy rysunek). Specyfikacja zawiera szczegółowe informacje o formatach komunikatów i wymianie komunikatów dla obu poziomów współdziałania. Niektóre zabezpieczenia, niezawodność i kodowanie dla wymiany między aplikacjami mają zastosowanie w przypadku regularnego wymiany aplikacji. Jednak pomyślne współdziałanie między menedżerami transakcji wymaga zawarcia umowy w ramach określonego powiązania, ponieważ zazwyczaj nie jest ona konfigurowana przez użytkownika.  
  
 W tym temacie opisano kompozycję specyfikacji transakcji WS-AT (WS-AT) z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji. Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacyjnych, w tym IBM, IONA, Sun Microsystems i innych.  
  
 Na poniższej ilustracji przedstawiono współdziałanie między dwoma menedżerami transakcji, menedżerem transakcji 1 i menedżerem transakcji 2 oraz dwiema aplikacjami, aplikacjami 1 i aplikacją 2:  
  
 ![Zrzut ekranu przedstawiający interakcję między menedżerami transakcji.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Rozważmy typowy scenariusz transakcji WS-koordynacyjny/WS-Atomowej z jednym inicjatorem (I) i jednym uczestnikiem (P). Inicjator i uczestnik mają menedżerów transakcji (odpowiednio ITM i PTM). Dwufazowe zatwierdzanie jest określane jako 2PC w tym temacie.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. odpowiedź na komunikat aplikacji|  
|2. CreateCoordinationContextResponse|13. zatwierdzenie (zakończenie)|  
|3. Rejestr (uzupełnianie)|14. Przygotuj (2PC)|  
|4. RegisterResponse|15. Prepare (2PC)|  
|5. komunikat aplikacji|16. przygotowane (2PC)|  
|6. CreateCoordinationContext z kontekstem|17. przygotowane (2PC)|  
|7. Zarejestruj (trwałe)|18. zatwierdzone (zakończenie)|  
|8. RegisterResponse|19. zatwierdzenie (2PC)|  
|9. CreateCoordinationContextResponse|20. Zatwierdzanie (2PC)|  
|10. Rejestr (trwałe)|21. zatwierdzone (2PC)|  
|11. RegisterResponse|22. zatwierdzone (2PC)|  
  
 W tym dokumencie opisano kompozycję specyfikacji WS-AtomicTransaction z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji. Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacyjnych.  
  
 Ilustracja i tabela przedstawiają cztery klasy komunikatów z punktu widzenia zabezpieczeń:  
  
- Komunikaty aktywacji (CreateCoordinationContext i CreateCoordinationContextResponse).  
  
- Wiadomości rejestracyjne (Register i RegisterResponse)  
  
- Komunikaty protokołu (przygotowanie, wycofanie, zatwierdzenie, przerwane itd.).  
  
- Komunikaty aplikacji.  
  
 Pierwsze trzy klasy komunikatów są uznawane za komunikaty Menedżera transakcji, a ich konfiguracja powiązań została opisana w sekcji "Wymiana komunikatów aplikacji" w dalszej części tego tematu. Czwarta klasa komunikatu to aplikacja do komunikatów aplikacji i została opisana w sekcji "Przykłady komunikatów" w dalszej części tego tematu. W tej sekcji opisano powiązania protokołów używane dla każdej z tych klas przez funkcję WCF.  
  
 W tym dokumencie są używane następujące przestrzenie nazw XML i skojarzone prefiksy.  
  
|Prefiks|Identyfikator URI przestrzeni nazw|  
|------------|-------------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|WSA|`http://www.w3.org/2004/08/addressing`|  
|wscoor|`http://schemas.xmlsoap.org/ws/2004/10/wscoor`|  
|WSAT|`http://schemas.xmlsoap.org/ws/2004/10/wsat`|  
|t|`http://schemas.xmlsoap.org/ws/2005/02/trust`|  
|o|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd`|  
|XSD|`http://www.w3.org/2001/XMLSchema`|  
  
## <a name="transaction-manager-bindings"></a>Powiązania Menedżera transakcji  
 R1001: menedżerowie transakcji muszą używać protokołu SOAP 1,1 i WS-Addressing 2004/08 dla transakcji WS-i wymiany komunikatów z obsługą protokołu WS-AT.  
  
 Komunikaty aplikacji nie są ograniczone do tych powiązań i są opisane w dalszej części.  
  
### <a name="transaction-manager-https-binding"></a>Powiązanie HTTPS Menedżera transakcji  
 Powiązanie HTTPS Menedżera transakcji polega wyłącznie na zabezpieczeniach transportu, aby zapewnić bezpieczeństwo i ustanowić relację zaufania między każdą parę nadawcy-odbiornik w drzewie transakcji.  
  
#### <a name="https-transport-configuration"></a>Konfiguracja transportu HTTPS  
 Certyfikaty X. 509 są używane do ustanowienia tożsamości Menedżera transakcji. Wymagane jest uwierzytelnianie klient/serwer, a autoryzacja klienta/serwera jest pozostawiana jako szczegóły implementacji:  
  
- R1111: certyfikat X. 509 przedstawiony w sieci musi mieć nazwę podmiotu zgodną z w pełni kwalifikowaną nazwą domeny (FQDN) maszyny źródłowej.  
  
- B1112: usługa DNS musi być funkcjonalna między poszczególnymi parami nadawcy a odbiornikiem w systemie dla nazwy podmiotu X. 509.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Konfiguracja powiązania aktywacji i rejestracji  
 Funkcja WCF wymaga powiązania dwustronnego żądania/odpowiedzi z korelacją za pośrednictwem protokołu HTTPS. (Aby uzyskać więcej informacji na temat korelacji i opisów wzorców wymiany komunikatów żądania/odpowiedzi, zobacz temat transakcja WS-niepodzielna, sekcja 8.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfiguracja powiązania protokołu 2PC  
 Usługa WCF obsługuje jednokierunkowe komunikaty (Datagram) za pośrednictwem protokołu HTTPS. Korelacja wśród komunikatów jest pozostawiana jako szczegóły implementacji.  
  
 B2131: implementacje muszą obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing, aby osiągnąć korelację komunikatów 2PC programu WCF.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Mieszane powiązanie zabezpieczeń programu Transaction Manager  
 Jest to alternatywne powiązanie (w trybie mieszanym), które korzysta z zabezpieczeń transportu połączonej z modelem tokenów wystawionych przez usługę WS-koordynacyjny do celów ustanowienia tożsamości.  Aktywacja i rejestracja są jedynymi elementami, które różnią się między dwoma powiązaniami.  
  
#### <a name="https-transport-configuration"></a>Konfiguracja transportu HTTPS  
 Certyfikaty X. 509 są używane do ustanowienia tożsamości Menedżera transakcji. Wymagane jest uwierzytelnianie klient/serwer, a autoryzacja klienta/serwera jest pozostawiana jako szczegóły implementacji.  
  
#### <a name="activation-message-binding-configuration"></a>Konfiguracja powiązania komunikatów aktywacji  
 Komunikaty o aktywacji zwykle nie uczestniczą w współdziałaniu, ponieważ zazwyczaj występują między aplikacją a jej lokalnym menedżerem transakcji.  
  
 B1221: WCF używa dupleksowego powiązania HTTPS (opisanego w [protokole obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla komunikatów aktywacji. Komunikaty Request i reply są skorelowane przy użyciu protokołu WS-Addressing 2004/08.  
  
 Specyfikacja transakcji WS-niepodzielna, sekcja 8, opis dalszych szczegółowych informacji o korelacji i wzorcach wymiany komunikatów.  
  
- R1222: po odebraniu `CreateCoordinationContext` , koordynator musi wydać `SecurityContextToken` ze skojarzonym kluczem tajnym `STx` . Ten token jest zwracany w `t:IssuedTokens` nagłówku następującej specyfikacji WS-Trust.  
  
- R1223: Jeśli aktywacja odbywa się w istniejącym kontekście koordynacji, `t:IssuedTokens` Nagłówek z `SecurityContextToken` skojarzonym z istniejącym kontekstem musi przepływać w `CreateCoordinationContext` komunikacie.  
  
 W `t:IssuedTokens` celu dołączenia do wiadomości wychodzącej należy wygenerować nowy nagłówek `wscoor:CreateCoordinationContextResponse` .  
  
#### <a name="registration-message-binding-configuration"></a>Konfiguracja powiązania komunikatu rejestracji  
 B1231: WCF używa dupleksowego powiązania HTTPS (opisanego w [protokole obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). Komunikaty Request i reply są skorelowane przy użyciu protokołu WS-Addressing 2004/08.  
  
 WS-AtomicTransaction, sekcja 8, zawiera szczegółowe informacje o korelacji i opisach wzorców wymiany komunikatów.  
  
 R1232: komunikaty wychodzące `wscoor:Register` muszą używać `IssuedTokenOverTransport` trybu uwierzytelniania opisanego w [protokole zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 `wsse:Timestamp`Element musi być podpisany przy użyciu `SecurityContextToken STx` wystawionego elementu. Podpis jest dowodem posiadania tokenu powiązanego z określoną transakcją i jest używany do uwierzytelniania uczestnika rejestracji w transakcji. Wiadomość RegistrationResponse jest wysyłana z powrotem za pośrednictwem protokołu HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfiguracja powiązania protokołu 2PC  
 Usługa WCF obsługuje jednokierunkowe komunikaty (Datagram) za pośrednictwem protokołu HTTPS. Korelacja wśród komunikatów jest pozostawiana jako szczegóły implementacji.  
  
 B2131: implementacje muszą obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing, aby osiągnąć korelację komunikatów 2PC programu WCF.  
  
## <a name="application-message-exchange"></a>Wymiana komunikatów aplikacji  
 Aplikacje mogą korzystać z dowolnego określonego powiązania dla komunikatów aplikacji do aplikacji, o ile powiązanie spełnia następujące wymagania dotyczące zabezpieczeń:  
  
- R2001: komunikaty między aplikacjami muszą przepływać z `t:IssuedTokens` nagłówka wraz z `CoordinationContext` nagłówkiem komunikatu.  
  
- R2002: należy podać integralność i poufność `t:IssuedToken` .  
  
 `CoordinationContext`Nagłówek zawiera `wscoor:Identifier` . Chociaż definicja `xsd:AnyURI` zezwala na używanie bezwzględnych i względnych identyfikatorów URI, WCF obsługuje tylko `wscoor:Identifiers` , które są bezwzględnymi identyfikatorami URI.  
  
 Jeśli `wscoor:Identifier` `wscoor:CoordinationContext` jest WZGLĘDnym identyfikatorem URI, błędy zostaną zwrócone z transakcyjnych usług WCF.  
  
## <a name="message-examples"></a>Przykłady komunikatów  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Komunikaty żądania/odpowiedzi CreateCoordinationContext  
 Poniższe komunikaty obserwują wzorzec żądania/odpowiedzi.  
  
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
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
### <a name="registration-messages"></a>Komunikaty rejestracji  
 Następujące komunikaty są komunikatami rejestracji.  
  
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
  
#### <a name="register-response"></a>Rejestruj odpowiedź  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a>Komunikaty protokołu zatwierdzania dwóch faz  
 Następujący komunikat odnosi się do protokołu zatwierdzania dwufazowego (2PC).  
  
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
 Następujące komunikaty są komunikatami aplikacji.  
  
#### <a name="application-message-request"></a>Komunikat aplikacji — żądanie  
  
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
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
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
