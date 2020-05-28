---
title: Reliable Messaging Protocol w wersji 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: ef45df0f1cae1f20cf34d07d154baee2cad34b29
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143448"
---
# <a name="reliable-messaging-protocol-version-10"></a>Reliable Messaging Protocol w wersji 1.0

W tym temacie omówiono szczegóły implementacji programu Windows Communication Foundation (WCF) dotyczące protokołu WS-niezawodnej obsługi komunikatów 2005 (wersja 1,0) niezbędnego do przeprowadzenia operacji międzyoperacyjnego przy użyciu transportu HTTP. Funkcja WCF zgodna ze specyfikacją WS-niezawodnej obsługi komunikatów z ograniczeniami i wyjaśnieniami wyjaśnionymi w tym temacie. Należy pamiętać, że protokół WS-ReliableMessaging w wersji 1,0 jest implementowany począwszy od programu WinFX.

Protokół WS-niezawodnej obsługi komunikatów w lutym 2005 jest implementowany w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .

Dla wygody w temacie są stosowane następujące role:

- Inicjator: klient inicjujący tworzenie niezawodnych sekwencji komunikatów usługi WS-niezawodny

- Responder: usługa odbierająca żądania inicjatora

W tym dokumencie są stosowane prefiksy i przestrzenie nazw w poniższej tabeli.

|Prefiks|Przestrzeń nazw|
|------------|---------------|
|WSRM|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|netrm|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|WSA|`http://schemas.xmlsoap.org/ws/2005/08/addressing|
|wsse|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a>Obsługa komunikatów

### <a name="sequence-establishment-messages"></a>Komunikaty dotyczące sekwencji

Funkcja WCF implementuje `CreateSequence` i `CreateSequenceResponse` wysyła komunikaty w celu ustanowienia niezawodnej sekwencji komunikatów. Obowiązują następujące ograniczenia:

- B1101: inicjator WCF nie generuje opcjonalnego elementu Expires w `CreateSequence` komunikacie lub, w przypadkach, gdy `CreateSequence` komunikat zawiera `Offer` element, opcjonalny `Expires` element w `Offer` elemencie.

- B1102: podczas uzyskiwania dostępu do `CreateSequence` komunikatu Funkcja WCF `Responder` wysyła i odbiera oba `Expires` elementy, jeśli istnieją, ale nie używa ich wartości.

Obsługa komunikatów w usłudze WS-niezawodny wprowadza `Offer` mechanizm do ustanowienia dwóch odwrotnych sekwencji skorelowanych, które tworzą sesję.

- R1103: Jeśli `CreateSequence` zawiera `Offer` element, obiekt odpowiadający niezawodnej obsługi komunikatów musi akceptować sekwencję i odpowiadać, `CreateSequenceResponse` która zawiera `wsrm:Accept` element, tworząc dwie skorelowane sekwencje lub odrzucić `CreateSequence` żądanie.

- R1104: `SequenceAcknowledgement` i komunikaty aplikacji przepływające na sekwencję odwrotną muszą być wysyłane `ReplyTo` do odwołania do punktu końcowego `CreateSequence` .

- R1105: `AcksTo` i `ReplyTo` odwołania do punktów końcowych w elemencie `CreateSequence` muszą mieć wartości adresu, które pasują do oktetu.

  Obiekt odpowiadający WCF sprawdza, czy część `AcksTo` i EPRs identyfikatora URI `ReplyTo` są identyczne przed utworzeniem sekwencji.

- R1106: `AcksTo` i `ReplyTo` odwołania do punktów końcowych w elemencie `CreateSequence` powinny mieć ten sam zestaw parametrów referencyjnych.

  Funkcja WCF nie wymusił wymuszania, ale zakłada, że [parametry referencyjne] dla `AcksTo` i `ReplyTo` on `CreateSequence` są identyczne i używa [parametrów referencyjnych] z `ReplyTo` odwołania do punktu końcowego dla potwierdzeń i komunikatów sekwencji z kolejnością.

- R1107: Kiedy dwie sekwencje odwrotne są ustanawiane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` a komunikaty aplikacji przepływające na sekwencje odwrotne muszą być wysyłane do `ReplyTo` odwołania do punktu końcowego `CreateSequence` .

- R1108: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu mechanizmu oferty, `[address]` Właściwość `wsrm:AcksTo` elementu podrzędnego odwołania do punktu końcowego `wsrm:Accept` elementu `CreateSequenceResponse` musi być zgodna z docelowym identyfikatorem URI `CreateSequence` .

- R1109: Kiedy dwie sekwencje odwrotne są ustanawiane przy użyciu `Offer` mechanizmu, komunikaty wysyłane przez inicjatora i potwierdzenia do wiadomości według obiektu odpowiadającego muszą być wysyłane do tego samego odwołania do punktu końcowego.

  Funkcja WCF używa protokołu WS-niezawodnej obsługi komunikatów do ustanawiania niezawodnych sesji między inicjatorem a obiektem odpowiadającym. Implementacja nieniezawodnej obsługi komunikatów w usłudze WCF zapewnia niezawodną sesję w przypadku wzorców jednokierunkowych, odpowiedzi na żądanie i pełnego dupleksu. Mechanizm obsługi komunikatów w usłudze WS-niezawodny `Offer` w systemie `CreateSequence` / `CreateSequenceResponse` umożliwia ustanowienie dwóch skorelowanych sekwencji i zapewnia protokół sesji odpowiedni dla wszystkich punktów końcowych komunikatów. Ponieważ WCF zapewnia gwarancję zabezpieczeń dla takiej sesji, w tym kompleksową ochronę integralności sesji, praktyczne jest zapewnienie, że komunikaty przeznaczone dla tej samej strony docierają do tego samego miejsca docelowego. Umożliwia to również piggye potwierdzeń sekwencji w komunikatach aplikacji. W związku z tym ograniczenia R1104, R1105 i R1108 dotyczą usługi WCF.

Przykład `CreateSequence` komunikatu.

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

 Przykład `CreateSequenceResponse` komunikatu.

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

Poniżej znajduje się lista ograniczeń, które są stosowane do sekwencji:

- B1201: Funkcja WCF generuje numery sekwencji i uzyskuje do nich dostęp, nie wyższą niż `xs:long` Maksymalna wartość łącznie, 9223372036854775807.

- B1202: Funkcja WCF zawsze generuje pustą ostatnią wiadomość z identyfikatorem URI akcji `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .

- B1203: Funkcja WCF odbiera i dostarcza komunikat z nagłówkiem sekwencji, który zawiera element, o ile `LastMessage` nie jest to identyfikator URI akcji `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .

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

### <a name="ackrequested-header"></a>AckRequested — nagłówek

WCF używa `AckRequested` nagłówka jako mechanizmu Keep-Alive. Funkcja WCF nie generuje opcjonalnego `MessageNumber` elementu. Po odebraniu komunikatu z `AckRequested` nagłówkiem zawierającym `MessageNumber` element WCF ignoruje `MessageNumber` wartość elementu, jak pokazano w poniższym przykładzie.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement — nagłówek

Funkcja WCF używa mechanizmu piggy-back dla potwierdzeń sekwencji zapewnianych w ramach komunikatów usługi WS-niezawodny.

- R1401: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` nagłówek może być zawarty w komunikacie aplikacji przesyłanym do zamierzonego odbiorcy.

- B1402: Gdy WCF musi wygenerować potwierdzenie przed odebraniem jakichkolwiek komunikatów sekwencji (na przykład w celu zaspokojenia `AckRequested` wiadomości), WCF generuje nagłówek zawierający `SequenceAcknowledgement` zakres 0-0, jak pokazano w poniższym przykładzie.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- B1403: Funkcja WCF nie generuje `SequenceAcknowledgement` nagłówków zawierających element, `Nack` ale obsługuje `Nack` elementy.

### <a name="ws-reliablemessaging-faults"></a>Błędy WS-ReliableMessaging

Poniżej znajduje się lista ograniczeń, które dotyczą implementacji WCF niezawodnych komunikatów usługi WS-niezawodny:

- B1501: Funkcja WCF nie generuje `MessageNumberRollover` błędów.

- B1502: punkt końcowy WCF może generować `CreateSequenceRefused` Błędy zgodnie z opisem w specyfikacji.

- B1503: gdy punkt końcowy usługi osiągnie limit połączeń i nie może przetwarzać nowych połączeń, usługa WCF generuje dodatkowy `CreateSequenceRefused` podkod błędu, `netrm:ConnectionLimitReached` jak pokazano w poniższym przykładzie.

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

### <a name="ws-addressing-faults"></a>Usługi WS-Addressing faults

Ponieważ obsługa komunikatów w usłudze WS-niezawodny używa protokołu WS-Addressing, implementacja obsługi komunikatów w usłudze WCF WS-niezawodny może generować błędy WS-Addressing. W tej sekcji omówiono błędy usługi WS-Addressing jawnie generowane przez usługę WCF w warstwie komunikatów niezawodnych:

- B1601: Funkcja WCF generuje nagłówek adresowania komunikatu o błędzie wymagany, gdy jest spełniony jeden z następujących warunków:

  - Brak `Sequence` nagłówka i nagłówka w wiadomości `Action` .

  - `CreateSequence`Brak nagłówka w wiadomości `MessageId` .

  - `CreateSequence`Brak nagłówka w wiadomości `ReplyTo` .

- B1602: Funkcja WCF generuje nieobsługiwaną akcję błędu w odpowiedzi na komunikat, który nie zawiera `Sequence` nagłówka i ma `Action` nagłówek, który nie jest rozpoznawany w specyfikacji obsługi komunikatów w usłudze WS-niezawodny.

- B1603: Funkcja WCF generuje punkt końcowy błędu niedostępny, aby wskazać, że punkt końcowy nie przetwarza sekwencji na podstawie badania `CreateSequence` nagłówków adresowania wiadomości.

## <a name="protocol-composition"></a>Kompozycja protokołu

### <a name="composition-with-ws-addressing"></a>Tworzenie kompozycji przy użyciu protokołu WS-Addressing

WCF obsługuje dwie wersje WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1,0 rekomendacje [WS-ADDR-CORE] i [WS-ADDR-SOAP].

Chociaż Specyfikacja komunikatów niezawodnych WS zawiera tylko adresy WS-Addressing 2004/08, nie ogranicza do użycia wersji WS-Addressing. Poniżej znajduje się lista ograniczeń dotyczących programu WCF:

- R2101: adresy WS-Addressing 2004/08 i WS-Addressing 1,0 mogą być używane z obsługą komunikatów przy użyciu protokołu WS-niezawodny.

- R2102: jedna wersja WS-Addressing musi być używana w ramach danej sekwencji komunikatów z obsługą protokołu WS-niezawodnego lub parę sekwencji odwrotnych skorelowanych przy użyciu `wsrm:Offer` mechanizmu.

### <a name="composition-with-soap"></a>Kompozycja przy użyciu protokołu SOAP

Usługa WCF obsługuje używanie protokołu SOAP 1,1 i protokołu SOAP 1,2 z obsługą komunikatów przy użyciu protokołu WS-niezawodny.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Tworzenie kompozycji przy użyciu protokołu WS-Security i WS-SecureConversation

Funkcja WCF zapewnia ochronę dla niezawodnych sekwencji komunikatów przy użyciu protokołu Secure transport (HTTPS), składa się z protokołu WS-Security i kompozycji przy użyciu funkcji WS-Secure konwersacja. Poniżej znajduje się lista ograniczeń dotyczących programu WCF:

- R2301: aby chronić integralność sekwencji komunikatów z obsługą protokołu WS-niezawodnego oraz integralność i poufność poszczególnych komunikatów, WCF wymaga użycia protokołu WS-Secure konwersacja.

- R2302: AWS — należy ustanowić sesję bezpiecznej konwersacji przed ustanowieniem niezawodnych sekwencji komunikatów.

- R2303: Jeśli okres istnienia sekwencji wiadomości w usłudze WS-niezawodny przekroczy okres istnienia sesji komunikacji za pośrednictwem protokołu WS-Secure, `SecurityContextToken` ustanowiony przy użyciu protokołu WS-Secure konwersacja należy odnowić przy użyciu odpowiedniego powiązania odnowienia konwersacji WS-Secure.

- B2304: sekwencja obsługi komunikatów w usłudze WS-niezawodny lub para powiązanych sekwencji są zawsze powiązane z jedną sesją usługi WS-SecureConversation.

  Źródło WCF generuje `wsse:SecurityTokenReference` element w sekcji rozszerzalności elementu `CreateSequence` komunikatu.

- R2305: gdy jest tworzony z konwersacją WS-Secure, `CreateSequence` komunikat musi zawierać `wsse:SecurityTokenReference` element.

## <a name="ws-reliable-messaging-ws-policy-assertion"></a>Potwierdzenie protokołu WS-niezawodnej obsługi komunikatów WS-Policy

Funkcja WCF używa protokołu WS-niezawodnej obsługi komunikatów usługi WS-Policy `wsrm:RMAssertion` do opisywania możliwości punktów końcowych. Poniżej znajduje się lista ograniczeń dotyczących programu WCF:

- B3001: Funkcja WCF dołącza `wsrm:RMAssertion` do elementów potwierdzenie WS-Policy `wsdl:binding` . Program WCF obsługuje oba załączniki `wsdl:binding` do `wsdl:port` elementów i.

- B3002: usługa WCF obsługuje następujące opcjonalne właściwości potwierdzania niezawodnych komunikatów i zapewnia kontrolę nad nimi w programie WCF `ReliableMessagingBindingElement` :

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  Poniżej przedstawiono przykład.

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a>Sterowanie przepływem — rozszerzenie WS-niezawodnej obsługi komunikatów

Funkcja WCF używa rozszerzalności komunikatów niezawodnych w celu zapewnienia opcjonalnej dodatkowej, ściślejszej kontroli przepływu komunikatów sekwencji.

Sterowanie przepływem jest włączane przez ustawienie <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> właściwości na `true` . Poniżej znajduje się lista ograniczeń dotyczących programu WCF:

- B4001: gdy jest włączona funkcja niezawodne sterowanie przepływem komunikatów, usługa WCF generuje `netrm:BufferRemaining` element w rozszerzeniu elementu w `SequenceAcknowledgement` nagłówku.

- B4002: gdy jest włączona funkcja niezawodnej kontroli przepływu komunikatów, usługa WCF nie wymaga, `netrm:BufferRemaining` aby element był obecny w `SequenceAcknowledgement` nagłówku, jak pokazano w poniższym przykładzie.

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

- B4003: Funkcja WCF służy `netrm:BufferRemaining` do wskazywania, ile nowych komunikatów może buforować niezawodne miejsce docelowe komunikatów.

- B4004: usługa niezawodnej obsługi komunikatów programu WCF ogranicza liczbę komunikatów przesyłanych, gdy aplikacja docelowa niezawodnej obsługi komunikatów nie może szybko odbierać wiadomości. Komunikaty o niezawodnych buforach docelowych komunikatów i wartości elementu spadnie do 0.

- B4005: Funkcja WCF generuje `netrm:BufferRemaining` wartości całkowite z zakresu od 0 do 4096 włącznie i odczytuje wartości całkowite z przedziału od 0 do `xs:int` `maxInclusive` 214748364 włącznie.

## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów

W tej sekcji opisano zachowanie programu WCF, gdy obsługa komunikatów przy użyciu protokołu WS-niezawodny jest używana w przypadku różnych wzorców wymiany komunikatów. Dla każdego wzorca wymiany komunikatów są brane pod uwagę następujące dwa scenariusze wdrażania:

- Inicjator bez adresu: inicjator znajduje się za zaporą; Obiekt odpowiadający może dostarczać komunikaty do inicjatora tylko na odpowiedziach HTTP.

- Inicjator obsługujący adresy: zarówno inicjator, jak i obiekt odpowiadający mogą wysyłać żądania HTTP; Innymi słowy, można nawiązać dwa odwrotne połączenia HTTP.

### <a name="one-way-non-addressable-initiator"></a>Jednokierunkowy inicjator bez adresu

#### <a name="binding"></a>Wiązanie

Usługa WCF zapewnia jednokierunkowy wzorzec wymiany komunikatów przy użyciu jednej sekwencji na jeden kanał HTTP. Funkcja WCF używa żądań HTTP do przesyłania wszystkich komunikatów z usługi RMS do RMD i odpowiedzi HTTP w celu przesyłania wszystkich komunikatów z RMD do usługi RMS.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF generuje `CreateSequence` komunikat bez oferty. Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` nie ma oferty przed utworzeniem sekwencji. Obiekt odpowiadający WCF odpowiada na `CreateSequence` żądanie z `CreateSequenceResponse` komunikatem.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

Inicjator WCF przetwarza potwierdzenia odpowiedzi wszystkich komunikatów poza `CreateSequence` komunikatami i komunikaty o błędach. Obiekt odpowiadający WCF zawsze generuje autonomiczną potwierdzenie w odpowiedzi na sekwencję i `AckRequested` wiadomości.

#### <a name="terminatesequence-message"></a>Komunikat TerminateSequence

WCF traktuje `TerminateSequence` się jako operację jednokierunkową, co oznacza, że odpowiedź HTTP ma pustą treść i kod stanu HTTP 202.

### <a name="one-way-addressable-initiator"></a>Jeden ze sposobów, inicjator adresowany

#### <a name="binding"></a>Wiązanie

Usługa WCF zapewnia jednokierunkowy wzorzec wymiany komunikatów przy użyciu jednej sekwencji przez ruch przychodzący i wychodzący. Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów. Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF generuje `CreateSequence` komunikat bez oferty. Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` nie ma oferty przed utworzeniem sekwencji. Obiekt odpowiadający WCF przesyła `CreateSequenceResponse` komunikat w ŻĄDANIU http, który jest kierowany do `ReplyTo` odwołania do punktu końcowego.

### <a name="duplex-addressable-initiator"></a>Dupleks, inicjator z adresami

#### <a name="binding"></a>Wiązanie

Usługa WCF udostępnia w pełni asynchroniczny wzorzec wymiany komunikatów dwukierunkowych przy użyciu dwóch sekwencji za pośrednictwem przychodzącego i wychodzącego kanału HTTP. Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów. Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF generuje `CreateSequence` komunikat z ofertą. Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma ofertę przed utworzeniem sekwencji. Usługa WCF wysyła `CreateSequenceResponse` żądanie HTTP do `CreateSequence` `ReplyTo` odwołania do punktu końcowego.

#### <a name="sequence-lifetime"></a>Okres istnienia sekwencji

Usługa WCF traktuje dwie sekwencje jako jedną sesję w pełni dupleks.

Po wygenerowaniu błędu, który powoduje błąd jednej sekwencji, usługa WCF oczekuje, że zdalny punkt końcowy wystąpi błąd obu sekwencji. Po odczytaniu błędu powodującego błąd jednej sekwencji błędy programu WCF są obie sekwencją.

Funkcja WCF może zamknąć swoją sekwencję wychodzącą i kontynuować przetwarzanie komunikatów w sekwencji przychodzącej. Z kolei WCF może przetworzyć zamknięcie sekwencji przychodzącej i kontynuować wysyłanie komunikatów do sekwencji wychodzącej.

### <a name="request-reply-non-addressable-initiator"></a>Inicjator żądania-odpowiedź, niebędący w adresie

#### <a name="binding"></a>Wiązanie

Usługa WCF udostępnia wzorzec wymiany komunikatów jednokierunkowych i z żądaniami odpowiedzi przy użyciu dwóch sekwencji w ramach jednego kanału HTTP. Funkcja WCF używa żądań HTTP do przesyłania komunikatów sekwencji żądań i używa odpowiedzi HTTP do przesyłania komunikatów sekwencji odpowiedzi.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF generuje `CreateSequence` komunikat z ofertą. Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma ofertę przed utworzeniem sekwencji. Obiekt odpowiadający WCF odpowiada na `CreateSequence` żądanie z `CreateSequenceResponse` komunikatem.

#### <a name="one-way-message"></a>Komunikat jednokierunkowy

Aby pomyślnie ukończyć jednokierunkową metodę wymiany komunikatów, inicjator WCF przesyła komunikat sekwencji żądania w żądaniu HTTP i odbiera w `SequenceAcknowledgement` odpowiedzi HTTP komunikat autonomiczny. `SequenceAcknowledgement`Musi potwierdzić komunikat przesłany.

Obiekt odpowiadający WCF może odpowiedzieć na żądanie z potwierdzeniem, błędem lub odpowiedzią z pustym identyfikatorem treści i kodem stanu HTTP 202.

#### <a name="two-way-messages"></a>Komunikaty dwukierunkowe

Aby pomyślnie wykonać dwukierunkową metodę wymiany komunikatów, inicjator WCF przesyła komunikat sekwencji żądania w żądaniu HTTP i odbiera komunikat sekwencji odpowiedzi w odpowiedzi HTTP. Odpowiedź musi zawierać `SequenceAcknowledgement` potwierdzenie przesłania komunikatu sekwencji żądania.

Obiekt odpowiadający WCF może odpowiedzieć na żądanie za pomocą odpowiedzi aplikacji, błędu lub odpowiedzi z pustym identyfikatorem treści i kodem stanu HTTP 202.

Ze względu na obecność komunikatów jednokierunkowych i chronometrażu odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądań i numer sekwencyjny komunikatu odpowiedzi nie mają korelacji.

#### <a name="retrying-replies"></a>Ponawianie odpowiedzi

Funkcja WCF korzysta z korelacji żądanie HTTP-odpowiedź dla dwukierunkowej korelacji protokołu wymiany komunikatów. W związku z tym inicjator WCF nie przerywa ponawiania próby wysłania komunikatu sekwencji żądania, gdy komunikat sekwencji żądań zostanie potwierdzony, ale gdy odpowiedź HTTP przeprowadzi potwierdzenie, komunikat użytkownika lub błąd. Obiekt odpowiadający w programie WCF ponawia odpowiedzi na etapie żądania HTTP żądania, do którego jest skorelowana odpowiedź.

#### <a name="lastmessage-exchange"></a>LastMessage Exchange

Inicjator WCF generuje i przesyła pustą ostatnią wiadomość z zabudowanego komunikatu w postawce żądania HTTP. Funkcja WCF wymaga odpowiedzi, ale ignoruje rzeczywisty komunikat odpowiedzi. Obiekt odpowiadający programu WCF odpowiada ostatniemu komunikatowi o pustej zaposiadaniu żądania sekwencji odpowiedzi z pustą wiadomością.

Jeśli obiekt odpowiadający programu WCF odbiera ostatni komunikat, w którym nie jest identyfikator URI akcji `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` , program WCF będzie odpowiedzi z ostatnim komunikatem. W przypadku protokołu wymiany komunikatów dwukierunkowych ostatni komunikat przenosi komunikat aplikacji. w przypadku protokołu wymiany komunikatów jednokierunkowych ostatni komunikat jest pusty.

Obiekt odbiorczy programu WCF nie wymaga potwierdzenia dla ostatniego zabudowanego komunikatu sekwencji odpowiedzi.

#### <a name="terminatesequence-exchange"></a>Wymiana TerminateSequence

Po odebraniu przez wszystkie żądania prawidłowej odpowiedzi inicjator WCF generuje i przesyła komunikat sekwencji żądania `TerminateSequence` w postawce żądania HTTP. Funkcja WCF wymaga odpowiedzi, ale ignoruje rzeczywisty komunikat odpowiedzi. Obiekt odpowiadający programu WCF odpowiada na komunikat sekwencji żądań `TerminateSequence` z komunikatem o sekwencji odpowiedzi `TerminateSequence` .

W normalnej sekwencji zamykania oba komunikaty mają `TerminateSequence` pełen zakres `SequenceAcknowledgement` .

### <a name="requestreply-addressable-initiator"></a>Żądanie/odpowiedź, inicjator z adresami

#### <a name="binding"></a>Wiązanie

Funkcja WCF udostępnia wzorzec wymiany komunikatów typu żądanie-odpowiedź przy użyciu dwóch sekwencji w ramach ruchu przychodzącego i wychodzącego. Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów. Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF generuje `CreateSequence` komunikat z ofertą. Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma ofertę przed utworzeniem sekwencji. Usługa WCF wysyła `CreateSequenceResponse` żądanie HTTP do `CreateSequence` `ReplyTo` odwołania do punktu końcowego.

#### <a name="requestreply-correlation"></a>Korelacja żądania/odpowiedzi

Inicjator WCF gwarantuje, że wszystkie komunikaty żądania aplikacji są opatrzone `MessageId` i `ReplyTo` odwołaniem do punktu końcowego. Inicjator WCF stosuje odwołanie do `CreateSequence` `ReplyTo` punktu końcowego komunikatu dla każdego komunikatu żądania aplikacji. Obiekt odpowiadający WCF wymaga, aby przychodzące komunikaty żądań miały `MessageId` a i `ReplyTo` . Obiekt odpowiadający WCF gwarantuje, że identyfikator URI odwołania punktu końcowego obu `CreateSequence` komunikatów żądania aplikacji jest identyczny.
