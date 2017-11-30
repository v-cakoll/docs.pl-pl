---
title: Reliable Messaging Protocol w wersji 1.0
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d204600682ec8acbc229240c4e1bc859d8ea4d21
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-10"></a>Reliable Messaging Protocol w wersji 1.0
W tym temacie omówiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WS-Reliable Messaging szczegóły implementacji protokołu niezbędne do współpracy przy użyciu transportu HTTP February 2005 (w wersji 1.0). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zgodny ze specyfikacją WS-Reliable Messaging z ograniczeniami i wyjaśnienia opisanego w tym temacie. Należy pamiętać, protokół WS-ReliableMessaging w wersji 1.0 jest zaimplementowana, począwszy od [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 WS-Reliable Messaging February 2005 protokół jest zaimplementowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Dla wygody tematu są używane następujące role:  
  
-   Inicjator: klienta, który inicjuje tworzenia sekwencji WS-Reliable wiadomości  
  
-   Obiekt odpowiadający w trybie: usługa, która odbiera żądania inicjatora  
  
 Ten dokument używa prefiksy i przestrzenie nazw w poniższej tabeli.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|Menedżer zasobów systemu Windows|http://schemas.xmlsoap.org/ws/2005/02/RM|  
|netrm|http://schemas.microsoft.com/ws/2006/05/RM|  
|s|http://www.w3.org/2003/05/SOAP-Envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/Addressing|  
|wsse|http://docs.oasis-open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>Obsługa wiadomości  
  
### <a name="sequence-establishment-messages"></a>Komunikaty ustanowienia sekwencji  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje `CreateSequence` i `CreateSequenceResponse` komunikaty, aby ustanowić sekwencji niezawodny komunikatu. Obowiązują następujące ograniczenia:  
  
-   B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora nie generuje opcjonalny element wygasa w `CreateSequence` wiadomości lub, w przypadku gdy `CreateSequence` komunikat zawiera `Offer` element, opcjonalny `Expires` element w `Offer` element.  
  
-   B1102: Podczas uzyskiwania dostępu do `CreateSequence` wiadomości, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Responder` wysyła i odbiera zarówno `Expires` elementu, jeśli istnieje, ale nie używa ich wartości.  
  
 WS-Reliable Messaging wprowadza `Offer` mechanizmu ustanowienie dwa konwersacji skorelowane sekwencji, które tworzą sesji.  
  
-   R1103: Jeśli `CreateSequence` zawiera `Offer` elementu niezawodnej obsługi komunikatów udzielenia musi zaakceptować sekwencji oraz odpowiadać, podając `CreateSequenceResponse` zawierający `wsrm:Accept` element tworzące dwa skorelowane konwersacji sekwencji lub odrzucić `CreateSequence` żądania.  
  
-   R1104: `SequenceAcknowledgement` i komunikatów aplikacji przepływu w kolejności odwrotnej musi zostać wysłany do `ReplyTo` odwołania do punktu końcowego z `CreateSequence`.  
  
-   R1105: `AcksTo` i `ReplyTo` odwołania do punktu końcowego w `CreateSequence` musi mieć wartości adresów, które odpowiadają octet-wise.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie sprawdza, czy identyfikator URI części `AcksTo` i `ReplyTo` określenia opcji są identyczne, przed utworzeniem sekwencji.  
  
-   R1106: `AcksTo` i `ReplyTo` odwołania do punktu końcowego w `CreateSequence` powinny mieć ten sam zestaw parametrów odwołania.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nie wymusza, ale przyjęto założenie, że [Odwołanie parametry] `AcksTo` i `ReplyTo` na `CreateSequence` są identyczne i używa [Odwołanie parametrów] z `ReplyTo` odwołania do punktu końcowego dla potwierdzeń i odwrotnej sekwencji komunikatów.  
  
-   R1107: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` i przechodzenia w odwrotnej sekwencji komunikatów aplikacji musi zostać wysłany do `ReplyTo` odwołania do punktu końcowego z `CreateSequence`.  
  
-   R1108: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą mechanizmu oferta `[address]` właściwość `wsrm:AcksTo` odwołania do punktu końcowego elementu podrzędnego `wsrm:Accept` elementu `CreateSequenceResponse` musi odpowiadać byte-wise docelowego identyfikatora URI z `CreateSequence`.  
  
-   R1109: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, komunikaty wysyłane przez inicjatora i potwierdzeń wiadomości przez obiekt odpowiadający w trybie muszą zostać przesłane do odwołania do tego samego punktu końcowego.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa WS-Reliable Messaging ustanowienie sesji niezawodnej między Inicjator i obiekt odpowiadający w trybie. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]w implementacji protokołu WS-Reliable Messaging zapewnia niezawodnej sesji dla jednokierunkowe żądanie odpowiedź i pełny dupleks wzorców do obsługi komunikatów. WS-Reliable Messaging `Offer` mechanizmu na `CreateSequence` / `CreateSequenceResponse` pozwala ustanowić dwóch sekwencji skorelowane odwrotnej i zapewnia protokół sesji, które jest odpowiednie dla wszystkich komunikatów punktów końcowych. Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia gwarancję zabezpieczeń takich sesji w tym end-to-end ochronę integralności sesji, jest to możliwe zapewnienie komunikaty kierowane do tej samej strony docierają tego samego miejsca docelowego. Umożliwia to także piggy zapasowy potwierdzeń sekwencji komunikatów aplikacji. W związku z tym ograniczenia R1104, R1105 i R1108 dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Przykład `CreateSequence` wiadomości.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 Przykład `CreateSequenceResponse` wiadomości.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a>Sekwencja  
 Oto lista ograniczeń, które są stosowane do sekwencji:  
  
-   B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje i uzyskuje dostęp do numerów sekwencji. nie jest wyższa niż `xs:long`przez wartość maksymalna włącznie, 9223372036854775807.  
  
-   B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawsze generuje zabudowanych pusta ostatniego komunikatu z akcją http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage identyfikatora URI.  
  
-   B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odbiera, a następnie dostarcza wiadomość z nagłówkiem sekwencji, który zawiera `LastMessage` tak długo, jak identyfikator URI akcji nie jest http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage elementu.  
  
 Przykład nagłówka sekwencji.  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a>Nagłówek AckRequested  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa `AckRequested` nagłówka jako mechanizmu keep-alive. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nie generuje opcjonalny `MessageNumber` elementu. Po otrzymaniu wiadomości z `AckRequested` nagłówek, który zawiera `MessageNumber` elementu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje `MessageNumber` wartości elementu, jak pokazano w poniższym przykładzie.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>Nagłówka SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa mechanizmu nakładka — dla potwierdzeń sekwencji w WS-Reliable Messaging.  
  
-   R1401: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` nagłówka może być zawarta w każdej wiadomości aplikacji przesyłane do określonego adresata.  
  
-   B1402: Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] należy wygenerować potwierdzenia przed odebraniem komunikaty sekwencji (na przykład, aby spełniać `AckRequested` wiadomości), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `SequenceAcknowledgement` nagłówka, który zawiera zakres 0-0, jak pokazano w następującym przykład.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementu, ale obsługuje `Nack` elementów.  
  
### <a name="ws-reliablemessaging-faults"></a>Błędy protokołu WS-ReliableMessaging.  
 Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacji protokołu WS-Reliable Messaging błędów:  
  
-   B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie generuje `MessageNumberRollover` błędów.  
  
-   B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego może generować `CreateSequenceRefused` błędów zgodnie z opisem w specyfikacji.  
  
-   B1503:when punktu końcowego usługi przez nią miejsce osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje dodatkowe `CreateSequenceRefused` fault podrzędny, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a>Protokół WS-Addressing błędów  
 Ponieważ WS-Reliable Messaging korzysta z protokołu WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacji protokołu WS-Reliable Messaging może generować błędy protokołu WS-Addressing. Ta obejmuje sekcji WS-Addressing błędów, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje jawnie w warstwie usługi WS-Reliable Messaging:  
  
-   B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje błędów komunikat adresowania nagłówka wymagane, gdy jest spełniony jeden z następujących czynności:  
  
    -   Brak komunikatu `Sequence` nagłówka i `Action` nagłówka.  
  
    -   A `CreateSequence` Brak komunikatu `MessageId` nagłówka.  
  
    -   A `CreateSequence` Brak komunikatu `ReplyTo` nagłówka.  
  
-   B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje błąd akcja nie jest obsługiwana w odpowiedzi na komunikat, który nie istnieje `Sequence` nagłówka i ma `Action` nagłówek, który nie jest rozpoznawaną w specyfikacji WS-Reliable Messaging.  
  
-   B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje błąd punktu końcowego niedostępne, co wskazuje, czy punkt końcowy nie może przetwarzać sekwencji ustalane na podstawie analizy `CreateSequence` nagłówków adresowych wiadomości.  
  
## <a name="protocol-composition"></a>Protokół kompozycji  
  
### <a name="composition-with-ws-addressing"></a>Kompozycja z protokołu WS-Addressing  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje protokół WS-Addressing dwie wersje: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1.0 zalecenia [WS-ADDR-CORE] i [WS-ADDR — SOAP].  
  
 Podczas uwagi specyfikacji WS-Reliable Messaging tylko WS-Addressing 2004-08 nie uniemożliwia wersji WS-Addressing do użycia. Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2101: zarówno WS-Addressing 2004/08 i WS-Addressing 1.0 mogą być używane z WS-Reliable Messaging.  
  
-   R2102:A jednej wersji WS-Addressing musi używanego w danej sekwencji WS-Reliable Messaging dysków lub para skorelowane przy użyciu sekwencji odwrotnej `wsrm:Offer` mechanizmu.  
  
### <a name="composition-with-soap"></a>Kompozycja z protokołu SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje stosowanie SOAP 1.1 i SOAP 1.2 z WS-Reliable Messaging.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Kompozycja i WS-Security WS-SecureConversation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zapewnia ochronę sekwencji WS-Reliable Messaging przy użyciu zabezpieczenia WS konwersacji bezpieczne transportowych (HTTPS), kompozycji z WS-Security i kompozycji. Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2301: ochrony integralności sekwencji WS-Reliable Messaging oprócz integralności i poufności poszczególne wiadomości [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga, należy użyć zabezpieczenia WS konwersacji.  
  
-   R2302:AWS-Secure Conversation sesji muszą być ustalane przed ustanawianie sequence(s) WS-Reliable Messaging.  
  
-   R2303: Jeśli WS-Reliable Messaging sekwencji okres istnienia przekracza zabezpieczenia WS konwersacji istnienia sesji `SecurityContextToken` ustanowione przy użyciu zabezpieczenia WS konwersacji należy odnawiać przy użyciu odpowiedniego powiązania odnawiania zabezpieczenia WS konwersacji.  
  
-   B2304:ws-niezawodna obsługa komunikatów sekwencji dysków lub para skorelowane odwrotnej sekwencje są zawsze powiązane z jednej sesji WS-SecureConversation.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Źródło generuje `wsse:SecurityTokenReference` element w sekcji rozszerzeń element `CreateSequence` wiadomości.  
  
-   R2305:when składa się z zabezpieczenia WS konwersacji `CreateSequence` wiadomości musi zawierać `wsse:SecurityTokenReference` elementu.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-Reliable potwierdzenia obsługi wiadomości WS-Policy.  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa usługi WS-Reliable Messaging potwierdzenia WS-Policy `wsrm:RMAssertion` do opisywania możliwości punktów końcowych. Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dołącza `wsrm:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementy.  
  
-   B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje następujące właściwości opcjonalne WS-Reliable Messaging potwierdzenia i zapewnia kontrolę nad nimi na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableMessagingBindingElement`:  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     Poniżej przedstawiono przykład.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>Rozszerzenie obsługi wiadomości WS-Reliable sterowania przepływem  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa WS-Reliable Messaging rozszerzalności, aby zapewnić opcjonalne dodatkowe zwiększenie poziomu kontrolę nad przepływ komunikatów sekwencji.  
  
 Przez ustawienie włączone jest sterowanie przepływem `ReliableSessionBindingElement`w `FlowControlEnabled``bool` właściwości `true`. Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B4001: Podczas kontroli przepływu komunikatów niezawodnej jest włączona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` elementu w element możliwość rozszerzania `SequenceAcknowledgement` nagłówka.  
  
-   B4002: Podczas kontroli przepływu komunikatów niezawodnej jest włączona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie wymaga `netrm:BufferRemaining` element znajdować się w `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa `netrm:BufferRemaining` można buforu wskazująca, ile nowe komunikaty niezawodnej obsługi komunikatów docelowego.  
  
-   B4004: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodnej obsługi komunikatów usługi ogranicza liczbę wiadomości przesyłane, gdy aplikację docelową niezawodnej obsługi komunikatów nie może szybko odbierać wiadomości. Komunikaty niezawodnej obsługi komunikatów buforów docelowego i wartości elementu spadnie do 0.  
  
-   B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 włącznie i odczytuje wartości Liczba całkowita między 0 a `xs:int`w `maxInclusive` wartość 214748364 włącznie.  
  
## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 W tej sekcji opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tego zachowania, gdy WS-Reliable Messaging służy do różnych wzorców wymiany wiadomości. Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są traktowane jako:  
  
-   Inicjator nie rozpozna: Inicjator znajduje się za zaporą; Obiekt odpowiadający w trybie wiadomości mogą być dostarczane do inicjatora tylko na odpowiedzi HTTP.  
  
-   Inicjator adresowanego: Inicjator i obiekt odpowiadający mogą być wysyłane żądania HTTP; innymi słowy można ustanowić dwa połączenia HTTP odwrotnej.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednokierunkowe, nie mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji przez jeden kanał HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa żądania HTTP do przekazywania wszystkie komunikaty z usług RMS RMD i odpowiedzi HTTP do przekazywania wszystkich komunikatów z RMD RMS.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z żadne oferty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma żadne oferty przed utworzeniem sekwencji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie odpowiada `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Inicjatora przetwarza potwierdzenia w odpowiedzi wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie zawsze generuje autonomicznej potwierdzenia w odpowiedzi na oba sekwencji i `AckRequested` wiadomości.  
  
#### <a name="terminatesequence-message"></a>Komunikat TerminateSequence  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]traktuje `TerminateSequence` jako Operacja jednokierunkowa, co oznacza odpowiedzi HTTP ma pustej treści i kod stanu HTTP 202.  
  
### <a name="one-way-addressable-initiator"></a>Jednym ze sposobów, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału Http. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z żadne oferty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma żadne oferty przed utworzeniem sekwencji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła obiektu odpowiadającego w trybie `CreateSequenceResponse` wiadomości na żądanie HTTP skierowane z `ReplyTo` odwołania do punktu końcowego.  
  
### <a name="duplex-addressable-initiator"></a>Dupleks, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia pełni asynchroniczne dwukierunkowe wymiany komunikatów za pomocą dwóch sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z ofertą. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma oferty przed utworzeniem sekwencji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]wysyła `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`w `ReplyTo` odwołania do punktu końcowego.  
  
#### <a name="sequence-lifetime"></a>Okres istnienia sekwencji  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]traktuje dwóch sekwencji jako jedna sesja pełni dupleksowych.  
  
 Podczas generowania błędów, które błędów jedną sekwencję [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oczekuje, że zdalny punkt końcowy do obu sekwencji. Podczas odczytywania usterek, które błędów jedną sekwencję [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] błędów zarówno sekwencji.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Zamknij jego sekwencji wychodzących i dalsze przetwarzanie komunikatów na jego przychodzących sekwencji. Z drugiej strony [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] można przetwarzać zamknięcia sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości na jego wychodzące sekwencji.  
  
### <a name="request-reply-non-addressable-initiator"></a>Żądanie odpowiedź, nie mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zapewnia możliwość jednokierunkowych i żądanie odpowiedź wymiany komunikatów za pomocą dwóch sekwencji ponad jeden kanał HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]korzysta z żądania HTTP do przekazywania wiadomości sekwencji żądań, a odpowiedzi HTTP do przekazywania komunikatów sekwencji odpowiedzi.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z ofertą. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma oferty przed utworzeniem sekwencji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie odpowiada `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.  
  
#### <a name="one-way-message"></a>Komunikat jednokierunkowy  
 Protokół wymiany komunikat jednokierunkowy pomyślnego wykonania, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP. `SequenceAcknowledgement` Musi potwierdzić wiadomości przesyłane.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie może odpowiedzieć na żądanie z potwierdzeniem, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.  
  
#### <a name="two-way-messages"></a>Dwa komunikaty sposób  
 Pomyślnie protokół exchange dwukierunkowej wiadomości, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora przesyła żądanie komunikatu sekwencji na żądania HTTP i odbierania komunikatu sekwencji odpowiedzi na odpowiedzi HTTP. Odpowiedzi muszą oni nosić przy sobie `SequenceAcknowledgement` potwierdzeniem wiadomość sekwencji żądanie przesyłane.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie może odpowiedzieć na żądanie z odpowiedzi aplikacji, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.  
  
 Z powodu obecności jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądania i numer sekwencyjny komunikatu odpowiedzi mają nie korelacji.  
  
#### <a name="retrying-replies"></a>Ponawianie próby odpowiedzi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zależy od korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości. W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora nie zatrzymuje ponowieniem próby wykonania żądania komunikatu sekwencji żądanie sekwencji komunikat zostaje potwierdzony, ale raczej po, odpowiedź HTTP niesie potwierdzenia, komunikat użytkownika lub fault. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie ponowi próbę odpowiedzi na etap żądania HTTP żądania, do której są korelowane z odpowiedzi.  
  
#### <a name="lastmessage-exchange"></a>LastMessage programu Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Inicjatora generuje i przesyła pusty zabudowanego ostatniego komunikatu w gałęzi żądania HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]wymaga odpowiedzi, ale ignoruje komunikat odpowiedzi rzeczywistych. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie odpowiada sekwencji żądań zabudowanych pusta ostatniego komunikatu o zabudowanych pusta ostatnią wiadomość w sekwencji odpowiedzi.  
  
 Jeśli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ostatniego komunikatu, w którym Akcja identyfikator URI nie jest http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, otrzymuje obiekt odpowiadający w trybie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odpowiedzi z ostatniego komunikatu. W przypadku protokołu exchange dwukierunkowej wiadomości ostatniego komunikatu niesie komunikat aplikacji; w przypadku protokołu exchange komunikat jednokierunkowy ostatniego komunikatu jest pusta.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie nie wymaga potwierdzenia do zabudowanych pusta ostatnią wiadomość w sekwencji odpowiedzi.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence programu Exchange  
 Gdy wszystkie żądania otrzymali prawidłowy odpowiedzi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora generuje i przesyła sekwencji żądań `TerminateSequence` wiadomości na etap żądania HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]wymaga odpowiedzi, ale ignoruje komunikat odpowiedzi rzeczywistych. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie odpowiada sekwencji żądań `TerminateSequence` wiadomość sekwencji odpowiedzi `TerminateSequence` wiadomości.  
  
 W normalnych zamykania zarówno `TerminateSequence` pełny zakres przenoszenia wiadomości `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>Żądanie/odpowiedź, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia wymiany komunikatów żądanie odpowiedź przy użyciu dwóch sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z ofertą. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma oferty przed utworzeniem sekwencji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]wysyła `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`w `ReplyTo` odwołania do punktu końcowego.  
  
#### <a name="requestreply-correlation"></a>Żądanie i odpowiedź korelacji  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Inicjatora zapewnia wszystkie posiadają komunikaty żądania aplikacji `MessageId` i `ReplyTo` odwołanie do punktu końcowego. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Stosuje inicjatora `CreateSequence` komunikatu `ReplyTo` odwołanie do punktu końcowego na każdy komunikat żądania aplikacji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie wymaga tego żądania przychodzące komunikaty opatrzone `MessageId` i `ReplyTo`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie zapewnia, że identyfikator URI odwołania do punktu końcowego obu `CreateSequence` i wszystkie komunikaty żądania aplikacji są identyczne.
