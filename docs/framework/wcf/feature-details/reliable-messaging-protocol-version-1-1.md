---
title: Reliable Messaging Protocol w wersji 1,1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 9320787317131f42c4a82c6114a16fdea87567f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283314"
---
# <a name="reliable-messaging-protocol-version-11"></a>Reliable Messaging Protocol w wersji 1,1

W tym temacie omówiono szczegóły implementacji Windows Communication Foundation (WCF) dotyczące protokołu WS-ReliableMessaging luty 2007 (wersja 1,1) niezbędnego do przeprowadzenia operacji międzyoperacyjnego przy użyciu transportu HTTP. Funkcja WCF jest zgodna ze specyfikacją WS-ReliableMessaging z ograniczeniami i wyjaśnieniami opisanymi w tym temacie. Należy pamiętać, że protokół WS-ReliableMessaging w wersji 1,1 jest zaimplementowany począwszy od .NET Framework 3,5.

Protokół WS-ReliableMessaging luty 2007 jest zaimplementowany w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.

Dla wygody w temacie są stosowane następujące role:

- Inicjator: klient inicjujący tworzenie niezawodnych sekwencji komunikatów przez usługę WS-niezawodny.

- Responder: usługa, która odbiera żądania inicjatora.

 W tym dokumencie są stosowane prefiksy i przestrzenie nazw w poniższej tabeli.

|prefiks|Przestrzeń nazw|
|-|-|
|WSRM|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|
|s|http://www.w3.org/2003/05/soap-envelope|
|WSA|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|wsp|(WS-Policy 1,2 lub WS-Policy 1,5)|

## <a name="messaging"></a>Obsługa wiadomości

### <a name="sequence-creation"></a>Tworzenie sekwencji

Funkcja WCF implementuje `CreateSequence` i `CreateSequenceResponse` komunikatów w celu ustanowienia niezawodnej sekwencji komunikatów. Obowiązują następujące ograniczenia:

- B1101: inicjator WCF używa tego samego odwołania do punktu końcowego, co `ReplyTo``CreateSequence` komunikatu, `AcksTo` i `Offer/Endpoint`.

- R1102: odwołania do punktów końcowych `AcksTo`, `ReplyTo` i `Offer/Endpoint` w komunikacie `CreateSequence` muszą mieć wartości adresów z identycznymi reprezentacjami ciągów, tak że są one zgodne z oktetem.

  - Obiekt odpowiadający programu WCF sprawdza, czy część identyfikatora URI `AcksTo`, `ReplyTo` i `Endpoint` odwołania do punktu końcowego są identyczne przed utworzeniem sekwencji.

- R1103: odwołania do punktów końcowych `AcksTo`, `ReplyTo` i `Offer/Endpoint` w komunikacie `CreateSequence` powinny mieć ten sam zestaw parametrów referencyjnych.

  - Funkcja WCF nie wymusi, ale zakłada, że parametry odniesienia `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołania do punktów końcowych na `CreateSequence` są identyczne i używają parametrów referencyjnych z odwołania `ReplyTo` punktów końcowych dla potwierdzeń i komunikatów sekwencji z kolejnością.

- B1104: inicjator WCF nie generuje opcjonalnego elementu `Expires` lub `Offer/Expires` w komunikacie `CreateSequence`.

- B1105: podczas uzyskiwania dostępu do komunikatu `CreateSequence`, obiekt odpowiadający WCF używa wartości `Expires` w elemencie `CreateSequence` jako wartość `Expires` w `CreateSequenceResponse` elemencie. W przeciwnym razie obiekt odpowiadający WCF odczytuje i ignoruje wartości `Expires` i `Offer/Expires`.

- B1106: podczas uzyskiwania dostępu do komunikatu `CreateSequenceResponse` inicjator WCF odczytuje opcjonalną wartość `Expires`, ale nie używa jej.

- B1107: inicjator WCF i obiekt odpowiadający zawsze generują opcjonalny element `IncompleteSequenceBehavior` w elementach `CreateSequence/Offer` i `CreateSequenceResponse`.

- B1108: WCF używa tylko wartości `DiscardFollowingFirstGap` i `NoDiscard` w elemencie `IncompleteSequenceBehavior`.

  - WS-ReliableMessaging wykorzystuje mechanizm `Offer` do ustanowienia dwóch odwrotnych sekwencji skorelowanych, które tworzą sesję.

- B1109: Jeśli `CreateSequence` zawiera element `Offer`, jeden ze sposobów obiekt odpowiadający WCF odrzuca oferowaną sekwencję, odpowiadając na `CreateSequenceResponse` bez elementu `Accept`.

- B1110: Jeśli obiekt odpowiadający niezawodnej obsługi komunikatów odrzuci proponowaną sekwencję, inicjator WCF błędnie wyznaczonej sekwencji.

- B1111: Jeśli `CreateSequence` nie zawiera elementu `Offer`, dwukierunkowy obiekt odbiorczy WCF odrzuca oferowaną sekwencję, odpowiadając na błąd `CreateSequenceRefused`.

- R1112: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu mechanizmu `Offer`, właściwość `[address]` odwołania do punktu końcowego `CreateSequenceResponse/Accept/AcksTo` musi być zgodna z docelowym identyfikatorem URI `CreateSequence` bajt komunikatu dla bajtu.

- R1113: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu mechanizmu `Offer`, wszystkie komunikaty przesyłane z inicjatora do obiektu odpowiadającego muszą być wysyłane do tego samego odwołania do punktu końcowego.

WCF używa protokołu WS-ReliableMessaging do ustanawiania niezawodnych sesji między inicjatorem a obiektem odpowiadającym. Implementacja WS-ReliableMessaging WCF zapewnia niezawodną sesję w przypadku wzorców jednokierunkowych, odpowiedzi na żądanie i pełnego dupleksu. Mechanizm `Offer` WS-ReliableMessaging na `CreateSequence` i `CreateSequenceResponse` umożliwia ustanowienie dwóch skorelowanych sekwencji i udostępnia protokół sesji odpowiedni dla wszystkich punktów końcowych komunikatów. Ponieważ WCF zapewnia gwarancję zabezpieczeń dla takiej sesji, w tym kompleksową ochronę integralności sesji, praktyczne jest zapewnienie, że komunikaty przeznaczone dla tej samej strony docierają do tego samego miejsca docelowego. Umożliwia to również "piggy-back" potwierdzeń sekwencji w komunikatach aplikacji. W związku z tym ograniczenia R1102, R1112 i R1113 dotyczą usługi WCF.

Przykład komunikatu `CreateSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>
    <wsa:ReplyTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
      </wsrm:AcksTo>
      <wsrm:Offer>
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>
        <wsrm:Endpoint>
          <wsa:Address>http://Business456.com/clientA</wsa:Address>
        </wsrm:Endpoint>
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      </wsrm:Offer>
    </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

Przykład komunikatu `CreateSequenceResponse`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      <wsrm:Accept>
        <wsrm:AcksTo>
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>
        </wsrm:AcksTo>
      </wsrm:Accept>
    </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="closing-a-sequence"></a>Zamykanie sekwencji

Usługa WCF używa komunikatów `CloseSequence` i `CloseSequenceResponse` do wyłączania niezawodnego zainicjowanego źródła komunikatów. Miejsce docelowe niezawodnej obsługi komunikatów WCF nie inicjuje zamknięcia, a źródło niezawodnej obsługi komunikatów w programie WCF nie obsługuje zamykania niezawodnej obsługi komunikatów w miejscu docelowym. Obowiązują następujące ograniczenia:

- B1201: Źródło niezawodnej obsługi komunikatów WCF zawsze wysyła komunikat `CloseSequence`, aby zamknąć sekwencję.

- B1202: Źródło niezawodnej obsługi komunikatów oczekuje na potwierdzenie pełnego zakresu komunikatów sekwencji przed wysłaniem komunikatu `CloseSequence`.

- B1203: Źródło niezawodnej obsługi komunikatów zawsze zawiera opcjonalny element `LastMsgNumber`, chyba że sekwencja nie zawiera komunikatów.

- R1204: Niezawodna lokalizacja docelowa obsługi komunikatów nie może zainicjować zamknięcia, wysyłając wiadomość `CloseSequence`.

- B1205: po odebraniu komunikatu `CloseSequence`, Źródło niezawodnej obsługi komunikatów programu WCF uważa niekompletną sekwencję i wysyła błąd.

 Przykład komunikatu `CloseSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
    </wsrm:CloseSequence>
  </s:Body>
</s:Envelope>
```

Przykładowy komunikat `CloseSequenceResponse`:

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:CloseSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence-termination"></a>Zakończenie sekwencji

Funkcja WCF używa przede wszystkim uzgodnienia `TerminateSequence/TerminateSequenceResponse` po zakończeniu uzgadniania `CloseSequence/CloseSequenceResponse`. Miejsce docelowe niezawodnej obsługi komunikatów w programie WCF nie inicjuje zakończenia, a źródło niezawodnej obsługi komunikatów nie obsługuje wykończenia niezawodnego działania w miejscu docelowym. Obowiązują następujące ograniczenia:

- B1301: inicjator WCF wysyła komunikat `TerminateSequence` po pomyślnym zakończeniu uzgadniania `CloseSequence/CloseSequenceResponse`.

- R1302: Funkcja WCF sprawdza, czy element `LastMsgNumber` jest spójny dla wszystkich `CloseSequence` i komunikatów `TerminateSequence` dla danej sekwencji. Oznacza to, że `LastMsgNumber` nie są obecne we wszystkich `CloseSequence` i `TerminateSequence` wiadomościach, albo jest obecne i identyczne na wszystkich `CloseSequence` i `TerminateSequence` komunikatów.

- B1303: w przypadku odebrania komunikatu `TerminateSequence` po uzgadnianiu `CloseSequence/CloseSequenceResponse`, miejsce docelowe wiadomości jest odpowiedzią na komunikat `TerminateSequenceResponse`. Ze względu na to, że źródło niezawodnej obsługi komunikatów ma ostateczne potwierdzenie przed wysłaniem komunikatu `TerminateSequence`, Niezawodna docelowa obsługa komunikatów wie, że sekwencja kończy się niewątpliwie i natychmiast przejmuje zasoby.

- B1304: podczas otrzymywania komunikatu `TerminateSequence` przed uzgodnieniem `CloseSequence/CloseSequenceResponse`, miejsce docelowe niezawodnej obsługi komunikatów WCF odpowiada za pomocą wiadomości `TerminateSequenceResponse`. Jeśli miejsce docelowe niezawodnej obsługi komunikatów określa, że nie występują żadne niespójności w sekwencji, niezawodna lokalizacja docelowa do obsługi komunikatów oczekuje na odinstalowanie zasobów przez określony czas docelowy aplikacji, aby umożliwić klientowi otrzymanie szansy ostateczne potwierdzenie. W przeciwnym razie Niezawodna docelowa obsługa komunikatów natychmiast przejmuje zasoby i wskazuje na miejsce docelowe aplikacji, którą sekwencja ma wątpliwości, poprzez podnoszenie poziomu zdarzenia `Faulted`.

Przykład komunikatu `TerminateSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
      </wsrm:TerminateSequence>
  </s:Body>
</s:Envelope>
```

Przykładowy komunikat `TerminateSequenceResponse`:

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:TerminateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequences"></a>Sekwencje

Poniżej znajduje się lista ograniczeń, które są stosowane do sekwencji:

- B1401: Funkcja WCF generuje numery sekwencji i uzyskuje do nich dostęp, nie wyższą `xs:long`niż maksymalna wartość, 9223372036854775807.

Przykład nagłówka `Sequence`.

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a>Potwierdzenie żądania

Funkcja WCF używa nagłówka `AckRequested` jako mechanizmu Keep-Alive.

Przykład nagłówka `AckRequested`.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

Funkcja WCF używa mechanizmu "piggy-back" dla potwierdzeń sekwencji udostępnianych w ramach komunikatów usługi WS-niezawodny. Obowiązują następujące ograniczenia:

- R1601: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu mechanizmu `Offer`, nagłówek `SequenceAcknowledgement` może być zawarty w komunikacie aplikacji przesyłanym do zamierzonego odbiorcy. Zdalny punkt końcowy musi mieć możliwość dostępu do nagłówka `SequenceAcknowledgement` piggybacked.

- B1602: Funkcja WCF nie generuje nagłówków `SequenceAcknowledgement` zawierających elementy `Nack`. Funkcja WCF sprawdza, czy każdy element `Nack` zawiera numer sekwencyjny, ale w przeciwnym razie ignoruje `Nack` element i wartość.

 Przykład nagłówka `SequenceAcknowledgement`.

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a>Błędy WS-ReliableMessaging

Poniżej znajduje się lista ograniczeń, które dotyczą implementacji WCF błędów WS-ReliableMessaging. Obowiązują następujące ograniczenia:

- B1701: Funkcja WCF nie generuje błędów `MessageNumberRollover`.

- B1702: za pośrednictwem protokołu SOAP 1,2, gdy punkt końcowy usługi osiągnie limit połączeń i nie może przetwarzać nowych połączeń, funkcja WCF generuje zagnieżdżony kod `CreateSequenceRefused` błędów `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>
  </s:Header>
  <s:Body>
    <s:Fault>
      <s:Code>
        <s:Value>s:Receiver</s:Value>
        <s:Subcode>
          <s:Value>wsrm:CreateSequenceRefused</s:Value>
          <s:Subcode>
            <s:Value>netrm:ConnectionLimitReached</s:Value>
          </s:Subcode>
        </s:Subcode>
      </s:Code>
      <s:Reason>
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>
      </s:Reason>
    </s:Fault>
  </s:Body>
</s:Envelope>
```

### <a name="ws-addressing-faults"></a>Usługi WS-Addressing faults

Ponieważ WS-ReliableMessaging używa WS-Addressing, implementacja WS-ReliableMessaging programu WCF może generować i przesyłać błędy dotyczące adresowania WS-Exception. W tej sekcji opisano błędy WS-Addressing, które jawnie generują i przesyłają w ramach warstwy WS-ReliableMessaging:

- B1801: Funkcja WCF generuje i przesyła błąd `Message Addressing Header Required`, gdy jest spełniony jeden z następujących warunków:

  - `CreateSequence`, `CloseSequence` lub `TerminateSequence` wiadomości brakuje nagłówka `MessageId`.

  - `CreateSequence`, `CloseSequence` lub `TerminateSequence` wiadomości brakuje nagłówka `ReplyTo`.

  - W wiadomości `CreateSequenceResponse`, `CloseSequenceResponse`lub `TerminateSequenceResponse` brakuje nagłówka `RelatesTo`.

- B1802: Funkcja WCF generuje i przesyła błąd `Endpoint Unavailable`, aby wskazać, że nie ma punktu końcowego nasłuchu, który może przetworzyć sekwencję w oparciu o badanie nagłówków adresowych w komunikacie `CreateSequence`.

## <a name="protocol-composition"></a>Kompozycja protokołu

### <a name="composition-with-ws-addressing"></a>Tworzenie kompozycji przy użyciu protokołu WS-Addressing

WCF obsługuje dwie wersje WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1,0 rekomendacje [WS-ADDR-CORE] i [WS-ADDR-SOAP].

Chociaż Specyfikacja WS-ReliableMessaging wymienia tylko adresy WS-Addressing 2004/08, nie ogranicza do użycia wersji WS-Addressing. Poniżej znajduje się lista ograniczeń dotyczących programu WCF:

- R2101: adresy WS-Addressing 2004/08 i WS-Addressing 1,0 mogą być używane z obsługą komunikatów przy użyciu protokołu WS-niezawodny.

- R2102: jedna wersja WS-Addressing musi być używana przez daną sekwencję WS-ReliableMessaging lub parę sekwencji odwrotnych skorelowanych przy użyciu mechanizmu `Offer`.

### <a name="composition-with-soap"></a>Kompozycja przy użyciu protokołu SOAP

Usługa WCF obsługuje używanie protokołu SOAP 1,1 i protokołu SOAP 1,2 z obsługą komunikatów przy użyciu protokołu WS-niezawodny.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Tworzenie kompozycji przy użyciu protokołu WS-Security i WS-SecureConversation

Funkcja WCF zapewnia ochronę dla sekwencji WS-ReliableMessaging przy użyciu protokołu Secure transport (HTTPS), składa się z protokołu WS-Security i kompozycji przy użyciu funkcji WS-Secure konwersacja. Protokół WS-ReliableMessaging 1,1, protokół WS-Security 1,1 i WS-Secure 1,3 konwersacje w protokole SSL powinny być używane razem. Poniżej znajduje się lista ograniczeń dotyczących programu WCF:

- R2301: aby chronić integralność sekwencji WS-ReliableMessaging, a także integralność i poufność poszczególnych komunikatów, WCF wymaga użycia protokołu WS-Secure konwersacja.

- R2302: AWS — należy ustanowić sesję bezpiecznej konwersacji przed ustanowieniem sekwencji WS-ReliableMessaging.

- R2303: Jeśli okres istnienia sekwencji WS-ReliableMessaging przekroczy okres istnienia sesji komunikacji za pomocą protokołu WS-Secure, `SecurityContextToken` ustanowiony przy użyciu usługi WS-Secure konwersacja musi zostać odnowiony przy użyciu odpowiedniego powiązania odnowienia konwersacji WS-Secure.

- B2304: Metoda WS-ReliableMessaging lub para skorelowanych sekwencji są zawsze powiązane z jedną sesją WS-SecureConversation.

- R2305: Jeśli jest tworzony przy użyciu konwersacji WS-Secure, obiekt odbiorczy programu WCF wymaga, aby komunikat `CreateSequence` zawierał element `wsse:SecurityTokenReference` i nagłówek `wsrm:UsesSequenceSTR`.

 Przykład nagłówka `UsesSequenceSTR`.

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a>Kompozycja z sesjami SSL/TLS

Funkcja WCF nie obsługuje tworzenia kompozycji z użyciem sesji SSL/TLS:

- B2401: Funkcja WCF nie generuje nagłówka `wsrm:UsesSequenceSSL`.

- R2402: inicjator niezawodnej obsługi komunikatów nie może wysyłać komunikatu `CreateSequence` z nagłówkiem `wsrm:UsesSequenceSSL` do obiektu odpowiadającego programu WCF.

### <a name="composition-with-ws-policy"></a>Kompozycja przy użyciu usługi WS-Policy

WCF obsługuje dwie wersje WS-Policy: WS-Policy 1,2 i WS-Policy 1,5.

## <a name="ws-reliablemessaging-ws-policy-assertion"></a>Potwierdzenie WS-ReliableMessaging WS-Policy

W programie WCF są stosowane usługi WS-ReliableMessaging WS-Policy `wsrm:RMAssertion` do opisywania możliwości punktów końcowych. Poniżej znajduje się lista ograniczeń dotyczących programu WCF:

- B3001: Funkcja WCF dołącza `wsrmn:RMAssertion` potwierdzenia WS-Policy do `wsdl:binding` elementów. Program WCF obsługuje obydwa załączniki do `wsdl:binding` i `wsdl:port` elementów.

- B3002: WCF nigdy nie generuje tagu `wsp:Optional`.

- B3003: podczas uzyskiwania dostępu do `wsrmp:RMAssertion` protokołu WS-Policy WCF ignoruje znacznik `wsp:Optional` i traktuje zasady WS-RM jako obowiązkowe.

- R3004: ponieważ WCF nie składa się z sesji SSL/TLS, funkcja WCF nie akceptuje zasad, które określają `wsrmp:SequenceTransportSecurity`.

- B3005: Funkcja WCF zawsze generuje element `wsrmp:DeliveryAssurance`.

- B3006: Funkcja WCF zawsze określa `wsrmp:ExactlyOnce` gwarancja dostarczania.

- B3007: Funkcja WCF generuje i odczytuje następujące właściwości potwierdzenia WS-ReliableMessaging i zapewnia kontrolę nad nimi w`ReliableSessionBindingElement`WCF:

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  Przykład `RMAssertion`.

  ```xml
  <wsrmp:RMAssertion>
    <wsp:Policy>
      <wsrmp:SequenceSTR/>
      <wsrmp:DeliveryAssurance>
        <wsp:Policy>
          <wsrmp:ExactlyOnce/>
          <wsrmp:InOrder/>
        </wsp:Policy>
      </wsrmp:DeliveryAssurance>
    </wsp:Policy>
    <netrmp:InactivityTimeout Milliseconds="600000"/>
    <netrmp:AcknowledgementInterval Milliseconds="200"/>
  </wsrmp:RMAssertion>
  ```

## <a name="flow-control-ws-reliablemessaging-extension"></a>Rozszerzenie WS-ReliableMessaging sterowania przepływem

Funkcja WCF używa rozszerzalności WS-ReliableMessaging w celu zapewnienia opcjonalnej dodatkowej, ściślejszej kontroli przepływu komunikatów sekwencji.

Sterowanie przepływem jest włączane przez ustawienie właściwości <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> na `true`. Poniżej znajduje się lista ograniczeń dotyczących programu WCF:

- B4001: gdy jest włączona funkcja niezawodne sterowanie przepływem komunikatów, usługa WCF generuje element `netrm:BufferRemaining` w rozszerzeniu `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4002: nawet w przypadku włączenia niezawodnej kontroli przepływów komunikatów Funkcja WCF nie wymaga elementu `netrm:BufferRemaining` w nagłówku `SequenceAcknowledgement`.

- B4003: miejsce docelowe komunikatów niezawodnych WCF używa `netrm:BufferRemaining`, aby wskazać liczbę nowych komunikatów, które może buforować.

- B4004: gdy jest włączona funkcja niezawodnej kontroli przepływu komunikatów, Źródło niezawodnych komunikatów WCF używa wartości `netrm:BufferRemaining`, aby ograniczyć przesyłanie komunikatów.

- B4005: Funkcja WCF generuje `netrm:BufferRemaining` wartość całkowitą z zakresu od 0 do 4096 włącznie i odczytuje wartości całkowite z przedziału od 0 do `xs:int``maxInclusive` wartość 214748364 włącznie.

## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów

W tej sekcji opisano zachowanie WCF, gdy funkcja WS-ReliableMessaging jest używana w przypadku różnych wzorców wymiany komunikatów. Dla każdego wzorca wymiany komunikatów są brane pod uwagę następujące dwa scenariusze wdrażania:

- Inicjator bez adresu: inicjator znajduje się za zaporą; Obiekt odpowiadający może dostarczać komunikaty do inicjatora tylko na odpowiedziach HTTP.

- Inicjator obsługujący adresy: zarówno inicjator, jak i obiekt odpowiadający mogą wysyłać żądania HTTP; Innymi słowy, można nawiązać dwa odwrotne połączenia HTTP.

### <a name="one-way-non-addressable-initiator"></a>Jednokierunkowy inicjator bez adresu

#### <a name="binding"></a>Powiązanie

Usługa WCF zapewnia jednokierunkowy wzorzec wymiany komunikatów przy użyciu jednej sekwencji na jeden kanał HTTP. Funkcja WCF używa żądań HTTP do przesyłania wszystkich komunikatów z inicjatora do obiektu odpowiadającego i odpowiedzi HTTP w celu przesłania wszystkich komunikatów z obiektu odpowiadającego do inicjatora.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF przesyła komunikat `CreateSequence` bez elementu `Offer` w żądaniu HTTP i oczekuje komunikatu `CreateSequenceResponse` w odpowiedzi HTTP. Obiekt odpowiadający WCF tworzy sekwencję i przesyła komunikat `CreateSequenceResponse` bez elementu `Accept` w odpowiedzi HTTP.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

Inicjator WCF przetwarza potwierdzenia odpowiedzi wszystkich komunikatów z wyjątkiem komunikatu `CreateSequence` i komunikatów o błędach. Obiekt odpowiadający WCF zawsze przesyła autonomiczną potwierdzenie w odpowiedzi HTTP do wszystkich komunikatów sekwencji i `AckRequested`.

#### <a name="closesequence-exchange"></a>CloseSequence Exchange

Inicjator WCF przesyła komunikat `CloseSequence` w żądaniu HTTP i oczekuje komunikatu `CreateSequenceResponse` w odpowiedzi HTTP. Obiekt odpowiadający WCF przesyła komunikat `CloseSequenceResponse` w odpowiedzi HTTP.

#### <a name="terminatesequence-exchange"></a>Wymiana TerminateSequence

Inicjator WCF przesyła komunikat `TerminateSequence` w żądaniu HTTP i oczekuje komunikatu `TerminateSequenceResponse` w odpowiedzi HTTP. Obiekt odpowiadający WCF przesyła komunikat `TerminateSequenceResponse` w odpowiedzi HTTP.

### <a name="one-way-addressable-initiator"></a>Jeden ze sposobów, inicjator adresowany

#### <a name="binding"></a>Powiązanie

Usługa WCF zapewnia jednokierunkowy wzorzec wymiany komunikatów przy użyciu jednej sekwencji przez jeden kanał ruchu przychodzącego i jednego ruchu wychodzącego HTTP. Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów. Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF przesyła komunikat `CreateSequence` bez elementu `Offer` w żądaniu HTTP. Obiekt odpowiadający WCF tworzy sekwencję i przesyła komunikat `CreateSequenceResponse` bez elementu `Accept` w żądaniu HTTP.

### <a name="duplex-addressable-initiator"></a>Dupleks, inicjator z adresami

#### <a name="binding"></a>Powiązanie

Funkcja WCF udostępnia w pełni asynchroniczny, dwukierunkowy wzorzec wymiany komunikatów przy użyciu dwóch sekwencji w ramach jednego ruchu przychodzącego i jednego wychodzącego kanału HTTP. Ten wzorzec wymiany komunikatów może być mieszany z `Request/Reply`, `Addressable` wzorzec wymiany komunikatów inicjatora w ograniczony sposób. Funkcja WCF używa żądań HTTP do przesyłania wszystkich komunikatów. Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF przesyła `CreateSequence` komunikat z elementem `Offer` w żądaniu HTTP. Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma `Offer` elementu, a następnie tworzy sekwencję i przesyła komunikat `CreateSequenceResponse` z elementem `Accept`.

#### <a name="sequence-lifetime"></a>Okres istnienia sekwencji

Usługa WCF traktuje dwie sekwencje jako jedną sesję w pełni dupleks.

Po wygenerowaniu błędu, który powoduje błąd jednej sekwencji, usługa WCF oczekuje, że zdalny punkt końcowy wystąpi błąd obu sekwencji. Po odczytaniu błędu powodującego błąd jednej sekwencji błędy programu WCF są obie sekwencją.

Funkcja WCF może zamknąć swoją sekwencję wychodzącą i kontynuować przetwarzanie komunikatów w sekwencji przychodzącej. Z kolei WCF może przetworzyć zamknięcie sekwencji przychodzącej i kontynuować wysyłanie komunikatów do sekwencji wychodzącej.

### <a name="request-reply-and-one-way-non-addressable-initiator"></a>"Żądanie-odpowiedź" i "jednokierunkowy" inicjator bez adresu

#### <a name="binding"></a>Powiązanie

Usługa WCF udostępnia wzorzec wymiany komunikatów jednokierunkowych i z żądaniami odpowiedzi przy użyciu dwóch sekwencji w ramach jednego kanału HTTP. Funkcja WCF używa żądań HTTP do przesyłania wszystkich komunikatów z inicjatora do obiektu odpowiadającego i odpowiedzi HTTP w celu przesłania wszystkich komunikatów z obiektu odpowiadającego do inicjatora.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF przesyła komunikat `CreateSequence` z elementem `Offer` w żądaniu HTTP i oczekuje komunikatu `CreateSequenceResponse` w odpowiedzi HTTP. Obiekt odpowiadający WCF tworzy sekwencję i przesyła `CreateSequenceResponse` komunikat z elementem `Accept` w odpowiedzi HTTP.

#### <a name="one-way-message"></a>Komunikat jednokierunkowy

Aby pomyślnie zakończyć wymianę komunikatów jednokierunkowych, inicjator WCF przesyła komunikat sekwencji żądania w żądaniu HTTP i odbiera autonomiczny komunikat `SequenceAcknowledgement` w odpowiedzi HTTP. `SequenceAcknowledgement` musi potwierdzić komunikat przesłany.

Obiekt odpowiadający WCF może odpowiedzieć na żądanie z potwierdzeniem, błędem lub odpowiedzią z pustym identyfikatorem treści i kodem stanu HTTP 202.

#### <a name="two-way-messages"></a>Komunikaty dwukierunkowe

Aby pomyślnie wykonać dwukierunkową metodę wymiany komunikatów, inicjator WCF przesyła komunikat sekwencji żądania w żądaniu HTTP i odbiera komunikat sekwencji odpowiedzi w odpowiedzi HTTP. Odpowiedź musi zawierać `SequenceAcknowledgement` potwierdzenia przesyłanego komunikatu sekwencji żądania.

Obiekt odpowiadający WCF może odpowiedzieć na żądanie za pomocą odpowiedzi aplikacji, błędu lub odpowiedzi z pustym identyfikatorem treści i kodem stanu HTTP 202.

Ze względu na obecność komunikatów jednokierunkowych i chronometrażu odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądań i numer sekwencyjny komunikatu odpowiedzi nie mają korelacji.

#### <a name="retrying-replies"></a>Ponawianie odpowiedzi

Funkcja WCF korzysta z korelacji żądanie HTTP-odpowiedź dla dwukierunkowej korelacji protokołu wymiany komunikatów. W związku z tym inicjator WCF nie przerywa próby przeprowadzenia komunikatu sekwencji żądania, gdy komunikat sekwencji żądań zostanie potwierdzony, ale zamiast tego, gdy odpowiedź HTTP przeprowadzi `SequenceAcknowledgement`, odpowiedzi aplikacji lub błędu. Obiekt odpowiadający programu WCF ponawia odpowiedzi na odpowiedź HTTP żądania, z którym jest skorelowana odpowiedź.

#### <a name="closesequence-exchange"></a>CloseSequence Exchange

Po odebraniu wszystkich komunikatów sekwencji odpowiedzi i potwierdzeń dla wszystkich jednokierunkowych komunikatów sekwencji żądania inicjator WCF przesyła `CloseSequence` komunikat dla sekwencji żądań w żądaniu HTTP i oczekuje `CloseSequenceResponse` w odpowiedzi HTTP.

Zamknięcie sekwencji żądań niejawnie powoduje zamknięcie sekwencji odpowiedzi. Oznacza to, że inicjator WCF obejmuje ostateczną `SequenceAcknowledgement` sekwencji odpowiedzi w komunikacie `CloseSequence`, a sekwencja odpowiedzi nie ma `CloseSequence` Exchange.

Obiekt odpowiadający WCF gwarantuje, że wszystkie odpowiedzi są potwierdzane i przesyła komunikat `CloseSequenceResponse` w odpowiedzi HTTP.

#### <a name="terminatesequence-exchange"></a>Wymiana TerminateSequence

Po odebraniu komunikatu `CloseSequenceResponse` inicjator WCF przesyła komunikat `TerminateSequence` dla sekwencji żądań w żądaniu HTTP i oczekuje `TerminateSequenceResponse` w odpowiedzi HTTP.

Podobnie jak w przypadku `CloseSequence` Exchange, zakończenie sekwencji żądań niejawnie kończy sekwencję odpowiedzi. Oznacza to, że inicjator WCF obejmuje ostateczną `SequenceAcknowledgement` sekwencji odpowiedzi w komunikacie `TerminateSequence`, a sekwencja odpowiedzi nie ma `TerminateSequence` Exchange.

Obiekt odpowiadający WCF przesyła komunikat `TerminateSequenceResponse` w odpowiedzi HTTP.

### <a name="requestreply-addressable-initiator"></a>Żądanie/odpowiedź, inicjator z adresami

#### <a name="binding"></a>Powiązanie

Funkcja WCF udostępnia wzorzec wymiany komunikatów typu żądanie-odpowiedź przy użyciu dwóch sekwencji w ramach jednego ruchu przychodzącego i jednego wychodzącego kanału HTTP. Ten wzorzec wymiany komunikatów może być mieszany z `Duplex, Addressable` wzorzec wymiany komunikatów inicjatora w ograniczony sposób. Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów. Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.

#### <a name="createsequence-exchange"></a>Sekwencja w programie

Inicjator WCF przesyła `CreateSequence` komunikat z elementem `Offer` w żądaniu HTTP. Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma element `Offer`, a następnie tworzy sekwencję i przesyła komunikat `CreateSequenceResponse` z elementem `Accept`.

#### <a name="requestreply-correlation"></a>Korelacja żądania/odpowiedzi

Poniższe zasady dotyczą wszystkich skorelowanych żądań i odpowiedzi:

- Funkcja WCF gwarantuje, że wszystkie komunikaty żądania aplikacji zawierają `ReplyTo` odwołanie do punktu końcowego i `MessageId`.

- Program WCF stosuje odwołanie do lokalnego punktu końcowego, ponieważ każdy komunikat żądania aplikacji jest `ReplyTo`. Odwołanie do lokalnego punktu końcowego jest `ReplyTo` komunikatu `CreateSequence` dla inicjatora i `To` komunikatu `CreateSequence` dla obiektu odpowiadającego.

- Funkcja WCF zapewnia, że przychodzące komunikaty żądania zawierają `MessageId` i `ReplyTo`.

- Funkcja WCF zapewnia, że identyfikator URI odwołania do punktu końcowego `ReplyTo` wszystkich komunikatów żądania aplikacji jest zgodny z odwołaniem do lokalnego punktu końcowego zgodnie z definicją wcześniejszą.

- Funkcja WCF gwarantuje, że wszystkie odpowiedzi będą mieć poprawne `RelatesTo` i `To` nagłówki po `wsa` reguł korelacji żądania/odpowiedzi.
