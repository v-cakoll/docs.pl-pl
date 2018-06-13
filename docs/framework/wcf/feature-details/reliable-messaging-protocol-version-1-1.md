---
title: Reliable Messaging Protocol w wersji 1,1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 8ff02bc6953ec1e5030dd0b592a352b7e23ab0d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496961"
---
# <a name="reliable-messaging-protocol-version-11"></a>Reliable Messaging Protocol w wersji 1,1
W tym temacie omówiono szczegóły implementacji usługi Windows Communication Foundation (WCF) dla protokołu WS-ReliableMessaging protokołu lutego 2007 (w wersji 1.1) niezbędne do współpracy przy użyciu protokołu HTTP. Usługi WCF zgodna ze specyfikacją WS-ReliableMessaging, ograniczenia i wyjaśnienia opisanego w tym temacie. Należy pamiętać, że protokołu WS-ReliableMessaging w wersji 1.1 jest wykonywane, począwszy od [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].  
  
 WS-ReliableMessaging February 2007 protokół jest zaimplementowana w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Dla wygody tematu są używane następujące role:  
  
-   Inicjator: Klienta, który inicjuje tworzenia sekwencji WS-Reliable wiadomości.  
  
-   Obiekt odpowiadający w trybie: Usługa służącą do odbierania żądań inicjatora.  
  
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
|WSP|(WS-Policy 1.2 lub WS-Policy 1.5)|  
  
## <a name="messaging"></a>Obsługa wiadomości  
  
### <a name="sequence-creation"></a>Tworzenie sekwencji  
 Implementuje WCF `CreateSequence` i `CreateSequenceResponse` komunikaty, aby ustanowić niezawodna obsługa komunikatów sekwencji. Obowiązują następujące ograniczenia:  
  
-   B1101: Odwołanie do tego samego punktu końcowego jako używa inicjatora WCF `CreateSequence` komunikatu `ReplyTo`, `AcksTo` i `Offer/Endpoint`.  
  
-   R1102: `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołania do punktu końcowego w `CreateSequence` wiadomości musi mieć adres wartości z reprezentacji ciągu identyczne tak, aby odpowiadały octet-wise.  
  
    -   Obiekt odpowiadający w trybie WCF sprawdza, czy identyfikator URI części `AcksTo`, `ReplyTo` i `Endpoint` odwołania do punktu końcowego są identyczne, przed utworzeniem sekwencji.  
  
-   R1103: `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołania do punktu końcowego w `CreateSequence` wiadomości powinny mieć ten sam zestaw parametrów odwołania.  
  
    -   Usługi WCF nie wymusza, ale przyjęto założenie, że odwołanie parametry `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołuje się do punktu końcowego na `CreateSequence` są identyczne i korzysta z parametrów odwołania z `ReplyTo` odwołania do punktu końcowego dla Potwierdzanie i komunikaty sekwencji odwrotnej.  
  
-   B1104: Inicjator WCF nie generuje opcjonalny `Expires` lub `Offer/Expires` element `CreateSequence` wiadomości.  
  
-   B1105: Podczas uzyskiwania dostępu do `CreateSequence` używa obiektu odpowiadającego w trybie WCF wiadomości, `Expires` wartość w `CreateSequence` element jako `Expires` wartość w `CreateSequenceResponse` elementu. W przeciwnym wypadku obiekt odpowiadający w trybie WCF odczytuje i ignoruje `Expires` i `Offer/Expires` wartości.  
  
-   B1106: Podczas uzyskiwania dostępu do `CreateSequenceResponse` komunikat, inicjator WCF: opcjonalny `Expires` wartość, ale nie używa ich.  
  
-   B1107: WCF Inicjator i obiekt odpowiadający zawsze Generuj opcjonalny `IncompleteSequenceBehavior` element `CreateSequence/Offer` i `CreateSequenceResponse` elementy.  
  
-   B1108: WCF używa tylko `DiscardFollowingFirstGap` i `NoDiscard` wartości w `IncompleteSequenceBehavior` elementu.  
  
    -   Korzysta z protokołu WS-ReliableMessaging `Offer` mechanizmu ustanowienie dwa konwersacji skorelowane sekwencji, które tworzą sesji.  
  
-   B1109: Jeśli `CreateSequence` zawiera `Offer` elementu jednokierunkowej udzielenia WCF odrzuca oferowany sekwencji odpowiedzi z `CreateSequenceResponse` bez `Accept` elementu.  
  
-   B1110: Jeśli obiekt odpowiadający niezawodnej obsługi komunikatów odrzuci oferowany sekwencji, inicjator WCF błędów nowo utworzonego sekwencji.  
  
-   B1111: Jeśli `CreateSequence` nie zawiera `Offer` elementu dwukierunkowe udzielenia WCF odrzuca oferowany sekwencji odpowiedzi z `CreateSequenceRefused` usterek.  
  
-   R1112: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `[address]` właściwość `CreateSequenceResponse/Accept/AcksTo` odwołania do punktu końcowego musi być zgodna docelowego identyfikatora URI z `CreateSequence` bajtów wiadomości dla bajtu.  
  
-   R1113: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, wszystkie komunikaty o obu sekwencji wynikających z inicjatora do udzielenia muszą zostać przesłane do odwołania do tego samego punktu końcowego.  
  
 Usługi WCF używa WS-ReliableMessaging do nawiązywania niezawodnych sesji między Inicjator i obiekt odpowiadający. Implementacja WCF WS-ReliableMessaging udostępnia niezawodnej sesji dla jednokierunkowe żądanie odpowiedź i pełny dupleks wzorców do obsługi komunikatów. WS-ReliableMessaging `Offer` mechanizmu na `CreateSequence` i `CreateSequenceResponse` umożliwia ustanawianie odwrotnej skorelowane dwóch sekwencji i zapewnia protokołu sesji, które jest odpowiednie dla wszystkich komunikatów punktów końcowych. Ponieważ WCF zapewnia gwarancję zabezpieczeń dla sesji, w tym na trasie ochronę integralności sesji, jest praktyczne upewnij się, że wiadomości przeznaczony dla tej samej strony do tego samego miejsca docelowego. Umożliwia to także "piggy zapasowy" potwierdzeń sekwencji komunikatów aplikacji. W związku z tym ograniczenia R1102, R1112 i R1113 dotyczą WCF.  
  
 Przykład `CreateSequence` wiadomości.  
  
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
  
 Przykład `CreateSequenceResponse` wiadomości.  
  
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
  
### <a name="closing-a-sequence"></a>Zamknięcie sekwencji  
 Używa WCF `CloseSequence` i `CloseSequenceResponse` komunikatów dla niezawodna obsługa komunikatów zamknięcia zainicjowanego źródła. Niezawodna obsługa komunikatów usługi WCF w miejscu docelowym nie zainicjować operacji zamykania i źródło niezawodna obsługa komunikatów usługi WCF nie obsługuje zamknięcia zainicjowanego przez miejsce docelowe niezawodna obsługa komunikatów. Obowiązują następujące ograniczenia:  
  
-   B1201: Źródło niezawodna obsługa komunikatów usługi WCF zawsze wysyła `CloseSequence` komunikat zamknięcia sekwencji.  
  
-   B1202: Źródło niezawodna obsługa komunikatów czeka na potwierdzenie pełnego zakresu sekwencji wiadomości przed wysłaniem `CloseSequence` wiadomości.  
  
-   B1203: Źródło niezawodna obsługa komunikatów zawsze zawiera opcjonalny `LastMsgNumber` element chyba, że sekwencja nie zawiera wiadomości.  
  
-   R1204: Niezawodna obsługa komunikatów w miejscu docelowym musi nie zainicjować operacji zamykania, wysyłając `CloseSequence` wiadomości.  
  
-   B1205: odebrane `CloseSequence` wiadomości, uznaje sekwencji, niekompletna źródła niezawodna obsługa komunikatów usługi WCF i wysyła błąd.  
  
 Przykład `CloseSequence` wiadomości.  
  
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
 Przede wszystkim używa WCF `TerminateSequence/TerminateSequenceResponse` uzgadniania po zakończeniu `CloseSequence/CloseSequenceResponse` uzgadniania. Niezawodna obsługa komunikatów usługi WCF w miejscu docelowym nie inicjuje zakończenia i źródła niezawodna obsługa komunikatów nie obsługuje zakończenia niezawodna obsługa komunikatów zainicjowanego przez miejsce docelowe. Obowiązują następujące ograniczenia:  
  
-   B1301: Inicjator WCF wysyła tylko `TerminateSequence` komunikat po pomyślnym zarejestrowaniu `CloseSequence/CloseSequenceResponse` uzgadniania.  
  
-   R1302: WCF sprawdza, czy `LastMsgNumber` element jest spójny we wszystkich `CloseSequence` i `TerminateSequence` wiadomości dla danej sekwencji. Oznacza to, że `LastMsgNumber` albo nie występuje na wszystkie `CloseSequence` i `TerminateSequence` wiadomości, lub jest obecny i identyczne we wszystkich `CloseSequence` i `TerminateSequence` wiadomości.  
  
-   B1303: Podczas odbierania `TerminateSequence` komunikatu po `CloseSequence/CloseSequenceResponse` uzgadniania odpowiada docelowego niezawodna obsługa komunikatów `TerminateSequenceResponse` wiadomości. Ponieważ źródła niezawodna obsługa komunikatów ma ostateczne potwierdzenie przed wysłaniem `TerminateSequence` wiadomości, niezawodna obsługa komunikatów w miejscu docelowym zna bez wątpienia czy kończy się sekwencja i natychmiast zwraca zasobów.  
  
-   B1304: Podczas odbierania `TerminateSequence` komunikatów przed `CloseSequence/CloseSequenceResponse` uzgadniania odpowiada docelowego WCF niezawodna obsługa komunikatów `TerminateSequenceResponse` wiadomości. Jeśli docelowy niezawodna obsługa komunikatów Określa, że nie ma żadnych niespójności w sekwencji, docelowy niezawodna obsługa komunikatów oczekiwania przez czas określony docelowy aplikacji przed odzyskiwanie zasobów, aby umożliwić klientom możliwość odbierania ostateczne potwierdzenie. W przeciwnym razie wartość docelową niezawodnej obsługi komunikatów natychmiast zwraca zasobów i wskazuje przeznaczenia aplikacji, że sekwencja kończy się wątpliwości, podnosząc `Faulted` zdarzeń.  
  
 Przykład `TerminateSequence` wiadomości.  
  
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
 Oto lista ograniczeń, które są stosowane do sekwencji:  
  
-   Generuje B1401:WCF i uzyskuje dostęp do sekwencji liczb nie jest wyższa niż `xs:long`na maksymalną wartość z wartościami granicznymi 9223372036854775807.  
  
 Przykład `Sequence` nagłówka.  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>Potwierdzenie żądania  
 Używa WCF `AckRequested` nagłówka jako mechanizmu keep-alive.  
  
 Przykład `AckRequested` nagłówka.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 Usługi WCF używa mechanizmu "nakładka" dla potwierdzeń sekwencji w WS-Reliable Messaging. Obowiązują następujące ograniczenia:  
  
-   R1601: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` nagłówka może być zawarta w każdej wiadomości aplikacji przesyłane do określonego adresata. Zdalny punkt końcowy musi mieć możliwość dostępu nakładane `SequenceAcknowledgement` nagłówka.  
  
-   B1602: Usługi WCF nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementów. Usługi WCF weryfikuje każdy `Nack` element zawiera numer sekwencji, ale w przeciwnym razie ignoruje `Nack` elementu i wartość.  
  
 Przykład `SequenceAcknowledgement` nagłówka.  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>Błędy protokołu WS-ReliableMessaging.  
 Poniżej znajduje się lista ograniczenia, które dotyczą implementacji WCF błędów WS-ReliableMessaging. Obowiązują następujące ograniczenia:  
  
-   B1701: Usługi WCF nie generuje `MessageNumberRollover` błędów.  
  
-   B1702: Za pośrednictwem protokołu SOAP 1.2, gdy punkt końcowy usługi przez nią miejsce osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia, WCF generuje zagnieżdżoną `CreateSequenceRefused` fault podrzędny, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.  
  
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
  
### <a name="ws-addressing-faults"></a>Protokół WS-Addressing błędów  
 Ponieważ WS-ReliableMessaging korzysta z protokołu WS-Addressing, implementacji protokołu WS-ReliableMessaging WCF może generować i przekazywania błędów protokołu WS-Addressing. W tej sekcji omówiono WS-Addressing usterek, które jawnie WCF generuje i przesyła w warstwie usługi WS-ReliableMessaging:  
  
-   B1801:WCF generuje i przesyła `Message Addressing Header Required` fault, gdy spełniony jest jeden z następujących czynności:  
  
    -   A `CreateSequence`, `CloseSequence` lub `TerminateSequence` Brak komunikatu `MessageId` nagłówka.  
  
    -   A `CreateSequence`, `CloseSequence` lub `TerminateSequence` Brak komunikatu `ReplyTo` nagłówka.  
  
    -   A `CreateSequenceResponse`, `CloseSequenceResponse`, lub `TerminateSequenceResponse` Brak komunikatu `RelatesTo` nagłówka.  
  
-   B1802:WCF generuje i przesyła `Endpoint Unavailable` błędów, aby wskazać żadnego punktu końcowego nasłuchiwania, który może przetwarzać sekwencji oparte na badania adresowania nagłówków `CreateSequence` wiadomości.  
  
## <a name="protocol-composition"></a>Protokół kompozycji  
  
### <a name="composition-with-ws-addressing"></a>Kompozycja z protokołu WS-Addressing  
 Usługi WCF obsługuje dwie wersje usługi WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1.0 zalecenia [WS-ADDR-CORE] i [WS-ADDR — SOAP].  
  
 Podczas uwagi specyfikacji WS-ReliableMessaging tylko WS-Addressing 2004-08 nie uniemożliwia wersji WS-Addressing do użycia. Oto lista ograniczeń, które są stosowane do programu WCF:  
  
-   R2101: Zarówno WS-Addressing 2004/08 i WS-Addressing 1.0 mogą być używane z WS-Reliable Messaging.  
  
-   R2102: Jednej wersji WS-Addressing można używać w danej sekwencji WS-ReliableMessaging dysków lub para skorelowane przy użyciu sekwencji odwrotnej `Offer` mechanizmu.  
  
### <a name="composition-with-soap"></a>Kompozycja z protokołu SOAP  
 Usługi WCF obsługuje SOAP 1.1 i SOAP 1.2 z WS-Reliable Messaging.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Kompozycja i WS-Security WS-SecureConversation  
 Usługi WCF zapewnia ochronę sekwencji WS-ReliableMessaging za pomocą zabezpieczenia WS konwersacji bezpieczne transportowych (HTTPS), kompozycji z WS-Security i kompozycji. Protokół WS-ReliableMessaging 1.1, WS-Security 1.1 i zabezpieczenia WS konwersacji 1.3 protokołu powinny być używane razem. Oto lista ograniczeń, które są stosowane do programu WCF:  
  
-   R2301: Aby chronić integralność sekwencji WS-ReliableMessaging oprócz integralności i poufności poszczególne wiadomości, WCF wymaga, należy użyć zabezpieczenia WS konwersacji.  
  
-   R2302:AWS-Secure Conversation sesji muszą być ustalane przed ustanawianie sequence(s) WS-ReliableMessaging.  
  
-   R2303: Jeśli okres istnienia sekwencji WS-ReliableMessaging przekracza zabezpieczenia WS konwersacji istnienia sesji `SecurityContextToken` ustanowione przy użyciu zabezpieczenia WS konwersacji należy odnawiać przy użyciu odpowiedniego powiązania odnawiania zabezpieczenia WS konwersacji.  
  
-   B2304:ws-sekwencji ReliableMessaging dysków lub para skorelowane odwrotnej sekwencje są zawsze powiązane z jednej sesji WS-SecureConversation.  
  
-   R2305: Jeżeli składa się z zabezpieczenia WS konwersacji, obiekt odpowiadający w trybie WCF wymaga, aby `CreateSequence` komunikat zawiera `wsse:SecurityTokenReference` elementu i `wsrm:UsesSequenceSTR` nagłówka.  
  
 Przykład `UsesSequenceSTR` nagłówka.  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>Kompozycja z sesji SSL/TLS  
 Usługi WCF nie obsługuje kompozycji z sesji SSL/TLS:  
  
-   B2401: Usługi WCF nie generuje `wsrm:UsesSequenceSSL` nagłówka.  
  
-   R2402: Niezawodnej inicjatora wiadomości nie musi wysyłać `CreateSequence` komunikatów z `wsrm:UsesSequenceSSL` nagłówka do obiekt odpowiadający WCF.  
  
### <a name="composition-with-ws-policy"></a>Kompozycja z WS-Policy.  
 Usługi WCF obsługuje dwie wersje usługi WS-Policy: WS-Policy 1.2 i 1.5 WS-Policy.  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-potwierdzenia zasad  
 Usługi WCF używa protokołu WS-ReliableMessaging WS-Policy potwierdzenia `wsrm:RMAssertion` do opisywania możliwości punktów końcowych. Oto lista ograniczeń, które są stosowane do programu WCF:  
  
-   B3001: Dołącza WCF `wsrmn:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów. Usługi WCF obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementy.  
  
-   B3002: Nigdy nie generuje WCF `wsp:Optional` tagu.  
  
-   B3003: Podczas uzyskiwania dostępu do `wsrmp:RMAssertion` ignoruje WCF potwierdzenia WS-Policy `wsp:Optional` tagu i traktuje zasady protokołu WS-RM jako obowiązkowe.  
  
-   R3004: Ponieważ WCF nie tworzą z sesji SSL/TLS, usługi WCF nie akceptuje zasady, które określają `wsrmp:SequenceTransportSecurity`.  
  
-   B3005: WCF zawsze generuje `wsrmp:DeliveryAssurance` elementu.  
  
-   B3006: WCF określa zawsze `wsrmp:ExactlyOnce` gwarancji dostarczenia.  
  
-   B3007: WCF generuje i odczytuje następujące właściwości potwierdzenia WS-ReliableMessaging i zapewnia kontrolę nad nimi na usługi WCF`ReliableSessionBindingElement`:  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a>Przepływ sterowania WS-ReliableMessaging rozszerzenia  
 Usługi WCF używa rozszerzalności WS-ReliableMessaging, aby zapewnić opcjonalne dodatkowe zwiększenie poziomu kontrolę nad przepływ komunikatów sekwencji.  
  
 Przez ustawienie włączone jest sterowanie przepływem `ReliableSessionBindingElement`w `FlowControlEnabled``boolean` właściwości `true`. Oto lista ograniczeń, które są stosowane do programu WCF:  
  
-   B4001: Po włączeniu niezawodnej obsługi komunikatów sterowanie przepływem WCF generuje `netrm:BufferRemaining` elementu w element możliwość rozszerzania `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: Nawet wtedy, gdy niezawodnej obsługi komunikatów sterowanie przepływem jest włączone, usługi WCF nie wymaga `netrm:BufferRemaining` element `SequenceAcknowledgement` nagłówka.  
  
-   B4003: Używa WCF niezawodnej obsługi komunikatów docelowego `netrm:BufferRemaining` można buforu wskazująca, jak wiele nowych komunikatów go.  
  
-   B4004:when niezawodnej obsługi komunikatów sterowanie przepływem jest włączona, źródło WCF niezawodnej obsługi komunikatów używa wartości `netrm:BufferRemaining` do ograniczania przesyłania komunikatów.  
  
-   B4005: Generuje WCF `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 włącznie i odczytuje wartości Liczba całkowita między 0 a `xs:int`w `maxInclusive` wartość 214748364 włącznie.  
  
## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 W tej sekcji opisano zachowanie WCF w przypadku WS-ReliableMessaging służy do różnych wzorców wymiany wiadomości. Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są traktowane jako:  
  
-   Inicjator nie rozpozna: Inicjator znajduje się za zaporą; Obiekt odpowiadający w trybie wiadomości mogą być dostarczane do inicjatora tylko na odpowiedzi HTTP.  
  
-   Inicjator adresowanego: Inicjator i obiekt odpowiadający mogą być wysyłane żądania HTTP; innymi słowy można ustanowić dwa połączenia HTTP odwrotnej.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednokierunkowe, nie mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 Usługi WCF zawiera jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji przez jeden kanał HTTP. WCF używa żądania HTTP do przekazywania wszystkich komunikatów z inicjatora obiektu odpowiadającego w trybie i HTTP odpowiedzi do przesyłania wszystkie komunikaty z udzielenia do inicjatora.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 Przesyła inicjatora WCF `CreateSequence` wiadomość bez `Offer` elementu na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP. Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` wiadomość bez `Accept` elementu na odpowiedzi HTTP.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 Inicjator WCF przetwarza potwierdzenia w odpowiedzi wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach. Obiekt odpowiadający w trybie WCF zawsze przesyła autonomicznej potwierdzenia w odpowiedzi HTTP do wszystkich sekwencji i `AckRequested` wiadomości.  
  
#### <a name="closesequence-exchange"></a>CloseSequence programu Exchange  
 Przesyła inicjatora WCF `CloseSequence` wiadomości na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP. Obiekt odpowiadający w trybie WCF przesyła `CloseSequenceResponse` komunikat odpowiedzi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence programu Exchange  
 Przesyła inicjatora WCF `TerminateSequence` wiadomości na żądania HTTP i oczekuje `TerminateSequenceResponse` komunikat odpowiedzi HTTP. Obiekt odpowiadający w trybie WCF przesyła `TerminateSequenceResponse` komunikat odpowiedzi HTTP.  
  
### <a name="one-way-addressable-initiator"></a>Jednym ze sposobów, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 WCF zapewnia jednokierunkowe wymiany komunikatów za pomocą jednego sekwencji za pośrednictwem jednej dla ruchu przychodzącego i jeden wychodzący kanał HTTP. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 Przesyła inicjatora WCF `CreateSequence` wiadomość bez `Offer` elementu na żądania HTTP. Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` wiadomość bez `Accept` elementu na żądania HTTP.  
  
### <a name="duplex-addressable-initiator"></a>Dupleks, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 Udostępnia WCF pełni asynchroniczne, dwukierunkowe wymiany komunikatów za pomocą dwóch sekwencji do jednego dla ruchu przychodzącego i jeden wychodzący kanał HTTP. Ta wymiany komunikatów można łączyć z `Request/Reply`, `Addressable` inicjatora wymiany komunikatów w sposób ograniczony. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 Przesyła inicjatora WCF `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP. Obiekt odpowiadający w trybie WCF upewnia się, że `CreateSequence` ma `Offer` elementu, następnie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu.  
  
#### <a name="sequence-lifetime"></a>Okres istnienia sekwencji  
 Usługi WCF traktuje dwóch sekwencji jako jedna sesja pełni duplex.  
  
 Podczas generowania błędów, które błędów jedną sekwencję, WCF oczekuje, że zdalny punkt końcowy do obu sekwencji. Podczas odczytywania usterek, które błędów jedną sekwencję, WCF błędów zarówno sekwencji.  
  
 WCF można zamknąć ich wychodzącego sekwencji i dalsze przetwarzanie komunikatów na jego przychodzących sekwencji. Z drugiej strony WCF można przetwarzać zamknięcia sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości na jego wychodzące sekwencji.  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Żądanie odpowiedź i jednokierunkowe, nie mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 Usługi WCF zapewnia jednokierunkowe i żądanie odpowiedź wymiany komunikatów za pomocą dwóch sekwencji ponad jeden kanał HTTP. WCF używa żądania HTTP do przekazywania wszystkich komunikatów z inicjatora obiektu odpowiadającego w trybie i HTTP odpowiedzi do przesyłania wszystkie komunikaty z udzielenia do inicjatora.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 Przesyła inicjatora WCF `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP. Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu na odpowiedzi HTTP.  
  
#### <a name="one-way-message"></a>Komunikat jednokierunkowy  
 Można pomyślnie ukończyć exchange komunikat jednokierunkowy inicjatora WCF przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP. `SequenceAcknowledgement` Musi potwierdzić wiadomości przesyłane.  
  
 Obiekt odpowiadający w trybie WCF może odpowiedzieć na żądanie z potwierdzeniem, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.  
  
#### <a name="two-way-messages"></a>Dwa komunikaty sposób  
 Pomyślnie protokół exchange dwukierunkowej wiadomości, inicjator WCF przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera odpowiedź komunikatu sekwencji odpowiedzi HTTP. Odpowiedzi muszą oni nosić przy sobie `SequenceAcknowledgement` potwierdzeniem wiadomość sekwencji żądanie przesyłane.  
  
 Obiekt odpowiadający w trybie WCF może odpowiedzieć na żądanie odpowiedzi aplikacji, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.  
  
 Z powodu obecności jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądania i numer sekwencyjny komunikatu odpowiedzi mają nie korelacji.  
  
#### <a name="retrying-replies"></a>Ponawianie próby odpowiedzi  
 Usługi WCF zależy od korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości. W związku z tym inicjatora WCF nie zatrzymuje ponowieniem próby wykonania żądania komunikatu sekwencji żądanie sekwencji komunikat zostaje potwierdzony, ale raczej, jeśli odpowiedź HTTP niesie `SequenceAcknowledgement`, odpowiedzi aplikacji lub fault. Obiekt odpowiadający w trybie WCF ponowi próbę odpowiedzi na odpowiedzi HTTP żądania, do której są korelowane z odpowiedzi.  
  
#### <a name="closesequence-exchange"></a>CloseSequence programu Exchange  
 Po otrzymaniu wszystkich komunikatów sekwencji odpowiedzi i potwierdzeń wszystkich komunikatów sekwencji żądań jednokierunkowej, przesyła inicjatora WCF `CloseSequence` wiadomości dla żądania kolejności na żądania HTTP i oczekuje `CloseSequenceResponse` na odpowiedzi HTTP.  
  
 Niejawnie zamknięciem sekwencji żądań zamyka sekwencji odpowiedzi. Oznacza to, że inicjatora WCF obejmuje Final sekwencji odpowiedzi `SequenceAcknowledgement` na `CloseSequence` komunikat i sekwencji odpowiedzi nie ma `CloseSequence` programu exchange.  
  
 Obiekt odpowiadający w trybie WCF zapewnia wszystkie odpowiedzi są potwierdzone i przesyła `CloseSequenceResponse` komunikat odpowiedzi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence programu Exchange  
 Od momentu odebrania `CloseSequenceResponse` przesyła inicjatora WCF wiadomości, `TerminateSequence` wiadomości dla żądania kolejności na żądania HTTP i oczekuje `TerminateSequenceResponse` na odpowiedzi HTTP.  
  
 Podobnie jak `CloseSequence` programu exchange, niejawnie przerywanie sekwencji żądanie kończy sekwencji odpowiedzi. Oznacza to, że inicjatora WCF obejmuje final sekwencji odpowiedzi `SequenceAcknowledgement` na `TerminateSequence` komunikat i sekwencji odpowiedzi nie ma `TerminateSequence` programu exchange.  
  
 Obiekt odpowiadający w trybie WCF przesyła `TerminateSequenceResponse` komunikat odpowiedzi HTTP.  
  
### <a name="requestreply-addressable-initiator"></a>Żądanie/odpowiedź, mogą być adresowane inicjatora  
  
#### <a name="binding"></a>Powiązanie  
 Udostępnia WCF wymiany komunikatów "żądanie-odpowiedź" za pomocą dwóch sekwencji do jednego dla ruchu przychodzącego i jeden wychodzący kanał HTTP. Ta wymiany komunikatów można łączyć z `Duplex, Addressable` inicjatora wymiany komunikatów w sposób ograniczony. WCF używa żądania HTTP do przekazywania wszystkich wiadomości. Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence programu Exchange  
 Przesyła inicjatora WCF `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP. Obiekt odpowiadający w trybie WCF upewnia się, że `CreateSequence` ma `Offer` element następnie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu.  
  
#### <a name="requestreply-correlation"></a>Żądanie i odpowiedź korelacji  
 Poniższe informacje dotyczą wszystkich skorelowane żądań i odpowiedzi:  
  
-   Usługi WCF zapewnia wszystkie posiadają komunikaty żądania aplikacji `ReplyTo` odwołania do punktu końcowego i `MessageId`.  
  
-   Usługi WCF odnoszą się odwołania do lokalnego punktu końcowego jako każdy komunikat żądania aplikacji `ReplyTo`. Odwołanie do lokalnego punktu końcowego jest `CreateSequence` komunikatu `ReplyTo` inicjatora i `CreateSequence` komunikatu `To` obiektu odpowiadającego w trybie.  
  
-   Usługi WCF zapewnia to żądanie przychodzące komunikaty opatrzone `MessageId` i `ReplyTo`.  
  
-   Zapewnia WCF `ReplyTo` URI punktu końcowego odwołania wszystkich komunikatów żądania aplikacji odpowiada odwołaniu do lokalnego punktu końcowego, zgodnie z definicją wcześniej.  
  
-   WCF gwarantuje, że wszystkie odpowiedzi zawierać poprawny `RelatesTo` i `To` następujące nagłówki `wsa` żądania/odpowiedzi reguły korelacji.
