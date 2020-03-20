---
title: Protokoły obsługi komunikatów
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: d35cd496db32e1a2886f7ca06e7a3d0964f9c9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184580"
---
# <a name="messaging-protocols"></a>Protokoły obsługi komunikatów

Stos kanału Windows Communication Foundation (WCF) wykorzystuje kanały kodowania i transportu, aby przekształcić reprezentację wiadomości wewnętrznych w format sieci przewodowej i wysłać ją przy użyciu określonego transportu. Najczęstszym transportem używanym do współdziałania usług sieci Web jest HTTP, a najczęstszymi kodowaniami używanymi przez usługi sieci Web są oparte na języku XML SOAP 1.1, SOAP 1.2 i Mechanizm optymalizacji transmisji wiadomości (MTOM).

W tym temacie opisano szczegóły implementacji WCF <xref:System.ServiceModel.Channels.HttpTransportBindingElement>dla następujących protokołów zastosowanych przez program .

Specyfikacja/dokument:

- [Protokół HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [Oprawa HTTP SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Sekcja 7
- [Powiązanie HTTP w soap 1.2](https://www.w3.org/TR/soap12-part2) Sekcja 7

W tym temacie opisano szczegóły implementacji WCF dla następujących protokołów, które <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> zatrudniają.

Specyfikacja/dokument:

- [Xml](https://www.w3.org/TR/REC-xml)
- [MYDŁO 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [MYDŁO 1.2 Rdzeń](https://www.w3.org/TR/soap12-part1/)
- [Adresowanie WS 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [W3C Web Services Adresowanie 1.0 - Rdzeń](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [Adresowanie usług sieci Web W3C 1.0 — powiązanie z mydłem](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [Adresowanie usług sieci Web W3C 1.0 — powiązanie WSDL](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [Adresowanie usług sieci Web W3C 1.0 — metadane](https://www.w3.org/TR/ws-addr-metadata/)
- [Oprawa WSDL SOAP1.1](https://www.w3.org/TR/wsdl/)
- [Oprawa WSDL SOAP1.2](https://www.w3.org/Submission/wsdl11soap12/)

W tym temacie opisano szczegóły implementacji WCF dla następujących protokołów, który <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> zatrudnia.

Specyfikacja/dokument:

- [Xop](https://www.w3.org/TR/xop10/)
- [Wiązania MTOM + SOAP 1.2](https://www.w3.org/TR/soap12-mtom/)
- [Wiązania MTOM SOAP 1.1](https://www.w3.org/Submission/soap11mtom10/)
- [Twierdzenie zasad MTOM WS](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

W tym temacie używane są następujące przestrzenie nazw XML i skojarzone z nimi prefiksy:

| Prefiks | Jednolity identyfikator zasobów obszaru nazw (URI) |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| s12 |`http://www.w3.org/2003/05/soap-envelope` |
| Wsa |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| Xop |`http://www.w3.org/2004/08/xop/include` |
| xmime ( xmime ) |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| Dp |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>MYDŁO 1.1 i MYDŁO 1.2

### <a name="envelope-and-processing-model"></a>Model koperty i przetwarzania
WCF implementuje przetwarzanie koperty SOAP 1.1 zgodnie z profilem podstawowym 1.1 (BP11) i profilem podstawowym 1.0 (SSBP10). PRZETWARZANIE KOPERTY SOAP 1.2 jest realizowane zgodnie z mydłem 12-Part1.

W tej sekcji opisano niektóre wybory implementacji podjęte przez WCF w odniesieniu do BP11 i SOAP12-Part1.

#### <a name="mandatory-header-processing"></a>Obowiązkowe przetwarzanie nagłówka
WCF następuje zasady przetwarzania `mustUnderstand` nagłówków oznaczonych w wymaganiach PROTOKOŁU SOAP 1.1 i SOAP 1.2, z następującymi odmianami.

Komunikat, który wchodzi do stosu kanałów WCF jest przetwarzany przez poszczególne kanały skonfigurowane przez skojarzone elementy powiązania, na przykład kodowanie wiadomości tekstowych, zabezpieczenia, niezawodne wiadomości i transakcje. Każdy kanał rozpoznaje nagłówki z skojarzonego obszaru nazw i oznacza je jako zrozumiałe. Po wprowadzeniu komunikatu do dyspozytora program formatera operacji odczytuje nagłówki oczekiwane przez odpowiedni kontrakt na wiadomość/operację i oznacza je zrozumiane. Następnie dyspozytor sprawdza, czy wszystkie pozostałe nagłówki `mustUnderstand` nie są zrozumiałe, ale oznaczone jako i zgłasza wyjątek. Wiadomości zawierające `mustUnderstand` nagłówki przeznaczone dla adresata nie są przetwarzane przez kod aplikacji adresata.

Takie przetwarzanie warstwowe umożliwia oddzielenie warstw infrastruktury od warstw aplikacji węzła SOAP:

- B1111: Nagłówki, które nie są zrozumiałe, są wykrywane po przetworzyniu wiadomości przez stos kanału infrastruktury WCF, ale przed przetworzeniem przez aplikację

     Wartość `mustUnderstand` nagłówka różni się między MYDŁEM 1.1 i SOAP 1.2. Profil podstawowy 1.1 `mustUnderstand` wymaga, aby wartość 0 lub 1 dla komunikatów PROTOKOŁU SOAP 1.1. PROTOKÓŁ SOAP 1.2 pozwala na `false`0, 1 `true` i jako wartości, ale `xs:boolean` zaleca`false` `true`emitowanie kanonicznej reprezentacji wartości ( , ).

- B1112: WCF `mustUnderstand` emituje wartości 0 i 1 dla obu wersji SOAP 1.1 i SOAP 1.2 koperty SOAP. WCF akceptuje całą przestrzeń `xs:boolean` wartości `mustUnderstand` nagłówka (0, `false`1, , `true`)

#### <a name="soap-faults"></a>Błędy mydła
Poniżej znajduje się lista implementacji błędów protokołu SOAP specyficzne dla WCF.

- B2121: WCF zwraca następujące kody usterek `s11:mustUnderstand` `s11:Client`PROTOKOŁU `s11:Server`SOAP 1.1: , , i .

- B2122: WCF zwraca następujące kody usterek `s12:MustUnderstand` `s12:Sender`PROTOKOŁU `s12:Receiver`SOAP 1.2: , , i .

### <a name="http-binding"></a>Powiązanie HTTP

#### <a name="soap-11-http-binding"></a>Powiązanie HTTP w soap 1.1
WCF implementuje powiązanie HTTP SOAP1.1 zgodnie z sekcją 3.4 specyfikacji profilu podstawowego 1.1 z następującymi wyjaśnieniami:

- B2211: Usługa WCF nie implementuje przekierowywania żądań HTTP POST.

- B2212: Klienci WCF obsługują pliki cookie HTTP zgodnie z 3.4.8.

#### <a name="soap-12-http-binding"></a>Powiązanie HTTP w soap 1.2
WCF implementuje wiązanie HTTP PROTOKOŁU SOAP 1.2 zgodnie z opisem w specyfikacji SOAP 1.2-part 2 (SOAP12Part2) z następującymi wyjaśnieniami.

W programie SOAP 1.2 wprowadzono `application/soap+xml` opcjonalny parametr akcji dla typu nośnika. Ten parametr jest przydatny do optymalizacji wysyłania wiadomości bez konieczności analizowania treści komunikatu SOAP, gdy adresowanie WS nie jest używane.

- R2221: `application/soap+xml` Parametr akcji, gdy jest obecny w żądaniu SOAP `soapAction` 1.2, musi być zgodny z atrybutem `wsoap12:operation` elementu wewnątrz odpowiedniego powiązania WSDL.

- R2222: `application/soap+xml` Parametr akcji, jeśli jest obecny w komunikacie SOAP `wsa:Action` 1.2, musi być zgodny, gdy używane są adresowanie WS 2004/08 lub adresowanie WS 1.0.

Gdy adresowanie WS jest wyłączone, a żądanie przychodzące `Action` nie zawiera parametru akcji, komunikat jest uważany za nieokreślony.

## <a name="ws-addressing"></a>Adresowanie WS
WCF implementuje 3 wersje WS-Addressing:

- Adresowanie WS 2004/08

- W3C Web Services Adresowanie 1.0 Core (ADDR10-CORE) i mydło wiązania (ADDR10-SOAP)

- Adresowanie WS 1.0 - Metadane

### <a name="endpoint-references"></a>Odwołania do punktów końcowych
Wszystkie wersje WS-Addressing, który WCF implementuje używać odwołań do punktów końcowych do opisywania punktów końcowych.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Odwołania do punktów końcowych i wersje adresowania WS
WCF implementuje szereg protokołów infrastruktury, które używają WS-Addressing, a w szczególności `EndpointReference` element i `W3C.WsAddressing.EndpointReferenceType` klasy (na przykład WS-ReliableMessaging, WS-SecureConversation i WS-Trust). WCF obsługuje korzystanie z każdej wersji WS-Addressing z innymi protokołami infrastruktury. Punkty końcowe WCF obsługują jedną wersję adresowania WS na punkt końcowy.

Dla R3111 obszar nazw `EndpointReference` dla elementu lub typu używanego w wiadomościach wymienianych z punktem końcowym WCF musi być zgodna z wersją WS-Addressing zaimplementowane przez ten punkt końcowy.

Na przykład jeśli punkt końcowy WCF implementuje WS-ReliableMessaging, `AcksTo` nagłówek zwrócony przez taki punkt końcowy wewnątrz `EncodingBinding` `CreateSequenceResponse` używa wersji adresowania WS, która określa element dla tego punktu końcowego.

#### <a name="endpoint-references-and-metadata"></a>Odwołania i metadane punktów końcowych
Wiele scenariuszy wymaga przekazywania metadanych lub odwołania do metadanych dla danego punktu końcowego.

B3121: WCF wykorzystuje mechanizmy opisane w specyfikacji WS-MetadataExchange (MEX) sekcja 6, aby uwzględnić metadane dla odwołań do punktów końcowych według wartości lub odwołania.

Rozważmy scenariusz, w którym usługa WCF wymaga uwierzytelniania przy użyciu tokenu saml `http://sts.fabrikam123.com`(Security Assertions Markup Language) wystawionego przez wystawcę tokenu w . Punkt końcowy WCF opisuje to `sp:IssuedToken` wymaganie uwierzytelniania `sp:Issuer` przy użyciu potwierdzenia z zagnieżdżonego potwierdzenia wskazującego wystawcy tokenu. Aplikacje klienckie, które uzyskują dostęp do `sp:Issuer` potwierdzenia, muszą wiedzieć, jak komunikować się z punktem końcowym wystawcy tokenu. Klient musi znać metadane dotyczące wystawcy tokenu. Za pomocą rozszerzenia metadanych odniesienia punktu końcowego zdefiniowane w MEX, WCF zapewnia odwołanie do metadanych wystawcy tokenu.

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a>Nagłówki adresowania wiadomości

#### <a name="message-headers"></a>Nagłówki wiadomości
W obu wersjach WS-Addressing WCF używa następujących nagłówków komunikatów `wsa:Action`zgodnie `wsa:MessageID`ze `wsa:RelatesTo`specyfikacjami `wsa:To`, `wsa:ReplyTo`, , i .

B3211: Dla wszystkich wersji adresowania WS, WCF honoruje, ale nie produkuje po wyjęciu z pudełka, nagłówki komunikatów `wsa:FaultTo` adresowania WS i `wsa:From`.

Aplikacje, które współdziałają z aplikacjami WCF można dodać te nagłówki wiadomości i WCF będzie przetwarzać je odpowiednio.

#### <a name="reference-parameters-and-properties"></a>Parametry i właściwości odwołania

WCF implementuje przetwarzanie parametrów odniesienia punktu końcowego i właściwości referencyjnych zgodnie z odpowiednimi specyfikacjami.

B3221: Po skonfigurowaniu do używania adresu WS 2004/08, punkty końcowe WCF nie rozróżniają właściwości przetwarzania i parametrów referencyjnych.

### <a name="message-exchange-patterns"></a>Wzorce wymiany wiadomości
Sekwencja komunikatów zaangażowanych w wywołanie operacji usługi sieci Web jest określana jako *wzorzec wymiany wiadomości*. WCF obsługuje wzorce wymiany komunikatów jednokierunkowych, odpowiedzi na żądania i dupleksu. W tej sekcji wyjaśniono wymagania dotyczące adresowania WS dotyczące przetwarzania wiadomości w zależności od używanego wzorca wymiany wiadomości.

W tej sekcji żądający wysyła pierwszą wiadomość, a obiekt odpowiadający odbiera pierwszą wiadomość.

#### <a name="one-way-message"></a>Komunikat jednokierunkowy
Gdy punkt końcowy WCF jest skonfigurowany do `Action` obsługi komunikatów z podanym do naśladowania wzorca jednokierunkowego, punkt końcowy WCF następuje następujące zachowania i wymagania. O ile nie określono inaczej, zachowania i reguły mają zastosowanie do obu wersji WS-Addressing obsługiwanych w WCF:

- R3311: Żądający musi `wsa:To` `wsa:Action`zawierać , i nagłówki dla wszystkich parametrów referencyjnych określonych przez odwołanie do punktu końcowego. Gdy używany jest adresowanie WS 2004/08 i [właściwości odwołania] są określone przez odwołanie do punktu końcowego, odpowiednie nagłówki muszą zostać dodane do wiadomości zbyt.

- B3312: Żądający może `MessageID` `ReplyTo`zawierać `FaultTo` , i nagłówki. Infrastruktura odbiornika zignoruje je i zostaną przekazane do aplikacji.

- R3313: Gdy jest używany protokół HTTP i nie jest wysyłana żadna wiadomość w łzowej odpowiedzi HTTP, obiekt odpowiadający musi wysłać odpowiedź HTTP z pustą treścią i kodem stanu HTTP 202.

     Gdy transport HTTP jest w użyciu, a umowa operacji deklaruje wiadomość w jedną stronę, odpowiedź HTTP może nadal służyć `SequenceAcknowledgement` do wysyłania komunikatów infrastruktury — na przykład niezawodne wiadomości mogą wysyłać wiadomość w odpowiedzi HTTP.

- B3314: Obiekt odpowiadający WCF nie wysyła komunikatu o błędzie w odpowiedzi na komunikat jednokierunkowy.

#### <a name="request-reply"></a>Żądanie i odpowiedź
Gdy punkt końcowy WCF jest skonfigurowany dla `Action` wiadomości z danym do naśladowania wzorca żądania odpowiedzi, punkt końcowy WCF następuje zachowania i wymagania poniżej. O ile nie określono inaczej, zachowania i reguły mają zastosowanie do obu wersji WS-Addressing obsługiwanych w WCF:

- R3321: Żądający musi zawierać `wsa:To`w `wsa:Action` `wsa:MessageID`żądaniu , i nagłówki dla wszystkich parametrów referencyjnych lub właściwości odniesienia (lub obu) określonych przez odwołanie do punktu końcowego.

- R3322: Gdy używany jest adresowanie WS 2004/08, `ReplyTo` musi być również uwzględniony w żądaniu.

- R3323: Gdy WS-Addressing 1.0 `ReplyTo` jest używany i nie jest obecny w żądaniu, domyślne odwołanie do punktu końcowego z [address] właściwość równa `http://www.w3.org/2005/08/addressing/anonymous` jest używana.

- R3324: Żądający musi `wsa:To` `wsa:Action`zawierać `wsa:RelatesTo` , i nagłówki w wiadomości odpowiedzi, a także nagłówki dla wszystkich parametrów referencyjnych lub właściwości odwołania (lub obu) określonych przez odwołanie do punktu `ReplyTo` końcowego w żądaniu.

### <a name="web-services-addressing-faults"></a>Adresowanie błędów usług sieci Web
R3411: WCF produkuje następujące błędy zdefiniowane przez WS-Addressing 2004/08.

| Code | Przyczyna |
|----------|-----------|
| `wsa:DestinationUnreachable` | Wiadomość dotarła `ReplyTo` z treścią różniącą się od adresu odpowiedzi ustanowionego dla tego kanału; nie ma punktu końcowego nasłuchiwania pod adresem określonym w nagłówku Do. |
| `wsa:ActionNotSupported` | kanały infrastruktury lub dyspozytor skojarzony z punktem `Action` końcowym nie rozpoznają akcji określonej w nagłówku. |

R3412: WCF produkuje następujące błędy zdefiniowane przez WS-Addressing 1.0.

| Code | Przyczyna |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | Duplikat `wsa:To`, `wsa:ReplyTo`lub `wsa:From` `wsa:MessageID`. `wsa:RelatesTo` Duplikuj `RelationshipType`z tym samym . |
| `wsa10:MessageAddressingHeaderRequired` | Brak wymaganego nagłówka Adresowania. |
| `wsa10:DestinationUnreachable` | Wiadomość dotarła `ReplyTo` z treścią różniącą się od adresu odpowiedzi ustanowionego dla tego kanału. Nie ma punktu końcowego nasłuchiwania pod adresem określonym w nagłówku Do. |
| `wsa10:ActionNotSupported` | Akcja określona `Action` w nagłówku nie jest rozpoznawana przez kanały infrastruktury lub dyspozytora skojarzone z punktem końcowym. |
| `wsa10:EndpointUnavailable` | Kanał RM wysyła ten błąd z powrotem, wskazując, że punkt `CreateSequence` końcowy nie będzie przetwarzać sekwencji na podstawie badania nagłówków adresowania wiadomości. |

Kod w poprzednich tabelach `FaultCode` jest mapowany na `SubCode` w soap 1.1 i (z Code=Sender) w SOAP 1.2.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 Powiązania i WS-Policy Potwierdzenia

#### <a name="indicating-use-of-ws-addressing"></a>Wskazanie użycia adresowania WS
WCF używa potwierdzeń zasad, aby wskazać obsługę punktu końcowego dla określonej wersji adresowania WS.

Następujące twierdzenie zasad ma temat zasad punktu końcowego [WS-PA] i wskazuje wiadomości wysyłane i odbierane z punktu końcowego należy użyć WS-Addressing 2004/08.

```xml
<wsap:UsingAddressing />
```

To twierdzenie zasad rozszerza specyfikację WS-Addressing 2004/08.

Następujące twierdzenie zasad oznacza, że wiadomości wysłane/odebrane muszą używać adresu WS 1.0.

```xml
<wsam:Addressing/>
```

Następujące twierdzenie zasad ma temat zasad punktu końcowego [WS-PA] i wskazuje, że wiadomości wysyłane i odbierane z punktu końcowego muszą używać adresowania WS 2004/08.

```xml
<wsaw10:UsingAddressing />
```

Element `wsaw10:UsingAddressing` jest zapożyczony z [WS-Addressing-WSDL] i jest używany w kontekście WS-Policy zgodnie z tą specyfikacją, sekcja 3.1.2.

Użycie adresowania nie zmienia semantyki w 1.1, SOAP 1.1 i SOAP 1.2 POWIĄZANIA HTTP. Na przykład jeśli oczekuje się odpowiedzi na żądanie, które jest wysyłane do punktu końcowego, który używa adresowania i WSDL SOAP 1.x powiązanie HTTP, odpowiedź musi być wysłana przy użyciu odpowiedzi HTTP.

W przypadku odpowiedzi wysyłanych za pośrednictwem odpowiedzi http twierdzenie WS-AM jest:

```xml
<wsam:AnonymousResponses/>
```

Pełne twierdzenie zasad może wyglądać następująco:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Istnieją jednak wzorce wymiany komunikatów, które korzystają z dwóch niezależnych połączeń HTTP odwrotnych ustanowione między obiektem żądający i obiektu odpowiadającego, na przykład niechciane wiadomości jednokierunkowe wysyłane przez obiekt odpowiadający.

WCF oferuje funkcję, za pomocą której dwa podstawowe kanały transportu mogą tworzyć kanał composite duplex, gdzie jeden kanał jest używany dla komunikatów wejściowych, a drugi jest używany dla komunikatów wyjściowych. W przypadku transportu HTTP composite duplex zapewnia dwa odwrotne połączenia HTTP. Żądający używa jednego połączenia do wysyłania wiadomości do obiektu odpowiadającego, a osoba odpowiadająca używa drugiego do wysyłania wiadomości z powrotem do żądacza.

W przypadku odpowiedzi wysyłanych za pośrednictwem oddzielnych żądań http twierdzenie ws-am jest

```xml
<wsam:NonAnonymousResponses/>
```

Pełne twierdzenie zasad może wyglądać następująco:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Użycie następującego twierdzenia, które ma temat zasad punktu końcowego [WS-PA] w punktach końcowych, które używają wsdl 1.1 POWIĄZAŃ PROTOKOŁU HTTP PROTOKOŁU SOAP 1.x, wymaga użycia dwóch oddzielnych połączeń HTTP dla wiadomości płynących z osoby żądającej do obiektu odpowiadającego i osoby odpowiadającej do osoby żądającej, Odpowiednio.

```xml
<cdp:CompositeDuplex/>
```

Poprzednia instrukcja prowadzi do następujących `wsa:ReplyTo` wymagań w nagłówku dla komunikatów żądania:

- R3514: Żądania wiadomości wysyłane do punktu `ReplyTo` końcowego `[address]` musi mieć `http://www.w3.org/2005/08/addressing/anonymous` nagłówek z właściwości nie równa się, jeśli punkt końcowy używa WSDL 1.1 SOAP 1.x HTTP powiązania i ma alternatywę `wsap10:UsingAddressing` zasad z lub `wsap:UsingAddressing` potwierdzenia w połączeniu z `cdp:CompositeDuplex` dołączonym.

- R3515: Żądania wiadomości wysyłane do punktu `ReplyTo` końcowego `[address]` musi `http://www.w3.org/2005/08/addressing/anonymous`mieć nagłówek z `ReplyTo` właściwością równą , lub nie mają nagłówka w ogóle, jeśli punkt końcowy używa WSDL 1.1 SOAP 1.x HTTP powiązania i ma alternatywne zasady z `wsap10:UsingAddressing` twierdzeniem i nie `cdp:CompositeDuplex` potwierdzenia dołączone.

- R3516: Żądania wiadomości wysyłane do punktu `ReplyTo` końcowego `[address]` musi `http://www.w3.org/2005/08/addressing/anonymous` mieć nagłówek z właściwością równą, jeśli punkt końcowy używa WSDL 1.1 SOAP 1.x HTTP powiązania i ma alternatywę zasad z `wsap:UsingAddressing` twierdzeniem i nie `cdp:CompositeDuplex` potwierdzenia dołączone.

Specyfikacja WS-addressing WSDL próbuje opisać podobne powiązania protokołu, wprowadzając element `<wsaw:Anonymous/>` z trzema wartościami tekstowymi (wymaganymi, `wsa:ReplyTo` opcjonalnymi i zabronionymi) w celu wskazania wymagań w nagłówku (sekcja 3.2). Niestety taka definicja elementu nie jest szczególnie użyteczna jako twierdzenie w kontekście WS-Policy, ponieważ wymaga rozszerzenia specyficzne dla domeny do obsługi przecięcia alternatyw przy użyciu takiego elementu jako potwierdzenia. Taka definicja elementu wskazuje również `ReplyTo` wartość nagłówka, w przeciwieństwie do zachowania punktu końcowego w sieci, co sprawia, że specyficzne dla transportu HTTP.

#### <a name="action-definition"></a>Definicja akcji
Adresowanie WS 2004/08 definiuje `wsa:Action` atrybut dla `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementów. Powiązanie WS-Addressing 1.0 WSDL (WS-ADDR10-WSDL) definiuje `wsaw10:Action`podobny atrybut.

Jedyną różnicą między nimi jest domyślna semantyka wzorca akcji opisana odpowiednio w sekcji 3.3.2 WS-ADDR i sekcji 4.4.4 WS-ADDR10-WSDL.

Uzasadnione jest, aby mieć dwa punkty końcowe, które współużytkują takie same `portType` (lub umowy, w terminologii WCF), ale przy użyciu różnych wersji WS-Addressing. Ale biorąc pod uwagę, `portType` że akcja jest zdefiniowana przez `portType`i nie powinny zmieniać się w punktach końcowych, które implementują , staje się niemożliwe do obsługi obu wzorców akcji domyślnych.

Aby rozwiązać ten problem, WCF obsługuje `Action` jedną wersję atrybutu.

B3521: WCF używa `wsaw10:Action` atrybutu `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` na elementy zdefiniowane w WS-ADDR10-WSDL do określenia identyfikatora `Action` URI dla odpowiednich komunikatów, niezależnie od wersji adresowania WS używane przez punkt końcowy.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Korzystanie z odwołania do punktu końcowego wewnątrz portu WSDL
WS-ADDR10-WSDL sekcja 4.1 `wsdl:port` rozszerza element, `<wsa10:EndpointReference…/>` aby uwzględnić element podrzędny, aby opisać punkt końcowy w warunkach adresowania WS. WCF rozszerza to narzędzie na WS-Addressing 2004/08, pozwalając `<wsa:EndpointReference…/>` `wsdl:port`na pojawienie się jako element podrzędny .

- R3531: Jeśli punkt końcowy ma dołączoną `<wsaw10:UsingAddressing/>` alternatywę zasad `wsdl:port` z asercjami zasad, odpowiedni element może zawierać element `<wsa10:EndpointReference …/>`podrzędny .

- R3532: Jeśli `wsdl:port` zawiera element `<wsa10:EndpointReference …/>`podrzędny, `wsa10:EndpointReference/wsa10:Address` wartość elementu podrzędnego `@address` musi być `wsdl:port` zgodna z wartością atrybutu elementu równorzędnego. / `wsdl:location`

- R3533: Jeśli punkt końcowy ma dołączoną alternatywę zasad z `<wsap:UsingAddressing/>` twierdzeniem zasad, odpowiedni `wsdl:port` element może zawierać element `<wsa:EndpointReference …/>`podrzędny .

- R3534: Jeśli `wsdl:port` zawiera element `<wsa:EndpointReference …/>`podrzędny, `wsa:EndpointReference/wsa:Address` wartość elementu podrzędnego `@address` musi być `wsdl:port` zgodna z wartością atrybutu elementu równorzędnego. / `wsdl:location`

### <a name="composition-with-ws-security"></a>Kompozycja z WS-Security
Zgodnie z sekcjami zagadnienia dotyczące zabezpieczeń w WS-ADDR i WS-ADDR10, wszystkie nagłówki wiadomości adresowych są zalecane do podpisania razem z treścią wiadomości, aby powiązać je ze sobą.

Gdy usługa WS-Security jest używana do ochrony integralności wiadomości, nagłówki wiadomości adresowania WS oraz nagłówki wynikające z parametrów referencyjnych lub właściwości (lub obu) muszą być podpisane razem z treścią wiadomości.

### <a name="examples"></a>Przykłady

#### <a name="one-way-message"></a>Komunikat jednokierunkowy
W tym scenariuszu nadawca wysyła komunikat jednokierunkowy do odbiornika. Używane są adresy 1.2, HTTP 1.1 i W3C WS-Addressing 1.0.

Struktura żądania wiadomości: nagłówki wiadomości `wsa10:To` `wsa10:Action` zawierają i elementy. Treść wiadomości zawiera `<app:Ping>` określony element z obszaru nazw aplikacji.

Nagłówki HTTP: Miejsce docelowe w POST `wsa10:To` pasuje do identyfikatora URI w elemencie.

Nagłówek Typ zawartości ma wartość `application/soap+xml` wymaganą przez soap 1.2. Parametry `charset` `action` i są uwzględniane. Parametr `action` nagłówka Typ zawartości jest zgodny `wsa10:Action` z wartością nagłówka wiadomości.

```
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

Odbiorca odpowiada pustą odpowiedzią HTTP i stanem 202. Przykład odpowiedzi HTTP:

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a>Mechanizm optymalizacji transmisji komunikatów SOAP
W tej sekcji opisano szczegóły implementacji WCF dla protokołu HTTP SOAP MTOM. Technologia MTOM to mechanizm kodowania wiadomości SOAP tej samej klasy co tradycyjne kodowanie tekstu/XML lub kodowanie binarne WCF. MTOM obejmuje:

- Mechanizm kodowania i pakowania XML opisany przez [XOP], który optymalizuje elementy informacji XML zawierające dane binarne zakodowane w formacie base64 na oddzielne części binarne.

- Hermetyzacja MIME pakietu XOP, który serializuje zestaw informacji XML i każdą część binarną pakietu XOP do oddzielnej części MIME.

- Kodowanie MIME XOP zastosowane do koperty SOAP 1.x.

- Powiązanie transportu HTTP.

Możliwe jest użycie MTOM z transportami innych niż HTTP z WCF. Jednak w tym temacie skupimy się na HTTP.

Format MTOM wykorzystuje duży zestaw specyfikacji obejmujących sam mtom, XOP i MIME. Modułowość tego zestawu specyfikacji sprawia, że nieco trudno jest odtworzyć dokładne wymagania dotyczące formatu i przetwarzania semantyki. W tej sekcji opisano wymagania dotyczące formatu i przetwarzania powiązania HTTP MTOM.

### <a name="mtom-message-encoding"></a>Kodowanie komunikatów MTOM

#### <a name="generating-mtom-messages"></a>Generowanie komunikatów MTOM
Sekcja [XOP] 3.1 opisuje proces kodowania XML z elementami informacji, które zawierają wartości base64 w abstrakcyjnie zdefiniowanym pakiecie XOP.

Następująca sekwencja kroków opisuje proces kodowania specyficznego dla MTOM:

1. Upewnij się, że koperta PROTOKOŁU SOAP, która `[namespace name]` ma `http://www.w3.org/2004/08/xop/include` być `[local name]` `Include`zakodowana, nie zawiera elementu informacyjnego o a i a .

2. Utwórz pusty pakiet MIME.

3. Identyfikować w oryginalnym zestawie informacji XML elementy informacji o elemencie, które mają być zoptymalizowane. Aby elementy mają być zoptymalizowane, znaki, `[children]` które składają się na element informacji o `xs:base64Binary` elemencie musi być w formie kanonicznej (patrz XSD-2, 3.2.16 base64Binary) i nie może zawierać żadnych znaków odstępu poprzedzających, wbudowanych lub następujących po zawartości niebiału.

4. Utwórz kopertę XOP SOAP, która jest kopią oryginalnej koperty SOAP, ale z elementami podrzędnymi każdego elementu informacyjnego określonego w poprzednim kroku zastąpionym elementem informacji o elemencie `xop:Include` skonstruowanym w następujący sposób:

    1. Przekształć zastąpione znaki w dane binarne, przetwarzając je jako dane zakodowane w formacie base4.

    2. Wygeneruj unikatową wartość nagłówka content-id, która spełnia wymagania R3133 i R3134.

    3. Wygeneruj nagłówek MIME kodowania transferu zawartości z wartością binarną.

    4. Jeśli element informacji o elemencie, który jest `xop:Include` optymalizujący `xmime:contentType` ([nadrzędny] nowo wstawionego elementu informacyjnego) `xmime:contentType` ma element informacji o atrybutach, wygeneruj nagłówek MIME typu zawartości z wartością atrybutu.

    5. Wygeneruj nową binarną część MIME z zawartością utworzoną przez dane binarne zdekodowanych danych z zastąpionych znaków przetworzonych jako base64, nagłówek Content-ID z 4b, Nagłówek kodowania transferu zawartości z 4c, nagłówek typu zawartości, jeśli jest generowany w kroku 4d.

    6. Dodaj `href` atrybut do `xop:Include` elementu o wartości cid: uri pochodzące z content-id wartość nagłówka generowane w kroku 4b. Usuń otaczające\<znaki " " i ">", usuń adres URL z pozostałego ciągu i dodaj prefiks `cid:`. Następujący minimalny zestaw znaków musi być zmieniony przez RFC1738 i RFC2396. Inne znaki mogą być zmienione.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Utwórz główną część MIME za pomocą koperty XOP SOAP z kroku 4.

6. Napisz nagłówki HTTP, w tym nagłówek HTTP Content-Type.

7. Napisz pakiet MIME.

#### <a name="processing-mtom-messages"></a>Przetwarzanie komunikatów MTOM
Przetwarzanie wiadomości MTOM jest dokładnym odwrótem procesu opisanego w poprzedniej sekcji "Generowanie komunikatów MTOM":

1. Upewnij się, że główna część `application/xop+xml`MIME ma typ zawartości .

2. Skonstruuj kopertę protokołu SOAP, analizując główną część MIME pakietu jako dokument XML. Kodowanie znaków jest `charset` określane przez parametr typu zawartości głównej części MIME.

3. Dla każdego elementu elementu informacji element w skonstruowanej puli danych SOAP, który ma, jako jedyny element członkowski jego [elementy podrzędne] właściwość, element informacji o elemencie: `xop:Include`

    1. Usuń `cid:` prefiks i unescape wszystkie sekwencje URI-escape (RFC 2396) w wartości `@href` atrybutu `xop:Include` elementu. Ciąg wynikowy należy\<ująć w " ", ">".

    2. Zlokalizuj część MIME z wartością nagłówka Content-ID, która odpowiada ciągowi pochodnemu w kroku 3a.

    3. Zastąp `xop:Include` element informacji `children` o elemencie, który pojawia się we właściwości każdego elementu, elementami informacji o znakach reprezentującymi kanoniczne kodowanie base64 (patrz XSD-2, 3.2.16 base64Binary) treści jednostki części MIME identyfikowanej w kroku 3b (skutecznie zastąp element informacji `xop:Include` o elemencie elementu danymi zrekonstruowanymi z części pakietu).

#### <a name="http-content-type-header"></a>Nagłówek typu zawartości HTTP
Poniżej znajduje się lista wyjaśnień WCF dla formatu nagłówka http typu zawartości komunikatu zakodowanego przez protokół SOAP 1.x MTOM, pochodzących z wymagań określonych w samej specyfikacji MTOM i pochodzących z MTOM i RFC 2387.

- R4131: Nagłówek typu zawartości HTTP musi mieć wartość wieloczęściową/pokrewną (bez uwzględniania wielkości liter) i jego parametry. Nazwy parametrów są niewrażliwe na wielkości liter. Kolejność parametrów nie jest znacząca.

- Pełny formularz Backus-Naur (BNF) nagłówka typu zawartości dla wiadomości MIME jest wymieniony w RFC 2045, sekcja 5.1.

- R4132: Nagłówek typu zawartości HTTP musi mieć parametr `application/xop+xml` typu o wartości ujętej w cudzysłowy.

Chociaż wymóg używania podwójnych cudzysłowów nie jest jawny w RFC 2387, tekst zauważa, że wszystkie\@parametry multiczęści/pokrewne typy nośników najprawdopodobniej zawierają znaki zastrzeżone, takie jak " " lub "/" i dlatego potrzebują podwójnych cudzysłowów.

- R4133: Nagłówek typu zawartości HTTP powinien mieć parametr start z wartością nagłówka Content-ID części MIME zawierającej kopertę SOAP 1.x, ujętą w podwójne cudzysłowy. Jeśli parametr start zostanie pominięty, pierwsza część MIME musi zawierać kopertę SOAP 1.x.

- R4134: Nagłówek typu zawartości HTTP dla wiadomości zakodowanej w formacie SOAP 1.1 MTOM musi zawierać parametr informacji początkowej o wartości text/xml, ujęty w podwójne cudzysłowy.

- R4135: Nagłówek typu zawartości HTTP dla wiadomości zakodowanej w filtrze SOAP 1.2 MTOM `application/soap+xml`musi zawierać parametr informacji początkowej o wartości , ujętej w podwójny cudzysłów.

- R4136: Nagłówek typu zawartości HTTP dla wiadomości zakodowanej w technologii SOAP 1.x MTOM musi mieć parametr granicy z wartością (ujętą w cudzysłów), która odpowiada granicy MIME BNF zdefiniowanej w RFC 2046, sekcja 5.1.1

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Przykłady:

     Poprawne

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     Poprawne

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     Niepoprawne

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a>Część programu Infoset MIME
Koperta SOAP 1.x jest hermetyzowana jako główna część pakietu XOP `infoset` MIME i jest często nazywana częścią.

- R4141: Koperta SOAP 1.x musi być hermetyzowana jako główna część `infoset` pakietu XOP MIME, nazywana częścią i odwołująca się od typu zawartości HTTP.

- R4142: Część `Infoset` SOAP musi zawierać następujące nagłówki `Content-ID` `Content-Transfer-Encoding`MIME: , , i `Content-Type`.

Format nagłówka Content-ID jest zdefiniowany przez RFC 2045 jako

```
"Content-ID" ":" msg-id
```

gdzie `msg-id` jest zdefiniowany w RFC 2822 (który zastępuje RFC 822, o których mowa w RFC 2045) jako:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

i jest w rzeczywistości adresem\<e-mail zawartym w " " i ">". Prefiks `[CFWS]` i sufiks zostały dodane w RFC 2822 do przenoszenia komentarzy i nie powinny być używane do zachowania interoperacyjności.

R4143: Wartość nagłówka Content-ID dla części Infoset `msg-id` MIME musi być zgodna z `[CFWS]` produkcją z RFC 2822 z pominiętymi częściami prefiksu i sufiksu.

Wiele implementacji MIME złagodziło wymagania dotyczące\<wartości zawartej w " i ">" `absoluteURI` jako adresu\<e-mail i używanej w " , ">" oprócz adresu e-mail. Ta wersja WCF używa wartości nagłówka MIME Content-ID formularza:

```
Content-ID: <http://tempuri.org/0>
```

R4144: Procesory MTOM powinny akceptować wartości nagłówka `msg-id`Content-ID, które są zgodne z następującymi zrelaksowanymi .

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045) udostępnia nagłówek kodowania transferu zawartości do przekazywania kodowania zawartości części MIME. Domyślnie zdefiniowany dla kodowania transferu zawartości jest 7-bitowy, co nie jest odpowiednie dla większości komunikatów PROTOKOŁU SOAP, więc nagłówek kodowania transferu zawartości jest potrzebny do większej współdziałania:

- R4145: Część zestawu informacyjnego SOAP musi zawierać nagłówek kodowania transferu zawartości.

- R4146: Jeśli kodowanie znaków koperty PROTOKOŁU SOAP to UTF-8, wartość nagłówka Kodowanie transferu zawartości musi być 8-bitowa.

- R4147: Jeśli kodowanie znaków koperty PROTOKOŁU SOAP to UTF-16, wartość nagłówka Kodowanie transferu zawartości musi być binarna.

- Zgodnie z sekcją 5 [XOP]

- R4148: CZĘŚĆ zestawu informacyjnego SOAP1.1 musi zawierać nagłówek typ zawartości z aplikacją typu nośnika/xop+xml i parametrami type="text/xml" i charset

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: Część zestawu informacyjnego SOAP 1.2 musi zawierać `application/xop+xml` nagłówek Typ zawartości`application/soap+xml`z `charset`typem nośnika i parametrami type=" i .

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     Podczas XOP definiuje `charset` parametr, `application/xop+xml` aby być opcjonalne, jest on potrzebny do współdziałania podobne `charset` do `text/xml` wymagania BP 1.1 na parametr dla typu nośnika.

- R41410: `type` Parametry `charset` i parametry muszą znajdować się w nagłówku typ zawartości części zestawu informacyjnego SOAP 1.x.

#### <a name="wcf-endpoint-support-for-mtom"></a>Obsługa punktów końcowych WCF dla MTOM
Celem MTOM jest zakodowanie wiadomości SOAP w celu optymalizacji danych zakodowanych w bazie 64. Poniżej znajduje się lista ograniczeń:

- R4151: Każdy element informacji o elemencie zawierający dane zakodowane w bazie 64 mogą być zoptymalizowane.

- B4152: WCF optymalizuje elementy informacji o elemencie, które zawierają dane zakodowane w bazie 64 i przekraczają 1024 bajty długości.

Punkt końcowy WCF skonfigurowany do używania MTOM zawsze będzie wysyłać wiadomości zakodowane w MTOM. Nawet jeśli żadna część nie spełnia wymaganych kryteriów, wiadomość jest nadal zakodowana w MTOM (serializowana jako pakiet MIME z pojedynczą częścią MIME zawierającą otoczkę SOAP).

### <a name="ws-policy-assertion-for-mtom"></a>Twierdzenie zasad WS dla MTOM
WCF używa następującego potwierdzenia zasad, aby wskazać użycie MTOM według punktu końcowego:

```xml
<wsoma:OptimizedMimeSerialization ... />
```

- R4211: Poprzednie twierdzenie zasad ma temat zasad punktu końcowego i określa, że wszystkie wiadomości wysyłane do punktu końcowego i odbierane z punktu końcowego muszą być zoptymalizowane przy użyciu programu MTOM.

- B4212: Po skonfigurowaniu do używania optymalizacji MTOM punkt końcowy WCF dodaje twierdzenie zasad `wsdl:binding`MTOM do zasad dołączonych do odpowiedniego .

### <a name="composition-with-ws-security"></a>Kompozycja z WS-Security
MTOM jest mechanizmem kodowania, `text/xml` który jest podobny do i WCF Binary XML. MTOM oferuje naturalny skład z protokołami WS-Security i innymi protokołami WS-*: komunikat zabezpieczony za pomocą WS-Security można zoptymalizować za pomocą programu MTOM.

### <a name="examples"></a>Przykłady

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 Komunikat zakodowany przy użyciu MTOM

```
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>WCF Secure SOAP 1.2 Komunikat zakodowany za pomocą MTOM
W tym przykładzie komunikat jest kodowany przy użyciu MTOM i SOAP 1.2, który jest chroniony przy użyciu WS-Security. Części binarne zidentyfikowane do kodowania `BinarySecurityToken`są `CipherValue` zawartością , odpowiadającej `EncryptedData` zaszyfrowanemu podpisowi i zaszyfrowanej treści. Należy zauważyć, że `CipherValue` nie `EncryptedKey` został zidentyfikowany do optymalizacji przez WCF, ponieważ jego długość jest mniejsza niż 1024 bajtów.

```
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml";
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```
