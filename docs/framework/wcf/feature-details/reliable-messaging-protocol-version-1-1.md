---
title: Reliable Messaging Protocol w wersji 1,1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 6b8732e0b48797c219b53bb8bf70e1ba57e25c42
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55073229"
---
# <a name="reliable-messaging-protocol-version-11"></a>Reliable Messaging Protocol w wersji 1,1
W tym temacie omówiono szczegóły dotyczące implementacji usług Windows Communication Foundation (WCF) dla WS-ReliableMessaging protokołu lutego 2007 (w wersji 1.1) niezbędne do współpracy przy użyciu protokołu HTTP. Usługi WCF zgodna ze specyfikacją WS-ReliableMessaging, ograniczenia i wyjaśnienia szczegółowo opisane w tym temacie. Należy pamiętać, protokół WS-ReliableMessaging w wersji 1.1 jest implementowany, począwszy od [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].  
  
 WS-ReliableMessaging lutego 2007 protokołu jest zaimplementowana w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Dla wygody tematu są używane następujące role:  
  
-   Inicjator: Klient, który inicjuje WS-Reliable komunikat tworzenia sekwencji.  
  
-   Responder: Usługa, która odbiera żądania inicjatora.  
  
 Ten dokument używa prefiksy i przestrzenie nazw w poniższej tabeli.  
  
|Prefiks|Przestrzeń nazw|  
|-|-|  
|Menedżer zasobów systemu Windows|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|WSP|(WS-Policy 1.2 lub WS-Policy w wersji 1.5)|  
  
## <a name="messaging"></a>Obsługa wiadomości  
  
### <a name="sequence-creation"></a>Tworzenie sekwencji  
 Implementuje WCF `CreateSequence` i `CreateSequenceResponse` sekwencji komunikaty, aby ustanowić niezawodną obsługę komunikatów. Obowiązują następujące ograniczenia:  
  
-   B1101: Odwołanie do tego samego punktu końcowego jako korzysta z inicjatora WCF `CreateSequence` wiadomości `ReplyTo`, `AcksTo` i `Offer/Endpoint`.  
  
-   R1102: `AcksTo`, `ReplyTo` i `Offer/Endpoint` punktu końcowego, który odwołuje się w `CreateSequence` komunikatu musi zostać wartości adresów z identycznych ciągów reprezentujących w taki sposób, że spełniają octet-wise.  
  
    -   Obiekt odpowiadający w trybie WCF — sprawdza, czy identyfikator URI części `AcksTo`, `ReplyTo` i `Endpoint` odwołania do punktu końcowego są identyczne, przed utworzeniem sekwencji.  
  
-   R1103: `AcksTo`, `ReplyTo` i `Offer/Endpoint` punktu końcowego, który odwołuje się w `CreateSequence` komunikat powinny mieć ten sam zestaw parametrów odwołania.  
  
    -   Usługi WCF nie wymusza, ale przyjęto założenie, że odwołanie parametry `AcksTo`, `ReplyTo` i `Offer/Endpoint` punktu końcowego, który odwołuje się na `CreateSequence` są identyczne i używa parametrów odwołania z `ReplyTo` odwołania do punktu końcowego dla Potwierdzanie i komunikaty sekwencji prawdą.  
  
-   B1104: Inicjator WCF nie generuje opcjonalnego `Expires` lub `Offer/Expires` element `CreateSequence` wiadomości.  
  
-   B1105: Podczas uzyskiwania dostępu do `CreateSequence` używa obiektu odpowiadającego w trybie WCF komunikat `Expires` wartość w `CreateSequence` element jako `Expires` wartość w `CreateSequenceResponse` elementu. W przeciwnym razie obiektu odpowiadającego w trybie WCF odczytuje i ignoruje `Expires` i `Offer/Expires` wartości.  
  
-   B1106: Podczas uzyskiwania dostępu do `CreateSequenceResponse` komunikat, inicjator WCF: opcjonalny `Expires` wartość, ale nie jest używana.  
  
-   B1107: WCF inicjatora i Responder zawsze Generuj opcjonalnego `IncompleteSequenceBehavior` element `CreateSequence/Offer` i `CreateSequenceResponse` elementów.  
  
-   B1108: Usługi WCF używa tylko `DiscardFollowingFirstGap` i `NoDiscard` wartości w `IncompleteSequenceBehavior` elementu.  
  
    -   Korzysta z WS-ReliableMessaging `Offer` mechanizm nawiązać dwa konwersacji skorelowany sekwencji, które tworzą sesji.  
  
-   B1109: Jeśli `CreateSequence` zawiera `Offer` elementu, jeden ze sposobów Responder WCF odrzuca sekwencji oferowanych odpowiedzi z `CreateSequenceResponse` bez `Accept` elementu.  
  
-   B1110: Jeśli obiekt odpowiadający niezawodnej obsługi komunikatów odrzuci oferowane sekwencji, inicjator WCF błędów nowo utworzonego sekwencji.  
  
-   B1111: Jeśli `CreateSequence` nie zawiera `Offer` elementu, dwukierunkowe Responder WCF odrzuca sekwencji oferowane przez odpowiadamy przy użyciu `CreateSequenceRefused` błędów.  
  
-   R1112: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, `[address]` właściwość `CreateSequenceResponse/Accept/AcksTo` odwołania do punktu końcowego musi odpowiadać docelowy identyfikator URI z `CreateSequence` komunikat bajtu na potrzeby bajtów.  
  
-   R1113: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, wszystkie komunikaty o obu sekwencji przepływać z inicjatora do obiektu odpowiadającego w trybie muszą być wysyłane do tego samego odwołania do punktu końcowego.  
  
 Usługi WCF używa WS-ReliableMessaging w celu ustanowienia sesji niezawodnych między inicjatorem i obiekt odpowiadający. Implementacja WCF WS-ReliableMessaging udostępnia niezawodnej sesji, jednokierunkowe "żądanie-odpowiedź" i pełny dupleks wzorce obsługi wiadomości. WS-ReliableMessaging `Offer` mechanizm na `CreateSequence` i `CreateSequenceResponse` umożliwia ustanawianie prawdą skorelowany dwóch sekwencji i zapewnia protokół sesji, która jest odpowiednia dla wszystkich komunikatów z punktami końcowymi. Ponieważ WCF daje gwarancję zabezpieczeń dla sesji, w tym ochronę end-to-end spójność sesji, to praktyczne upewnić się, że wiadomości przeznaczony dla tej samej strony do tego samego miejsca docelowego. Dzięki temu również "piggy zapasowy" potwierdzeń sekwencji na wiadomościach aplikacji. W związku z tym ograniczenia R1102 R1112 i R1113 mają zastosowanie do programu WCF.  
  
 Przykładem `CreateSequence` wiadomości.  
  
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
  
 Przykładem `CreateSequenceResponse` wiadomości.  
  
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
 Korzysta z usługi WCF `CloseSequence` i `CloseSequenceResponse` komunikaty dotyczące zamykania niezawodną obsługę komunikatów zainicjowane źródła. Niezawodna obsługa komunikatów usługi WCF w miejscu docelowym nie zainicjować operacji zamykania i źródła niezawodna obsługa komunikatów usługi WCF nie obsługuje niezawodną obsługę komunikatów zamknięcia zainicjowanego docelowego. Obowiązują następujące ograniczenia:  
  
-   B1201: Niezawodna obsługa komunikatów WCF źródła zawsze wysyła `CloseSequence` komunikat zamknięcia sekwencji.  
  
-   B1202: Niezawodna obsługa komunikatów źródła czeka na potwierdzenie pełnego zakresu sekwencję wiadomości przed wysłaniem `CloseSequence` wiadomości.  
  
-   B1203: Niezawodna obsługa komunikatów źródła zawsze zawiera opcjonalne `LastMsgNumber` element chyba, że sekwencja nie zawiera komunikatów.  
  
-   R1204: Niezawodna obsługa komunikatów w miejscu docelowym nie musi inicjować zamykania, wysyłając `CloseSequence` wiadomości.  
  
-   B1205: Odebrane `CloseSequence` wiadomości, niezawodną obsługę komunikatów WCF źródła uważa, że sekwencja niekompletne i wysyła awarii.  
  
 Przykładem `CloseSequence` wiadomości.  
  
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
Example CloseSequenceResponse message:  
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
 Używany jako podstawowy WCF `TerminateSequence/TerminateSequenceResponse` uzgadnianie po ukończeniu `CloseSequence/CloseSequenceResponse` uzgadniania. Niezawodna obsługa komunikatów usługi WCF w miejscu docelowym nie zostanie zainicjowane zakończenia i niezawodną obsługę komunikatów źródła nie obsługuje przerwanie niezawodną obsługę komunikatów zainicjowane docelowego. Obowiązują następujące ograniczenia:  
  
-   B1301: Wysyła tylko inicjatora WCF `TerminateSequence` komunikat po pomyślnym `CloseSequence/CloseSequenceResponse` uzgadniania.  
  
-   R1302: Usługi WCF sprawdza, czy `LastMsgNumber` element jest spójny we wszystkich `CloseSequence` i `TerminateSequence` wiadomości dla danej sekwencji. Oznacza to, że `LastMsgNumber` nie jest obecny na wszystkich `CloseSequence` i `TerminateSequence` wiadomości, lub jest on obecny i identyczne we wszystkich `CloseSequence` i `TerminateSequence` wiadomości.  
  
-   B1303: Podczas odbierania `TerminateSequence` komunikat po `CloseSequence/CloseSequenceResponse` uzgadniania docelowego niezawodną obsługę komunikatów odpowiada za pomocą `TerminateSequenceResponse` wiadomości. Ponieważ źródło niezawodną obsługę komunikatów ma końcowe potwierdzenie przed wysłaniem `TerminateSequence` komunikat docelowy niezawodną obsługę komunikatów wie, bez wątpliwości sekwencji kończy się, że i od razu przejmuje zasobów.  
  
-   B1304: Podczas odbierania `TerminateSequence` komunikatów w systemach wcześniejszych niż `CloseSequence/CloseSequenceResponse` uzgadniania docelowego niezawodną obsługę komunikatów WCF odpowiada za pomocą `TerminateSequenceResponse` wiadomości. Jeśli docelowy niezawodną obsługę komunikatów okaże się, że istnieją nie niespójności w sekwencji, niezawodną obsługę komunikatów docelowego czeka przez czas określony docelowy aplikacji przed odzyskiwanie zasobów, aby umożliwić klientowi możliwość odbierania końcowe potwierdzenie. W przeciwnym razie docelowego niezawodną obsługę komunikatów natychmiast odzyskuje zasobów i wskazuje przeznaczenia aplikacji, że sekwencja kończy się wątpliwości, tworząc `Faulted` zdarzeń.  
  
 Przykładem `TerminateSequence` wiadomości.  
  
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
Example TerminateSequenceResponse message:  
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
 Oto lista ograniczeń, które dotyczą sekwencji:  
  
-   Generuje B1401:WCF i uzyskuje dostęp do sekwencji numerów nie jest wyższa niż `xs:long`firmy maksymalną wartość włącznie 9223372036854775807.  
  
 Przykładem `Sequence` nagłówka.  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>Potwierdzenie żądania  
 Korzysta z usługi WCF `AckRequested` nagłówek jako mechanizm utrzymywania aktywności.  
  
 Przykładem `AckRequested` nagłówka.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 Usługi WCF używa mechanizmu "nakładka" potwierdzeń sekwencji w WS-Reliable Messaging. Obowiązują następujące ograniczenia:  
  
-   R1601: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` nagłówek może być zawarta w każdy komunikat aplikacji przekazywane do określonego adresata. Zdalny punkt końcowy musi mieć możliwość dostępu nakładane `SequenceAcknowledgement` nagłówka.  
  
-   B1602: Usługi WCF nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementów. Usługi WCF weryfikuje, że każdy `Nack` element zawiera numer sekwencji, ale w przeciwnym razie ignoruje `Nack` elementu i wartości.  
  
 Przykładem `SequenceAcknowledgement` nagłówka.  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>Błędy WS-ReliableMessaging  
 Oto lista ograniczeń, które są stosowane do implementacji WCF WS-ReliableMessaging błędów. Obowiązują następujące ograniczenia:  
  
-   B1701: Usługi WCF nie generuje `MessageNumberRollover` błędów.  
  
-   B1702: Za pośrednictwem protokołu SOAP 1.2, gdy punkt końcowy usługi osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia, WCF generuje zagnieżdżoną `CreateSequenceRefused` błędów podrzędnego, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.  
  
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
  
### <a name="ws-addressing-faults"></a>Błędy usługi WS-Addressing  
 Ponieważ WS-ReliableMessaging korzysta z protokołu WS-Addressing, implementacja WCF WS-ReliableMessaging może wygenerować i transmisji błędów WS-Addressing. W tej sekcji omówiono WS-Addressing błędów, które WCF jawnie generuje i przesyła je w warstwie WS-ReliableMessaging:  
  
-   B1801:WCF generuje i przesyła `Message Addressing Header Required` błędów, gdy jest spełniony jeden z następujących czynności:  
  
    -   A `CreateSequence`, `CloseSequence` lub `TerminateSequence` Brak komunikatu `MessageId` nagłówka.  
  
    -   A `CreateSequence`, `CloseSequence` lub `TerminateSequence` Brak komunikatu `ReplyTo` nagłówka.  
  
    -   A `CreateSequenceResponse`, `CloseSequenceResponse`, lub `TerminateSequenceResponse` Brak komunikatu `RelatesTo` nagłówka.  
  
-   B1802:WCF generuje i przesyła `Endpoint Unavailable` błędów w celu wskazania jest nie nasłuchującego punktu końcowego, który może przetwarzać sekwencji, w oparciu o badanie adresowania nagłówków `CreateSequence` wiadomości.  
  
## <a name="protocol-composition"></a>Kompozycja protokołu  
  
### <a name="composition-with-ws-addressing"></a>Kompozycja za pomocą usługi WS-Addressing  
 Usługi WCF obsługuje dwie wersje usługi WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing zalecenia 1.0 [WS-ADDR-CORE] i [WS-ADDR — SOAP].  
  
 Podczas WS-ReliableMessaging wzmianki specyfikacji WS-Addressing 2004 tylko/08, nie powoduje to ograniczenia wersji WS-Addressing ma być używany. Oto lista ograniczeń, które dotyczą usługi WCF:  
  
-   R2101: WS-Addressing 2004/08 i WS-Addressing 1.0 można za pomocą usługi WS-Reliable Messaging.  
  
-   R2102: Należy użyć jednej wersji WS-Addressing w danej sekwencji WS-ReliableMessaging lub parę sekwencji prawdą skorelowane przy użyciu `Offer` mechanizm.  
  
### <a name="composition-with-soap"></a>Kompozycja przy użyciu protokołu SOAP  
 Usługi WCF obsługuje SOAP 1.1 i SOAP 1.2 za pomocą usługi WS-Reliable Messaging.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Kompozycja za pomocą usługi WS-Security i usługi WS-SecureConversation  
 Usługi WCF zapewnia ochronę sekwencje WS-ReliableMessaging przy użyciu zabezpieczenia WS konwersacji bezpiecznego transportowych (HTTPS), skład za pomocą usługi WS-Security i kompozycji. Protokół WS-ReliableMessaging 1.1, WS-Security 1.1 i protokołu zabezpieczenia WS konwersacji 1.3 powinny być używane razem. Oto lista ograniczeń, które dotyczą usługi WCF:  
  
-   R2301: Do ochrony integralności sekwencji WS-ReliableMessaging oprócz integralności i poufności poszczególnych wiadomości, WCF wymaga, należy użyć zabezpieczenia WS konwersacji.  
  
-   R2302:AWS-sesji konwersacji zabezpieczyć, należy ustanowić przed ustanawiania sequence(s) WS-ReliableMessaging.  
  
-   R2303: Jeśli okres istnienia sekwencji WS-ReliableMessaging przekracza zabezpieczenia WS konwersacji okres istnienia sesji `SecurityContextToken` nawiązane za pomocą, musi być odnawiany zabezpieczenia WS konwersacji za pomocą odpowiedniego powiązania zabezpieczenia WS konwersacji odnowienia.  
  
-   B2304:WS-ReliableMessaging sekwencji lub parę skorelowany prawdą sekwencji są zawsze powiązane z jednej sesji protokołu WS-SecureConversation.  
  
-   R2305: Jeżeli składa się z zabezpieczenia WS konwersacji, obiekt odpowiadający w trybie WCF wymaga `CreateSequence` komunikat zawiera `wsse:SecurityTokenReference` elementu i `wsrm:UsesSequenceSTR` nagłówka.  
  
 Przykładem `UsesSequenceSTR` nagłówka.  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>Kompozycja sesji SSL/TLS  
 Usługi WCF nie obsługuje tworzenia sesji SSL/TLS:  
  
-   B2401: Usługi WCF nie generuje `wsrm:UsesSequenceSSL` nagłówka.  
  
-   R2402: Niezawodne inicjatora komunikatów nie musi wysyłać `CreateSequence` komunikatu o `wsrm:UsesSequenceSSL` nagłówka do obiektu odpowiadającego w trybie usługi WCF.  
  
### <a name="composition-with-ws-policy"></a>Kompozycja za pomocą usługi WS-Policy  
 Usługi WCF obsługuje dwie wersje usługi WS-Policy: WS-Policy 1.2 i WS-Policy w wersji 1.5.  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-asercji zasad  
 Potwierdzenie WS-Policy WS-ReliableMessaging korzysta z usługi WCF `wsrm:RMAssertion` do opisania możliwości punktów końcowych. Oto lista ograniczeń, które dotyczą usługi WCF:  
  
-   B3001: Dołącza WCF `wsrmn:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów. Usługi WCF obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementów.  
  
-   B3002: Nigdy nie generuje WCF `wsp:Optional` tagu.  
  
-   B3003: Podczas uzyskiwania dostępu do `wsrmp:RMAssertion` ignoruje WCF potwierdzenie WS-Policy `wsp:Optional` oznaczać i traktuje zasad WS-RM jako obowiązkowe.  
  
-   R3004: Ponieważ usługi WCF nie tworzą sesji SSL/TLS, usługi WCF nie akceptuje zasady, które określają `wsrmp:SequenceTransportSecurity`.  
  
-   B3005: Usługi WCF zawsze generuje `wsrmp:DeliveryAssurance` elementu.  
  
-   B3006: Usługi WCF zawsze Określa `wsrmp:ExactlyOnce` assurance dostarczania.  
  
-   B3007: WCF generuje następujące właściwości potwierdzenie WS-ReliableMessaging odczytuje i zapewnia kontrolę nad nimi na WCF`ReliableSessionBindingElement`:  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     Przykładem `RMAssertion`.  
  
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
 Usługi WCF używa WS-ReliableMessaging rozszerzalności, aby zapewnić opcjonalne dodatkowe ściślejszą kontrolę przepływ komunikatów sekwencji.  
  
 Sterowanie przepływem jest włączona, ustawiając <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> właściwość `true`. Oto lista ograniczeń, które dotyczą usługi WCF:  
  
-   B4001: Po włączeniu Reliable Messaging sterowanie przepływem programu WCF generuje `netrm:BufferRemaining` elementu w elemencie rozszerzalności `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: Nawet po włączeniu Reliable Messaging sterowanie przepływem, usługi WCF nie wymaga `netrm:BufferRemaining` element `SequenceAcknowledgement` nagłówka.  
  
-   B4003: Korzysta z usługi WCF niezawodnej obsługi komunikatów docelowego `netrm:BufferRemaining` może buforować do wskazania, ilu nowych komunikatów go.  
  
-   Włączono B4004:when Reliable Messaging sterowanie przepływem, źródło WCF niezawodnej obsługi komunikatów używa wartości `netrm:BufferRemaining` do ograniczania transmisję wiadomości.  
  
-   B4005: Generuje WCF `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 (włącznie), a następnie odczytuje wartości liczby całkowitej z zakresu od 0 i `xs:int`firmy `maxInclusive` wartość 214748364 (włącznie).  
  
## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 W tej sekcji opisano zachowanie firmy WCF stosowania WS-ReliableMessaging dla różnych wzorców wymiany komunikatów. Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są uważane za:  
  
-   Nie mogą być adresowane inicjatora: Inicjator jest za zaporą; Obiekt odpowiadający w trybie dostarczać wiadomości do inicjatora tylko na odpowiedzi HTTP.  
  
-   Adresy inicjatorów: Inicjatora i Responder można wysłać żądania HTTP; innymi słowy może zostać nawiązana dwóch połączeń HTTP prawdą.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednokierunkowa, nie mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 Usługi WCF zapewnia wymiany komunikatów jednokierunkową przy użyciu jednej sekwencji przez jeden kanał HTTP. Usługi WCF używa żądania HTTP do przesłania wszystkie komunikaty z inicjatora do odpowiedzi obiektu odpowiadającego w trybie i HTTP do przesłania wszystkie komunikaty z obiektu odpowiadającego w trybie do inicjatora.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Przesyła inicjatora WCF `CreateSequence` wiadomość bez `Offer` element na żądania HTTP i oczekuje, że `CreateSequenceResponse` komunikat odpowiedzi HTTP. Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` wiadomość bez `Accept` element na odpowiedzi HTTP.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 Inicjator WCF przetwarza potwierdzeń na odpowiedź wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach. Obiekt odpowiadający w trybie WCF zawsze wysyła autonomicznej potwierdzenia w odpowiedzi HTTP do wszystkich sekwencji i `AckRequested` wiadomości.  
  
#### <a name="closesequence-exchange"></a>CloseSequence programu Exchange  
 Przesyła inicjatora WCF `CloseSequence` wiadomości na żądanie HTTP, a następnie oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP. Obiekt odpowiadający w trybie WCF przesyła `CloseSequenceResponse` komunikat odpowiedzi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence programu Exchange  
 Przesyła inicjatora WCF `TerminateSequence` wiadomości na żądanie HTTP, a następnie oczekuje `TerminateSequenceResponse` komunikat odpowiedzi HTTP. Obiekt odpowiadający w trybie WCF przesyła `TerminateSequenceResponse` komunikat odpowiedzi HTTP.  
  
### <a name="one-way-addressable-initiator"></a>Jednym ze sposobów, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 WCF zapewnia wymiany komunikatów jednokierunkową przy użyciu jednej sekwencji przez jedną dla ruchu przychodzącego i jeden wychodzących kanał HTTP. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Przesyła inicjatora WCF `CreateSequence` wiadomość bez `Offer` element na żądania HTTP. Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` wiadomość bez `Accept` element na żądania HTTP.  
  
### <a name="duplex-addressable-initiator"></a>Duplex, Addressable Initiator  
  
#### <a name="binding"></a>Powiązanie  
 Usługi WCF zapewnia wymiany komunikatów pełni asynchronicznego, dwukierunkowej, używając dwóch sekwencji przez jedną dla ruchu przychodzącego i jeden wychodzących kanał HTTP. Niepodstawowe tej wymiany komunikatów `Request/Reply`, `Addressable` wymiany komunikatów inicjatora w sposób ograniczony. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Przesyła inicjatora WCF `CreateSequence` komunikatu o `Offer` element na żądania HTTP. Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma `Offer` elementu, następnie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatu o `Accept` elementu.  
  
#### <a name="sequence-lifetime"></a>Okres istnienia sekwencji  
 Usługi WCF traktuje dwie sekwencje jako jedna sesja w pełni duplex.  
  
 Podczas generowania błędów, które błędów jednej sekwencji, WCF oczekuje, że zdalny punkt końcowy do błędów zarówno sekwencji. Podczas czytania błędów, które błędów jednej sekwencji, WCF błędów zarówno sekwencji.  
  
 WCF można zamknąć jego ruchu wychodzącego sekwencji i dalsze przetwarzanie komunikatów w jego przychodzących sekwencji. Z drugiej strony WCF jest przetwarzanie Zamknij sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości w jego ruchu wychodzącego sekwencji.  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>"Żądanie-odpowiedź" i inicjatorze jednokierunkowe, nie mogą być adresowane  
  
#### <a name="binding"></a>Powiązanie  
 Usługi WCF zapewnia jednokierunkowe i wymiany komunikatów "żądanie-odpowiedź" za pomocą dwóch sekwencji jednego kanał HTTP. Usługi WCF używa żądania HTTP do przesłania wszystkie komunikaty z inicjatora do odpowiedzi obiektu odpowiadającego w trybie i HTTP do przesłania wszystkie komunikaty z obiektu odpowiadającego w trybie do inicjatora.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Przesyła inicjatora WCF `CreateSequence` komunikatu o `Offer` element na żądanie HTTP, a oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP. Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatu o `Accept` element na odpowiedzi HTTP.  
  
#### <a name="one-way-message"></a>Komunikat jednokierunkowy  
 Pomyślnie exchange komunikat jednokierunkowy, inicjator WCF przesyła komunikat z żądaniem kolejności na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP. `SequenceAcknowledgement` Należy potwierdzić wiadomości przesyłane.  
  
 Obiekt odpowiadający w trybie usługi WCF może odpowiadać na żądania o potwierdzenie, błędów lub odpowiedzi z pustą treść i kod stanu HTTP 202.  
  
#### <a name="two-way-messages"></a>Dwa komunikaty sposób  
 Pomyślnie protokołem dwukierunkowej wiadomości programu exchange, inicjator WCF przesyła komunikat z żądaniem kolejności na żądania HTTP i odbiera komunikat sekwencji odpowiedzi na odpowiedzi HTTP. Odpowiedzi muszą posiadać `SequenceAcknowledgement` potwierdzając komunikat sekwencji żądanie przesyłane.  
  
 Obiekt odpowiadający w trybie WCF może odpowiedzieć na żądanie przy użyciu odpowiedzi aplikacji, błąd lub odpowiedzi z pustą treść i kod stanu HTTP 202.  
  
 Ze względu na obecność jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu żądania sekwencji numer sekwencyjny komunikatu odpowiedzi się brak korelacji.  
  
#### <a name="retrying-replies"></a>Trwa ponawianie próby odpowiedzi  
 Usługi WCF opiera się na korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości. W związku z tym inicjatora WCF nie zatrzymuje ponowieniem próby wykonania żądania komunikatu sekwencji komunikat sekwencji żądania zostało potwierdzone, ale raczej gdy odpowiedź HTTP niesie ze sobą `SequenceAcknowledgement`, odpowiedzi aplikacji lub błędów. Obiekt odpowiadający w trybie WCF ponawia próbę odpowiedzi na odpowiedzi HTTP żądania, do którego jest korelowany z odpowiedzią.  
  
#### <a name="closesequence-exchange"></a>CloseSequence programu Exchange  
 Po uzyskaniu wszystkich komunikatów sekwencji odpowiedzi i potwierdzeń wszystkie komunikaty sekwencji żądania jednokierunkowego, przesyła inicjatora WCF `CloseSequence` komunikatu w sekwencji żądania na żądanie HTTP, a następnie oczekuje `CloseSequenceResponse` na odpowiedzi HTTP.  
  
 Zamykanie sekwencji żądań niejawnie zamyka sekwencji odpowiedzi. Oznacza to, że inicjator WCF zawiera końcowe sekwencji odpowiedzi `SequenceAcknowledgement` na `CloseSequence` komunikat i sekwencji odpowiedzi nie ma `CloseSequence` programu exchange.  
  
 Obiekt odpowiadający w trybie WCF zapewnia wszystkie odpowiedzi są potwierdzone i przesyła `CloseSequenceResponse` komunikat odpowiedzi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence programu Exchange  
 Od momentu odebrania `CloseSequenceResponse` przesyła inicjatora WCF komunikat `TerminateSequence` komunikatu w sekwencji żądania na żądanie HTTP, a następnie oczekuje `TerminateSequenceResponse` na odpowiedzi HTTP.  
  
 Podobnie jak `CloseSequence` programu exchange, niejawnie przerywa sekwencji żądanie kończy się sekwencji odpowiedzi. Oznacza to, że inicjator WCF zawiera końcowe sekwencji odpowiedzi `SequenceAcknowledgement` na `TerminateSequence` komunikat i sekwencji odpowiedzi nie ma `TerminateSequence` programu exchange.  
  
 Obiekt odpowiadający w trybie WCF przesyła `TerminateSequenceResponse` komunikat odpowiedzi HTTP.  
  
### <a name="requestreply-addressable-initiator"></a>Żądanie/nietypizowana odpowiedź, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 Usługi WCF zapewnia wymiany komunikatów "żądanie-odpowiedź" za pomocą dwóch sekwencji przez jedną dla ruchu przychodzącego i jeden wychodzących kanał HTTP. Niepodstawowe tej wymiany komunikatów `Duplex, Addressable` wymiany komunikatów inicjatora w sposób ograniczony. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence — Exchange  
 Przesyła inicjatora WCF `CreateSequence` komunikatu o `Offer` element na żądania HTTP. Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma `Offer` element następnie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatu o `Accept` elementu.  
  
#### <a name="requestreply-correlation"></a>Korelacja żądanie/nietypizowana odpowiedź  
 Poniższe informacje dotyczą wszystkich skorelowany żądań i odpowiedzi:  
  
-   Usługi WCF zapewnia wszystkie opatrzone komunikaty żądania aplikacji `ReplyTo` odwołania do punktu końcowego i `MessageId`.  
  
-   Usługi WCF stosuje odniesienie lokalny punkt końcowy jako każdego komunikatu żądania aplikacji `ReplyTo`. Odwołanie lokalny punkt końcowy jest `CreateSequence` wiadomości `ReplyTo` inicjatora i `CreateSequence` wiadomości `To` obiektu odpowiadającego w trybie.  
  
-   Usługi WCF zapewnia to żądanie przychodzące komunikaty należy sobie zdawać sprawę `MessageId` i `ReplyTo`.  
  
-   Zapewnia WCF `ReplyTo` identyfikator URI punktu końcowego odwołania wszystkich komunikatów żądania aplikacji odpowiada odwołaniu lokalny punkt końcowy, zgodnie z definicją wcześniej.  
  
-   Usługi WCF zapewnia, że wszystkie odpowiedzi ponosić poprawny `RelatesTo` i `To` następujące nagłówki `wsa` żądanie/nietypizowana odpowiedź reguły korelacji.
