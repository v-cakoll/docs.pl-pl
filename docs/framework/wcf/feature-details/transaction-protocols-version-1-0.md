---
title: "Protokoły transakcyjne wersja 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e616f989416fcee77caa9b9a5d87cfa6812eab32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols-version-10"></a>Protokoły transakcyjne wersja 1.0
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Wersja 1 implementuje wersji 1.0 protokołów WS-Atomic Transaction i koordynacji WS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]w wersji 1.1, zobacz [protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|Koordynacji WS|http://msdn.microsoft.com/ws/2005/08/ws-Coordination/|  
|WS-AtomicTransaction|http://msdn.microsoft.com/ws/2005/08/WS-AtomicTransaction/|  
  
 Współdziałanie z tymi specyfikacjami protokołu jest wymagany na dwa poziomy: między aplikacjami i między menedżerowie transakcji (zobacz poniższą ilustrację). Specyfikacje opisano szczegółowo formaty wiadomości i wiadomości programu exchange na obu poziomach współdziałania. Niektóre bezpieczeństwa, niezawodności i kodowania dla aplikacji do aplikacji programu exchange mają zastosowanie tak samo, jak dla programu exchange regularne aplikacji. Pomyślne współdziałanie menedżerowie transakcji wymaga jednak umowy dla określonego powiązania, ponieważ zwykle nie jest skonfigurowany przez użytkownika.  
  
 W tym temacie opisuje kompozycji specyfikacji WS-Atomic Transaction (WS-AT) z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerami transakcji. Podejście opisane w niniejszym dokumencie zostały pomyślnie przetestowane z innych implementacji protokołu WS-AT i koordynacji WS tym IBM, IONA Sun Microsystems i inne.  
  
 Na poniższym rysunku przedstawiono współdziałanie między dwa menedżerowie transakcji transakcji Menedżera 1 i 2 Menedżera transakcji, a dwie aplikacje aplikacji 1 i 2 aplikacji.  
  
 ![Protokoły transakcji](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")  
  
 Należy wziąć pod uwagę typowy scenariusz WS-koordynacji/protokołu WS-AT z jednego inicjatora (I) i jednego uczestnika (P). Inicjator i uczestnika ma menedżerowie transakcji (ITM i PTM, odpowiednio). Dwufazowe nazywa się 2PC w tym temacie.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Odpowiedzi na komunikat aplikacji|  
|2. CreateCoordinationContextResponse|13. Zatwierdź (zakończenia)|  
|3. Rejestr (zakończenia)|14. Przygotowanie (2PC)|  
|4. RegisterResponse|15. Przygotowanie (2PC)|  
|5. Komunikat aplikacji|16. Przygotowane (2PC)|  
|6. CreateCoordinationContext z kontekstem|17. Przygotowane (2PC)|  
|7. Rejestr (niezawodny)|18. Zatwierdzone (zakończenia)|  
|8. RegisterResponse|19. Zatwierdź (2PC)|  
|9. CreateCoordinationContextResponse|20. Zatwierdź (2PC)|  
|10. Rejestr (niezawodny)|21. Zatwierdzone (2PC)|  
|11. RegisterResponse|22. Zatwierdzone (2PC)|  
  
 Ten dokument opisuje kompozycji specyfikacji WS-AtomicTransaction z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerami transakcji. Podejście opisane w tym dokumencie zostały pomyślnie przetestowane z innych implementacji protokołu WS-AT i koordynacji WS.  
  
 Ilustracja i tabela przedstawiono cztery rodzaje komunikaty z punktu widzenia zabezpieczeń:  
  
-   Aktywacja wiadomości (CreateCoordinationContext i CreateCoordinationContextResponse).  
  
-   Rejestracja wiadomości (rejestr i RegisterResponse)  
  
-   Komunikaty protokołu (przygotowanie, wycofanie, zatwierdzania, przerwane i tak dalej).  
  
-   Komunikatów aplikacji.  
  
 Pierwszy klas trzy wiadomości są traktowane jako wiadomości Menedżera transakcji i ich konfiguracja powiązania jest opisany w "Wymianie wiadomości aplikacji" w dalszej części tego tematu. Czwarty klasę wiadomości jest komunikatów aplikacji i jest opisana w sekcji "Komunikat przykłady" w dalszej części tego tematu. W tej sekcji opisano powiązania protokołu używane dla każdego z tych klas przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Następujące obszary nazw XML i prefiksy skojarzone są używane w tym dokumencie.  
  
|Prefiks|Identyfikator URI Namespace|  
|------------|-------------------|  
|S11|http://schemas.xmlsoap.org/SOAP/Envelope|  
|wsa|http://www.w3.org/2004/08/Addressing|  
|wscoor|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|WSAT|http://schemas.xmlsoap.org/ws/2004/10/WSAT|  
|t|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|O|http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-wssecurity-secext-1.0.xsd|  
|XSD|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a>Menedżer transakcji powiązania  
 R1001: Menedżerowie transakcji należy użyć protokołu SOAP 1.1 i WS-Addressing 2004/08 dla protokołu WS-AT i wymiany wiadomości WS-koordynacji.  
  
 Komunikaty aplikacji nie są ograniczone do tych powiązań i opisano później.  
  
### <a name="transaction-manager-https-binding"></a>Powiązanie HTTPS Menedżera transakcji  
 Powiązanie HTTPS Menedżera transakcji korzysta wyłącznie z zabezpieczeń transportu, aby osiągnąć zabezpieczeń i ustanowienia relacji zaufania między każda para odbiornika nadawcy w drzewie transakcji.  
  
#### <a name="https-transport-configuration"></a>Konfiguracja HTTPS transportu  
 Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji. Wymagane jest uwierzytelnienie klienta i serwera, a klient/serwer autoryzacji pozostaje szczegółów implementacji:  
  
-   R1111: Certyfikatów X.509 przedstawianych przez sieć musi mieć nazwę podmiotu, która jest zgodna z w pełni kwalifikowaną nazwę (FQDN) komputera źródłowego.  
  
-   B1112: DNS musi być funkcjonalności każda para odbiornika nadawcy w systemie kontroli nazwa podmiotu X.509 powiodło się.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Aktywacja i rejestracja powiązania konfiguracji  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]wymaga dwukierunkowego powiązania żądania/odpowiedzi z korelacją za pośrednictwem protokołu HTTPS. (Aby uzyskać więcej informacji na temat korelacji i opisy wzorców wymiany wiadomości żądania/odpowiedzi, zobacz WS-Atomic Transaction, sekcja 8).  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfiguracja powiązania protokołu 2PC  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS. Szczegóły implementacji pozostaje korelacji między wiadomości.  
  
 B2131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing, aby osiągnąć korelacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]firmy 2PC wiadomości.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Menedżer transakcji mieszanym powiązania zabezpieczeń  
 Jest to alternatywny (tryb mieszany) powiązanie zabezpieczenia transportu używa połączeniu z modelem koordynacji WS wystawionego tokenu na potrzeby określania tożsamości.  Aktywacji i rejestracji są tylko elementy, które różnią się między dwa powiązania.  
  
#### <a name="https-transport-configuration"></a>Konfiguracja HTTPS transportu  
 Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji. Wymagane jest uwierzytelnienie klienta i serwera, a klient/serwer autoryzacji pozostaje szczegóły implementacji.  
  
#### <a name="activation-message-binding-configuration"></a>Konfiguracja powiązania komunikat aktywacji  
 Aktywacja komunikaty zwykle nie uczestniczą w współdziałanie ponieważ zwykle występują między aplikacją a jego lokalnego Menedżera transakcji.  
  
 B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa dwukierunkowego powiązania HTTPS (opisany w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla wiadomości aktywacji. Za pomocą usługi WS-Addressing 2004/08 są skorelowane żądanie i odpowiedź.  
  
 Specyfikacja WS-Atomic Transaction, 8 sekcji opisano dalsze szczegóły dotyczące korelacji i wzorce wymiany wiadomości.  
  
-   R1222: odebrane `CreateCoordinationContext`, należy wygenerować koordynator `SecurityContextToken` z skojarzony klucz tajny `STx`. Token ten jest zwracany wewnątrz `t:IssuedTokens` nagłówka następującej specyfikacji WS-Trust.  
  
-   R1223: W przypadku aktywacji w ramach istniejącego kontekstu koordynacji `t:IssuedTokens` nagłówek o `SecurityContextToken` skojarzony z istniejącym kontekstu musi przepływać na `CreateCoordinationContext` wiadomości.  
  
 Nowy `t:IssuedTokens` nagłówka ma być generowany dla dołączania do wychodzącej `wscoor:CreateCoordinationContextResponse` wiadomości.  
  
#### <a name="registration-message-binding-configuration"></a>Konfiguracja powiązania komunikatu rejestracji  
 B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa dwukierunkowego powiązania HTTPS (opisany w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). Za pomocą usługi WS-Addressing 2004/08 są skorelowane żądanie i odpowiedź.  
  
 WS-AtomicTransaction, 8 sekcji, w tym artykule opisano dodatkowe szczegóły dotyczące korelacji i opisy wzorców wymiany wiadomości.  
  
 R1232: Wychodzące `wscoor:Register` komunikaty muszą używać `IssuedTokenOverTransport` tryb uwierzytelniania opisanego w [protokołów zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 `wsse:Timestamp` Elementu muszą być podpisane przy użyciu `SecurityContextToken``STx` wystawione. Podpis jest potwierdzenie posiadania token skojarzony z określonej transakcji i jest używany do uwierzytelniania uczestnika rejestracji w transakcji. RegistrationResponse wiadomości jest ponownie przy użyciu protokołu HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfiguracja powiązania protokołu 2PC  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS. Szczegóły implementacji pozostaje korelacji między wiadomości.  
  
 B2131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing, aby osiągnąć korelacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]firmy 2PC wiadomości.  
  
## <a name="application-message-exchange"></a>Komunikat aplikacji programu Exchange  
 Aplikacje mogą użyć dowolnego określonego powiązania dla komunikatów aplikacji do aplikacji, tak długo, jak powiązania spełnia następujące wymagania dotyczące zabezpieczeń:  
  
-   R2001: Komunikatów aplikacji do aplikacji musi przepływać `t:IssuedTokens` nagłówka wraz z programem `CoordinationContext` w nagłówku wiadomości.  
  
-   R2002: Integralności i poufności `t:IssuedToken` należy podać.  
  
 `CoordinationContext` Nagłówek zawiera `wscoor:Identifier`. Podczas definicji `xsd:AnyURI` umożliwia wykorzystanie bezwzględne i względne identyfikatory URI, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje tylko `wscoor:Identifiers`, będące bezwzględny identyfikator URI.  
  
 Jeśli `wscoor:Identifier` z `wscoor:CoordinationContext` jest względnym identyfikatorem URI, błędów, które zostaną zwrócone z transakcyjnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.  
  
## <a name="message-examples"></a>Przykłady wiadomości  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Komunikaty CreateCoordinationContext żądania/odpowiedzi  
 Następujące komunikaty wykonaj wzorzec żądań i odpowiedzi.  
  
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
 Następujące komunikaty są komunikaty rejestracji.  
  
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
  
#### <a name="register-response"></a>Zarejestruj odpowiedzi  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a>Dwa komunikaty protokołu zatwierdzania fazy  
 Następujący komunikat odnosi się do protokołu dwufazowego (2PC).  
  
#### <a name="commit"></a>Zatwierdź  
  
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
  
### <a name="application-messages"></a>Komunikatów aplikacji  
 Następujące komunikaty są komunikatów aplikacji.  
  
#### <a name="application-message-request"></a>Komunikat żądania aplikacji  
  
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
