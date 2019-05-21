---
title: Reliable Messaging Protocol w wersji 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: db4761efb34e7436ae54819b8e5056c732bd2fab
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959949"
---
# <a name="reliable-messaging-protocol-version-10"></a>Reliable Messaging Protocol w wersji 1.0
W tym temacie omówiono szczegóły dotyczące implementacji usług Windows Communication Foundation (WCF) dla protokołu WS-Reliable Messaging protocol February 2005 (w wersji 1.0) niezbędne do współpracy przy użyciu protokołu HTTP. Usługi WCF następuje specyfikacji WS-Reliable Messaging z ograniczeniami i wyjaśnienia szczegółowo opisane w tym temacie. Należy pamiętać, że protokół WS-ReliableMessaging w wersji 1.0 jest wykonywane począwszy od WinFX.  
  
 WS-Reliable Messaging February 2005 protokołu jest zaimplementowana w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Dla wygody tematu są używane następujące role:  
  
- Inicjator: klienta, który inicjuje WS-Reliable komunikat tworzenia sekwencji  
  
- Obiekt odpowiadający w trybie: usługa, która odbiera żądania inicjatora  
  
 Ten dokument używa prefiksy i przestrzenie nazw w poniższej tabeli.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|Menedżer zasobów systemu Windows|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>Obsługa komunikatów  
  
### <a name="sequence-establishment-messages"></a>Komunikaty do określania sekwencji  
 Implementuje WCF `CreateSequence` i `CreateSequenceResponse` komunikaty, aby ustanowić sekwencji niezawodnych komunikatów. Obowiązują następujące ograniczenia:  
  
- B1101: Inicjator WCF nie generuje opcjonalny element wygasa w `CreateSequence` komunikatu lub w przypadkach podczas `CreateSequence` wiadomość zawiera `Offer` element, opcjonalny `Expires` elementu w `Offer` elementu.  
  
- B1102: Podczas uzyskiwania dostępu do `CreateSequence` komunikatów WCF`Responder` wysyła i odbiera zarówno `Expires` elementów, jeśli istnieje, ale nie używa ich wartości.  
  
 WS-Reliable Messaging wprowadza `Offer` mechanizm nawiązać dwa konwersacji skorelowany sekwencji, które tworzą sesji.  
  
- R1103: Jeśli `CreateSequence` zawiera `Offer` elemencie Reliable Messaging obiektu odpowiadającego w trybie musi zaakceptować sekwencji i elastyczniejsze `CreateSequenceResponse` zawierający `wsrm:Accept` elementu tworzących dwa skorelowane konwersacji sekwencji lub odrzucić `CreateSequence`żądania.  
  
- R1104: `SequenceAcknowledgement` i komunikatów aplikacji przepływają w odwrotnej kolejności musi zostać wysłany do `ReplyTo` odwołania do endpoint `CreateSequence`.  
  
- R1105: `AcksTo` i `ReplyTo` punktu końcowego, który odwołuje się w `CreateSequence` musi mieć wartości adresów, które odpowiadają octet-wise.  
  
     Obiekt odpowiadający w trybie WCF — sprawdza, czy identyfikator URI części `AcksTo` i `ReplyTo` określenia opcji są identyczne, przed utworzeniem sekwencji.  
  
- R1106: `AcksTo` i `ReplyTo` odwołania do punktu końcowego w `CreateSequence` powinny mieć ten sam zestaw parametrów odwołania.  
  
     Usługi WCF nie wymusza, ale przyjmuje wartość tego [dokumentacja parametry] `AcksTo` i `ReplyTo` na `CreateSequence` są identyczne i używa [dokumentacja parametry] z `ReplyTo` odwołania do punktu końcowego dla Potwierdzanie i komunikaty sekwencji prawdą.  
  
- R1107: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` i komunikatów aplikacji przepływają w przeciwny sekwencji musi zostać wysłany do `ReplyTo` odwołania do endpoint `CreateSequence`.  
  
- R1108: Gdy dwie sekwencje prawdą są określane przy użyciu mechanizmu oferty `[address]` właściwość `wsrm:AcksTo` odwołania do punktu końcowego elementu podrzędnego `wsrm:Accept` elementu `CreateSequenceResponse` musi odpowiadać byte-wise miejsca docelowego identyfikatora URI `CreateSequence`.  
  
- R1109: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, komunikaty wysyłane przez inicjatora i potwierdzeń komunikatów przez obiekt odpowiadający w trybie muszą być wysyłane do tego samego odwołania do punktu końcowego.  
  
     Usługi WCF używa do ustanawiania niezawodnych sesji między inicjatora i Responder WS-Reliable Messaging. Implementacja WS-Reliable Messaging WCF firmy udostępnia niezawodnej sesji, jednokierunkowe "żądanie-odpowiedź" i pełny dupleks wzorce obsługi wiadomości. WS-Reliable Messaging `Offer` mechanizm na `CreateSequence` / `CreateSequenceResponse` umożliwia ustanawianie dwie sekwencje skorelowany prawdą i zapewnia protokół sesji, która jest odpowiednia dla wszystkich komunikatów z punktami końcowymi. Ponieważ WCF daje gwarancję zabezpieczeń dla sesji, w tym ochronę end-to-end spójność sesji, jest praktyczne w celu zapewnienia, że komunikaty przeznaczone do tej samej strony docierają tego samego miejsca docelowego. Dzięki temu również piggy zapasowy potwierdzeń sekwencji na wiadomościach aplikacji. W związku z tym ograniczenia R1104 R1105 i R1108 mają zastosowanie do programu WCF.  
  
 Przykładem `CreateSequence` wiadomości.  
  
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
  
 Przykładem `CreateSequenceResponse` wiadomości.  
  
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
  
### <a name="sequence"></a>Sequence  
 Oto lista ograniczeń, które dotyczą sekwencji:  
  
- Generuje B1201:WCF i uzyskuje dostęp do sekwencji numerów nie jest wyższa niż `xs:long`firmy maksymalną wartość włącznie 9223372036854775807.  
  
- B1202:WCF zawsze generuje zabudowanych pusta ostatni komunikat z identyfikator URI akcji z `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.  
  
- B1203: Usługi WCF odbiera i zapewnia komunikat z nagłówkiem sekwencji, który zawiera `LastMessage` tak długo, jak identyfikator URI akcji nie jest elementem `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.  
  
 Przykład nagłówek sekwencji.  
  
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
  
### <a name="ackrequested-header"></a>Nagłówek bloku nagłówka AckRequested  
 Korzysta z usługi WCF `AckRequested` nagłówek jako mechanizm utrzymywania aktywności. Usługi WCF nie generuje opcjonalnego `MessageNumber` elementu. Po odebraniu komunikatu z `AckRequested` nagłówek, który zawiera `MessageNumber` ignoruje WCF elementu `MessageNumber` wartości elementu, jak pokazano w poniższym przykładzie.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>Nagłówek SequenceAcknowledgement  
 Usługi WCF używa mechanizmu nakładka potwierdzeń sekwencji w WS-Reliable Messaging.  
  
- R1401: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` nagłówek może być zawarta w każdy komunikat aplikacji przekazywane do określonego adresata.  
  
- B1402: Gdy WCF musi wygenerować potwierdzenia przed odebraniem wiadomości dowolnej sekwencji (na przykład, aby spełnić `AckRequested` wiadomości), generuje WCF `SequenceAcknowledgement` nagłówek, który zawiera zakres 0-0, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
- B1403: Usługi WCF nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementu, ale obsługuje `Nack` elementów.  
  
### <a name="ws-reliablemessaging-faults"></a>Błędy WS-ReliableMessaging  
 Oto lista ograniczeń, które są stosowane do implementacji WCF WS-Reliable Messaging błędów:  
  
- B1501: Usługi WCF nie generuje `MessageNumberRollover` błędów.  
  
- Punkt końcowy B1502:WCF może generować `CreateSequenceRefused` błędów, jak opisano w specyfikacji.  
  
- B1503:when punktu końcowego usługi osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia, WCF, generuje dodatkowe `CreateSequenceRefused` błędów podrzędnego, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.  
  
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
  
### <a name="ws-addressing-faults"></a>Błędy usługi WS-Addressing  
 Ponieważ WS-Reliable Messaging korzysta z protokołu WS-Addressing, WS-Reliable Messaging WCF implementacji może generować błędy WS-Addressing. W tej sekcji omówiono WS-Addressing błędy, generowane WCF jawnie w warstwie usługi WS-Reliable Messaging:  
  
- B1601:WCF generuje odporności komunikat adresowania nagłówka wymagane, gdy jest spełniony jeden z następujących czynności:  
  
    - Brak komunikatu `Sequence` nagłówka i `Action` nagłówka.  
  
    - A `CreateSequence` Brak komunikatu `MessageId` nagłówka.  
  
    - A `CreateSequence` Brak komunikatu `ReplyTo` nagłówka.  
  
- B1602:WCF generuje błędów nie obsługuje akcji w odpowiedzi na wiadomość, których brakuje `Sequence` nagłówka i ma `Action` nagłówek, który nie jest rozpoznawaną w specyfikacji WS-Reliable Messaging.  
  
- B1603:WCF generuje błąd punktu końcowego niedostępna, aby wskazać, że punkt końcowy nie przetwarza sekwencji na podstawie badania `CreateSequence` nagłówków adresowych wiadomości.  
  
## <a name="protocol-composition"></a>Kompozycja protokołu  
  
### <a name="composition-with-ws-addressing"></a>Kompozycja za pomocą usługi WS-Addressing  
 Usługi WCF obsługuje dwie wersje usługi WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing zalecenia 1.0 [WS-ADDR-CORE] i [WS-ADDR — SOAP].  
  
 Podczas gdy wzmianki specyfikacji WS-Reliable Messaging tylko WS-Addressing 2004/08, nie powoduje to ograniczenia wersji WS-Addressing ma być używany. Oto lista ograniczeń, które dotyczą usługi WCF:  
  
- R2101: obu WS-Addressing 2004/08 i WS-Addressing 1.0 mogą być używane z WS-Reliable Messaging.  
  
- R2102:A jedną wersją protokołu WS-Addressing należy użyć w danej sekwencji WS-Reliable Messaging lub parę sekwencji prawdą skorelowane przy użyciu `wsrm:Offer` mechanizm.  
  
### <a name="composition-with-soap"></a>Kompozycja przy użyciu protokołu SOAP  
 Usługi WCF obsługuje korzystanie z protokołu SOAP 1.1 i SOAP 1.2 za pomocą usługi WS-Reliable Messaging.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Kompozycja za pomocą usługi WS-Security i usługi WS-SecureConversation  
 Usługi WCF zapewnia ochronę sekwencji WS-Reliable Messaging przy użyciu zabezpieczenia WS konwersacji bezpiecznego transportowych (HTTPS), skład za pomocą usługi WS-Security i kompozycji. Oto lista ograniczeń, które dotyczą usługi WCF:  
  
- R2301: ochrona integralności sekwencji WS-Reliable Messaging oprócz integralności i poufności poszczególnych wiadomości, WCF wymaga, należy użyć zabezpieczenia WS konwersacji.  
  
- R2302:AWS — zabezpieczanie konwersacji sesji należy ustanowić przed ustanawiania sequence(s) WS-Reliable Messaging.  
  
- R2303: Jeśli okres istnienia sekwencji WS-Reliable Messaging przekracza zabezpieczenia WS konwersacji okres istnienia sesji `SecurityContextToken` nawiązane za pomocą, musi być odnawiany zabezpieczenia WS konwersacji za pomocą odpowiedniego powiązania zabezpieczenia WS konwersacji odnowienia.  
  
- B2304:ws-sekwencji niezawodna obsługa komunikatów lub parę sekwencji skorelowany prawdą są zawsze powiązane z jednej sesji protokołu WS-SecureConversation.  
  
     Źródło WCF generuje `wsse:SecurityTokenReference` element w sekcji rozszerzalności element `CreateSequence` wiadomości.  
  
- R2305:when składającą się z zabezpieczenia WS konwersacji, `CreateSequence` wiadomości musi zawierać `wsse:SecurityTokenReference` elementu.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-Reliable komunikatów potwierdzenia WS-Policy  
 Usługi WCF używa WS-Reliable Messaging potwierdzenie WS-Policy `wsrm:RMAssertion` do opisania możliwości punktów końcowych. Oto lista ograniczeń, które dotyczą usługi WCF:  
  
- B3001: Dołącza WCF `wsrm:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów. Usługi WCF obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementów.  
  
- B3002: Program WCF obsługuje następujące opcjonalne właściwości WS-Reliable Messaging potwierdzenia i zapewnia kontrolę nad nimi na WCF`ReliableMessagingBindingElement`:  
  
    - `wsrm:InactivityTimeout`  
  
    - `wsrm:AcknowledgementInterval`  
  
     Oto przykład.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>Rozszerzenie WS-Reliable Messaging sterowania przepływem  
 Usługi WCF używa WS-Reliable Messaging rozszerzalności, aby zapewnić opcjonalne dodatkowe ściślejszą kontrolę przepływ komunikatów sekwencji.  
  
 Sterowanie przepływem jest włączona, ustawiając <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> właściwość `true`. Oto lista ograniczeń, które dotyczą usługi WCF:  
  
- B4001: Po włączeniu Reliable Messaging sterowanie przepływem programu WCF generuje `netrm:BufferRemaining` elementu w elemencie rozszerzalności `SequenceAcknowledgement` nagłówka.  
  
- B4002: Po włączeniu Reliable Messaging sterowanie przepływem programu WCF nie wymaga `netrm:BufferRemaining` element ma być obecne w `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.  
  
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
  
- B4003: Korzysta z usługi WCF `netrm:BufferRemaining` wskazuje, ile nowe komunikaty niezawodnej obsługi komunikatów docelowy może buforować.  
  
- B4004: niezawodnej obsługi komunikatów usługi WCF ogranicza liczbę wiadomości przesyłanych podczas aplikacji docelowej niezawodną obsługę komunikatów nie może odbierać wiadomości szybko. Komunikaty niezawodnej obsługi komunikatów buforów docelowego i wartości elementu spada na 0.  
  
- B4005: Generuje WCF `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 (włącznie), a następnie odczytuje wartości liczby całkowitej z zakresu od 0 i `xs:int`firmy `maxInclusive` wartość 214748364 (włącznie).  
  
## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 W tej sekcji opisano zachowanie firmy WCF stosowania WS-Reliable Messaging dla różnych wzorców wymiany komunikatów. Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są uważane za:  
  
- Nie mogą być adresowane inicjatora: Inicjator jest za zaporą; Obiekt odpowiadający w trybie wiadomości mogą być dostarczane do inicjatora tylko na odpowiedzi HTTP.  
  
- Adresy inicjatorów: Inicjatora i Responder można wysłać żądania HTTP; innymi słowy może zostać nawiązana dwóch połączeń HTTP prawdą.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednokierunkowa, nie mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Wiązanie  
 Usługi WCF zapewnia wymiany komunikatów jednokierunkową przy użyciu jednej sekwencji przez jeden kanał HTTP. Usługi WCF używa żądania HTTP do przesłania wszystkie komunikaty z usługi RMS RMD i odpowiedzi HTTP do przesłania wszystkie komunikaty z RMD na serwer RMS.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Generuje inicjatora WCF `CreateSequence` wiadomości z żadne oferty. Obiekt odpowiadający w trybie WCF zapewnia `CreateSequence` ma żadne oferty przed utworzeniem sekwencji. Obiekt odpowiadający w trybie WCF zdecyduje się odpowiedzieć `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 Inicjator WCF przetwarza potwierdzeń na odpowiedź wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach. Obiekt odpowiadający w trybie WCF zawsze generuje autonomicznej potwierdzenia w odpowiedzi na oba sekwencji i `AckRequested` wiadomości.  
  
#### <a name="terminatesequence-message"></a>Komunikat TerminateteSequence  
 Traktuje WCF `TerminateSequence` jako Operacja jednokierunkowa, co oznacza odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
### <a name="one-way-addressable-initiator"></a>Jednym ze sposobów, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Wiązanie  
 Usługi WCF zapewnia wymiany komunikatów jednokierunkową przy użyciu jednej sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanał Http. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Generuje inicjatora WCF `CreateSequence` wiadomości z żadne oferty. Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma żadne oferty przed utworzeniem sekwencji. Obiekt odpowiadający w trybie WCF przesyła `CreateSequenceResponse` komunikat na żądania HTTP kierowane za pomocą `ReplyTo` odwołania do punktu końcowego.  
  
### <a name="duplex-addressable-initiator"></a>Duplex, Addressable Initiator  
  
#### <a name="binding"></a>Wiązanie  
 Usługi WCF zapewnia wymiany komunikatów pełni asynchronicznych dwukierunkowe przy użyciu dwóch sekwencji dla ruchu przychodzącego i wychodzącego kanał HTTP. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą. Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma oferty przed utworzeniem sekwencji. Wysyła WCF `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`firmy `ReplyTo` odwołania do punktu końcowego.  
  
#### <a name="sequence-lifetime"></a>Okres istnienia sekwencji  
 Usługi WCF traktuje dwie sekwencje jako jedna sesja w pełni dwukierunkowego.  
  
 Podczas generowania błędów, które błędów jednej sekwencji, WCF oczekuje, że zdalny punkt końcowy do błędów zarówno sekwencji. Podczas czytania błędów, które błędów jednej sekwencji, WCF błędów zarówno sekwencji.  
  
 WCF można zamknąć jego ruchu wychodzącego sekwencji i dalsze przetwarzanie komunikatów w jego przychodzących sekwencji. Z drugiej strony WCF jest przetwarzanie Zamknij sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości w jego ruchu wychodzącego sekwencji.  
  
### <a name="request-reply-non-addressable-initiator"></a>Żądanie odpowiedź, nie mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Wiązanie  
 Usługi WCF zapewnia jednokierunkowe i wymiany komunikatów "żądanie-odpowiedź" za pomocą dwóch sekwencji jednego kanał HTTP. Usługi WCF używa żądań HTTP przesyłają komunikaty z sekwencji żądań i przesyłają komunikaty z sekwencji odpowiedzi przy użyciu odpowiedzi HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą. Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma oferty przed utworzeniem sekwencji. Obiekt odpowiadający w trybie WCF zdecyduje się odpowiedzieć `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.  
  
#### <a name="one-way-message"></a>Komunikat jednokierunkowy  
 Pomyślnie protokół wymiany komunikat jednokierunkowy, inicjator WCF przesyła komunikat z żądaniem kolejności na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP. `SequenceAcknowledgement` Należy potwierdzić wiadomości przesyłane.  
  
 Obiekt odpowiadający w trybie WCF można odpowiedzieć na żądanie z potwierdzeniem, błędów lub odpowiedzi z pustą treść i kod stanu HTTP 202.  
  
#### <a name="two-way-messages"></a>Dwa komunikaty sposób  
 Pomyślnie protokołem dwukierunkowej wiadomości programu exchange, inicjator WCF przesyła komunikat z żądaniem kolejności na żądania HTTP i odbiera komunikat sekwencji odpowiedzi na odpowiedzi HTTP. Odpowiedzi muszą posiadać `SequenceAcknowledgement` potwierdzając komunikat sekwencji żądanie przesyłane.  
  
 Obiekt odpowiadający w trybie WCF można odpowiedzieć na żądanie przy użyciu odpowiedzi aplikacji, błąd lub odpowiedzi z pustą treść i kod stanu HTTP 202.  
  
 Ze względu na obecność jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu żądania sekwencji numer sekwencyjny komunikatu odpowiedzi się brak korelacji.  
  
#### <a name="retrying-replies"></a>Trwa ponawianie próby odpowiedzi  
 Usługi WCF opiera się na korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości. W związku z tym inicjatora WCF nie zatrzymuje ponawianie próby komunikat z żądaniem sekwencji, gdy komunikat sekwencji żądania zostało potwierdzone, lecz raczej w przypadku, gdy odpowiedź HTTP niesie ze sobą, potwierdzenia dla użytkownika komunikat o i błędów. Obiekt odpowiadający w trybie WCF ponawia próbę odpowiedzi na gałęzi żądania HTTP, żądania, do którego jest korelowany z odpowiedzią.  
  
#### <a name="lastmessage-exchange"></a>LastMessage programu Exchange  
 Inicjator WCF generuje i przesyła pustego komunikatu ostatniej zabudowanego na gałęzi żądania HTTP. Usługi WCF wymaga odpowiedzi, ale ignoruje komunikat rzeczywiste odpowiedzi. Obiekt odpowiadający w trybie usługi WCF odpowiada na sekwencji żądanie zabudowanych pusta ostatni komunikat przy użyciu sekwencji odpowiedzi zabudowanych pusta ostatniego komunikatu.  
  
 Jeśli obiekt odpowiadający w trybie WCF otrzyma ostatniej wiadomości, w którym identyfikator URI akcji nie jest `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF odpowiedzi z ostatnią wiadomość. W przypadku protokół wymiany komunikatów dwukierunkowe komunikatu ostatniej niesie komunikat aplikacji; w przypadku protokół wymiany komunikat jednokierunkowy ostatni komunikat jest pusty.  
  
 Obiekt odpowiadający w trybie usługi WCF nie wymaga potwierdzenia komunikatu ostatniej zabudowanych pusta sekwencji odpowiedzi.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence programu Exchange  
 Gdy wszystkie żądania otrzymane prawidłowy odpowiedzi, inicjator WCF generuje i przesyła sekwencji żądanie `TerminateSequence` komunikat na gałęzi żądania HTTP. Usługi WCF wymaga odpowiedzi, ale ignoruje komunikat rzeczywiste odpowiedzi. Obiekt odpowiadający w trybie WCF odpowiada sekwencji żądanie `TerminateSequence` wiadomości z sekwencji odpowiedzi `TerminateSequence` wiadomości.  
  
 W normalnych zamykania zarówno `TerminateSequence` komunikaty zawierają pełny zakres `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>Żądanie/nietypizowana odpowiedź, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Wiązanie  
 Usługi WCF zapewnia wymiany komunikatów typu żądanie odpowiedź przy użyciu dwóch sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanał HTTP. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą. Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma oferty przed utworzeniem sekwencji. Wysyła WCF `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`firmy `ReplyTo` odwołania do punktu końcowego.  
  
#### <a name="requestreply-correlation"></a>Korelacja żądanie/nietypizowana odpowiedź  
 Inicjator WCF zapewnia wszystkie opatrzone komunikaty żądania aplikacji `MessageId` i `ReplyTo` odwołania do punktu końcowego. Stosuje inicjatora WCF `CreateSequence` wiadomości `ReplyTo` odwołania do punktu końcowego dla każdego komunikatu żądania aplikacji. Obiekt odpowiadający w trybie WCF wymaga to żądanie przychodzące komunikaty należy sobie zdawać sprawę `MessageId` i `ReplyTo`. Obiekt odpowiadający w trybie WCF zapewnia, że identyfikator URI odwołania do punktu końcowego w obu `CreateSequence` i wszystkie komunikaty żądania aplikacji są identyczne.
