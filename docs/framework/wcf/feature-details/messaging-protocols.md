---
title: Protokoły obsługi komunikatów
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 814347c77b54c4450aabf0a4f3966df223360663
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463833"
---
# <a name="messaging-protocols"></a><span data-ttu-id="01a18-102">Protokoły obsługi komunikatów</span><span class="sxs-lookup"><span data-stu-id="01a18-102">Messaging Protocols</span></span>

<span data-ttu-id="01a18-103">Stos kanału Windows Communication Foundation (WCF) wykorzystuje kanały kodowania i transportu, aby przekształcić reprezentację wiadomości wewnętrznych w format sieci przewodowej i wysłać ją przy użyciu określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="01a18-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="01a18-104">Najczęstszym transportem używanym do współdziałania usług sieci Web jest HTTP, a najczęstszymi kodowaniami używanymi przez usługi sieci Web są oparte na języku XML SOAP 1.1, SOAP 1.2 i Mechanizm optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="01a18-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="01a18-105">W tym temacie opisano szczegóły implementacji WCF <xref:System.ServiceModel.Channels.HttpTransportBindingElement>dla następujących protokołów zastosowanych przez program .</span><span class="sxs-lookup"><span data-stu-id="01a18-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="01a18-106">Specyfikacja/dokument:</span><span class="sxs-lookup"><span data-stu-id="01a18-106">Specification/document:</span></span>

- [<span data-ttu-id="01a18-107">Protokół HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="01a18-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="01a18-108">[Oprawa HTTP SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Sekcja 7</span><span class="sxs-lookup"><span data-stu-id="01a18-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="01a18-109">[Powiązanie HTTP w soap 1.2](https://www.w3.org/TR/soap12-part2) Sekcja 7</span><span class="sxs-lookup"><span data-stu-id="01a18-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="01a18-110">W tym temacie opisano szczegóły implementacji WCF dla następujących protokołów, które <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> zatrudniają.</span><span class="sxs-lookup"><span data-stu-id="01a18-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="01a18-111">Specyfikacja/dokument:</span><span class="sxs-lookup"><span data-stu-id="01a18-111">Specification/Document:</span></span>

- [<span data-ttu-id="01a18-112">XML</span><span class="sxs-lookup"><span data-stu-id="01a18-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="01a18-113">MYDŁO 1.1</span><span class="sxs-lookup"><span data-stu-id="01a18-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="01a18-114">MYDŁO 1.2 Rdzeń</span><span class="sxs-lookup"><span data-stu-id="01a18-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="01a18-115">Adresowanie WS 2004/08</span><span class="sxs-lookup"><span data-stu-id="01a18-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="01a18-116">W3C Web Services Adresowanie 1.0 - Rdzeń</span><span class="sxs-lookup"><span data-stu-id="01a18-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="01a18-117">Adresowanie usług sieci Web W3C 1.0 — powiązanie z mydłem</span><span class="sxs-lookup"><span data-stu-id="01a18-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="01a18-118">Adresowanie usług sieci Web W3C 1.0 — powiązanie WSDL</span><span class="sxs-lookup"><span data-stu-id="01a18-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="01a18-119">Adresowanie usług sieci Web W3C 1.0 — metadane</span><span class="sxs-lookup"><span data-stu-id="01a18-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="01a18-120">Oprawa WSDL SOAP1.1</span><span class="sxs-lookup"><span data-stu-id="01a18-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="01a18-121">Oprawa WSDL SOAP1.2</span><span class="sxs-lookup"><span data-stu-id="01a18-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="01a18-122">W tym temacie opisano szczegóły implementacji WCF dla następujących protokołów, który <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> zatrudnia.</span><span class="sxs-lookup"><span data-stu-id="01a18-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="01a18-123">Specyfikacja/dokument:</span><span class="sxs-lookup"><span data-stu-id="01a18-123">Specification/document:</span></span>

- [<span data-ttu-id="01a18-124">Xop</span><span class="sxs-lookup"><span data-stu-id="01a18-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="01a18-125">Wiązania MTOM + SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="01a18-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="01a18-126">Wiązania MTOM SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="01a18-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="01a18-127">Twierdzenie zasad MTOM WS</span><span class="sxs-lookup"><span data-stu-id="01a18-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="01a18-128">W tym temacie używane są następujące przestrzenie nazw XML i skojarzone z nimi prefiksy:</span><span class="sxs-lookup"><span data-stu-id="01a18-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="01a18-129">Prefiks</span><span class="sxs-lookup"><span data-stu-id="01a18-129">Prefix</span></span> | <span data-ttu-id="01a18-130">Jednolity identyfikator zasobów obszaru nazw (URI)</span><span class="sxs-lookup"><span data-stu-id="01a18-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="01a18-131">s11</span><span class="sxs-lookup"><span data-stu-id="01a18-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="01a18-132">s12</span><span class="sxs-lookup"><span data-stu-id="01a18-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="01a18-133">Wsa</span><span class="sxs-lookup"><span data-stu-id="01a18-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="01a18-134">wsam</span><span class="sxs-lookup"><span data-stu-id="01a18-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="01a18-135">wsap</span><span class="sxs-lookup"><span data-stu-id="01a18-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="01a18-136">wsa10</span><span class="sxs-lookup"><span data-stu-id="01a18-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="01a18-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="01a18-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="01a18-138">Xop</span><span class="sxs-lookup"><span data-stu-id="01a18-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="01a18-139">xmime ( xmime )</span><span class="sxs-lookup"><span data-stu-id="01a18-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="01a18-140">Dp</span><span class="sxs-lookup"><span data-stu-id="01a18-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="01a18-141">MYDŁO 1.1 i MYDŁO 1.2</span><span class="sxs-lookup"><span data-stu-id="01a18-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="01a18-142">Model koperty i przetwarzania</span><span class="sxs-lookup"><span data-stu-id="01a18-142">Envelope and Processing Model</span></span>
<span data-ttu-id="01a18-143">WCF implementuje przetwarzanie koperty SOAP 1.1 zgodnie z profilem podstawowym 1.1 (BP11) i profilem podstawowym 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="01a18-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="01a18-144">PRZETWARZANIE KOPERTY SOAP 1.2 jest realizowane zgodnie z mydłem 12-Part1.</span><span class="sxs-lookup"><span data-stu-id="01a18-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="01a18-145">W tej sekcji opisano niektóre wybory implementacji podjęte przez WCF w odniesieniu do BP11 i SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="01a18-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="01a18-146">Obowiązkowe przetwarzanie nagłówka</span><span class="sxs-lookup"><span data-stu-id="01a18-146">Mandatory Header Processing</span></span>
<span data-ttu-id="01a18-147">WCF następuje zasady przetwarzania `mustUnderstand` nagłówków oznaczonych w wymaganiach PROTOKOŁU SOAP 1.1 i SOAP 1.2, z następującymi odmianami.</span><span class="sxs-lookup"><span data-stu-id="01a18-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="01a18-148">Komunikat, który wchodzi do stosu kanałów WCF jest przetwarzany przez poszczególne kanały skonfigurowane przez skojarzone elementy powiązania, na przykład kodowanie wiadomości tekstowych, zabezpieczenia, niezawodne wiadomości i transakcje.</span><span class="sxs-lookup"><span data-stu-id="01a18-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="01a18-149">Każdy kanał rozpoznaje nagłówki z skojarzonego obszaru nazw i oznacza je jako zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="01a18-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="01a18-150">Po wprowadzeniu komunikatu do dyspozytora program formatera operacji odczytuje nagłówki oczekiwane przez odpowiedni kontrakt na wiadomość/operację i oznacza je zrozumiane.</span><span class="sxs-lookup"><span data-stu-id="01a18-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="01a18-151">Następnie dyspozytor sprawdza, czy wszystkie pozostałe nagłówki `mustUnderstand` nie są zrozumiałe, ale oznaczone jako i zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="01a18-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="01a18-152">Wiadomości zawierające `mustUnderstand` nagłówki przeznaczone dla adresata nie są przetwarzane przez kod aplikacji adresata.</span><span class="sxs-lookup"><span data-stu-id="01a18-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="01a18-153">Takie przetwarzanie warstwowe umożliwia oddzielenie warstw infrastruktury od warstw aplikacji węzła SOAP:</span><span class="sxs-lookup"><span data-stu-id="01a18-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="01a18-154">B1111: Nagłówki, które nie są zrozumiałe, są wykrywane po przetworzyniu wiadomości przez stos kanału infrastruktury WCF, ale przed przetworzeniem przez aplikację</span><span class="sxs-lookup"><span data-stu-id="01a18-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="01a18-155">Wartość `mustUnderstand` nagłówka różni się między MYDŁEM 1.1 i SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="01a18-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="01a18-156">Profil podstawowy 1.1 `mustUnderstand` wymaga, aby wartość 0 lub 1 dla komunikatów PROTOKOŁU SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="01a18-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="01a18-157">PROTOKÓŁ SOAP 1.2 pozwala na `false`0, 1 `true` i jako wartości, ale `xs:boolean` zaleca`false` `true`emitowanie kanonicznej reprezentacji wartości ( , ).</span><span class="sxs-lookup"><span data-stu-id="01a18-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="01a18-158">B1112: WCF `mustUnderstand` emituje wartości 0 i 1 dla obu wersji SOAP 1.1 i SOAP 1.2 koperty SOAP.</span><span class="sxs-lookup"><span data-stu-id="01a18-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="01a18-159">WCF akceptuje całą przestrzeń `xs:boolean` wartości `mustUnderstand` nagłówka (0, `false`1, , `true`)</span><span class="sxs-lookup"><span data-stu-id="01a18-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="01a18-160">Błędy mydła</span><span class="sxs-lookup"><span data-stu-id="01a18-160">SOAP Faults</span></span>
<span data-ttu-id="01a18-161">Poniżej znajduje się lista implementacji błędów protokołu SOAP specyficzne dla WCF.</span><span class="sxs-lookup"><span data-stu-id="01a18-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="01a18-162">B2121: WCF zwraca następujące kody usterek `s11:mustUnderstand` `s11:Client`PROTOKOŁU `s11:Server`SOAP 1.1: , , i .</span><span class="sxs-lookup"><span data-stu-id="01a18-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="01a18-163">B2122: WCF zwraca następujące kody usterek `s12:MustUnderstand` `s12:Sender`PROTOKOŁU `s12:Receiver`SOAP 1.2: , , i .</span><span class="sxs-lookup"><span data-stu-id="01a18-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="01a18-164">Powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="01a18-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="01a18-165">Powiązanie HTTP w soap 1.1</span><span class="sxs-lookup"><span data-stu-id="01a18-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="01a18-166">WCF implementuje powiązanie HTTP SOAP1.1 zgodnie z sekcją 3.4 specyfikacji profilu podstawowego 1.1 z następującymi wyjaśnieniami:</span><span class="sxs-lookup"><span data-stu-id="01a18-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="01a18-167">B2211: Usługa WCF nie implementuje przekierowywania żądań HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="01a18-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="01a18-168">B2212: Klienci WCF obsługują pliki cookie HTTP zgodnie z 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="01a18-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="01a18-169">Powiązanie HTTP w soap 1.2</span><span class="sxs-lookup"><span data-stu-id="01a18-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="01a18-170">WCF implementuje wiązanie HTTP PROTOKOŁU SOAP 1.2 zgodnie z opisem w specyfikacji SOAP 1.2-part 2 (SOAP12Part2) z następującymi wyjaśnieniami.</span><span class="sxs-lookup"><span data-stu-id="01a18-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="01a18-171">W programie SOAP 1.2 wprowadzono `application/soap+xml` opcjonalny parametr akcji dla typu nośnika.</span><span class="sxs-lookup"><span data-stu-id="01a18-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="01a18-172">Ten parametr jest przydatny do optymalizacji wysyłania wiadomości bez konieczności analizowania treści komunikatu SOAP, gdy adresowanie WS nie jest używane.</span><span class="sxs-lookup"><span data-stu-id="01a18-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="01a18-173">R2221: `application/soap+xml` Parametr akcji, gdy jest obecny w żądaniu SOAP `soapAction` 1.2, musi być zgodny z atrybutem `wsoap12:operation` elementu wewnątrz odpowiedniego powiązania WSDL.</span><span class="sxs-lookup"><span data-stu-id="01a18-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="01a18-174">R2222: `application/soap+xml` Parametr akcji, jeśli jest obecny w komunikacie SOAP `wsa:Action` 1.2, musi być zgodny, gdy używane są adresowanie WS 2004/08 lub adresowanie WS 1.0.</span><span class="sxs-lookup"><span data-stu-id="01a18-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="01a18-175">Gdy adresowanie WS jest wyłączone, a żądanie przychodzące `Action` nie zawiera parametru akcji, komunikat jest uważany za nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="01a18-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="01a18-176">Adresowanie WS</span><span class="sxs-lookup"><span data-stu-id="01a18-176">WS-Addressing</span></span>
<span data-ttu-id="01a18-177">WCF implementuje 3 wersje WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="01a18-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="01a18-178">Adresowanie WS 2004/08</span><span class="sxs-lookup"><span data-stu-id="01a18-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="01a18-179">W3C Web Services Adresowanie 1.0 Core (ADDR10-CORE) i mydło wiązania (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="01a18-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="01a18-180">Adresowanie WS 1.0 - Metadane</span><span class="sxs-lookup"><span data-stu-id="01a18-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="01a18-181">Odwołania do punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="01a18-181">Endpoint References</span></span>
<span data-ttu-id="01a18-182">Wszystkie wersje WS-Addressing, który WCF implementuje używać odwołań do punktów końcowych do opisywania punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="01a18-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="01a18-183">Odwołania do punktów końcowych i wersje adresowania WS</span><span class="sxs-lookup"><span data-stu-id="01a18-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="01a18-184">WCF implementuje szereg protokołów infrastruktury, które używają WS-Addressing, a w szczególności `EndpointReference` element i `W3C.WsAddressing.EndpointReferenceType` klasy (na przykład WS-ReliableMessaging, WS-SecureConversation i WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="01a18-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="01a18-185">WCF obsługuje korzystanie z każdej wersji WS-Addressing z innymi protokołami infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="01a18-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="01a18-186">Punkty końcowe WCF obsługują jedną wersję adresowania WS na punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="01a18-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="01a18-187">Dla R3111 obszar nazw `EndpointReference` dla elementu lub typu używanego w wiadomościach wymienianych z punktem końcowym WCF musi być zgodna z wersją WS-Addressing zaimplementowane przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="01a18-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="01a18-188">Na przykład jeśli punkt końcowy WCF implementuje WS-ReliableMessaging, `AcksTo` nagłówek zwrócony przez taki punkt końcowy wewnątrz `EncodingBinding` `CreateSequenceResponse` używa wersji adresowania WS, która określa element dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="01a18-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="01a18-189">Odwołania i metadane punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="01a18-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="01a18-190">Wiele scenariuszy wymaga przekazywania metadanych lub odwołania do metadanych dla danego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="01a18-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="01a18-191">B3121: WCF wykorzystuje mechanizmy opisane w specyfikacji WS-MetadataExchange (MEX) sekcja 6, aby uwzględnić metadane dla odwołań do punktów końcowych według wartości lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="01a18-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="01a18-192">Rozważmy scenariusz, w którym usługa WCF wymaga uwierzytelniania przy użyciu tokenu saml `http://sts.fabrikam123.com`(Security Assertions Markup Language) wystawionego przez wystawcę tokenu w .</span><span class="sxs-lookup"><span data-stu-id="01a18-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="01a18-193">Punkt końcowy WCF opisuje to `sp:IssuedToken` wymaganie uwierzytelniania `sp:Issuer` przy użyciu potwierdzenia z zagnieżdżonego potwierdzenia wskazującego wystawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="01a18-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="01a18-194">Aplikacje klienckie, które uzyskują dostęp do `sp:Issuer` potwierdzenia, muszą wiedzieć, jak komunikować się z punktem końcowym wystawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="01a18-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="01a18-195">Klient musi znać metadane dotyczące wystawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="01a18-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="01a18-196">Za pomocą rozszerzenia metadanych odniesienia punktu końcowego zdefiniowane w MEX, WCF zapewnia odwołanie do metadanych wystawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="01a18-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

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

### <a name="message-addressing-headers"></a><span data-ttu-id="01a18-197">Nagłówki adresowania wiadomości</span><span class="sxs-lookup"><span data-stu-id="01a18-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="01a18-198">Nagłówki wiadomości</span><span class="sxs-lookup"><span data-stu-id="01a18-198">Message Headers</span></span>
<span data-ttu-id="01a18-199">W obu wersjach WS-Addressing WCF używa następujących nagłówków komunikatów `wsa:Action`zgodnie `wsa:MessageID`ze `wsa:RelatesTo`specyfikacjami `wsa:To`, `wsa:ReplyTo`, , i .</span><span class="sxs-lookup"><span data-stu-id="01a18-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="01a18-200">B3211: Dla wszystkich wersji adresowania WS, WCF honoruje, ale nie produkuje po wyjęciu z pudełka, nagłówki komunikatów `wsa:FaultTo` adresowania WS i `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="01a18-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="01a18-201">Aplikacje, które współdziałają z aplikacjami WCF można dodać te nagłówki wiadomości i WCF będzie przetwarzać je odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="01a18-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="01a18-202">Parametry i właściwości odwołania</span><span class="sxs-lookup"><span data-stu-id="01a18-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="01a18-203">WCF implementuje przetwarzanie parametrów odniesienia punktu końcowego i właściwości referencyjnych zgodnie z odpowiednimi specyfikacjami.</span><span class="sxs-lookup"><span data-stu-id="01a18-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="01a18-204">B3221: Po skonfigurowaniu do używania adresu WS 2004/08, punkty końcowe WCF nie rozróżniają właściwości przetwarzania i parametrów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="01a18-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="01a18-205">Wzorce wymiany wiadomości</span><span class="sxs-lookup"><span data-stu-id="01a18-205">Message Exchange Patterns</span></span>
<span data-ttu-id="01a18-206">Sekwencja komunikatów zaangażowanych w wywołanie operacji usługi sieci Web jest określana jako *wzorzec wymiany wiadomości*.</span><span class="sxs-lookup"><span data-stu-id="01a18-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="01a18-207">WCF obsługuje wzorce wymiany komunikatów jednokierunkowych, odpowiedzi na żądania i dupleksu.</span><span class="sxs-lookup"><span data-stu-id="01a18-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="01a18-208">W tej sekcji wyjaśniono wymagania dotyczące adresowania WS dotyczące przetwarzania wiadomości w zależności od używanego wzorca wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="01a18-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="01a18-209">W tej sekcji żądający wysyła pierwszą wiadomość, a obiekt odpowiadający odbiera pierwszą wiadomość.</span><span class="sxs-lookup"><span data-stu-id="01a18-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="01a18-210">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="01a18-210">One-Way Message</span></span>
<span data-ttu-id="01a18-211">Gdy punkt końcowy WCF jest skonfigurowany do `Action` obsługi komunikatów z podanym do naśladowania wzorca jednokierunkowego, punkt końcowy WCF następuje następujące zachowania i wymagania.</span><span class="sxs-lookup"><span data-stu-id="01a18-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="01a18-212">O ile nie określono inaczej, zachowania i reguły mają zastosowanie do obu wersji WS-Addressing obsługiwanych w WCF:</span><span class="sxs-lookup"><span data-stu-id="01a18-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="01a18-213">R3311: Żądający musi `wsa:To` `wsa:Action`zawierać , i nagłówki dla wszystkich parametrów referencyjnych określonych przez odwołanie do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="01a18-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="01a18-214">Gdy używany jest adresowanie WS 2004/08 i [właściwości odwołania] są określone przez odwołanie do punktu końcowego, odpowiednie nagłówki muszą zostać dodane do wiadomości zbyt.</span><span class="sxs-lookup"><span data-stu-id="01a18-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="01a18-215">B3312: Żądający może `MessageID` `ReplyTo`zawierać `FaultTo` , i nagłówki.</span><span class="sxs-lookup"><span data-stu-id="01a18-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="01a18-216">Infrastruktura odbiornika zignoruje je i zostaną przekazane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01a18-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="01a18-217">R3313: Gdy jest używany protokół HTTP i nie jest wysyłana żadna wiadomość w łzowej odpowiedzi HTTP, obiekt odpowiadający musi wysłać odpowiedź HTTP z pustą treścią i kodem stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="01a18-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="01a18-218">Gdy transport HTTP jest w użyciu, a umowa operacji deklaruje wiadomość w jedną stronę, odpowiedź HTTP może nadal służyć `SequenceAcknowledgement` do wysyłania komunikatów infrastruktury — na przykład niezawodne wiadomości mogą wysyłać wiadomość w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="01a18-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="01a18-219">B3314: Obiekt odpowiadający WCF nie wysyła komunikatu o błędzie w odpowiedzi na komunikat jednokierunkowy.</span><span class="sxs-lookup"><span data-stu-id="01a18-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="01a18-220">Żądanie i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="01a18-220">Request-Reply</span></span>
<span data-ttu-id="01a18-221">Gdy punkt końcowy WCF jest skonfigurowany dla `Action` wiadomości z danym do naśladowania wzorca żądania odpowiedzi, punkt końcowy WCF następuje zachowania i wymagania poniżej.</span><span class="sxs-lookup"><span data-stu-id="01a18-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="01a18-222">O ile nie określono inaczej, zachowania i reguły mają zastosowanie do obu wersji WS-Addressing obsługiwanych w WCF:</span><span class="sxs-lookup"><span data-stu-id="01a18-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="01a18-223">R3321: Żądający musi zawierać `wsa:To`w `wsa:Action` `wsa:MessageID`żądaniu , i nagłówki dla wszystkich parametrów referencyjnych lub właściwości odniesienia (lub obu) określonych przez odwołanie do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="01a18-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="01a18-224">R3322: Gdy używany jest adresowanie WS 2004/08, `ReplyTo` musi być również uwzględniony w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="01a18-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="01a18-225">R3323: Gdy WS-Addressing 1.0 `ReplyTo` jest używany i nie jest obecny w żądaniu, domyślne odwołanie do punktu końcowego z [address] właściwość równa `http://www.w3.org/2005/08/addressing/anonymous` jest używana.</span><span class="sxs-lookup"><span data-stu-id="01a18-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="01a18-226">R3324: Żądający musi `wsa:To` `wsa:Action`zawierać `wsa:RelatesTo` , i nagłówki w wiadomości odpowiedzi, a także nagłówki dla wszystkich parametrów referencyjnych lub właściwości odwołania (lub obu) określonych przez odwołanie do punktu `ReplyTo` końcowego w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="01a18-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="01a18-227">Adresowanie błędów usług sieci Web</span><span class="sxs-lookup"><span data-stu-id="01a18-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="01a18-228">R3411: WCF produkuje następujące błędy zdefiniowane przez WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="01a18-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="01a18-229">Code</span><span class="sxs-lookup"><span data-stu-id="01a18-229">Code</span></span> | <span data-ttu-id="01a18-230">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="01a18-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="01a18-231">Wiadomość dotarła `ReplyTo` z treścią różniącą się od adresu odpowiedzi ustanowionego dla tego kanału; nie ma punktu końcowego nasłuchiwania pod adresem określonym w nagłówku Do.</span><span class="sxs-lookup"><span data-stu-id="01a18-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="01a18-232">kanały infrastruktury lub dyspozytor skojarzony z punktem `Action` końcowym nie rozpoznają akcji określonej w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="01a18-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="01a18-233">R3412: WCF produkuje następujące błędy zdefiniowane przez WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="01a18-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="01a18-234">Code</span><span class="sxs-lookup"><span data-stu-id="01a18-234">Code</span></span> | <span data-ttu-id="01a18-235">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="01a18-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="01a18-236">Duplikat `wsa:To`, `wsa:ReplyTo`lub `wsa:From` `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="01a18-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="01a18-237">`wsa:RelatesTo` Duplikuj `RelationshipType`z tym samym .</span><span class="sxs-lookup"><span data-stu-id="01a18-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="01a18-238">Brak wymaganego nagłówka Adresowania.</span><span class="sxs-lookup"><span data-stu-id="01a18-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="01a18-239">Wiadomość dotarła `ReplyTo` z treścią różniącą się od adresu odpowiedzi ustanowionego dla tego kanału.</span><span class="sxs-lookup"><span data-stu-id="01a18-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="01a18-240">Nie ma punktu końcowego nasłuchiwania pod adresem określonym w nagłówku Do.</span><span class="sxs-lookup"><span data-stu-id="01a18-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="01a18-241">Akcja określona `Action` w nagłówku nie jest rozpoznawana przez kanały infrastruktury lub dyspozytora skojarzone z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="01a18-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="01a18-242">Kanał RM wysyła ten błąd z powrotem, wskazując, że punkt `CreateSequence` końcowy nie będzie przetwarzać sekwencji na podstawie badania nagłówków adresowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="01a18-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="01a18-243">Kod w poprzednich tabelach `FaultCode` jest mapowany na `SubCode` w soap 1.1 i (z Code=Sender) w SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="01a18-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="01a18-244">WSDL 1.1 Powiązania i WS-Policy Potwierdzenia</span><span class="sxs-lookup"><span data-stu-id="01a18-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="01a18-245">Wskazanie użycia adresowania WS</span><span class="sxs-lookup"><span data-stu-id="01a18-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="01a18-246">WCF używa potwierdzeń zasad, aby wskazać obsługę punktu końcowego dla określonej wersji adresowania WS.</span><span class="sxs-lookup"><span data-stu-id="01a18-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="01a18-247">Następujące twierdzenie zasad ma temat zasad punktu końcowego [WS-PA] i wskazuje wiadomości wysyłane i odbierane z punktu końcowego należy użyć WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="01a18-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="01a18-248">To twierdzenie zasad rozszerza specyfikację WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="01a18-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="01a18-249">Następujące twierdzenie zasad oznacza, że wiadomości wysłane/odebrane muszą używać adresu WS 1.0.</span><span class="sxs-lookup"><span data-stu-id="01a18-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="01a18-250">Następujące twierdzenie zasad ma temat zasad punktu końcowego [WS-PA] i wskazuje, że wiadomości wysyłane i odbierane z punktu końcowego muszą używać adresowania WS 2004/08.</span><span class="sxs-lookup"><span data-stu-id="01a18-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="01a18-251">Element `wsaw10:UsingAddressing` jest zapożyczony z [WS-Addressing-WSDL] i jest używany w kontekście WS-Policy zgodnie z tą specyfikacją, sekcja 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="01a18-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="01a18-252">Użycie adresowania nie zmienia semantyki w 1.1, SOAP 1.1 i SOAP 1.2 POWIĄZANIA HTTP.</span><span class="sxs-lookup"><span data-stu-id="01a18-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="01a18-253">Na przykład jeśli oczekuje się odpowiedzi na żądanie, które jest wysyłane do punktu końcowego, który używa adresowania i WSDL SOAP 1.x powiązanie HTTP, odpowiedź musi być wysłana przy użyciu odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="01a18-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="01a18-254">W przypadku odpowiedzi wysyłanych za pośrednictwem odpowiedzi http twierdzenie WS-AM jest:</span><span class="sxs-lookup"><span data-stu-id="01a18-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="01a18-255">Pełne twierdzenie zasad może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="01a18-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="01a18-256">Istnieją jednak wzorce wymiany komunikatów, które korzystają z dwóch niezależnych połączeń HTTP odwrotnych ustanowione między obiektem żądający i obiektu odpowiadającego, na przykład niechciane wiadomości jednokierunkowe wysyłane przez obiekt odpowiadający.</span><span class="sxs-lookup"><span data-stu-id="01a18-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="01a18-257">WCF oferuje funkcję, za pomocą której dwa podstawowe kanały transportu mogą tworzyć kanał composite duplex, gdzie jeden kanał jest używany dla komunikatów wejściowych, a drugi jest używany dla komunikatów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="01a18-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="01a18-258">W przypadku transportu HTTP composite duplex zapewnia dwa odwrotne połączenia HTTP.</span><span class="sxs-lookup"><span data-stu-id="01a18-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="01a18-259">Żądający używa jednego połączenia do wysyłania wiadomości do obiektu odpowiadającego, a osoba odpowiadająca używa drugiego do wysyłania wiadomości z powrotem do żądacza.</span><span class="sxs-lookup"><span data-stu-id="01a18-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="01a18-260">W przypadku odpowiedzi wysyłanych za pośrednictwem oddzielnych żądań http twierdzenie ws-am jest</span><span class="sxs-lookup"><span data-stu-id="01a18-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="01a18-261">Pełne twierdzenie zasad może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="01a18-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="01a18-262">Użycie następującego potwierdzenia, które ma temat zasad punktu końcowego [WS-PA] w punktach końcowych, które używają wsdl 1.1 SOAP 1.x powiązania HTTP wymaga dwóch oddzielnych połączeń HTTP odwrotnych do wiadomości płynących z żądającego do obiektu odpowiadającego i obiektu odpowiadającego do żądającego, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="01a18-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="01a18-263">Poprzednia instrukcja prowadzi do następujących `wsa:ReplyTo` wymagań w nagłówku dla komunikatów żądania:</span><span class="sxs-lookup"><span data-stu-id="01a18-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="01a18-264">R3514: Żądania wiadomości wysyłane do punktu `ReplyTo` końcowego `[address]` musi mieć `http://www.w3.org/2005/08/addressing/anonymous` nagłówek z właściwości nie równa się, jeśli punkt końcowy używa WSDL 1.1 SOAP 1.x HTTP powiązania i ma alternatywę `wsap10:UsingAddressing` zasad z lub `wsap:UsingAddressing` potwierdzenia w połączeniu z `cdp:CompositeDuplex` dołączonym.</span><span class="sxs-lookup"><span data-stu-id="01a18-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="01a18-265">R3515: Żądania wiadomości wysyłane do punktu `ReplyTo` końcowego `[address]` musi `http://www.w3.org/2005/08/addressing/anonymous`mieć nagłówek z `ReplyTo` właściwością równą , lub nie mają nagłówka w ogóle, jeśli punkt końcowy używa WSDL 1.1 SOAP 1.x HTTP powiązania i ma alternatywne zasady z `wsap10:UsingAddressing` twierdzeniem i nie `cdp:CompositeDuplex` potwierdzenia dołączone.</span><span class="sxs-lookup"><span data-stu-id="01a18-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="01a18-266">R3516: Żądania wiadomości wysyłane do punktu `ReplyTo` końcowego `[address]` musi `http://www.w3.org/2005/08/addressing/anonymous` mieć nagłówek z właściwością równą, jeśli punkt końcowy używa WSDL 1.1 SOAP 1.x HTTP powiązania i ma alternatywę zasad z `wsap:UsingAddressing` twierdzeniem i nie `cdp:CompositeDuplex` potwierdzenia dołączone.</span><span class="sxs-lookup"><span data-stu-id="01a18-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="01a18-267">Specyfikacja WS-addressing WSDL próbuje opisać podobne powiązania protokołu, wprowadzając element `<wsaw:Anonymous/>` z trzema wartościami tekstowymi (wymaganymi, `wsa:ReplyTo` opcjonalnymi i zabronionymi) w celu wskazania wymagań w nagłówku (sekcja 3.2).</span><span class="sxs-lookup"><span data-stu-id="01a18-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="01a18-268">Niestety taka definicja elementu nie jest szczególnie użyteczna jako twierdzenie w kontekście WS-Policy, ponieważ wymaga rozszerzenia specyficzne dla domeny do obsługi przecięcia alternatyw przy użyciu takiego elementu jako potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="01a18-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="01a18-269">Taka definicja elementu wskazuje również `ReplyTo` wartość nagłówka, w przeciwieństwie do zachowania punktu końcowego w sieci, co sprawia, że specyficzne dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="01a18-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="01a18-270">Definicja akcji</span><span class="sxs-lookup"><span data-stu-id="01a18-270">Action Definition</span></span>
<span data-ttu-id="01a18-271">Adresowanie WS 2004/08 definiuje `wsa:Action` atrybut dla `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementów.</span><span class="sxs-lookup"><span data-stu-id="01a18-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="01a18-272">Powiązanie WS-Addressing 1.0 WSDL (WS-ADDR10-WSDL) definiuje `wsaw10:Action`podobny atrybut.</span><span class="sxs-lookup"><span data-stu-id="01a18-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="01a18-273">Jedyną różnicą między nimi jest domyślna semantyka wzorca akcji opisana odpowiednio w sekcji 3.3.2 WS-ADDR i sekcji 4.4.4 WS-ADDR10-WSDL.</span><span class="sxs-lookup"><span data-stu-id="01a18-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="01a18-274">Uzasadnione jest, aby mieć dwa punkty końcowe, które współużytkują takie same `portType` (lub umowy, w terminologii WCF), ale przy użyciu różnych wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="01a18-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="01a18-275">Ale biorąc pod uwagę, `portType` że akcja jest zdefiniowana przez `portType`i nie powinny zmieniać się w punktach końcowych, które implementują , staje się niemożliwe do obsługi obu wzorców akcji domyślnych.</span><span class="sxs-lookup"><span data-stu-id="01a18-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="01a18-276">Aby rozwiązać ten problem, WCF obsługuje `Action` jedną wersję atrybutu.</span><span class="sxs-lookup"><span data-stu-id="01a18-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="01a18-277">B3521: WCF używa `wsaw10:Action` atrybutu `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` na elementy zdefiniowane w WS-ADDR10-WSDL do określenia identyfikatora `Action` URI dla odpowiednich komunikatów, niezależnie od wersji adresowania WS używane przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="01a18-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="01a18-278">Korzystanie z odwołania do punktu końcowego wewnątrz portu WSDL</span><span class="sxs-lookup"><span data-stu-id="01a18-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="01a18-279">WS-ADDR10-WSDL sekcja 4.1 `wsdl:port` rozszerza element, `<wsa10:EndpointReference…/>` aby uwzględnić element podrzędny, aby opisać punkt końcowy w warunkach adresowania WS.</span><span class="sxs-lookup"><span data-stu-id="01a18-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="01a18-280">WCF rozszerza to narzędzie na WS-Addressing 2004/08, pozwalając `<wsa:EndpointReference…/>` `wsdl:port`na pojawienie się jako element podrzędny .</span><span class="sxs-lookup"><span data-stu-id="01a18-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="01a18-281">R3531: Jeśli punkt końcowy ma dołączoną `<wsaw10:UsingAddressing/>` alternatywę zasad `wsdl:port` z asercjami zasad, odpowiedni element może zawierać element `<wsa10:EndpointReference …/>`podrzędny .</span><span class="sxs-lookup"><span data-stu-id="01a18-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="01a18-282">R3532: Jeśli `wsdl:port` zawiera element `<wsa10:EndpointReference …/>`podrzędny, `wsa10:EndpointReference/wsa10:Address` wartość elementu podrzędnego `@address` musi być `wsdl:port` zgodna z wartością atrybutu elementu równorzędnego. / `wsdl:location`</span><span class="sxs-lookup"><span data-stu-id="01a18-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="01a18-283">R3533: Jeśli punkt końcowy ma dołączoną alternatywę zasad z `<wsap:UsingAddressing/>` twierdzeniem zasad, odpowiedni `wsdl:port` element może zawierać element `<wsa:EndpointReference …/>`podrzędny .</span><span class="sxs-lookup"><span data-stu-id="01a18-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="01a18-284">R3534: Jeśli `wsdl:port` zawiera element `<wsa:EndpointReference …/>`podrzędny, `wsa:EndpointReference/wsa:Address` wartość elementu podrzędnego `@address` musi być `wsdl:port` zgodna z wartością atrybutu elementu równorzędnego. / `wsdl:location`</span><span class="sxs-lookup"><span data-stu-id="01a18-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="01a18-285">Kompozycja z WS-Security</span><span class="sxs-lookup"><span data-stu-id="01a18-285">Composition with WS-Security</span></span>
<span data-ttu-id="01a18-286">Zgodnie z sekcjami zagadnienia dotyczące zabezpieczeń w WS-ADDR i WS-ADDR10, wszystkie nagłówki wiadomości adresowych są zalecane do podpisania razem z treścią wiadomości, aby powiązać je ze sobą.</span><span class="sxs-lookup"><span data-stu-id="01a18-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="01a18-287">Gdy usługa WS-Security jest używana do ochrony integralności wiadomości, nagłówki wiadomości adresowania WS oraz nagłówki wynikające z parametrów referencyjnych lub właściwości (lub obu) muszą być podpisane razem z treścią wiadomości.</span><span class="sxs-lookup"><span data-stu-id="01a18-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="01a18-288">Przykłady</span><span class="sxs-lookup"><span data-stu-id="01a18-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="01a18-289">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="01a18-289">One-Way Message</span></span>
<span data-ttu-id="01a18-290">W tym scenariuszu nadawca wysyła komunikat jednokierunkowy do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="01a18-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="01a18-291">Używane są adresy 1.2, HTTP 1.1 i W3C WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="01a18-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="01a18-292">Struktura żądania wiadomości: nagłówki wiadomości `wsa10:To` `wsa10:Action` zawierają i elementy.</span><span class="sxs-lookup"><span data-stu-id="01a18-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="01a18-293">Treść wiadomości zawiera `<app:Ping>` określony element z obszaru nazw aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01a18-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="01a18-294">Nagłówki HTTP: Miejsce docelowe w POST `wsa10:To` pasuje do identyfikatora URI w elemencie.</span><span class="sxs-lookup"><span data-stu-id="01a18-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="01a18-295">Nagłówek Typ zawartości ma wartość `application/soap+xml` wymaganą przez soap 1.2.</span><span class="sxs-lookup"><span data-stu-id="01a18-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="01a18-296">Parametry `charset` `action` i są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="01a18-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="01a18-297">Parametr `action` nagłówka Typ zawartości jest zgodny `wsa10:Action` z wartością nagłówka wiadomości.</span><span class="sxs-lookup"><span data-stu-id="01a18-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

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

<span data-ttu-id="01a18-298">Odbiorca odpowiada pustą odpowiedzią HTTP i stanem 202.</span><span class="sxs-lookup"><span data-stu-id="01a18-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="01a18-299">Przykład odpowiedzi HTTP:</span><span class="sxs-lookup"><span data-stu-id="01a18-299">An example of the HTTP response:</span></span>

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

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="01a18-300">Mechanizm optymalizacji transmisji komunikatów SOAP</span><span class="sxs-lookup"><span data-stu-id="01a18-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="01a18-301">W tej sekcji opisano szczegóły implementacji WCF dla protokołu HTTP SOAP MTOM.</span><span class="sxs-lookup"><span data-stu-id="01a18-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="01a18-302">Technologia MTOM to mechanizm kodowania wiadomości SOAP tej samej klasy co tradycyjne kodowanie tekstu/XML lub kodowanie binarne WCF.</span><span class="sxs-lookup"><span data-stu-id="01a18-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="01a18-303">MTOM obejmuje:</span><span class="sxs-lookup"><span data-stu-id="01a18-303">MTOM includes the following:</span></span>

- <span data-ttu-id="01a18-304">Mechanizm kodowania i pakowania XML opisany przez [XOP], który optymalizuje elementy informacji XML zawierające dane binarne zakodowane w formacie base64 na oddzielne części binarne.</span><span class="sxs-lookup"><span data-stu-id="01a18-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="01a18-305">Hermetyzacja MIME pakietu XOP, który serializuje zestaw informacji XML i każdą część binarną pakietu XOP do oddzielnej części MIME.</span><span class="sxs-lookup"><span data-stu-id="01a18-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="01a18-306">Kodowanie MIME XOP zastosowane do koperty SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="01a18-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="01a18-307">Powiązanie transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="01a18-307">An HTTP transport binding.</span></span>

<span data-ttu-id="01a18-308">Możliwe jest użycie MTOM z transportami innych niż HTTP z WCF.</span><span class="sxs-lookup"><span data-stu-id="01a18-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="01a18-309">Jednak w tym temacie skupimy się na HTTP.</span><span class="sxs-lookup"><span data-stu-id="01a18-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="01a18-310">Format MTOM wykorzystuje duży zestaw specyfikacji obejmujących sam mtom, XOP i MIME.</span><span class="sxs-lookup"><span data-stu-id="01a18-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="01a18-311">Modułowość tego zestawu specyfikacji sprawia, że nieco trudno jest odtworzyć dokładne wymagania dotyczące formatu i przetwarzania semantyki.</span><span class="sxs-lookup"><span data-stu-id="01a18-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="01a18-312">W tej sekcji opisano wymagania dotyczące formatu i przetwarzania powiązania HTTP MTOM.</span><span class="sxs-lookup"><span data-stu-id="01a18-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="01a18-313">Kodowanie komunikatów MTOM</span><span class="sxs-lookup"><span data-stu-id="01a18-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="01a18-314">Generowanie komunikatów MTOM</span><span class="sxs-lookup"><span data-stu-id="01a18-314">Generating MTOM messages</span></span>
<span data-ttu-id="01a18-315">Sekcja [XOP] 3.1 opisuje proces kodowania XML z elementami informacji, które zawierają wartości base64 w abstrakcyjnie zdefiniowanym pakiecie XOP.</span><span class="sxs-lookup"><span data-stu-id="01a18-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="01a18-316">Następująca sekwencja kroków opisuje proces kodowania specyficznego dla MTOM:</span><span class="sxs-lookup"><span data-stu-id="01a18-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="01a18-317">Upewnij się, że koperta PROTOKOŁU SOAP, która `[namespace name]` ma `http://www.w3.org/2004/08/xop/include` być `[local name]` `Include`zakodowana, nie zawiera elementu informacyjnego o a i a .</span><span class="sxs-lookup"><span data-stu-id="01a18-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="01a18-318">Utwórz pusty pakiet MIME.</span><span class="sxs-lookup"><span data-stu-id="01a18-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="01a18-319">Identyfikować w oryginalnym zestawie informacji XML elementy informacji o elemencie, które mają być zoptymalizowane.</span><span class="sxs-lookup"><span data-stu-id="01a18-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="01a18-320">Aby elementy mają być zoptymalizowane, znaki, `[children]` które składają się na element informacji o `xs:base64Binary` elemencie musi być w formie kanonicznej (patrz XSD-2, 3.2.16 base64Binary) i nie może zawierać żadnych znaków odstępu poprzedzających, wbudowanych lub następujących po zawartości niebiału.</span><span class="sxs-lookup"><span data-stu-id="01a18-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="01a18-321">Utwórz kopertę XOP SOAP, która jest kopią oryginalnej koperty SOAP, ale z elementami podrzędnymi każdego elementu informacyjnego określonego w poprzednim kroku zastąpionym elementem informacji o elemencie `xop:Include` skonstruowanym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="01a18-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="01a18-322">Przekształć zastąpione znaki w dane binarne, przetwarzając je jako dane zakodowane w formacie base4.</span><span class="sxs-lookup"><span data-stu-id="01a18-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="01a18-323">Wygeneruj unikatową wartość nagłówka content-id, która spełnia wymagania R3133 i R3134.</span><span class="sxs-lookup"><span data-stu-id="01a18-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="01a18-324">Wygeneruj nagłówek MIME kodowania transferu zawartości z wartością binarną.</span><span class="sxs-lookup"><span data-stu-id="01a18-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="01a18-325">Jeśli element informacji o elemencie, który jest `xop:Include` optymalizujący `xmime:contentType` ([nadrzędny] nowo wstawionego elementu informacyjnego) `xmime:contentType` ma element informacji o atrybutach, wygeneruj nagłówek MIME typu zawartości z wartością atrybutu.</span><span class="sxs-lookup"><span data-stu-id="01a18-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="01a18-326">Wygeneruj nową binarną część MIME z zawartością utworzoną przez dane binarne zdekodowanych danych z zastąpionych znaków przetworzonych jako base64, nagłówek Content-ID z 4b, Nagłówek kodowania transferu zawartości z 4c, nagłówek typu zawartości, jeśli jest generowany w kroku 4d.</span><span class="sxs-lookup"><span data-stu-id="01a18-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="01a18-327">Dodaj `href` atrybut do `xop:Include` elementu o wartości cid: uri pochodzące z content-id wartość nagłówka generowane w kroku 4b.</span><span class="sxs-lookup"><span data-stu-id="01a18-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="01a18-328">Usuń otaczające\<znaki " " i ">", usuń adres URL z pozostałego ciągu i dodaj prefiks `cid:`.</span><span class="sxs-lookup"><span data-stu-id="01a18-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="01a18-329">Następujący minimalny zestaw znaków musi być zmieniony przez RFC1738 i RFC2396.</span><span class="sxs-lookup"><span data-stu-id="01a18-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="01a18-330">Inne znaki mogą być zmienione.</span><span class="sxs-lookup"><span data-stu-id="01a18-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="01a18-331">Utwórz główną część MIME za pomocą koperty XOP SOAP z kroku 4.</span><span class="sxs-lookup"><span data-stu-id="01a18-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="01a18-332">Napisz nagłówki HTTP, w tym nagłówek HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="01a18-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="01a18-333">Napisz pakiet MIME.</span><span class="sxs-lookup"><span data-stu-id="01a18-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="01a18-334">Przetwarzanie komunikatów MTOM</span><span class="sxs-lookup"><span data-stu-id="01a18-334">Processing MTOM messages</span></span>
<span data-ttu-id="01a18-335">Przetwarzanie wiadomości MTOM jest dokładnym odwrótem procesu opisanego w poprzedniej sekcji "Generowanie komunikatów MTOM":</span><span class="sxs-lookup"><span data-stu-id="01a18-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="01a18-336">Upewnij się, że główna część `application/xop+xml`MIME ma typ zawartości .</span><span class="sxs-lookup"><span data-stu-id="01a18-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="01a18-337">Skonstruuj kopertę protokołu SOAP, analizując główną część MIME pakietu jako dokument XML.</span><span class="sxs-lookup"><span data-stu-id="01a18-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="01a18-338">Kodowanie znaków jest `charset` określane przez parametr typu zawartości głównej części MIME.</span><span class="sxs-lookup"><span data-stu-id="01a18-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="01a18-339">Dla każdego elementu elementu informacji element w skonstruowanej puli danych SOAP, który ma, jako jedyny element członkowski jego [elementy podrzędne] właściwość, element informacji o elemencie: `xop:Include`</span><span class="sxs-lookup"><span data-stu-id="01a18-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="01a18-340">Usuń `cid:` prefiks i unescape wszystkie sekwencje URI-escape (RFC 2396) w wartości `@href` atrybutu `xop:Include` elementu.</span><span class="sxs-lookup"><span data-stu-id="01a18-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="01a18-341">Ciąg wynikowy należy\<ująć w " ", ">".</span><span class="sxs-lookup"><span data-stu-id="01a18-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="01a18-342">Zlokalizuj część MIME z wartością nagłówka Content-ID, która odpowiada ciągowi pochodnemu w kroku 3a.</span><span class="sxs-lookup"><span data-stu-id="01a18-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="01a18-343">Zastąp `xop:Include` element informacji `children` o elemencie, który pojawia się we właściwości każdego elementu, elementami informacji o znakach reprezentującymi kanoniczne kodowanie base64 (patrz XSD-2, 3.2.16 base64Binary) treści jednostki części MIME identyfikowanej w kroku 3b (skutecznie zastąp element informacji `xop:Include` o elemencie elementu danymi zrekonstruowanymi z części pakietu).</span><span class="sxs-lookup"><span data-stu-id="01a18-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="01a18-344">Nagłówek typu zawartości HTTP</span><span class="sxs-lookup"><span data-stu-id="01a18-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="01a18-345">Poniżej znajduje się lista wyjaśnień WCF dla formatu nagłówka http typu zawartości komunikatu zakodowanego przez protokół SOAP 1.x MTOM, pochodzących z wymagań określonych w samej specyfikacji MTOM i pochodzących z MTOM i RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="01a18-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="01a18-346">R4131: Nagłówek typu zawartości HTTP musi mieć wartość wieloczęściową/pokrewną (bez uwzględniania wielkości liter) i jego parametry.</span><span class="sxs-lookup"><span data-stu-id="01a18-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="01a18-347">Nazwy parametrów są niewrażliwe na wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="01a18-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="01a18-348">Kolejność parametrów nie jest znacząca.</span><span class="sxs-lookup"><span data-stu-id="01a18-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="01a18-349">Pełny formularz Backus-Naur (BNF) nagłówka typu zawartości dla wiadomości MIME jest wymieniony w RFC 2045, sekcja 5.1.</span><span class="sxs-lookup"><span data-stu-id="01a18-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="01a18-350">R4132: Nagłówek typu zawartości HTTP musi mieć parametr `application/xop+xml` typu o wartości ujętej w cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="01a18-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="01a18-351">Chociaż wymóg używania podwójnych cudzysłowów nie jest jawny w RFC 2387, tekst zauważa, że wszystkie\@parametry multiczęści/pokrewne typy nośników najprawdopodobniej zawierają znaki zastrzeżone, takie jak " " lub "/" i dlatego potrzebują podwójnych cudzysłowów.</span><span class="sxs-lookup"><span data-stu-id="01a18-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="01a18-352">R4133: Nagłówek typu zawartości HTTP powinien mieć parametr start z wartością nagłówka Content-ID części MIME zawierającej kopertę SOAP 1.x, ujętą w podwójne cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="01a18-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="01a18-353">Jeśli parametr start zostanie pominięty, pierwsza część MIME musi zawierać kopertę SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="01a18-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="01a18-354">R4134: Nagłówek typu zawartości HTTP dla wiadomości zakodowanej w formacie SOAP 1.1 MTOM musi zawierać parametr informacji początkowej o wartości text/xml, ujęty w podwójne cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="01a18-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="01a18-355">R4135: Nagłówek typu zawartości HTTP dla wiadomości zakodowanej w filtrze SOAP 1.2 MTOM `application/soap+xml`musi zawierać parametr informacji początkowej o wartości , ujętej w podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="01a18-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="01a18-356">R4136: Nagłówek typu zawartości HTTP dla wiadomości zakodowanej w technologii SOAP 1.x MTOM musi mieć parametr granicy z wartością (ujętą w cudzysłów), która odpowiada granicy MIME BNF zdefiniowanej w RFC 2046, sekcja 5.1.1</span><span class="sxs-lookup"><span data-stu-id="01a18-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="01a18-357">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="01a18-357">Examples:</span></span>

     <span data-ttu-id="01a18-358">Poprawne</span><span class="sxs-lookup"><span data-stu-id="01a18-358">CORRECT</span></span>

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="01a18-359">Poprawne</span><span class="sxs-lookup"><span data-stu-id="01a18-359">CORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="01a18-360">Niepoprawne</span><span class="sxs-lookup"><span data-stu-id="01a18-360">INCORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="01a18-361">Część programu Infoset MIME</span><span class="sxs-lookup"><span data-stu-id="01a18-361">Infoset MIME Part</span></span>
<span data-ttu-id="01a18-362">Koperta SOAP 1.x jest hermetyzowana jako główna część pakietu XOP `infoset` MIME i jest często nazywana częścią.</span><span class="sxs-lookup"><span data-stu-id="01a18-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="01a18-363">R4141: Koperta SOAP 1.x musi być hermetyzowana jako główna część `infoset` pakietu XOP MIME, nazywana częścią i odwołująca się od typu zawartości HTTP.</span><span class="sxs-lookup"><span data-stu-id="01a18-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="01a18-364">R4142: Część `Infoset` SOAP musi zawierać następujące nagłówki `Content-ID` `Content-Transfer-Encoding`MIME: , , i `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="01a18-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="01a18-365">Format nagłówka Content-ID jest zdefiniowany przez RFC 2045 jako</span><span class="sxs-lookup"><span data-stu-id="01a18-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="01a18-366">gdzie `msg-id` jest zdefiniowany w RFC 2822 (który zastępuje RFC 822, o których mowa w RFC 2045) jako:</span><span class="sxs-lookup"><span data-stu-id="01a18-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="01a18-367">i jest w rzeczywistości adresem\<e-mail zawartym w " " i ">".</span><span class="sxs-lookup"><span data-stu-id="01a18-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="01a18-368">Prefiks `[CFWS]` i sufiks zostały dodane w RFC 2822 do przenoszenia komentarzy i nie powinny być używane do zachowania interoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="01a18-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="01a18-369">R4143: Wartość nagłówka Content-ID dla części Infoset `msg-id` MIME musi być zgodna z `[CFWS]` produkcją z RFC 2822 z pominiętymi częściami prefiksu i sufiksu.</span><span class="sxs-lookup"><span data-stu-id="01a18-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="01a18-370">Wiele implementacji MIME złagodziło wymagania dotyczące\<wartości zawartej w " i ">" `absoluteURI` jako adresu\<e-mail i używanej w " , ">" oprócz adresu e-mail.</span><span class="sxs-lookup"><span data-stu-id="01a18-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="01a18-371">Ta wersja WCF używa wartości nagłówka MIME Content-ID formularza:</span><span class="sxs-lookup"><span data-stu-id="01a18-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="01a18-372">R4144: Procesory MTOM powinny akceptować wartości nagłówka `msg-id`Content-ID, które są zgodne z następującymi zrelaksowanymi .</span><span class="sxs-lookup"><span data-stu-id="01a18-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="01a18-373">MIME (RFC 2045) udostępnia nagłówek kodowania transferu zawartości do przekazywania kodowania zawartości części MIME.</span><span class="sxs-lookup"><span data-stu-id="01a18-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="01a18-374">Domyślnie zdefiniowany dla kodowania transferu zawartości jest 7-bitowy, co nie jest odpowiednie dla większości komunikatów PROTOKOŁU SOAP, więc nagłówek kodowania transferu zawartości jest potrzebny do większej współdziałania:</span><span class="sxs-lookup"><span data-stu-id="01a18-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="01a18-375">R4145: Część zestawu informacyjnego SOAP musi zawierać nagłówek kodowania transferu zawartości.</span><span class="sxs-lookup"><span data-stu-id="01a18-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="01a18-376">R4146: Jeśli kodowanie znaków koperty PROTOKOŁU SOAP to UTF-8, wartość nagłówka Kodowanie transferu zawartości musi być 8-bitowa.</span><span class="sxs-lookup"><span data-stu-id="01a18-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="01a18-377">R4147: Jeśli kodowanie znaków koperty PROTOKOŁU SOAP to UTF-16, wartość nagłówka Kodowanie transferu zawartości musi być binarna.</span><span class="sxs-lookup"><span data-stu-id="01a18-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="01a18-378">Zgodnie z sekcją 5 [XOP]</span><span class="sxs-lookup"><span data-stu-id="01a18-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="01a18-379">R4148: CZĘŚĆ zestawu informacyjnego SOAP1.1 musi zawierać nagłówek typ zawartości z aplikacją typu nośnika/xop+xml i parametrami type="text/xml" i charset</span><span class="sxs-lookup"><span data-stu-id="01a18-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="01a18-380">R4149: Część zestawu informacyjnego SOAP 1.2 musi zawierać `application/xop+xml` nagłówek Typ zawartości`application/soap+xml`z `charset`typem nośnika i parametrami type=" i .</span><span class="sxs-lookup"><span data-stu-id="01a18-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="01a18-381">Podczas XOP definiuje `charset` parametr, `application/xop+xml` aby być opcjonalne, jest on potrzebny do współdziałania podobne `charset` do `text/xml` wymagania BP 1.1 na parametr dla typu nośnika.</span><span class="sxs-lookup"><span data-stu-id="01a18-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="01a18-382">R41410: `type` Parametry `charset` i parametry muszą znajdować się w nagłówku typ zawartości części zestawu informacyjnego SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="01a18-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="01a18-383">Obsługa punktów końcowych WCF dla MTOM</span><span class="sxs-lookup"><span data-stu-id="01a18-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="01a18-384">Celem MTOM jest zakodowanie wiadomości SOAP w celu optymalizacji danych zakodowanych w bazie 64.</span><span class="sxs-lookup"><span data-stu-id="01a18-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="01a18-385">Poniżej znajduje się lista ograniczeń:</span><span class="sxs-lookup"><span data-stu-id="01a18-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="01a18-386">R4151: Każdy element informacji o elemencie zawierający dane zakodowane w bazie 64 mogą być zoptymalizowane.</span><span class="sxs-lookup"><span data-stu-id="01a18-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="01a18-387">B4152: WCF optymalizuje elementy informacji o elemencie, które zawierają dane zakodowane w bazie 64 i przekraczają 1024 bajty długości.</span><span class="sxs-lookup"><span data-stu-id="01a18-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="01a18-388">Punkt końcowy WCF skonfigurowany do używania MTOM zawsze będzie wysyłać wiadomości zakodowane w MTOM.</span><span class="sxs-lookup"><span data-stu-id="01a18-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="01a18-389">Nawet jeśli żadna część nie spełnia wymaganych kryteriów, wiadomość jest nadal zakodowana w MTOM (serializowana jako pakiet MIME z pojedynczą częścią MIME zawierającą otoczkę SOAP).</span><span class="sxs-lookup"><span data-stu-id="01a18-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="01a18-390">Twierdzenie zasad WS dla MTOM</span><span class="sxs-lookup"><span data-stu-id="01a18-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="01a18-391">WCF używa następującego potwierdzenia zasad, aby wskazać użycie MTOM według punktu końcowego:</span><span class="sxs-lookup"><span data-stu-id="01a18-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="01a18-392">R4211: Poprzednie twierdzenie zasad ma temat zasad punktu końcowego i określa, że wszystkie wiadomości wysyłane do punktu końcowego i odbierane z punktu końcowego muszą być zoptymalizowane przy użyciu programu MTOM.</span><span class="sxs-lookup"><span data-stu-id="01a18-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="01a18-393">B4212: Po skonfigurowaniu do używania optymalizacji MTOM punkt końcowy WCF dodaje twierdzenie zasad `wsdl:binding`MTOM do zasad dołączonych do odpowiedniego .</span><span class="sxs-lookup"><span data-stu-id="01a18-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="01a18-394">Kompozycja z WS-Security</span><span class="sxs-lookup"><span data-stu-id="01a18-394">Composition with WS-Security</span></span>
<span data-ttu-id="01a18-395">MTOM jest mechanizmem kodowania, `text/xml` który jest podobny do i WCF Binary XML.</span><span class="sxs-lookup"><span data-stu-id="01a18-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="01a18-396">MTOM oferuje naturalny skład z protokołami WS-Security i innymi protokołami WS-\*: komunikat zabezpieczony za pomocą WS-Security można zoptymalizować za pomocą programu MTOM.</span><span class="sxs-lookup"><span data-stu-id="01a18-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="01a18-397">Przykłady</span><span class="sxs-lookup"><span data-stu-id="01a18-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="01a18-398">WCF SOAP 1.1 Komunikat zakodowany przy użyciu MTOM</span><span class="sxs-lookup"><span data-stu-id="01a18-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="01a18-399">WCF Secure SOAP 1.2 Komunikat zakodowany za pomocą MTOM</span><span class="sxs-lookup"><span data-stu-id="01a18-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="01a18-400">W tym przykładzie komunikat jest kodowany przy użyciu MTOM i SOAP 1.2, który jest chroniony przy użyciu WS-Security.</span><span class="sxs-lookup"><span data-stu-id="01a18-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="01a18-401">Części binarne zidentyfikowane do kodowania `BinarySecurityToken`są `CipherValue` zawartością , odpowiadającej `EncryptedData` zaszyfrowanemu podpisowi i zaszyfrowanej treści.</span><span class="sxs-lookup"><span data-stu-id="01a18-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="01a18-402">Należy zauważyć, że `CipherValue` nie `EncryptedKey` został zidentyfikowany do optymalizacji przez WCF, ponieważ jego długość jest mniejsza niż 1024 bajtów.</span><span class="sxs-lookup"><span data-stu-id="01a18-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

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
