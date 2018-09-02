---
title: Protokoły obsługi komunikatów
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 3e56636e8364eec333f9585a0f62f6510561d1cc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405062"
---
# <a name="messaging-protocols"></a>Protokoły obsługi komunikatów
Stos kanał Windows Communication Foundation (WCF) wykorzystuje kanały transportu i kodowania do przekształcania reprezentacji wewnętrznej komunikatu do jego formatu i wysyłania go przy użyciu danego transportu. Najbardziej typowe transportu współdziałania w ramach usług sieci Web, jest protokół HTTP i najbardziej typowe kodowania, używane przez usługi sieci Web są oparte na języku XML protokołu SOAP 1.1, protokołu SOAP 1.2 i komunikat transmisji optymalizacji mechanizm (MTOM).  
  
 W tym temacie omówiono szczegóły implementacji programu WCF dla następujących protokołów przez <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|HTTP 1.1|http://www.ietf.org/rfc/rfc2616.txt|  
|SOAP 1.1 powiązania protokołu HTTP|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Sekcja 7|  
|SOAP 1.2 powiązania protokołu HTTP|http://www.w3.org/TR/soap12-part2/, Sekcja 7|  
  
 W tym temacie omówiono szczegóły implementacji programu WCF dla następujących protokołów <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> stosować.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|XML|http://www.w3.org/TR/REC-xml|  
|PROTOKOŁU SOAP 1.1|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|SOAP 1.2 Core|http://www.w3.org/TR/soap12-part1/|  
|WS-Addressing 2004/08|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|Eliminowanie Core 1.0 - usług sieci Web W3C|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|Eliminowanie 1.0 - powiązanie protokołu SOAP usług sieci Web W3C|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|Eliminowanie 1.0 - Powiązanie WSDL usług sieci Web W3C|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
Eliminowanie 1.0 - metadanych usług sieci Web W3C|http://www.w3.org/TR/ws-addr-metadata/|  
|Powiązanie SOAP1.1 WSDL|http://www.w3.org/TR/wsdl/|  
|Powiązanie SOAP1.2 WSDL|http://www.w3.org/Submission/wsdl11soap12/|  
  
 W tym temacie omówiono szczegóły implementacji programu WCF dla następujących protokołów <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> wykorzystuje.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|XOP|http://www.w3.org/TR/xop10/|  
|MTOM i SOAP 1.2 powiązania|http://www.w3.org/TR/soap12-mtom/|  
|MTOM SOAP 1.1 powiązania|http://www.w3.org/Submission/soap11mtom10/|  
|Potwierdzenie WS-Policy MTOM|http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.|  
  
 Następujące obszary nazw XML i skojarzone prefiksy są używane w tym temacie.  
  
|Prefiks|Namespace Uniform Resource Identifier (URI)|  
|------------|---------------------------------------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|s12|http://www.w3.org/2003/05/soap-envelope|  
|Aplikacja wsa|http://www.w3.org/2004/08/addressing|  
|wsam|http://www.w3.org/2007/05/addressing/metadata|  
|wsap|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|wsa10|http://www.w3.org/2005/08/addressing|  
|wsaw10|http://www.w3.org/2006/05/addressing/wsdl|  
|XOP|http://www.w3.org/2004/08/xop/include|  
|xmime|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
punkt dystrybucji|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a>Protokołu SOAP 1.1 i SOAP 1.2  
  
### <a name="envelope-and-processing-model"></a>Koperta i przetwarzanie modelu  
 Usługi WCF implementuje przetwarzania koperty protokołu SOAP 1.1 następującego Basic Profile 1.1 (BP11) oraz podstawowe profilu 1.0 (SSBP10). SOAP 1.2 koperty przetwarzania jest wdrażane zgodnie z SOAP12 — część 1.  
  
 W tej sekcji opisano niektóre opcje implementacji podjęte przez architekturę WCF w odniesieniu do BP11 i SOAP12 — część 1.  
  
#### <a name="mandatory-header-processing"></a>Wymagany nagłówek przetwarzania  
 Usługi WCF regułom do przetwarzania nagłówki oznaczony `mustUnderstand` opisane w specyfikacji protokołu SOAP 1.1 i SOAP 1.2, za pomocą następujących zmian.  
  
 Komunikat, który wprowadzi stosu kanału WCF jest przetwarzany przez poszczególnych kanałów skonfigurowane przez powiązanie skojarzone elementy, na przykład, kodowania wiadomości tekstowe, zabezpieczeń, niezawodną obsługę komunikatów i transakcji. Poszczególnych kanałów rozpoznaje nagłówki z skojarzone przestrzeni nazw i oznacza je jako zrozumiałe. W momencie komunikat wejścia dyspozytor, element formatujący operacji odczytuje nagłówki oczekiwany przez odpowiedni kontrakt komunikatów/operacji i znaczniki ich zrozumienie. Następnie Dyspozytor sprawdza, czy wszystkie pozostałe nagłówki nie są zrozumiałe, ale oznaczone jako `mustUnderstand` i zgłasza wyjątek. Komunikaty, które zawierają `mustUnderstand` nagłówki, które są przeznaczone dla odbiorcy nie są przetwarzane przez kod aplikacji odbiorcy.  
  
 Takie warstwie przetwarzania umożliwia oddzielenie warstwy infrastruktury i aplikacji węzła SOAP:  
  
-   B1111: Nagłówki, które nie są zrozumiałe są wykrywane po komunikat jest przetwarzany przez stos kanału infrastruktura WCF, ale przed jego przetworzeniem przez aplikację  
  
     `mustUnderstand` Wartość nagłówka różni się między SOAP 1.1 i SOAP 1.2. Basic Profile 1.1 wymaga, aby `mustUnderstand` wartość wynosić 0 lub 1 dla wiadomości SOAP 1.1. Protokołu SOAP 1.2 zezwala na 0, 1, `false`, i `true` jako wartości, ale zaleca się emitowanie canonical reprezentację `xs:boolean` wartości (`false`, `true`).  
  
-   B1112: Emituje WCF `mustUnderstand` wartości 0 i 1 dla wersji SOAP 1.1 i SOAP 1.2 koperty protokołu SOAP. Usługi WCF akceptuje miejsce całą wartość `xs:boolean` dla `mustUnderstand` nagłówka (0, 1, `false`, `true`)  
  
#### <a name="soap-faults"></a>Błędy protokołu SOAP  
 Oto lista SOAP WCF określonych błędów implementacji.  
  
-   B2121: WCF zwraca następujące kody błędów protokołu SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, i `s11:Server`.  
  
-   B2122: WCF zwraca następujące kody błędów protokołu SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, i `s12:Receiver`.  
  
### <a name="http-binding"></a>Powiązanie HTTP  
  
#### <a name="soap-11-http-binding"></a>SOAP 1.1 powiązania protokołu HTTP  
 Usługi WCF implementuje powiązania SOAP1.1 HTTP po specyfikacji Basic Profile 1.1, sekcji 3.4 wyjaśnienia następujące:  
  
-   B2211: Usługi WCF nie implementuje Przekierowywanie żądań HTTP POST.  
  
-   B2212: Klienci WCF obsługujących pliki cookie HTTP, zgodnie z 3.4.8.  
  
#### <a name="soap-12-http-binding"></a>SOAP 1.2 powiązania protokołu HTTP  
 Usługi WCF implementuje powiązania protokołu SOAP 1.2 HTTP, zgodnie z opisem w specyfikacją protokołu SOAP 1.2 — część 2 (SOAP12Part2) przy użyciu następujących wyjaśnienia.  
  
 Protokołu SOAP 1.2 wprowadzony parametr opcjonalny akcji dla `application/soap+xml` typu nośnika. Ten parametr jest przydatne do optymalizacji wysyłania wiadomości bez konieczności, czy treść komunikatu protokołu SOAP można w sytuacji, gdy nie zastosowano WS-Addressing.  
  
-   R2221: `application/soap+xml` parametr akcji, jeśli jest obecny w żądaniu SOAP 1.2, muszą być zgodne `soapAction` atrybutu na `wsoap12:operation` element wewnątrz odpowiednie Powiązanie WSDL.  
  
-   R2222: `application/soap+xml` parametr akcji, jeśli jest obecny na wiadomości SOAP 1.2, muszą być zgodne `wsa:Action` gdy są używane usługi WS-Addressing 2004/08 lub 1.0 WS-Addressing.  
  
 Gdy WS-Addressing jest wyłączona i przychodzące żądanie nie zawiera parametr akcji, komunikat `Action` zostanie uznane za określony.  
  
## <a name="ws-addressing"></a>WS-Addressing  
 Usługi WCF implementuje usługi WS-Addressing 3 wersjach:  
  
-   WS-Addressing 2004/08  
  
-   Usługi sieci Web W3C adresowania Core 1.0 (ADDR10-Rdzeniowe) i protokołu SOAP powiązania (ADDR10 SOAP)  
  
-   WS-Addressing 1.0 — metadanych  
  
### <a name="endpoint-references"></a>Odwołania do punktu końcowego  
 Wszystkie wersje WS-Addressing, który implementuje WCF użyć odwołania do punktu końcowego do opisania punktów końcowych.  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a>Odwołania do punktu końcowego i WS-Addressing wersji  
 Usługi WCF implementuje wiele protokołów infrastruktury, które używają protokołu WS-Addressing, w szczególności `EndpointReference` elementu i `W3C.WsAddressing.EndpointReferenceType` klasy (na przykład WS-ReliableMessaging, WS-SecureConversation i WS-Trust). Usługi WCF obsługuje dowolną wersję WS-Addressing z innymi protokołami infrastruktury. Punkty końcowe WCF obsługują jedną wersję WS-Addressing za punkt końcowy.  
  
 Dla R3111, przestrzeń nazw dla `EndpointReference` elementu lub typ użyty w komunikatów wymienianych z punktem końcowym WCF musi odpowiadać wersji WS-Addressing implementowany przez ten punkt końcowy.  
  
 Na przykład, jeśli punkt końcowy usługi WCF implementuje WS-ReliableMessaging `AcksTo` zwracane przez punkt końcowy, wewnątrz `CreateSequenceResponse` korzysta z wersji WS-Addressing, `EncodingBinding` element określa dla tego punktu końcowego.  
  
#### <a name="endpoint-references-and-metadata"></a>Odwołania do punktu końcowego i metadanych  
 Liczba scenariuszy wymagają komunikacji metadanych lub odwołanie do metadanych dla danego punktu końcowego.  
  
 B3121: WCF zatrudnia mechanizmów, które opisano w specyfikacji WS-MetadataExchange (MEX) 6 sekcji, aby zawierać metadane dotyczące odwołań do endpoint, przez wartość lub przez odwołanie.  
  
 Rozważmy scenariusz, w którym usługa WCF wymaga uwierzytelniania za pomocą tokenu potwierdzenia języka SAML (Security Markup) wystawiony przez emitenta tokenu w http://sts.fabrikam123.com. Punkt końcowy usługi WCF w tym artykule opisano to wymaganie uwierzytelniania za pomocą `sp:IssuedToken` potwierdzenia z zagnieżdżoną `sp:Issuer` potwierdzenie wskazujący wystawcy tokenów. Aplikacje klienckie, które uzyskują dostęp `sp:Issuer` potwierdzenia musi wiedzieć, jak komunikować się z punktem końcowym wystawcy tokenów. Klient musi wiedzieć, metadane dotyczące wystawcy tokenów. Korzystanie z rozszerzeń metadane odwołania punkt końcowy zdefiniowany w punkcie końcowym MEX, WCF zawiera odwołanie do metadanych wystawcy tokenów.  
  
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
  
### <a name="message-addressing-headers"></a>Nagłówki adresy wiadomości  
  
#### <a name="message-headers"></a>Nagłówki wiadomości  
 Dla obu wersji WS-Addressing WCF używa następujących nagłówków wiadomości według specyfikacji `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, i `wsa:RelatesTo`.  
  
 B3211: W przypadku wszystkich wersji WS-Addressing WCF honoruje, ale nie tworzy gotowych nagłówków wiadomości WS-Addressing `wsa:FaultTo` i `wsa:From`.  
  
 Te nagłówki komunikatów i WCF będzie przetwarzać je w związku z tym można dodać aplikacji, które współdziałają z aplikacjami usługi WCF.  
  
#### <a name="reference-parameters-and-properties"></a>Właściwości i parametrów w formie odwołań  
 Usługi WCF implementuje przetwarzania parametrów odwołania punktu końcowego i odwołania p  
  
 właściwości zgodnie z odpowiednimi wymaganiami.  
  
 B3221: Gdy skonfigurowana do używania protokołu WS-Addressing 2004/08, punktami końcowymi programu WCF nie odróżnić przetwarzania odwołanie do właściwości i parametrów w formie odwołań.  
  
### <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 Kolejność komunikatów związane z wywołania operacji usługi sieci Web jest nazywany *wymiany komunikatów*. Obsługuje WCF jednokierunkowe, "żądanie-odpowiedź" i dwukierunkowego wiadomości programu exchange wzorców. W tej sekcji wyjaśnia WS-Addressing na wymagania dotyczące przetwarzania w zależności od wymiany komunikatów używane wiadomości.  
  
 W tej sekcji osoby żądającej wysyła pierwszy komunikat, i obiekt odpowiadający odbiera pierwszy komunikat.  
  
#### <a name="one-way-message"></a>Komunikat jednokierunkowy  
 Po skonfigurowaniu punktu końcowego WCF w celu obsługi komunikatów z danego `Action` z jednokierunkową wzorzec, punkt końcowy usługi WCF następuje następujące zachowania i wymagania. O ile nie określono inaczej, zachowań i reguły mają zastosowanie dla obu wersji WS-Addressing obsługiwane w programie WCF:  
  
-   R3311: Strona żądająca może zawierać `wsa:To`, `wsa:Action`, nagłówki i dla wszystkich parametrów odwołania, określony przez odwołanie do punktu końcowego. Gdy służy WS-Addressing 2004/08 i [odwołanie do właściwości] są określone przez odwołanie do punktu końcowego, odpowiednie nagłówki muszą zostać dodane do komunikatu zbyt.  
  
-   B3312: Strona żądająca może obejmować `MessageID`, `ReplyTo`, i `FaultTo` nagłówków. Infrastruktura odbiorcy, zostaną one zignorowane, a zostaną one przekazane do aplikacji.  
  
-   R3313: Gdy HTTP jest używany żaden komunikat jest wysyłany na gałęzi odpowiedzi HTTP, odpowiadający musi wysyłać odpowiedź HTTP z pustą treść i kod stanu HTTP 202.  
  
     Podczas transportu HTTP jest używany i kontrakt operacji deklaruje jednokierunkowa wiadomość, odpowiedź HTTP nadal może być używany do wysyłania wiadomości infrastruktury — na przykład wysłać niezawodną obsługę komunikatów `SequenceAcknowledgement` komunikat na odpowiedzi HTTP.  
  
-   B3314: W odpowiedzi na komunikat jednokierunkowy obiektu odpowiadającego w trybie usługi WCF nie wysyła komunikat o błędzie.  
  
#### <a name="request-reply"></a>Żądanie i odpowiedź  
 Jeśli punkt końcowy usługi WCF została skonfigurowana do wiadomości z danym `Action` na zgodny z wzorcem "żądanie-odpowiedź" punktu końcowego WCF następuje zachowań i poniższe wymagania. Chyba że określono inaczej, zachowań i reguły mają zastosowanie w przypadku obu wersji WS-Addressing obsługiwane w programie WCF:  
  
-   R3321: W żądaniu musi zawierać osoby żądającej `wsa:To`, `wsa:Action`, `wsa:MessageID`, nagłówki i dla wszystkich parametrów odwołania lub odwołania właściwości (lub obie) określony przez odwołanie do punktu końcowego.  
  
-   R3322: Stosowania WS-Addressing 2004/08 `ReplyTo` również muszą być zawarte w żądaniu.  
  
-   R3323: Stosowania WS-Addressing 1.0 i `ReplyTo` nie jest obecne w żądaniu odwołanie do punktu końcowego domyślną właściwością [address] równa "http://www.w3.org/2005/08/addressing/anonymous" jest używany.  
  
-   R3324: Strona żądająca może zawierać `wsa:To`, `wsa:Action`, i `wsa:RelatesTo` nagłówków w komunikacie odpowiedzi, a także nagłówki dla wszystkich parametrów odwołania lub odwołanie do właściwości (lub obie) określony przez `ReplyTo` odwołania do punktu końcowego w żądanie.  
  
### <a name="web-services-addressing-faults"></a>Eliminowanie błędów usługi sieci Web  
 R3411: WCF tworzy następujące błędy, zdefiniowane przez WS-Addressing 2004/08.  
  
|Kod|Przyczyna|  
|----------|-----------|  
|wsa:DestinationUnreachable|Wiadomość dotarła z `ReplyTo` inny niż adres zwrotny ustanowione dla tego kanału; Brak punktów końcowych nasłuchujących pod adresem określonym w nagłówku na.|  
|wsa:ActionNotSupported|kanały infrastruktury lub dyspozytora skojarzonej z punktem końcowym nie rozpoznają action określony w `Action` nagłówka.|  
  
 R3412: WCF tworzy następujące błędy, zdefiniowane przez WS-Addressing 1.0.  
  
|Kod|Przyczyna|  
|----------|-----------|  
|wsa10:InvalidAddressingHeader|Duplikuj `wsa:To`, `wsa:ReplyTo`, `wsa:From` lub `wsa:MessageID`. Duplikuj `wsa:RelatesTo` o takiej samej `RelationshipType`.|  
|wsa10:MessageAddressingHeaderRequired|Brak wymaganego nagłówka adresowanie.|  
|wsa10:DestinationUnreachable|Wiadomość dotarła z `ReplyTo` innego niż adres zwrotny ustanowione dla tego kanału. Brak punktów końcowych nasłuchujących pod adresem określonym w nagłówku na.|  
|wsa10:ActionNotSupported|Akcja określona w `Action` nagłówka nie jest rozpoznawane przez infrastrukturę kanałów lub dyspozytora skojarzonej z punktem końcowym.|  
|wsa10:EndpointUnavailable|Kanał RM wysyła ten błąd, wskazujący na punkt końcowy nie będzie przetwarzać sekwencji na podstawie badania `CreateSequence` nagłówków adresowych wiadomości.|  
  
 Mapy kodu w poprzednich tabelach, aby `FaultCode` w SOAP 1.1 i `SubCode` (przy użyciu kodu = nadawcy) w SOAP 1.2.  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 powiązań i protokołu WS-Policy potwierdzenia  
  
#### <a name="indicating-use-of-ws-addressing"></a>Korzystanie z protokołu WS-Addressing wskazujący  
 Usługi WCF używa asercji zasad, aby wskazać punkt końcowy obsługi określonej wersji WS-Addressing.  
  
 Następujących asercji zasad ma punkt końcowy zasad tematu [WS-PA] i wskazuje, że komunikaty wysyłane i odbierane z punktu końcowego, należy użyć protokołu WS-Addressing 2004/08.  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 Potwierdzenie zasad rozszerza specyfikacji WS-Addressing 2004/08.  
  
 Następujących asercji zasad oznacza, że komunikaty wysłać/odebrać należy użyć protokołu WS-Addressing 1.0.  
  
```xml
<wsam:Addressing/>   
```  
  
 Następujących asercji zasad ma punkt końcowy tematu zasad [WS-PA] i wskazuje, że komunikaty wysyłane i odbierane z punktu końcowego musi używać protokołu WS-Addressing 2004/08.  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 `wsaw10:UsingAddressing` Element jest pobierają z [WS-Addressing-WSDL] i jest używana w kontekście usługi WS-Policy zgodnie z tym specyfikacją, sekcja 3.1.2.  
  
 Użyj adresowanie nie zmienia semantykę WSDL 1.1, SOAP 1.1 i SOAP 1.2 HTTP powiązania. Na przykład jeśli odpowiedź na żądanie, które są wysyłane do punktu końcowego, który używa powiązanie HTTP 1.x adresowanie i WSDL SOAP, odpowiedź musi wysyłane przy użyciu odpowiedzi HTTP.  
  
 Pojawieniu się odpowiedzi wysyłane przez odpowiedź http potwierdzenie WS AM jest:  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 Potwierdzenie zasad pełną może wyglądać następująco:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 Istnieją jednak wzorców wymiany komunikatów, które korzyści z posiadania dwóch połączeń HTTP niezależnie od prawdą między inicjatorem żądania a responder, na przykład na niechciane komunikaty jednokierunkowe wysyłane przez obiekt odpowiadający.  
  
 Usługi WCF oferuje funkcję za pomocą którego dwa kanały transportu podstawowej można tworzyć złożone dwukierunkowego kanału, gdzie jeden kanał jest używany dla komunikatów wejściowych, a drugi jest używany dla wiadomości danych wyjściowych. W przypadku transportu HTTP złożonego dwukierunkowego zawiera dwa połączenia HTTP prawdą. Osoby żądającej używa jednego połączenia do wysyłania komunikatów do obiektu odpowiadającego w trybie i obiekt odpowiadający używa innych do wysyłania komunikatów z powrotem do zleceniodawcy.  
  
 W przypadku pojawieniu się odpowiedzi wysyłane za pośrednictwem żądań http w oddzielnych jest potwierdzenie ws am  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 Potwierdzenie zasad pełną może wyglądać następująco:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 Użyj następujących asercji, zawierający punkt końcowy zasad tematu [WS-PA] dla punktów końcowych używających powiązania HTTP 1.x WSDL 1.1 SOAP wymaga dwóch połączeń HTTP oddzielne prawdą ma być używany dla komunikatów wynikających z zleceniodawcy obiektu odpowiadającego w trybie i obiekt odpowiadający w trybie żądającego, odpowiednio.  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 Poprzednia instrukcja prowadzi do następujących wymagań dotyczących `wsa:ReplyTo` nagłówka dla wiadomości żądania:  
  
-   R3514: Żądanie komunikaty wysyłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwość nie jest równa "http://www.w3.org/2005/08/addressing/anonymous" Jeśli punkt końcowy korzysta z powiązania 1.x HTTP WSDL 1.1 SOAP i jest to alternatywa zasad za pomocą `wsap10:UsingAddressing` lub `wsap:UsingAddressing` Potwierdzenie dzięki połączeniu z usługami `cdp:CompositeDuplex` dołączone.  
  
-   R3515: Żądanie komunikaty wysyłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwości jest równa "http://www.w3.org/2005/08/addressing/anonymous", lub nie masz `ReplyTo` nagłówka w ogóle, jeśli punkt końcowy korzysta z Powiązanie WSDL 1.1 SOAP 1.x HTTP i ma alternatywa zasad za pomocą `wsap10:UsingAddressing` potwierdzenia i nie `cdp:CompositeDuplex` potwierdzenie dołączone.  
  
-   R3516: Żądanie komunikaty wysyłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwości jest równa "http://www.w3.org/2005/08/addressing/anonymous" Jeśli punkt końcowy korzysta z powiązania 1.x HTTP WSDL 1.1 SOAP i jest to alternatywa zasad za pomocą `wsap:UsingAddressing` potwierdzenia i nie `cdp:CompositeDuplex`potwierdzenie dołączone.  
  
 Specyfikacja WS-addressing WSDL próbuje opisują podobne powiązania protokołu, wprowadzając element `<wsaw:Anonymous/>` z trzech wartości tekstowej (wymagane, opcjonalne i zabronione) do wskazania wymagania na `wsa:ReplyTo` nagłówka (sekcja 3.2). Niestety takie definicji elementu nie jest szczególnie użyteczne jako potwierdzenie w kontekście usługi WS-Policy, ponieważ wymaga specyficznego dla domeny rozszerzeń do obsługi przecięcia alternatywy przy użyciu takiego elementu jako potwierdzenie. Takie definicji elementu wskazuje także wartość `ReplyTo` nagłówka, w przeciwieństwie do zachowania punktu końcowego na potrzeby przesyłu, dzięki czemu określonego transportu HTTP.  
  
#### <a name="action-definition"></a>Definicja akcji  
 Definiuje WS-Addressing 2004/08 `wsa:Action` atrybutu dla `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementów. WS-Addressing Powiązanie WSDL 1.0 (WS-ADDR10 WSDL) definiuje atrybutem podobne `wsaw10:Action`.  
  
 Jedyną różnicą między tymi dwoma jest semantyki wzorzec Akcja domyślna opisanych w 3.3.2 WS-ADDR i sekcji 4.4.4 WS-ADDR10 — instrukcja języka WSDL, odpowiednio.  
  
 Uzasadnione mieć dwa punkty końcowe, które mają takie same `portType` (lub umowy w terminologii programu WCF), ale przy użyciu różnych wersji WS-Addressing. Ale biorąc pod uwagę, że akcja jest definiowany przez `portType` i nie należy zmieniać w obrębie punktów końcowych, które implementują `portType`, staje się niemożliwe do obsługi zarówno wzorców akcję domyślną.  
  
 Aby rozwiązać ten niejasności, WCF obsługuje jednej wersji `Action` atrybutu.  
  
 B3521: Używa WCF `wsaw10:Action` atrybutu na `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementów zgodnie z definicją w WS-ADDR10-WSDL, aby określić `Action` identyfikator URI dla odpowiednich komunikatów, niezależnie od wersji WS-Addressing używany przez punkt końcowy.  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Punkt końcowy odwołanie wewnątrz WSDL portów  
 Rozszerza WS ADDR10 WSDL sekcji 4.1 `wsdl:port` element, aby uwzględnić `<wsa10:EndpointReference…/>` element podrzędny do opisania punktu końcowego w warunkach WS-Addressing. WCF rozszerza to narzędzie na WS-Addressing 2004/08, dzięki czemu `<wsa:EndpointReference…/>` aby pojawiało się jako element podrzędny `wsdl:port`.  
  
-   R3531: Jeśli punkt końcowy ma alternatywa dołączonych zasad za pomocą `<wsaw10:UsingAddressing/>` asercję zasad, odpowiedni `wsdl:port` element może zawierać elementu podrzędnego `<wsa10:EndpointReference …/>`.  
  
-   R3532: Jeśli `wsdl:port` zawiera element podrzędny `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` wartość elementu podrzędnego musi odpowiadać wartości `@address` atrybut elementu równorzędnego `wsdl:port` / `wsdl:location` elementu.  
  
-   R3533: Jeśli punkt końcowy ma alternatywa dołączonych zasad za pomocą `<wsap:UsingAddressing/>` asercję zasad, odpowiedni `wsdl:port` element może zawierać elementu podrzędnego `<wsa:EndpointReference …/>`.  
  
-   R3534: Jeśli `wsdl:port` zawiera element podrzędny `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` wartość elementu podrzędnego musi odpowiadać wartości `@address` atrybut elementu równorzędnego `wsdl:port` / `wsdl:location` elementu.  
  
### <a name="composition-with-ws-security"></a>Kompozycja za pomocą usługi WS-Security  
 Zgodnie z zabezpieczeń sekcje pod uwagę WS-ADDR i WS-ADDR10 zaleca się wszystkie adresowania nagłówki wiadomości były podpisane wraz z treści wiadomości, aby powiązać je razem.  
  
 Gdy WS-Security jest używana do ochrony integralności komunikatu, WS-Addressing komunikat, że nagłówki, a także nagłówki wynika z parametrów odwołania (i właściwości) muszą być podpisane wraz z treści wiadomości.  
  
### <a name="examples"></a>Przykłady  
  
#### <a name="one-way-message"></a>Komunikat jednokierunkowy  
 W tym scenariuszu nadawca wysyła komunikat jednokierunkowy do odbiorcy. Protokołu SOAP 1.2, HTTP 1.1 i 1.0 W3C WS-Addressing są używane.  
  
 Struktura komunikatu żądania: Nagłówki wiadomości obejmują `wsa10:To` i `wsa10:Action` elementów. Treść wiadomości zawiera konkretną `<app:Ping>` element z przestrzeni nazw aplikacji.  
  
 Nagłówki HTTP: Docelowy WE WPISIE w pasuje do identyfikatora URI w `wsa10:To` elementu.  
  
 Nagłówek Content-Type ma wartość `application/soap+xml` zgodnie z wymaganiami protokołu SOAP 1.2. Parametry `charset` i `action` są uwzględniane. `action` Parametr nagłówek Content-Type odpowiada wartości `wsa10:Action` nagłówka komunikatu.  
  
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
  
 Odbiornik odpowiada za pomocą pustą odpowiedź HTTP i stan 202. Przykład odpowiedzi HTTP:  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a>Mechanizmu optymalizacji transmisji wiadomości protokołu SOAP  
 W tej sekcji opisano szczegóły implementacji programu WCF dla protokołu HTTP MTOM protokołu SOAP. Technologia MTOM jest mechanizm kodowania komunikatu protokołu SOAP tej samej klasy jako kodowanie tradycyjnych tekstu/XML lub kodowanie binarne WCF. MTOM obejmuje następujące funkcje:  
  
-   Kodowanie XML i tworzenia pakietów mechanizmu opisanego przez [XOP] który optymalizuje elementy informacji XML zawierający dane binarne zakodowane w formacie base64 na oddzielnych części binarnego.  
  
-   Hermetyzacja protokołu MIME XOP pakietu, który serializuje zestaw informacji XML i każda część binarne pakietu XOP do oddzielnych części MIME.  
  
-   MIME XOP kodowania, stosowane do protokołu SOAP 1.x koperty.  
  
-   HTTP powiązania transportu.  
  
 Istnieje możliwość MTOM za pomocą transportu protokołu HTTP z usługą WCF. Jednak w tym temacie skupimy się od protokołu HTTP.  
  
 MTOM format korzysta z szerokiej gamy specyfikacje obejmujące MTOM samego, XOP i MIME. Ten zestaw specyfikacji w znikomym zakresie sprawia, że trochę trudno odtworzyć dokładnych wymaganiach na semantyce format i przetwarzania. W tej sekcji opisano wymagania dotyczące formatu i przetwarzania dla wiązania MTOM HTTP.  
  
### <a name="mtom-message-encoding"></a>Kodowanie komunikatu MTOM  
  
#### <a name="generating-mtom-messages"></a>Generowanie wiadomości MTOM  
 [XOP] części 3.1 w tym artykule opisano proces kodowania XML z elementu informacji elementy, które zawierają wartości base64 do pakietu XOP abstrakcyjnie zdefiniowane.  
  
 Poniższą sekwencję czynności w tym artykule opisano proces kodowania specyficzne dla MTOM:  
  
1.  Upewnij się, że koperty protokołu SOAP, który ma być zdekodowany, zawiera żadnego elementu informacji elementu z `[namespace name]` z "http://www.w3.org/2004/08/xop/include" i `[local name]` z `Include`.  
  
2.  Utwórz pusty pakiet MIME.  
  
3.  Zidentyfikuj w oryginalnym zestaw informacji XML elementy informacji elementu można optymalizować. Dla elementów można optymalizować znaki tworzą `[children]` informacje o elemencie elementu musi być w formie kanonicznej `xs:base64Binary` (zobacz XSD-2, 3.2.16 base64Binary) i nie może zawierać dowolne znaki odstępu poprzedzających śródwierszowego, lub po zawartości bez odstępu.  
  
4.  Utwórz koperty protokołu SOAP XOP, który jest kopią oryginalnego koperty protokołu SOAP, ale podrzędnych informacje o każdym elemencie zastępuje element zidentyfikowany w poprzednim kroku `xop:Include` elementu informacji elementu skonstruowane w następujący sposób:  
  
    1.  Przekształć zastąpione znaki w danych binarnych, przetwarzając je jako dane zakodowane w formacie base64.  
  
    2.  Wygeneruj unikatową wartość nagłówka Content-ID, który spełnia wymagania R3133 i R3134.  
  
    3.  Generuje nagłówek MIME kodowanie transferu zawartości z dane binarne wartości.  
  
    4.  Jeśli element informacji elementu są zoptymalizowane pod kątem ([element nadrzędny] nowo wstawionej `xop:Include` element informacji elementu) ma `xmime:contentType` atrybutu elementu informacje, generuje nagłówek MIME Content-Type o wartości `xmime:contentType` atrybutu.  
  
    5.  Generuj nowe części MIME binarnej z zawartością utworzone przez dane binarne zdekodowane z zastąpione znaki przetwarzane jako base64, nagłówek Content-ID z 4b, kodowanie transferu zawartości nagłówka z 4c nagłówek Content-Type, jeśli wygenerowane w kroku 4d.  
  
    6.  Dodaj `href` atrybutu `xop:Include` element z cid wartość: identyfikator uri pochodną wartość nagłówka Content-ID wygenerowane w kroku 4b. Usuń otaczający "\<" i ">" znaki ucieczki adresu URL, pozostałe ciągu, a następnie Dodaj prefiks `cid:`. Następujący zestaw znaków minimalne będzie musiał być poprzedzone RFC1738 i specyfikacja RFC 2396. Inne znaki mogą być poprzedzone znakiem zmiany znaczenia.  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  Utwórz głównej części MIME z XOP koperty protokołu SOAP z kroku 4.  
  
6.  Zapisuje nagłówki HTTP, łącznie z nagłówkiem Content-Type protokołu HTTP.  
  
7.  Napisz pakietu MIME.  
  
#### <a name="processing-mtom-messages"></a>Przetwarzanie komunikatów MTOM  
 Przetwarzanie MTOM komunikat jest dokładnie odwrotnej proces opisany w kroku "Generowanie MTOM wiadomości" sekcji:  
  
1.  Upewnij się, w głównej części MIME ma właściwość Content-Type `application/xop+xml`.  
  
2.  Skonstruuj koperty protokołu SOAP, analizując głównej części MIME pakietu jako dokument XML. Kodowanie znaków zależy od `charset` parametru Content-Type głównej części MIME.  
  
3.  Dla każdego elementu informacji elementu w skonstruowany koperty protokołu SOAP, który ma, jako jedyny element członkowski jego właściwości [dzieci] `xop:Include` element informacji elementu:  
  
    1.  Usuń `cid:` prefiks i unescape wszystkie sekwencje ucieczki identyfikatora URI (RFC 2396) w wartości `@href` atrybutu `xop:Include` elementu. Ujmij ciąg wynikowy w "\<", ">".  
  
    2.  Znajdź części MIME o wartości nagłówka Content-ID, który pasuje do ciągu uzyskane w kroku 3a.  
  
    3.  Zastąp `xop:Include` element informacji elementu, który pojawia się w `children` właściwości poszczególnych elementów z elementami informacji znaków, które reprezentują kodowanie canonical base64 (zobacz XSD-2, 3.2.16 base64Binary) z treści jednostki części MIME zidentyfikowany w kroku 3b (skutecznie zastępują `xop:Include` elementu element informacji o danych odtworzone z części pakietu).  
  
#### <a name="http-content-type-header"></a>Nagłówek Content-Type protokołu HTTP  
 Poniżej znajduje się lista wyjaśnienia WCF format nagłówka HTTP Content-Type 1.x zakodowane w formacie MTOM komunikatu SOAP pochodną wymagania określone w specyfikacją MTOM i są uzyskiwane z MTOM i dokument RFC 2387.  
  
-   R4131: Nagłówek HTTP Content-Type musi mieć wartość multipart/związane z (bez uwzględniania wielkości liter) i jego parametrów. Nazwy parametrów jest rozróżniana wielkość liter. Kolejność parametrów nie ma znaczenia.  
  
-   Pełne formularza notacji Backusa-Naura (BNF) nagłówka Content-Type wiadomości MIME znajduje się w specyfikacji RFC 2045, sekcji 5.1.  
  
-   R4132: Nagłówek HTTP Content-Type musi mieć parametr typu o wartości `application/xop+xml` ujęty w znaki podwójnego cudzysłowu.  
  
 Gdy wymóg dotyczący używania podwójny cudzysłów nie jest jawną w dokument RFC 2387, tekst przestrzega wszystkie parametry typu multipart/związane z nośnika najprawdopodobniej zawierają zastrzeżone znaki, takie jak "\@" lub "/" i dlatego wymagają cudzysłowu Znaczniki.  
  
-   R4133: Nagłówek Content-Type protokołu HTTP powinien mieć start parametru o wartości nagłówka Content-ID części MIME, który zawiera SOAP 1.x koperty, ujęte w podwójny cudzysłów. W przypadku pominięcia parametru startowego pierwszej części MIME musi zawierać SOAP 1.x koperty.  
  
-   R4134: Nagłówek HTTP Content-Type komunikatu protokołu SOAP 1.1 MTOM zakodowane musi zawierać informacje o uruchomieniu parametru z wartością tekstu/xml, ujęte w podwójny cudzysłów.  
  
-   R4135: Nagłówek HTTP Content-Type zakodowane w formacie protokołu SOAP 1.2 MTOM wiadomości musi zawierać informacje o uruchomieniu parametru z wartością `application/soap+xml`, ujęty w znaki podwójnego cudzysłowu.  
  
-   R4136: Nagłówek Content-Type protokołu HTTP dla komunikatu SOAP zakodowane w formacie MTOM 1.x musi mieć parametr granic wartością (ujęty w znaki podwójnego cudzysłowu), która odpowiada granica MIME, w której BNF zdefiniowane w specyfikacji RFC 2046 sekcji 5.1.1  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     Przykłady:  
  
     POPRAW  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     POPRAW  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     NIEPOPRAWNE  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a>Części MIME zestaw informacji  
 SOAP 1.x koperty jest hermetyzowany jako część pakietu XOP MIME głównym i jest często określany mianem `infoset` części.  
  
-   R4141: SOAP 1.x koperty musi być zhermetyzowany w ramach głównym pakietu XOP MIME, o nazwie `infoset` wchodzi w skład i odwołania z HTTP Content-Type.  
  
-   R4142: SOAP `Infoset` części musi zawierać następujące nagłówki MIME: `Content-ID`, `Content-Transfer-Encoding`, i `Content-Type`.  
  
 Format nagłówka Content-ID jest definiowany przez 2045 RFC jako  
  
```  
"Content-ID" ":" msg-id  
```  
  
 gdzie `msg-id` jest zdefiniowany w specyfikacji RFC 2822, (zastępująca RFC 822, do którego odwołuje się RFC 2045) jako:  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 i znajduje się skutecznie adres e-mail w ciągu "\<" i ">". `[CFWS]` Prefiksem i sufiksem zostały dodane w RFC 2822 do przenoszenia komentarze i nie należy używać, aby zachować współdziałania.  
  
 R4143: Wartość nagłówka Content-ID dla części MIME zestaw informacji należy wykonać `msg-id` produkcji z RFC 2822 z `[CFWS]` prefiksem i sufiksem części pominięty.  
  
 Wiele implementacji MIME złagodzone wymagania dla wartości ujęte w "\<" i ">" jako adresu e-mail i użyć `absoluteURI` ujęty w znaki "\<", ">" oprócz adres e-mail. Ta wersja programu WCF używa wartości nagłówek MIME Content-ID w postaci:  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 R4144: Procesory MTOM powinna obsługiwać nagłówek Content-ID wartości, które pasują do następujących złagodzone `msg-id`.  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 MIME (RFC 2045) zawiera nagłówek kodowanie transferu zawartości do komunikowania się kodowania zawartości części MIME. Domyślnie zdefiniowane dla kodowanie transferu zawartości jest 7-bitowym, który nie jest odpowiedni dla większości komunikaty protokołu SOAP, więc kodowanie transferu zawartości nagłówka wymagane jest współdziałanie większa:  
  
-   R4145: Część zestaw informacji protokołu SOAP musi zawierać nagłówek kodowanie transferu zawartości.  
  
-   R4146: W przypadku koperty protokołu SOAP kodowania znaków UTF-8, wartość nagłówka kodowanie transferu zawartości musi być 8-bitowych.  
  
-   R4147: W przypadku koperty protokołu SOAP kodowania znaków UTF-16, wartość nagłówka kodowanie transferu zawartości musi być binarny.  
  
-   Zgodnie z [XOP] części 5,  
  
-   R4148: Zestaw informacji SOAP1.1 część może zawierać nagłówek Content-Type, typ nośnika application/xop + xml i parametry typu = "text/xml" i zestaw znaków  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   R4149: Część protokołu SOAP 1.2 w jedno odniesienie musi zawierać nagłówek Content-Type z typem nośnika `application/xop+xml` i parametry type = "`application/soap+xml`" i `charset`.  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     Gdy definiuje XOP `charset` parametr `application/xop+xml` na opcjonalny wymagana jest podobne do wymagań BP 1.1 na współdziałanie `charset` parametr `text/xml` typu nośnika.  
  
-   R41410: `type` i `charset` parametry muszą być obecne w nagłówku Content-Type części zestaw informacji 1.x protokołu SOAP.  
  
#### <a name="wcf-endpoint-support-for-mtom"></a>Obsługa punktu końcowego WCF MTOM  
 MTOM ma na celu zakodowania komunikatu protokołu SOAP, aby zoptymalizować dane zakodowane w formacie base64. Oto lista ograniczeń:  
  
-   R4151: Może być zoptymalizowany dowolny element informacji elementu, który zawiera dane zakodowane w formacie base64.  
  
-   B4152: WCF optymalizuje pozycje informacji elementów, które zawierają dane zakodowane w formacie base64 i przekracza 1024 bajty długości.  
  
 Punkt końcowy usługi WCF skonfigurowany do używania MTOM będą zawsze wysyłały zakodowane w formacie MTOM wiadomości. Nawet jeśli nie części spełnia wymagane kryteria, komunikat jest nadal MTOM zakodowane w formacie (zserializowanym w formacie MIME pakietu przy użyciu jednej części MIME zawierający koperty protokołu SOAP).  
  
### <a name="ws-policy-assertion-for-mtom"></a>Potwierdzenie WS-Policy dla MTOM  
 Usługi WCF używa następujących asercji zasad, aby wskazać MTOM użycia przez punkt końcowy:  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   R4211: Poprzedniego asercję zasad ma podmiotu zasad punktu końcowego i określa, że wszystkie komunikaty wysyłane do i odbierane z punktu końcowego musi być zoptymalizowany przy użyciu MTOM.  
  
-   B4212: W przypadku skonfigurowania, aby używać optymalizacji MTOM, punkt końcowy usługi WCF dodaje potwierdzenie zasad MTOM do zasady dołączone do odpowiednich `wsdl:binding`.  
  
### <a name="composition-with-ws-security"></a>Kompozycja za pomocą usługi WS-Security  
 MTOM jest mechanizm kodowania, która jest podobna do `text/xml` i WCF binarny kod XML. MTOM oferuje kompozycji fizyczną za pomocą usługi WS-Security i inne usługi WS-* protokoły: komunikat zabezpieczone przy użyciu usługi WS-Security można zoptymalizować za pomocą MTOM.  
  
### <a name="examples"></a>Przykłady  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>Usługi WCF SOAP 1.1 komunikat zakodowane przy użyciu MTOM  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>Usługi WCF bezpiecznego protokołu SOAP 1.2 komunikat zakodowane przy użyciu MTOM  
 W tym przykładzie wiadomość jest zakodowany przy użyciu MTOM i SOAP 1.2, który jest chroniony przy użyciu usługi WS-Security. Binarny części zidentyfikowane dla kodowania zawartości `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpowiadający zaszyfrowanych podpisu i treść zaszyfrowanego. Należy pamiętać, że `CipherValue` z `EncryptedKey` nie został zidentyfikowany na optymalizację przez architekturę WCF, ponieważ jego długość jest mniejsza następnie 1024 bajty.  
  
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
