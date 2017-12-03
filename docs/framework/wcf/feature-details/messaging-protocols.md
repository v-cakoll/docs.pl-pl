---
title: "Protokoły obsługi komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fef5fc58adeac99bcd2cac0fda8a72dde2797001
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="messaging-protocols"></a>Protokoły obsługi komunikatów
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Stosu kanału wykorzystuje kanały transportu i kodowanie do transformacji reprezentacji wewnętrznej komunikatu do jego format danych przesyłanych w sieci i wysłać go przy użyciu danego transportu. Transport najczęściej używane na współdziałanie usług sieci Web, jest protokół HTTP i są najczęściej używane kodowanie, używane przez usługi sieci Web opartych na języku XML SOAP 1.1 i SOAP 1.2, mechanizmu optymalizacji transmisji wiadomości (MTOM).  
  
 W tym temacie omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji dla następujących protokołów zatrudnieni przez <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|PROTOKOŁU HTTP 1.1|http://www.IETF.org/RFC/RFC2616.txt|  
|SOAP 1.1 powiązanie HTTP|http://www.w3.org/TR/2000/Note-SOAP-20000508/, sekcji 7|  
|SOAP 1.2 powiązanie HTTP|http://www.w3.org/TR/soap12-part2/, sekcji 7|  
  
 W tym temacie omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji dla następujące protokoły <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> fragmentów.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|XML|http://www.w3.org/TR/REC-XML|  
|SOAP 1.1|http://www.w3.org/TR/2000/Note-SOAP-20000508/|  
|SOAP 1.2 Core|http://www.w3.org/TR/soap12-Part1/|  
|Protokół WS-Addressing 2004/08|http://www.w3.org/submission/2004/SUBM-WS-Addressing-20040810/|  
|Usługi sieci Web W3C adresowania 1.0 — podstawowe|http://www.w3.org/TR/2006/rec-ws-addr-Core-20060509|  
|Adresowania 1.0 — wiązanie protokołu SOAP usług sieci Web W3C|http://www.w3.org/TR/2006/rec-ws-addr-SOAP-20060509|  
|Usługi sieci Web W3C adresowania 1.0 — wiązanie WSDL|http://www.w3.org/TR/2006/CR-ws-addr-WSDL-20060529/|  
Usługi sieci Web W3C adresowania 1.0 - metadanych|http://www.w3.org/TR/ws-addr-METADATA/|  
|Powiązanie WSDL SOAP1.1|http://www.w3.org/TR/WSDL/|  
|Powiązanie WSDL SOAP1.2|http://www.w3.org/submission/wsdl11soap12/|  
  
 W tym temacie omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji dla następujące protokoły <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> wykorzystuje.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|ELEMENT XOP|http://www.w3.org/TR/xop10/|  
|MTOM + SOAP 1.2 powiązania|http://www.w3.org/TR/soap12-MTOM/|  
|MTOM SOAP 1.1 powiązania|http://www.w3.org/submission/soap11mtom10/|  
|Potwierdzenie WS-Policy MTOM|http://www.w3.org/submission/2006/SUBM-ws-MTOMPolicy-20061101/.|  
  
 Następujące obszary nazw XML i prefiksy skojarzone są używane w tym temacie.  
  
|Prefiks|Namespace Uniform Resource Identifier (URI)|  
|------------|---------------------------------------------------|  
|S11|http://schemas.xmlsoap.org/SOAP/Envelope|  
|S12|http://www.w3.org/2003/05/SOAP-Envelope|  
|wsa|http://www.w3.org/2004/08/Addressing|  
|wsam|http://www.w3.org/2007/05/Addressing/METADATA|  
|wsap|http://schemas.xmlsoap.org/ws/2004/09/Policy/Addressing|  
|wsa10|http://www.w3.org/2005/08/Addressing|  
|wsaw10|http://www.w3.org/2006/05/Addressing/WSDL|  
|Element XOP|http://www.w3.org/2004/08/XOP/Include|  
|xmime|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
punkt dystrybucji|http://schemas.microsoft.com/NET/2006/06/Duplex|  
  
## <a name="soap-11-and-soap-12"></a>SOAP 1.1 i SOAP 1.2  
  
### <a name="envelope-and-processing-model"></a>Koperty i przetwarzania modelu  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje przetwarzania koperty protokołu SOAP 1.1 Basic Profile 1.1 (BP11) i Basic Profile 1.0 (SSBP10). SOAP 1.2 koperty przetwarzania jest zaimplementowana po SOAP12 — część 1.  
  
 W tej sekcji opisano niektóre opcje implementacji wykonywaną przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] BP11 i SOAP12 — część 1.  
  
#### <a name="mandatory-header-processing"></a>Wymagany nagłówek przetwarzania  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]następuje reguł do przetwarzania nagłówków oznaczony `mustUnderstand` opisanego w specyfikacji SOAP 1.1 i SOAP 1.2, z następujących zmian.  
  
 Komunikat, który przechodzi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanału stosu jest przetwarzany przez poszczególnych kanałów skonfigurowanych przez powiązanie skojarzone elementy, na przykład, kodowania wiadomości tekstowych, zabezpieczeń, niezawodna obsługa komunikatów i transakcji. Każdy kanał rozpoznaje nagłówków z skojarzona przestrzeń nazw i oznacza je jako rozumiem. W momencie komunikat wejścia dyspozytor, programu formatującego operacji odczytuje nagłówki oczekiwany przez odpowiednie kontraktu komunikatu na operację i znaczniki ich zrozumienie. Następnie Dyspozytor sprawdza, czy wszystkie pozostałe nagłówki nie są rozumieć, ale oznaczenie `mustUnderstand` i zgłasza wyjątek. Komunikaty, które zawierają `mustUnderstand` nagłówki, które są przeznaczone dla odbiorcy nie są przetwarzane przez kod aplikacji odbiorcy.  
  
 Takie warstwie przetwarzania umożliwia rozdzielenie warstwy infrastruktury i aplikacji węzła SOAP:  
  
-   B1111: Nagłówki, które nie są zrozumiałe są wykrywane po komunikat jest przetwarzany przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu kanału infrastruktury, ale przetworzenia przez aplikację  
  
     `mustUnderstand` Wartość nagłówka różni się między SOAP 1.1 i SOAP 1.2. Basic Profile 1.1 wymaga, aby `mustUnderstand` wartość wynosić 0 lub 1 dla wiadomości SOAP 1.1. SOAP 1.2 umożliwia 0, 1, `false`, i `true` jako wartości, ale zaleca emitowanie canonical reprezentację `xs:boolean` wartości (`false`, `true`).  
  
-   B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emituje `mustUnderstand` wartości 0 i 1 dla wersji zarówno SOAP 1.1 i SOAP 1.2 koperty protokołu SOAP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]akceptuje miejsce całą wartość `xs:boolean` dla `mustUnderstand` nagłówka (0, 1, `false`, `true`)  
  
#### <a name="soap-faults"></a>Błędach SOAP  
 Poniżej przedstawiono listę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-określonej implementacji błędu protokołu SOAP.  
  
-   B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zwraca następujące kody błędów protokołu SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, i `s11:Server`.  
  
-   B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zwraca następujące kody błędów protokołu SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, i `s12:Receiver`.  
  
### <a name="http-binding"></a>Wiązanie HTTP  
  
#### <a name="soap-11-http-binding"></a>SOAP 1.1 powiązanie HTTP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje powiązanie SOAP1.1 HTTP po specyfikacji Basic Profile 1.1 sekcji 3.4 o wyjaśnienia następujące:  
  
-   B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa nie implementuje przekierowania żądania HTTP POST.  
  
-   B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów obsługujących pliki cookie HTTP, zgodnie z 3.4.8.  
  
#### <a name="soap-12-http-binding"></a>SOAP 1.2 powiązanie HTTP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje powiązania SOAP 1.2 HTTP, zgodnie z opisem w SOAP 1.2, część 2 (SOAP12Part2) specyfikacji z następujących wyjaśnienia.  
  
 Parametr opcjonalny akcji dla wprowadzone SOAP 1.2 `application/soap+xml` typu nośnika. Ten parametr jest przydatne w celu zoptymalizowania wysyłania wiadomości bez konieczności czy treść komunikatu protokołu SOAP można w sytuacji, gdy WS-Addressing nie jest używany.  
  
-   R2221: `application/soap+xml` parametr akcji, jeśli jest obecny w żądaniu SOAP 1.2, muszą być zgodne `soapAction` atrybutu `wsoap12:operation` elementu w odpowiednich Powiązanie WSDL.  
  
-   R2222: `application/soap+xml` parametr akcji, jeśli jest obecny na wiadomości SOAP 1.2, muszą być zgodne `wsa:Action` stosowania WS-Addressing 2004/08 lub 1.0 WS-Addressing.  
  
 Gdy WS-Addressing jest wyłączona, a żądanie przychodzące nie zawiera parametr akcji, wiadomości `Action` jest traktowany jako okres bez określonej.  
  
## <a name="ws-addressing"></a>Protokół WS-Addressing  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje 3 wersji WS-Addressing:  
  
-   Protokół WS-Addressing 2004/08  
  
-   W3C usług sieci Web adresowanie SOAP powiązania (ADDR10 SOAP) i 1.0 Core (ADDR10 RDZENI)  
  
-   Protokół WS-Addressing 1.0 - metadanych  
  
### <a name="endpoint-references"></a>Odwołania do punktu końcowego  
 Wszystkie wersje usługi WS-Addressing który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje używać odwołań do punktu końcowego do opisywania punktów końcowych.  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a>Odwołania do punktu końcowego i wersji WS-Addressing  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje wiele protokołów infrastruktury, które używają protokołu WS-Addressing, w szczególności `EndpointReference` elementu i `W3C.WsAddressing.EndpointReferenceType` klasy (na przykład WS-ReliableMessaging, WS-SecureConversation i WS-Trust). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje korzystanie z danej wersji WS-Addressing z innymi protokołami infrastruktury. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]punkty końcowe obsługuje jedną wersję WS-Addressing na punkt końcowy.  
  
 Dla R3111, w obszarze nazw `EndpointReference` elementu lub typ używany w wiadomościach z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego musi odpowiadać wersji WS-Addressing implementowanych przez ten punkt końcowy.  
  
 Na przykład jeśli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego implementuje usługi WS-ReliableMessaging `AcksTo` zwrócony przez punkt końcowy, wewnątrz nagłówka `CreateSequenceResponse` korzysta z wersji WS-Addressing który `EncodingBinding` określa element dla tego punktu końcowego.  
  
#### <a name="endpoint-references-and-metadata"></a>Odwołania do punktu końcowego i metadane  
 Liczba scenariuszy wymagają komunikacji metadanych lub odwołanie do metadanych dla danego punktu końcowego.  
  
 B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wykorzystuje mechanizm opisane w sekcji 6, aby uwzględnić metadanych dla odwołania do punktu końcowego według wartości lub według odwołania specyfikacji WS-MetadataExchange (MEX).  
  
 Rozważmy scenariusz, w którym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa wymaga uwierzytelnienia za pomocą tokenu zabezpieczeń potwierdzenia Markup Language (SAML) wydanego przez emitenta tokenu w http://sts.fabrikam123.com. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Punktu końcowego opisano to wymaganie uwierzytelniania przy użyciu `sp:IssuedToken` asercja z zagnieżdżoną `sp:Issuer` wskazujący emitenta tokenu potwierdzenia. Aplikacje klienckie, które uzyskują dostęp do `sp:Issuer` potwierdzenia trzeba znać sposób komunikacji z punktem końcowym wystawcy tokenów. Klient musi wiedzieć, metadane dotyczące wystawcy tokenów. Korzystanie z rozszerzeń metadanych odwołania punktu końcowego zdefiniowana w punkcie końcowym MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera odwołanie do metadanych wystawca tokenów.  
  
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
  
### <a name="message-addressing-headers"></a>Adresowanie nagłówki komunikatów  
  
#### <a name="message-headers"></a>Nagłówki komunikatów  
 W przypadku obu wersji WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa następujące nagłówki komunikatów według specyfikacji `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, i `wsa:RelatesTo`.  
  
 B3211: dla wszystkich wersji WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honoruje, ale nie tworzy fabrycznej nagłówków wiadomości WS-Addressing `wsa:FaultTo` i `wsa:From`.  
  
 Aplikacje, które współdziałają z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji można dodać te wiadomości nagłówki i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odpowiednio przetworzy je.  
  
#### <a name="reference-parameters-and-properties"></a>Odwołanie do parametrów i właściwości  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje przetwarzania parametrów odwołanie do punktu końcowego i odwołanie p  
  
 właściwości zgodnie z odpowiednimi wymaganiami.  
  
 B3221: Gdy skonfigurowany do używania protokołu WS-Addressing 2004/08 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych nie odróżnienie przetwarzania właściwości odwołania i parametrów odwołania.  
  
### <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 Sekwencja komunikatów związane z wywołania operacji usługi sieci Web nazywa się *wymiany komunikatów*. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje jednokierunkowe, żądanie odpowiedź i dupleksu wiadomości wymiany wzorce. W tej sekcji wyjaśnia WS-Addressing wymagania dotyczące przetwarzania w zależności od wymiany komunikatów używany komunikatów.  
  
 W tej sekcji żądający wysyła pierwszy komunikat i obiekt odpowiadający odbiera pierwszego komunikatu.  
  
#### <a name="one-way-message"></a>Komunikat jednokierunkowy  
 Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punkt końcowy jest skonfigurowana do obsługi komunikatów z danego `Action` wykonać wzorzec jednokierunkowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego obowiązują następujące zachowania i wymagania. Inaczej, zachowania i zasady mają zastosowanie zarówno wersji WS-Addressing obsługiwane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R3311: Żądający musi zawierać `wsa:To`, `wsa:Action`, a nagłówki dla wszystkich parametrów odwołanie określone przez odwołanie do punktu końcowego. Po jest używany protokół WS-Addressing 2004/08 i [właściwości odwołania] są określone przez odwołanie do punktu końcowego odpowiednie nagłówki musi zostać dodany do komunikatu za.  
  
-   B3312: Żądający może obejmować `MessageID`, `ReplyTo`, i `FaultTo` nagłówków. Infrastruktura odbiornik, zostaną one zignorowane, a zostaną przekazane do aplikacji.  
  
-   R3313: Gdy HTTP jest używany, a żaden komunikat jest wysyłany na etap odpowiedzi HTTP, odpowiadający musi wysłać odpowiedź HTTP z pustej treści i kod stanu HTTP 202.  
  
     Podczas transportu HTTP jest w użyciu i kontrakt operacji deklaruje komunikatu jednokierunkowego, odpowiedź HTTP nadal może być używany do wysyłania wiadomości infrastruktury — na przykład wysłać niezawodna obsługa komunikatów `SequenceAcknowledgement` komunikat odpowiedzi HTTP.  
  
-   B3314: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu odpowiadającego w trybie nie wysyła w odpowiedzi na komunikat jednokierunkowy komunikat o błędzie.  
  
#### <a name="request-reply"></a>Żądanie i odpowiedź  
 Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punkt końcowy jest skonfigurowana dla komunikatu o danej `Action` postępuj zgodnie ze wzorcem "żądanie-odpowiedź" [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego następuje zachowania i poniższe wymagania. Chyba że określono inaczej, zachowania i zasady mają zastosowanie zarówno wersji WS-Addressing obsługiwane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R3321: W żądaniu musi zawierać żądający `wsa:To`, `wsa:Action`, `wsa:MessageID`, a nagłówki dla wszystkich parametrów odwołania odwołania (i właściwości) określone przez odwołanie do punktu końcowego.  
  
-   R3322: W przypadku protokołu WS-Addressing 2004/08 `ReplyTo` muszą także być ujęte w żądaniu.  
  
-   R3323: Gdy jest używany protokół WS-Addressing 1.0 i `ReplyTo` jest domyślnym odwołaniem punktu końcowego z właściwością [address] równa "http://www.w3.org/2005/08/addressing/anonymous" nie znajduje się w żądaniu, jest używany.  
  
-   R3324: Żądający musi zawierać `wsa:To`, `wsa:Action`, i `wsa:RelatesTo` nagłówków komunikatu odpowiedzi, a także nagłówki dla wszystkich parametrów odwołania odwołania (i właściwości) określone przez `ReplyTo` w odwołaniu do punktu końcowego żądanie.  
  
### <a name="web-services-addressing-faults"></a>Usługi sieci Web adresowanie błędów  
 R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tworzy następujące błędy, zdefiniowane przez protokół WS-Addressing 2004/08.  
  
|Kod|Przyczyna|  
|----------|-----------|  
|wsa:DestinationUnreachable|Odebrano komunikat z `ReplyTo` innego niż adres dla tego kanału; nie istnieje brak nasłuchującego pod adresem określonym w nagłówku do punktu końcowego.|  
|wsa:ActionNotSupported|kanały infrastruktury lub skojarzone z punktem końcowym Dyspozytor nie rozpoznają z akcją określoną w `Action` nagłówka.|  
  
 R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tworzy następujące błędy, zdefiniowane przez protokół WS-Addressing 1.0.  
  
|Kod|Przyczyna|  
|----------|-----------|  
|wsa10:InvalidAddressingHeader|Zduplikowana `wsa:To`, `wsa:ReplyTo`, `wsa:From` lub `wsa:MessageID`. Zduplikowana `wsa:RelatesTo` o takiej samej `RelationshipType`.|  
|wsa10:MessageAddressingHeaderRequired|Brak wymaganego nagłówka adresowanie.|  
|wsa10:DestinationUnreachable|Odebrano komunikat z `ReplyTo` innego niż adres dla tego kanału. Brak nasłuchującego pod adresem określonym w nagłówku do punktu końcowego nie istnieje.|  
|wsa10:ActionNotSupported|Action określony w `Action` nagłówka nie jest rozpoznawane przez infrastrukturę kanały lub dyspozytora skojarzonej z punktem końcowym.|  
|wsa10:EndpointUnavailable|Kanał RM wysyła ten błąd, wskazujący punkt końcowy nie będzie przetwarzał sekwencji oparte na badanie `CreateSequence` nagłówków adresowych wiadomości.|  
  
 Kod w poprzednich tabelach mapuje `FaultCode` w SOAP 1.1 i `SubCode` (z kodem = nadawca) w SOAP 1.2.  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 wiązania i protokołu WS-Policy potwierdzeń  
  
#### <a name="indicating-use-of-ws-addressing"></a>Używanie protokołu WS-Addressing wskazujący  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa potwierdzeń zasad, aby wskazać punkt końcowy obsługę konkretnej wersji WS-Addressing.  
  
 Następujące potwierdzenia zasad ma punkt końcowy zasad podmiotu [WS-PA] i wskazuje, że komunikaty wysyłane i odbierane z punktem końcowym muszą używać protokołu WS-Addressing 2004/08.  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 Potwierdzenie zasad wspomaga specyfikacji WS-Addressing 2004/08.  
  
 Następujące potwierdzenia zasad, oznacza to, że komunikaty który wysłać/odebrać musi używać protokołu WS-Addressing 1.0.  
  
```xml
<wsam:Addressing/>   
```  
  
 Następujące potwierdzenia zasad ma punkt końcowy podmiotu zasad [WS-PA] i wskazuje, że komunikaty wysyłane i odbierane z punktu końcowego musi używać protokołu WS-Addressing 2004/08.  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 `wsaw10:UsingAddressing` Element jest pobierają z [WS-Addressing-WSDL] i jest używany w ramach usługi WS-Policy zgodnie z tym specyfikacją, sekcja 3.1.2.  
  
 Użyj adresowanie nie zmienia semantykę wersji 1.1 języka WSDL SOAP 1.1 i SOAP 1.2 HTTP powiązania. Na przykład jeśli odpowiedź ma żądanie, które są wysyłane do punktu końcowego, który używa powiązanie HTTP 1.x adresowanie i WSDL SOAP, odpowiedź należy wysłać przy użyciu odpowiedzi HTTP.  
  
 Odpowiedzi na wysłane za pośrednictwem odpowiedzi http WS-AM potwierdzenia jest:  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 Potwierdzenie pełną zasad może wyglądać następująco:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 Istnieją jednak wzorce wymiany wiadomości, korzystających z o dwa połączenia HTTP niezależne odwrotnej między obiektu żądającego i odpowiadający, na przykład na niechciane komunikaty jednokierunkowe wysyłane przez odpowiadający.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferuje funkcję za pomocą którego dwa kanały transportu źródłowego utworzenia złożonego dupleksu kanału, gdzie jeden kanał służy do wprowadzania wiadomości, a drugi służy do komunikaty wyjściowe. W przypadku transportu HTTP złożonego dupleksu zawiera dwa połączenia HTTP odwrotnej. Żądający używa jednego połączenia do wysyłania komunikatów do udzielenia i udzielenia używa innych wysyłania wiadomości z powrotem do strony żądającej.  
  
 Odpowiedzi na wysłane za pośrednictwem żądania http oddzielne jest potwierdzenie ws am  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 Potwierdzenie pełną zasad może wyglądać następująco:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 Użyj następujących potwierdzenia o temacie zasady punktu końcowego [WS-PA] dla punktów końcowych używających powiązania HTTP 1.x WSDL 1.1 SOAP wymaga dwóch oddzielnych odwrotnej połączeń HTTP używanego do wiadomości przesyłane od osoby żądającej do obiektu odpowiadającego w trybie i obiekt odpowiadający w trybie żądającej, odpowiednio.  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 Poprzednia prowadzi do następujących wymagań dotyczących `wsa:ReplyTo` nagłówek dla wiadomości żądania:  
  
-   R3514: Żądanie wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwość nie ma wartości "http://www.w3.org/2005/08/addressing/anonymous" Jeśli punkt końcowy nie używa powiązania WSDL 1.1 SOAP 1.x HTTP i nie ma stanowi alternatywę zasad z `wsap10:UsingAddressing` lub `wsap:UsingAddressing` potwierdzenia połączone z `cdp:CompositeDuplex` dołączony.  
  
-   R3515: Żądanie wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwości równa się "http://www.w3.org/2005/08/addressing/anonymous" lub nie ma `ReplyTo` 1.x HTTP SOAP nagłówka gwarancja, jeśli korzysta z punktu końcowego WSDL 1.1 powiązanie i jest to alternatywa zasad z `wsap10:UsingAddressing` potwierdzenia i nie `cdp:CompositeDuplex` potwierdzenia dołączony.  
  
-   R3516: Żądanie wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwości jest równa "http://www.w3.org/2005/08/addressing/anonymous" Jeśli punkt końcowy używa 1.x HTTP powiązania WSDL 1.1 SOAP i ma stanowi alternatywę zasad z `wsap:UsingAddressing` potwierdzenia i nie `cdp:CompositeDuplex` potwierdzenia dołączony.  
  
 Specyfikacja WS-addressing WSDL próbuje opisano podobnymi powiązaniami protokołu, wprowadzając element `<wsaw:Anonymous/>` z trzech wartości tekstowej (wymagane, opcjonalne i zabronionych) wskazująca wymagania na `wsa:ReplyTo` nagłówka (sekcji 3.2). Niestety taka definicja elementu nie jest szczególnie użyteczne jako potwierdzenia w ramach usługi WS-Policy, ponieważ wymaga rozszerzenia specyficznego dla domeny do obsługi przecięcie alternatyw za pomocą takiego elementu jako potwierdzenia. Wartość wskazuje także takie definicji elementu `ReplyTo` nagłówka, w przeciwieństwie do zachowania punktu końcowego przesyłania, dzięki czemu określonego transportu HTTP.  
  
#### <a name="action-definition"></a>Definicja akcji  
 Definiuje WS-Addressing 2004/08 `wsa:Action` atrybutu dla `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementów. WS-Addressing powiązania WSDL 1.0 (WS-ADDR10 WSDL) definiuje atrybut podobne `wsaw10:Action`.  
  
 Jedyną różnicą między tymi dwoma jest opisanych w 3.3.2 WS-ADDR i sekcji 4.4.4 WS-ADDR10-WSDL, odpowiednio semantykę wzorzec domyślnej akcji.  
  
 Jest uzasadnione ma dwa punkty końcowe, które mają taki sam `portType` (lub umowy, w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminologii), ale przy użyciu różnych wersji WS-Addressing. Ale biorąc pod uwagę, że akcja jest definiowana za pomocą `portType` i nie należy zmieniać w obrębie punktów końcowych, które implementują `portType`, staje się niemożliwe do obsługi oba wzorce akcji domyślnej.  
  
 Aby rozwiązać ten rozbieżność [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje jednej wersji `Action` atrybutu.  
  
 B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa `wsaw10:Action` atrybutu `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy zgodnie z definicją w WS ADDR10 WSDL ustalenie `Action` identyfikator URI dla odpowiednich komunikatów niezależnie od wersji WS-Addressing używany przez punkt końcowy.  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Punkt końcowy odwołanie wewnątrz WSDL portów  
 Rozszerza WS ADDR10 WSDL sekcji 4.1 `wsdl:port` element, aby uwzględnić `<wsa10:EndpointReference…/>` elementu podrzędnego do opisywania punktu końcowego usługi WS-Addressing warunków. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]rozwija tego narzędzia na WS-Addressing 2004/08, umożliwiając `<wsa:EndpointReference…/>` były wyświetlane jako elementu podrzędnego `wsdl:port`.  
  
-   R3531: Jeśli punkt końcowy ma zamiast dołączonych zasad z `<wsaw10:UsingAddressing/>` potwierdzenia zasad, odpowiadającego `wsdl:port` element może zawierać elementu podrzędnego `<wsa10:EndpointReference …/>`.  
  
-   R3532: Jeśli `wsdl:port` zawiera element podrzędny `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` wartość elementu podrzędnego musi być zgodna z wartością `@address` atrybutu elementu równorzędnego `wsdl:port` / `wsdl:location` elementu.  
  
-   R3533: Jeśli punkt końcowy ma zamiast dołączonych zasad z `<wsap:UsingAddressing/>` potwierdzenia zasad, odpowiadającego `wsdl:port` element może zawierać elementu podrzędnego `<wsa:EndpointReference …/>`.  
  
-   R3534: Jeśli `wsdl:port` zawiera element podrzędny `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` wartość elementu podrzędnego musi być zgodna z wartością `@address` atrybutu elementu równorzędnego `wsdl:port` / `wsdl:location` elementu.  
  
### <a name="composition-with-ws-security"></a>Kompozycja z zabezpieczenia WS  
 Zgodnie z zabezpieczeń sekcje brany pod uwagę WS-ADDR i WS-ADDR10 zaleca się wszystkie nagłówki komunikatów adresowania podpisywane wraz z treści wiadomości powiązać je razem.  
  
 Gdy WS-Security jest używany na potrzeby ochrony integralności komunikatu, WS-Addressing wiadomości nagłówków, a także nagłówki wynika z parametrów odwołania (i właściwości) muszą być podpisane wraz z treści wiadomości.  
  
### <a name="examples"></a>Przykłady  
  
#### <a name="one-way-message"></a>Komunikat jednokierunkowy  
 W tym scenariuszu nadawca wysyła komunikat jednokierunkowy do odbiornika. Są używane SOAP 1.2, protokołu HTTP 1.1 i 1.0 W3C WS-Addressing.  
  
 Struktura komunikatu żądania: Nagłówki komunikatów obejmują `wsa10:To` i `wsa10:Action` elementy. Treść wiadomości zawiera określony `<app:Ping>` element z przestrzeni nazw aplikacji.  
  
 Nagłówki HTTP: Odpowiada docelowego w POST identyfikator URI w `wsa10:To` elementu.  
  
 Nagłówek Content-Type ma wartość `application/soap+xml` zgodnie z żądaniem protokołu SOAP 1.2. Parametry `charset` i `action` są uwzględniane. `action` Parametr nagłówka Content-Type jest zgodna z wartością elementu `wsa10:Action` nagłówka wiadomości.  
  
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
  
 Odbiornik odpowiada pustą odpowiedź HTTP i stan 202. Przykład odpowiedzi HTTP:  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a>Mechanizmu optymalizacji transmisji wiadomości SOAP  
 W tej sekcji opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji MTOM SOAP protokołu HTTP. Technologia MTOM jest mechanizm kodowania wiadomości SOAP do tej samej klasy jako kodowania tradycyjnych tekstu/XML lub [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodowania binarnego. MTOM obejmuje następujące funkcje:  
  
-   Kodowanie XML i mechanizmu pakowania opisanego przez [XOP] który optymalizuje elementów informacji XML zawierający dane binarne algorytmem base64 na oddzielnych części binarnej.  
  
-   Hermetyzacja protokołu MIME pakietu XOP, który serializuje XML typu infoset sprawdzonych i każdej części binarnej pakietu XOP w oddzielnych części MIME.  
  
-   MIME XOP kodowanie stosowane do SOAP 1.x koperty.  
  
-   HTTP powiązania transportu.  
  
 Istnieje możliwość MTOM za pomocą transportu innego niż HTTP z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Jednak w tym temacie firma Microsoft koncentruje się na HTTP.  
  
 MTOM format wykorzystuje dużego zestawu specyfikacji obejmujące MTOM samego, XOP i MIME. Modułowość tego zestawu specyfikacji utrudnia nieco rekonstrukcji dokładnych wymaganiach na format i przetwarzania semantyki. W tej sekcji opisano wymagania formatu i przetwarzania dla wiązania MTOM HTTP.  
  
### <a name="mtom-message-encoding"></a>Kodowanie komunikatu MTOM  
  
#### <a name="generating-mtom-messages"></a>Komunikaty mechanizmu MTOM generowania  
 [XOP] 3.1 sekcji opisano proces kodowania XML z elementu informacji elementów, które zawierają wartości base64 w zdefiniowanych abstrakcyjnie pakiet XOP.  
  
 Następująca sekwencja kroków opisano proces kodowania MTOM specyficzne:  
  
1.  Sprawdź, czy koperty protokołu SOAP ma być zdekodowany, zawiera żadnego elementu elementu informacji z `[namespace name]` z "http://www.w3.org/2004/08/xop/include" i `[local name]` z `Include`.  
  
2.  Utwórz pusty pakiet MIME.  
  
3.  Zidentyfikuj w oryginalnym XML typu infoset sprawdzonych elementów informacji elementu Optymalizacja. Dla elementów Optymalizacja znaki które tworzą `[children]` informacje o elementach elementu musi być w formie kanonicznej `xs:base64Binary` (zobacz XSD-2, 3.2.16 base64Binary) i nie może zawierać białych znaków poprzedzających wbudowany, lub po zawartości odstępem.  
  
4.  Utwórz XOP koperty protokołu SOAP, który jest kopią oryginalnego koperty protokołu SOAP, ale z elementów informacje o poszczególnych elementach podrzędnych elementu w poprzednim kroku zastępuje `xop:Include` elementu informacji elementu następującą postać:  
  
    1.  Przekształć zastąpionego znaków w danych binarnych przez przetwarzanie je jako dane zakodowane w formacie base64.  
  
    2.  Generuj unikatowy wartość nagłówka Content-ID, który spełnia wymagania R3133 i R3134.  
  
    3.  Wygeneruj nagłówek MIME Content-Transfer-Encoding o wartości binarnej.  
  
    4.  Jeśli element elementu informacje są optymalizowane ([nadrzędny] nowo wstawionej `xop:Include` elementu informacji element) ma `xmime:contentType` atrybutu elementu informacji, wygeneruj nagłówek MIME Content-Type o wartości `xmime:contentType` atrybutu.  
  
    5.  Generowanie nowej części MIME binarnego z zawartością utworzone przez dane binarne odczytany z zastąpionego znaki przetwarzane jako base64, nagłówek Content-ID z 4b, nagłówek Content-Transfer-Encoding z 4c nagłówka Content-Type, jeśli generowany w kroku 4d.  
  
    6.  Dodaj `href` atrybutu `xop:Include` elementu o wartości cid: identyfikator uri pochodzące z wartość nagłówka Content-ID wygenerowany w kroku 4b. Usuń otaczający "\<" i ">" znaki ucieczki adresu URL pozostałe ciąg i Dodaj prefiks `cid:`. Następujący zestaw znaków minimalna jest wymagany do ucieczkę można zastosować RFC1738 i specyfikacja RFC 2396. Można użyć znaków ucieczki innych znaków.  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  Utwórz głównej części MIME o XOP koperty protokołu SOAP z kroku 4.  
  
6.  Zapisać nagłówków HTTP, w tym nagłówka HTTP Content-Type.  
  
7.  Należy zapisać pakiet MIME.  
  
#### <a name="processing-mtom-messages"></a>Komunikaty mechanizmu MTOM przetwarzania  
 Przetwarzanie MTOM wiadomość jest dokładną odwrotnością proces opisany w poprzednim "Generowanie MTOM wiadomości" sekcji:  
  
1.  Upewnij się, głównej części MIME ma typ zawartości `application/xop+xml`.  
  
2.  Konstruować koperty protokołu SOAP, analizując głównej części MIME pakietu jako dokument XML. Kodowanie znaków jest określany przez `charset` parametru Content-Type dla głównej części MIME.  
  
3.  Dla każdego elementu informacji elementu skonstruowane koperty protokołu SOAP, który ma, jedynym członkiem właściwości [dzieci] `xop:Include` elementu informacji elementu:  
  
    1.  Usuń `cid:` prefiks i unescape wszystkie sekwencje ucieczki identyfikatora URI (RFC 2396) w wartości `@href` atrybutu `xop:Include` elementu. Umieść ciąg wyniku w "\<", ">".  
  
    2.  Znajdź części MIME o pasującej do ciągu uzyskane w kroku 3a wartość nagłówka Content-ID.  
  
    3.  Zastąp `xop:Include` element informacji elementu z `children` właściwości każdego elementu z elementami informacji znak reprezentujących kodowania base64 kanoniczny (zobacz XSD-2, 3.2.16 base64Binary) z treści jednostki części MIME zidentyfikowany w kroku 3b (skutecznie zastępują `xop:Include` elementu element informacji o danych odtworzone z części pakietu).  
  
#### <a name="http-content-type-header"></a>Nagłówek Content-Type protokołu HTTP  
 Poniżej przedstawiono listę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wyjaśnienia formatu nagłówka HTTP Content-Type komunikatu MTOM zakodowane w formacie 1.x SOAP pochodzi od wymagania określone w specyfikacji MTOM sam i pochodne MTOM i dokument RFC 2387.  
  
-   R4131: Nagłówek HTTP Content-Type musi mieć wartość multipart/powiązane (bez uwzględniania wielkości liter) i jego parametrów. Nazwa parametru jest rozróżniana wielkość liter. Kolejność parametrów nie ma znaczenia.  
  
-   Pełna formularz Backus-Naur formularza (BNF) nagłówka Content-Type dla wiadomości MIME ma na liście 2045 RFC, sekcji 5.1.  
  
-   R4132: Nagłówek HTTP Content-Type musi mieć parametr typu o wartości `application/xop+xml` ujęta w znaki podwójnego cudzysłowu.  
  
 Podczas wymaganie, aby użyć podwójnego cudzysłowu nie jest jawną w dokumencie RFC 2387, tekst przestrzega, że wszystkie typu multipart/związane z nośnika, najprawdopodobniej parametrów zawiera zarezerwowanych znaków, takich jak "@" or "/" i w związku z tym należy podwójnych cudzysłowów prostych.  
  
-   R4133: Nagłówek HTTP Content-Type musi mieć parametr start o wartości nagłówka Identyfikatora zawartości części MIME, który zawiera SOAP 1.x koperty ujęta w znaki podwójnego cudzysłowu. W przypadku pominięcia początkowa pierwsza część MIME musi zawierać SOAP 1.x koperty.  
  
-   R4134: Nagłówek HTTP Content-Type dla komunikatu SOAP 1.1 MTOM zakodowane musi zawierać informacje o uruchomieniu parametru z wartością tekstu/xml, ujęta w znaki podwójnego cudzysłowu.  
  
-   R4135: Nagłówka HTTP Content-Type komunikatu kodowany w formacie protokołu SOAP 1.2 MTOM muszą zawierać informacje o uruchomieniu parametru z wartością `application/soap+xml`, ujęty w podwójny cudzysłów.  
  
-   R4136: Nagłówek HTTP Content-Type dla komunikatu MTOM zakodowane w formacie 1.x SOAP musi mieć parametr granic o wartości (ujęta w znaki podwójnego cudzysłowu) odpowiadający granicą MIME, zdefiniowanych w specyfikacji RFC 2046 sekcji 5.1.1 BNF  
  
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
  
#### <a name="infoset-mime-part"></a>Obiekt typu infoset części MIME  
 SOAP 1.x koperty jest hermetyzowany jako część pakietu XOP MIME głównym i jest często nazywana `infoset` części.  
  
-   R4141: SOAP 1.x koperty musi hermetyzowany jako część pakietu XOP MIME o nazwie głównego `infoset` należą i do którego istnieje odwołanie z HTTP Content-Type.  
  
-   R4142: SOAP `Infoset` części musi zawierać następujące nagłówki MIME: `Content-ID`, `Content-Transfer-Encoding`, i `Content-Type`.  
  
 Format nagłówka Content-ID jest zdefiniowany w dokumencie RFC 2045 jako  
  
```  
"Content-ID" ":" msg-id  
```  
  
 gdzie `msg-id` jest zdefiniowana w dokumencie RFC 2822, (zastępującym RFC 822, do którego odwołuje się RFC 2045) jako:  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 i jest efektywne adresu e-mail ujętą w nawiasy klamrowe "\<" i ">". `[CFWS]` Prefiksu i sufiksu dodano RFC 2822 do przenoszenia komentarze i nie powinna być używana w celu zachowania współdziałania.  
  
 R4143: Wartość nagłówka Content-ID części MIME typu Infoset wykonaj `msg-id` produkcyjnych z RFC 2822 z `[CFWS]` części prefiksu i sufiksu pominięty.  
  
 Liczba wdrożeń MIME rozluźnić, wymagania dotyczące wartości ujętych w nawiasy klamrowe "\<" i ">" jako adres e-mail i użyć `absoluteURI` ujęta w "\<", ">" oprócz adresu e-mail. Ta wersja [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa wartości nagłówek MIME Content-ID w postaci:  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 R4144: Procesorów MTOM powinna obsługiwać zgodnych rozluźnić, poniżej wartości nagłówka Content-ID `msg-id`.  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 MIME (RFC 2045) zawiera nagłówek Content-Transfer-Encoding do komunikacji, kodowania zawartości części MIME. Domyślnie zdefiniowane dla Content-Transfer-Encoding jest 7-bitowym, który nie jest odpowiedni dla większości wiadomości SOAP, więc nagłówka Content-Transfer-Encoding jest potrzebny większy współdziałania:  
  
-   R4145: Część obiektu typu Infoset SOAP musi zawierać nagłówek Content-Transfer-Encoding.  
  
-   R4146: W przypadku koperty protokołu SOAP kodowania znaków UTF-8, wartość nagłówka Content-Transfer-Encoding musi być 8-bitową.  
  
-   R4147: W przypadku koperty protokołu SOAP kodowania znaków UTF-16, wartość nagłówka Content-Transfer-Encoding musi być binarny.  
  
-   Zgodnie z [XOP] sekcji 5,  
  
-   R4148: Część obiektu typu Infoset SOAP1.1 musi zawierać nagłówek Content-Type o typ nośnika application/xop + xml i parametry typu = "text/xml" i zestawu znaków  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   R4149: Część obiektu typu Infoset SOAP 1.2 musi zawierać nagłówek Content-Type z typem nośnika `application/xop+xml` i parametry type = "`application/soap+xml`" i `charset`.  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     Gdy definiuje XOP `charset` parametr `application/xop+xml` jako opcjonalną, wymagana jest podobne do wymagań BP 1.1 na współdziałanie `charset` parametr `text/xml` typu nośnika.  
  
-   R41410: `type` i `charset` parametry muszą być obecne w nagłówku Content-Type części typu Infoset 1.x protokołu SOAP.  
  
#### <a name="wcf-endpoint-support-for-mtom"></a>Obsługa punktu końcowego WCF MTOM  
 MTOM ma na celu kodowania komunikatu protokołu SOAP, aby zoptymalizować dane zakodowane w formacie base64. Poniżej znajduje się lista warunków ograniczających:  
  
-   R4151: Może zostać zoptymalizowany dowolny element informacji elementu zawierającego dane zakodowane w formacie base64.  
  
-   B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optymalizuje element informacji elementy, które zawierają dane zakodowane w formacie base64 i przekracza 1024 bajtów długości.  
  
 A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punkt końcowy jest skonfigurowana do używania MTOM zawsze będzie wysyłać wiadomości w formacie MTOM. Nawet jeśli żadne części spełniają kryteria wymagane, wiadomość jest nadal MTOM kodowany w formacie (serializowany jako pakiet MIME z jednej części MIME zawierającej koperty protokołu SOAP).  
  
### <a name="ws-policy-assertion-for-mtom"></a>Potwierdzenie WS-Policy dla MTOM  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa następujących potwierdzenia zasad w celu wskazania MTOM użycia przez punkt końcowy:  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   R4211: Poprzedniego potwierdzenia zasad ma temat zasady punktu końcowego i określa, że wszystkie wiadomości wysyłane do i odbierane z punktu końcowego musi być zoptymalizowany przy użyciu mechanizmu MTOM.  
  
-   B4212: Podczas konfigurowania używania optymalizacji MTOM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego dodaje potwierdzenia zasad MTOM do zasady dołączone do odpowiedniej `wsdl:binding`.  
  
### <a name="composition-with-ws-security"></a>Kompozycja z zabezpieczenia WS  
 MTOM jest mechanizmem kodowania, która jest podobna do `text/xml` i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binarny XML. MTOM oferuje fizycznych kompozycji WS-Security i inne usługi WS-* protokoły: wiadomości uwierzytelnionej za pomocą usługi WS-Security mogą być optymalizowane za pomocą mechanizmu MTOM.  
  
### <a name="examples"></a>Przykłady  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>Usługi WCF SOAP 1.1 komunikat zakodowane przy użyciu mechanizmu MTOM  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>Usługi WCF bezpiecznego protokołu SOAP 1.2 komunikat zakodowane przy użyciu mechanizmu MTOM  
 W tym przykładzie wiadomość jest zakodowany przy użyciu mechanizmu MTOM i SOAP 1.2, która jest chroniona za pomocą usługi WS-Security. Części binarnej zidentyfikowane dla kodowania zawartości `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpowiedniego podpisu zaszyfrowanego i zaszyfrowanej treści. Należy pamiętać, że `CipherValue` z `EncryptedKey` nie została zidentyfikowana optymalizacji przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ponieważ jego długość jest mniej następnie 1024 bajty.  
  
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
