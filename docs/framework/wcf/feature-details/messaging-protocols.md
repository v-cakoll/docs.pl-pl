---
title: Protokoły obsługi komunikatów
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: d188c79d3879ef383d24f56c81d66973266636bc
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37072725"
---
# <a name="messaging-protocols"></a><span data-ttu-id="b2594-102">Protokoły obsługi komunikatów</span><span class="sxs-lookup"><span data-stu-id="b2594-102">Messaging Protocols</span></span>
<span data-ttu-id="b2594-103">Stos kanał Windows Communication Foundation (WCF) zostają kanały transportu i kodowanie do transformacji reprezentacji wewnętrznej komunikatu do jego format danych przesyłanych w sieci i wysłać go przy użyciu danego transportu.</span><span class="sxs-lookup"><span data-stu-id="b2594-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="b2594-104">Transport najczęściej używane na współdziałanie usług sieci Web, jest protokół HTTP i są najczęściej używane kodowanie, używane przez usługi sieci Web opartych na języku XML SOAP 1.1 i SOAP 1.2, mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b2594-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="b2594-105">W tym temacie omówiono szczegóły implementacji WCF dla następujących protokołów zatrudnieni przez <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b2594-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="b2594-106">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="b2594-106">Specification/document</span></span>|<span data-ttu-id="b2594-107">Łącze</span><span class="sxs-lookup"><span data-stu-id="b2594-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="b2594-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="b2594-108">HTTP 1.1</span></span>|http://www.ietf.org/rfc/rfc2616.txt|  
|<span data-ttu-id="b2594-109">SOAP 1.1 powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="b2594-109">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="b2594-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Sekcji 7</span><span class="sxs-lookup"><span data-stu-id="b2594-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="b2594-111">SOAP 1.2 powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="b2594-111">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="b2594-112">http://www.w3.org/TR/soap12-part2/, Sekcji 7</span><span class="sxs-lookup"><span data-stu-id="b2594-112">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="b2594-113">W tym temacie omówiono szczegóły implementacji WCF dla następujące protokoły <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> fragmentów.</span><span class="sxs-lookup"><span data-stu-id="b2594-113">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="b2594-114">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="b2594-114">Specification/Document</span></span>|<span data-ttu-id="b2594-115">Łącze</span><span class="sxs-lookup"><span data-stu-id="b2594-115">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="b2594-116">XML</span><span class="sxs-lookup"><span data-stu-id="b2594-116">XML</span></span>|http://www.w3.org/TR/REC-xml|  
|<span data-ttu-id="b2594-117">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="b2594-117">SOAP 1.1</span></span>|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|<span data-ttu-id="b2594-118">SOAP 1.2 Core</span><span class="sxs-lookup"><span data-stu-id="b2594-118">SOAP 1.2 Core</span></span>|http://www.w3.org/TR/soap12-part1/|  
|<span data-ttu-id="b2594-119">Protokół WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="b2594-119">WS-Addressing 2004/08</span></span>|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|<span data-ttu-id="b2594-120">Usługi sieci Web W3C adresowania 1.0 — podstawowe</span><span class="sxs-lookup"><span data-stu-id="b2594-120">W3C Web Services Addressing 1.0 - Core</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|<span data-ttu-id="b2594-121">Adresowania 1.0 — wiązanie protokołu SOAP usług sieci Web W3C</span><span class="sxs-lookup"><span data-stu-id="b2594-121">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|<span data-ttu-id="b2594-122">Usługi sieci Web W3C adresowania 1.0 — wiązanie WSDL</span><span class="sxs-lookup"><span data-stu-id="b2594-122">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
<span data-ttu-id="b2594-123">Usługi sieci Web W3C adresowania 1.0 - metadanych</span><span class="sxs-lookup"><span data-stu-id="b2594-123">W3C Web Services Addressing 1.0 - Metadata</span></span>|http://www.w3.org/TR/ws-addr-metadata/|  
|<span data-ttu-id="b2594-124">Powiązanie WSDL SOAP1.1</span><span class="sxs-lookup"><span data-stu-id="b2594-124">WSDL SOAP1.1 Binding</span></span>|http://www.w3.org/TR/wsdl/|  
|<span data-ttu-id="b2594-125">Powiązanie WSDL SOAP1.2</span><span class="sxs-lookup"><span data-stu-id="b2594-125">WSDL SOAP1.2 Binding</span></span>|http://www.w3.org/Submission/wsdl11soap12/|  
  
 <span data-ttu-id="b2594-126">W tym temacie omówiono szczegóły implementacji WCF dla następujące protokoły <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> wykorzystuje.</span><span class="sxs-lookup"><span data-stu-id="b2594-126">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="b2594-127">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="b2594-127">Specification/document</span></span>|<span data-ttu-id="b2594-128">Łącze</span><span class="sxs-lookup"><span data-stu-id="b2594-128">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="b2594-129">XOP</span><span class="sxs-lookup"><span data-stu-id="b2594-129">XOP</span></span>|http://www.w3.org/TR/xop10/|  
|<span data-ttu-id="b2594-130">MTOM + SOAP 1.2 powiązania</span><span class="sxs-lookup"><span data-stu-id="b2594-130">MTOM + SOAP 1.2 Binding</span></span>|http://www.w3.org/TR/soap12-mtom/|  
|<span data-ttu-id="b2594-131">MTOM SOAP 1.1 powiązania</span><span class="sxs-lookup"><span data-stu-id="b2594-131">MTOM SOAP 1.1 Binding</span></span>|http://www.w3.org/Submission/soap11mtom10/|  
|<span data-ttu-id="b2594-132">Potwierdzenie WS-Policy MTOM</span><span class="sxs-lookup"><span data-stu-id="b2594-132">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="b2594-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="b2594-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="b2594-134">Następujące obszary nazw XML i prefiksy skojarzone są używane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="b2594-134">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="b2594-135">Prefiks</span><span class="sxs-lookup"><span data-stu-id="b2594-135">Prefix</span></span>|<span data-ttu-id="b2594-136">Namespace Uniform Resource Identifier (URI)</span><span class="sxs-lookup"><span data-stu-id="b2594-136">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="b2594-137">s11</span><span class="sxs-lookup"><span data-stu-id="b2594-137">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="b2594-138">s12</span><span class="sxs-lookup"><span data-stu-id="b2594-138">s12</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="b2594-139">wsa</span><span class="sxs-lookup"><span data-stu-id="b2594-139">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="b2594-140">wsam</span><span class="sxs-lookup"><span data-stu-id="b2594-140">wsam</span></span>|http://www.w3.org/2007/05/addressing/metadata|  
|<span data-ttu-id="b2594-141">wsap</span><span class="sxs-lookup"><span data-stu-id="b2594-141">wsap</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|<span data-ttu-id="b2594-142">wsa10</span><span class="sxs-lookup"><span data-stu-id="b2594-142">wsa10</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="b2594-143">wsaw10</span><span class="sxs-lookup"><span data-stu-id="b2594-143">wsaw10</span></span>|http://www.w3.org/2006/05/addressing/wsdl|  
|<span data-ttu-id="b2594-144">Element XOP</span><span class="sxs-lookup"><span data-stu-id="b2594-144">xop</span></span>|http://www.w3.org/2004/08/xop/include|  
|<span data-ttu-id="b2594-145">xmime</span><span class="sxs-lookup"><span data-stu-id="b2594-145">xmime</span></span>|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
<span data-ttu-id="b2594-146">punkt dystrybucji</span><span class="sxs-lookup"><span data-stu-id="b2594-146">dp</span></span>|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="b2594-147">SOAP 1.1 i SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="b2594-147">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="b2594-148">Koperty i przetwarzania modelu</span><span class="sxs-lookup"><span data-stu-id="b2594-148">Envelope and Processing Model</span></span>  
 <span data-ttu-id="b2594-149">Usługi WCF implementuje przetwarzania koperty protokołu SOAP 1.1 Basic Profile 1.1 (BP11) i Basic Profile 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="b2594-149">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="b2594-150">SOAP 1.2 koperty przetwarzania jest zaimplementowana po SOAP12 — część 1.</span><span class="sxs-lookup"><span data-stu-id="b2594-150">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="b2594-151">W tej sekcji opisano niektóre opcje implementacji wykonywaną przez WCF BP11 i SOAP12 — część 1.</span><span class="sxs-lookup"><span data-stu-id="b2594-151">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="b2594-152">Wymagany nagłówek przetwarzania</span><span class="sxs-lookup"><span data-stu-id="b2594-152">Mandatory Header Processing</span></span>  
 <span data-ttu-id="b2594-153">WCF następuje reguł do przetwarzania nagłówków oznaczony `mustUnderstand` opisanego w specyfikacji SOAP 1.1 i SOAP 1.2, z następujących zmian.</span><span class="sxs-lookup"><span data-stu-id="b2594-153">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="b2594-154">Komunikat, który przechodzi stosu kanału WCF jest przetwarzany przez poszczególnych kanałów skonfigurowanych przez powiązanie skojarzone elementy, na przykład, kodowania wiadomości tekstowych, zabezpieczeń, niezawodna obsługa komunikatów i transakcji.</span><span class="sxs-lookup"><span data-stu-id="b2594-154">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="b2594-155">Każdy kanał rozpoznaje nagłówków z skojarzona przestrzeń nazw i oznacza je jako rozumiem.</span><span class="sxs-lookup"><span data-stu-id="b2594-155">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="b2594-156">W momencie komunikat wejścia dyspozytor, programu formatującego operacji odczytuje nagłówki oczekiwany przez odpowiednie kontraktu komunikatu na operację i znaczniki ich zrozumienie.</span><span class="sxs-lookup"><span data-stu-id="b2594-156">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="b2594-157">Następnie Dyspozytor sprawdza, czy wszystkie pozostałe nagłówki nie są rozumieć, ale oznaczenie `mustUnderstand` i zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b2594-157">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="b2594-158">Komunikaty, które zawierają `mustUnderstand` nagłówki, które są przeznaczone dla odbiorcy nie są przetwarzane przez kod aplikacji odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="b2594-158">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="b2594-159">Takie warstwie przetwarzania umożliwia rozdzielenie warstwy infrastruktury i aplikacji węzła SOAP:</span><span class="sxs-lookup"><span data-stu-id="b2594-159">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="b2594-160">B1111: Nagłówki, które nie są zrozumiałe są wykrywane po przetworzeniu komunikatu przez stos kanału WCF infrastruktury, ale przetworzenia przez aplikację</span><span class="sxs-lookup"><span data-stu-id="b2594-160">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="b2594-161">`mustUnderstand` Wartość nagłówka różni się między SOAP 1.1 i SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="b2594-161">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="b2594-162">Basic Profile 1.1 wymaga, aby `mustUnderstand` wartość wynosić 0 lub 1 dla wiadomości SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="b2594-162">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="b2594-163">SOAP 1.2 umożliwia 0, 1, `false`, i `true` jako wartości, ale zaleca emitowanie canonical reprezentację `xs:boolean` wartości (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="b2594-163">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="b2594-164">B1112: Emituje WCF `mustUnderstand` wartości 0 i 1 dla wersji zarówno SOAP 1.1 i SOAP 1.2 koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b2594-164">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="b2594-165">Usługi WCF akceptuje miejsce całą wartość `xs:boolean` dla `mustUnderstand` nagłówka (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="b2594-165">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="b2594-166">Błędach SOAP</span><span class="sxs-lookup"><span data-stu-id="b2594-166">SOAP Faults</span></span>  
 <span data-ttu-id="b2594-167">Poniżej znajduje się lista implementacje błędu SOAP specyficzne dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b2594-167">The following is a list of WCF-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="b2594-168">B2121: WCF zwraca następujące kody błędów protokołu SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, i `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="b2594-168">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="b2594-169">B2122: WCF zwraca następujące kody błędów protokołu SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, i `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="b2594-169">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="b2594-170">Wiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="b2594-170">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="b2594-171">SOAP 1.1 powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="b2594-171">SOAP 1.1 HTTP Binding</span></span>  
 <span data-ttu-id="b2594-172">Usługi WCF implementuje powiązanie SOAP1.1 HTTP po specyfikacji Basic Profile 1.1 sekcji 3.4 o wyjaśnienia następujące:</span><span class="sxs-lookup"><span data-stu-id="b2594-172">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="b2594-173">B2211: Usługi WCF nie implementuje przekierowania żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="b2594-173">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="b2594-174">B2212: WCF klientów obsługujących pliki cookie HTTP, zgodnie z 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="b2594-174">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="b2594-175">SOAP 1.2 powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="b2594-175">SOAP 1.2 HTTP Binding</span></span>  
 <span data-ttu-id="b2594-176">Usługi WCF implementuje powiązania SOAP 1.2 HTTP, zgodnie z opisem w SOAP 1.2, część 2 (SOAP12Part2) specyfikacji z następujących wyjaśnienia.</span><span class="sxs-lookup"><span data-stu-id="b2594-176">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="b2594-177">Parametr opcjonalny akcji dla wprowadzone SOAP 1.2 `application/soap+xml` typu nośnika.</span><span class="sxs-lookup"><span data-stu-id="b2594-177">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="b2594-178">Ten parametr jest przydatne w celu zoptymalizowania wysyłania wiadomości bez konieczności czy treść komunikatu protokołu SOAP można w sytuacji, gdy WS-Addressing nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="b2594-178">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="b2594-179">R2221: `application/soap+xml` parametr akcji, jeśli jest obecny w żądaniu SOAP 1.2, muszą być zgodne `soapAction` atrybutu `wsoap12:operation` elementu w odpowiednich Powiązanie WSDL.</span><span class="sxs-lookup"><span data-stu-id="b2594-179">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="b2594-180">R2222: `application/soap+xml` parametr akcji, jeśli jest obecny na wiadomości SOAP 1.2, muszą być zgodne `wsa:Action` stosowania WS-Addressing 2004/08 lub 1.0 WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b2594-180">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="b2594-181">Gdy WS-Addressing jest wyłączona, a żądanie przychodzące nie zawiera parametr akcji, wiadomości `Action` jest traktowany jako okres bez określonej.</span><span class="sxs-lookup"><span data-stu-id="b2594-181">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="b2594-182">Protokół WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="b2594-182">WS-Addressing</span></span>  
 <span data-ttu-id="b2594-183">Usługi WCF implementuje 3 wersji WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="b2594-183">WCF implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="b2594-184">Protokół WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="b2594-184">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="b2594-185">W3C usług sieci Web adresowanie SOAP powiązania (ADDR10 SOAP) i 1.0 Core (ADDR10 RDZENI)</span><span class="sxs-lookup"><span data-stu-id="b2594-185">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="b2594-186">Protokół WS-Addressing 1.0 - metadanych</span><span class="sxs-lookup"><span data-stu-id="b2594-186">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="b2594-187">Odwołania do punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="b2594-187">Endpoint References</span></span>  
 <span data-ttu-id="b2594-188">Wszystkie wersje WS-Addressing, który implementuje WCF używać odwołań do punktu końcowego do opisywania punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="b2594-188">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="b2594-189">Odwołania do punktu końcowego i wersji WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="b2594-189">Endpoint References and WS-Addressing Versions</span></span>  
 <span data-ttu-id="b2594-190">Usługi WCF implementuje wiele protokołów infrastruktury, które używają protokołu WS-Addressing, w szczególności `EndpointReference` elementu i `W3C.WsAddressing.EndpointReferenceType` klasy (na przykład WS-ReliableMessaging, WS-SecureConversation i WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="b2594-190">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="b2594-191">Usługi WCF obsługuje korzystanie z danej wersji WS-Addressing z innymi protokołami infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="b2594-191">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="b2594-192">Punkty końcowe WCF obsługuje jedną wersję WS-Addressing na punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="b2594-192">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="b2594-193">Dla R3111, w obszarze nazw `EndpointReference` elementu lub typ używany w wiadomościach z punktu końcowego WCF musi odpowiadać wersji WS-Addressing implementowanych przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="b2594-193">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="b2594-194">Na przykład, jeśli punktu końcowego WCF implementuje usługi WS-ReliableMessaging `AcksTo` zwrócony przez punkt końcowy, wewnątrz nagłówka `CreateSequenceResponse` korzysta z wersji WS-Addressing który `EncodingBinding` określa element dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b2594-194">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="b2594-195">Odwołania do punktu końcowego i metadane</span><span class="sxs-lookup"><span data-stu-id="b2594-195">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="b2594-196">Liczba scenariuszy wymagają komunikacji metadanych lub odwołanie do metadanych dla danego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b2594-196">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="b2594-197">B3121: WCF wykorzystuje mechanizm opisane w sekcji 6, aby uwzględnić metadanych dla odwołania do punktu końcowego według wartości lub według odwołania specyfikacji WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="b2594-197">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="b2594-198">Rozważmy scenariusz, w którym usługa WCF wymaga uwierzytelniania za pomocą tokenu zabezpieczeń potwierdzenia Markup Language (SAML) wydanego przez emitenta tokenu w http://sts.fabrikam123.com.</span><span class="sxs-lookup"><span data-stu-id="b2594-198">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com.</span></span> <span data-ttu-id="b2594-199">Punkt końcowy usługi WCF w tym artykule opisano to wymaganie uwierzytelniania przy użyciu `sp:IssuedToken` asercja z zagnieżdżoną `sp:Issuer` wskazujący emitenta tokenu potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="b2594-199">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="b2594-200">Aplikacje klienckie, które uzyskują dostęp do `sp:Issuer` potwierdzenia trzeba znać sposób komunikacji z punktem końcowym wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="b2594-200">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="b2594-201">Klient musi wiedzieć, metadane dotyczące wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="b2594-201">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="b2594-202">Korzystanie z rozszerzeń metadanych odwołania punktu końcowego zdefiniowana w punkcie końcowym MEX, WCF zawiera odwołanie do metadanych wystawca tokenów.</span><span class="sxs-lookup"><span data-stu-id="b2594-202">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>  
  
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
  
### <a name="message-addressing-headers"></a><span data-ttu-id="b2594-203">Adresowanie nagłówki komunikatów</span><span class="sxs-lookup"><span data-stu-id="b2594-203">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="b2594-204">Nagłówki komunikatów</span><span class="sxs-lookup"><span data-stu-id="b2594-204">Message Headers</span></span>  
 <span data-ttu-id="b2594-205">W przypadku obu wersji WS-Addressing WCF używa następujące nagłówki komunikatów według specyfikacji `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, i `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="b2594-205">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="b2594-206">B3211: Dla wszystkich wersji WS-Addressing WCF honoruje, ale nie tworzy fabrycznej nagłówków wiadomości WS-Addressing `wsa:FaultTo` i `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="b2594-206">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="b2594-207">Aplikacje wchodzące w interakcje z aplikacjami WCF można dodać te nagłówki komunikatów i WCF przetworzy je odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b2594-207">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="b2594-208">Odwołanie do parametrów i właściwości</span><span class="sxs-lookup"><span data-stu-id="b2594-208">Reference Parameters and Properties</span></span>  
 <span data-ttu-id="b2594-209">Przetwarzanie parametry odwołanie do punktu końcowego i odwołanie p implementuje WCF</span><span class="sxs-lookup"><span data-stu-id="b2594-209">WCF implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="b2594-210">właściwości zgodnie z odpowiednimi wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="b2594-210">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="b2594-211">B3221: Gdy skonfigurowany do używania protokołu WS-Addressing 2004/08, punkty końcowe WCF nie odróżnić przetwarzania właściwości odwołania i parametrów odwołania.</span><span class="sxs-lookup"><span data-stu-id="b2594-211">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="b2594-212">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="b2594-212">Message Exchange Patterns</span></span>  
 <span data-ttu-id="b2594-213">Sekwencja komunikatów związane z wywołania operacji usługi sieci Web nazywa się *wymiany komunikatów*.</span><span class="sxs-lookup"><span data-stu-id="b2594-213">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="b2594-214">Obsługuje WCF jednokierunkowe, żądanie odpowiedź i dupleksu wiadomości wymiany wzorce.</span><span class="sxs-lookup"><span data-stu-id="b2594-214">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="b2594-215">W tej sekcji wyjaśnia WS-Addressing wymagania dotyczące przetwarzania w zależności od wymiany komunikatów używany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b2594-215">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="b2594-216">W tej sekcji żądający wysyła pierwszy komunikat i obiekt odpowiadający odbiera pierwszego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b2594-216">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="b2594-217">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="b2594-217">One-Way Message</span></span>  
 <span data-ttu-id="b2594-218">Gdy punkt końcowy usługi WCF jest skonfigurowany do obsługi komunikatów z danego `Action` wykonać jednokierunkowe wzorzec, punktu końcowego WCF wykonuje następujące zachowania i wymagania.</span><span class="sxs-lookup"><span data-stu-id="b2594-218">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="b2594-219">Inaczej, zachowania i zasady są stosowane dla obu wersji WS-Addressing obsługiwane w programie WCF:</span><span class="sxs-lookup"><span data-stu-id="b2594-219">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="b2594-220">R3311: Żądający musi zawierać `wsa:To`, `wsa:Action`, a nagłówki dla wszystkich parametrów odwołanie określone przez odwołanie do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b2594-220">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="b2594-221">Po jest używany protokół WS-Addressing 2004/08 i [właściwości odwołania] są określone przez odwołanie do punktu końcowego odpowiednie nagłówki musi zostać dodany do komunikatu za.</span><span class="sxs-lookup"><span data-stu-id="b2594-221">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="b2594-222">B3312: Żądający może obejmować `MessageID`, `ReplyTo`, i `FaultTo` nagłówków.</span><span class="sxs-lookup"><span data-stu-id="b2594-222">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="b2594-223">Infrastruktura odbiornik, zostaną one zignorowane, a zostaną przekazane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2594-223">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="b2594-224">R3313: Gdy HTTP jest używany, a żaden komunikat jest wysyłany na etap odpowiedzi HTTP, odpowiadający musi wysłać odpowiedź HTTP z pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="b2594-224">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="b2594-225">Podczas transportu HTTP jest w użyciu i kontrakt operacji deklaruje komunikatu jednokierunkowego, odpowiedź HTTP nadal może być używany do wysyłania wiadomości infrastruktury — na przykład wysłać niezawodna obsługa komunikatów `SequenceAcknowledgement` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2594-225">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="b2594-226">B3314: W odpowiedzi na komunikat jednokierunkowy obiektu odpowiadającego w trybie usługi WCF nie wysyła komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="b2594-226">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="b2594-227">Żądanie i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="b2594-227">Request-Reply</span></span>  
 <span data-ttu-id="b2594-228">Gdy punkt końcowy usługi WCF jest skonfigurowany dla komunikatów z danego `Action` postępuj zgodnie ze wzorcem żądanie odpowiedź, punktu końcowego WCF następuje zachowania i poniższe wymagania.</span><span class="sxs-lookup"><span data-stu-id="b2594-228">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="b2594-229">Chyba że określono inaczej, zachowania i zasady są stosowane dla obu wersji WS-Addressing obsługiwane w programie WCF:</span><span class="sxs-lookup"><span data-stu-id="b2594-229">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="b2594-230">R3321: W żądaniu musi zawierać żądający `wsa:To`, `wsa:Action`, `wsa:MessageID`, a nagłówki dla wszystkich parametrów odwołania odwołania (i właściwości) określone przez odwołanie do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b2594-230">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="b2594-231">R3322: W przypadku protokołu WS-Addressing 2004/08 `ReplyTo` muszą także być ujęte w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="b2594-231">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="b2594-232">R3323: Gdy jest używany protokół WS-Addressing 1.0 i `ReplyTo` nie jest obecne w żądaniu odwołanie do punktu końcowego domyślnej z właściwością [address] równa "http://www.w3.org/2005/08/addressing/anonymous" jest używany.</span><span class="sxs-lookup"><span data-stu-id="b2594-232">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="b2594-233">R3324: Żądający musi zawierać `wsa:To`, `wsa:Action`, i `wsa:RelatesTo` nagłówków komunikatu odpowiedzi, a także nagłówki dla wszystkich parametrów odwołania odwołania (i właściwości) określone przez `ReplyTo` w odwołaniu do punktu końcowego żądanie.</span><span class="sxs-lookup"><span data-stu-id="b2594-233">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="b2594-234">Usługi sieci Web adresowanie błędów</span><span class="sxs-lookup"><span data-stu-id="b2594-234">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="b2594-235">R3411: WCF tworzy następujące błędy, zdefiniowane przez protokół WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="b2594-235">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="b2594-236">Kod</span><span class="sxs-lookup"><span data-stu-id="b2594-236">Code</span></span>|<span data-ttu-id="b2594-237">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="b2594-237">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="b2594-238">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="b2594-238">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="b2594-239">Odebrano komunikat z `ReplyTo` innego niż adres dla tego kanału; nie istnieje brak nasłuchującego pod adresem określonym w nagłówku do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b2594-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="b2594-240">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="b2594-240">wsa:ActionNotSupported</span></span>|<span data-ttu-id="b2594-241">kanały infrastruktury lub skojarzone z punktem końcowym Dyspozytor nie rozpoznają z akcją określoną w `Action` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="b2594-241">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="b2594-242">R3412: WCF tworzy następujące błędy, zdefiniowane przez protokół WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="b2594-242">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="b2594-243">Kod</span><span class="sxs-lookup"><span data-stu-id="b2594-243">Code</span></span>|<span data-ttu-id="b2594-244">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="b2594-244">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="b2594-245">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="b2594-245">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="b2594-246">Zduplikowana `wsa:To`, `wsa:ReplyTo`, `wsa:From` lub `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="b2594-246">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="b2594-247">Zduplikowana `wsa:RelatesTo` o takiej samej `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="b2594-247">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="b2594-248">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="b2594-248">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="b2594-249">Brak wymaganego nagłówka adresowanie.</span><span class="sxs-lookup"><span data-stu-id="b2594-249">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="b2594-250">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="b2594-250">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="b2594-251">Odebrano komunikat z `ReplyTo` innego niż adres dla tego kanału.</span><span class="sxs-lookup"><span data-stu-id="b2594-251">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="b2594-252">Brak nasłuchującego pod adresem określonym w nagłówku do punktu końcowego nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="b2594-252">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="b2594-253">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="b2594-253">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="b2594-254">Action określony w `Action` nagłówka nie jest rozpoznawane przez infrastrukturę kanały lub dyspozytora skojarzonej z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="b2594-254">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="b2594-255">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="b2594-255">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="b2594-256">Kanał RM wysyła ten błąd, wskazujący punkt końcowy nie będzie przetwarzał sekwencji oparte na badanie `CreateSequence` nagłówków adresowych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b2594-256">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="b2594-257">Kod w poprzednich tabelach mapuje `FaultCode` w SOAP 1.1 i `SubCode` (z kodem = nadawca) w SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="b2594-257">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="b2594-258">WSDL 1.1 wiązania i protokołu WS-Policy potwierdzeń</span><span class="sxs-lookup"><span data-stu-id="b2594-258">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="b2594-259">Używanie protokołu WS-Addressing wskazujący</span><span class="sxs-lookup"><span data-stu-id="b2594-259">Indicating Use of WS-Addressing</span></span>  
 <span data-ttu-id="b2594-260">Usługi WCF używa potwierdzenia zasad w celu wskazania obsługi punktu końcowego dla określonej wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b2594-260">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="b2594-261">Następujące potwierdzenia zasad ma punkt końcowy zasad podmiotu [WS-PA] i wskazuje, że komunikaty wysyłane i odbierane z punktem końcowym muszą używać protokołu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="b2594-261">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="b2594-262">Potwierdzenie zasad wspomaga specyfikacji WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="b2594-262">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="b2594-263">Następujące potwierdzenia zasad, oznacza to, że komunikaty który wysłać/odebrać musi używać protokołu WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="b2594-263">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="b2594-264">Następujące potwierdzenia zasad ma punkt końcowy podmiotu zasad [WS-PA] i wskazuje, że komunikaty wysyłane i odbierane z punktu końcowego musi używać protokołu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="b2594-264">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="b2594-265">`wsaw10:UsingAddressing` Element jest pobierają z [WS-Addressing-WSDL] i jest używany w ramach usługi WS-Policy zgodnie z tym specyfikacją, sekcja 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="b2594-265">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="b2594-266">Użyj adresowanie nie zmienia semantykę wersji 1.1 języka WSDL SOAP 1.1 i SOAP 1.2 HTTP powiązania.</span><span class="sxs-lookup"><span data-stu-id="b2594-266">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="b2594-267">Na przykład jeśli odpowiedź ma żądanie, które są wysyłane do punktu końcowego, który używa powiązanie HTTP 1.x adresowanie i WSDL SOAP, odpowiedź należy wysłać przy użyciu odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2594-267">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="b2594-268">Odpowiedzi na wysłane za pośrednictwem odpowiedzi http WS-AM potwierdzenia jest:</span><span class="sxs-lookup"><span data-stu-id="b2594-268">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="b2594-269">Potwierdzenie pełną zasad może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="b2594-269">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="b2594-270">Istnieją jednak wzorce wymiany wiadomości, korzystających z o dwa połączenia HTTP niezależne odwrotnej między obiektu żądającego i odpowiadający, na przykład na niechciane komunikaty jednokierunkowe wysyłane przez odpowiadający.</span><span class="sxs-lookup"><span data-stu-id="b2594-270">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 <span data-ttu-id="b2594-271">Usługi WCF oferuje funkcję za pomocą którego dwa kanały transportu źródłowego utworzenia złożonego dupleksu kanału, gdzie jeden kanał służy do wprowadzania wiadomości, a drugi służy do komunikaty wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b2594-271">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="b2594-272">W przypadku transportu HTTP złożonego dupleksu zawiera dwa połączenia HTTP odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="b2594-272">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="b2594-273">Żądający używa jednego połączenia do wysyłania komunikatów do udzielenia i udzielenia używa innych wysyłania wiadomości z powrotem do strony żądającej.</span><span class="sxs-lookup"><span data-stu-id="b2594-273">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="b2594-274">Odpowiedzi na wysłane za pośrednictwem żądania http oddzielne jest potwierdzenie ws am</span><span class="sxs-lookup"><span data-stu-id="b2594-274">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="b2594-275">Potwierdzenie pełną zasad może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="b2594-275">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="b2594-276">Użyj następujących potwierdzenia o temacie zasady punktu końcowego [WS-PA] dla punktów końcowych używających powiązania HTTP 1.x WSDL 1.1 SOAP wymaga dwóch oddzielnych odwrotnej połączeń HTTP używanego do wiadomości przesyłane od osoby żądającej do obiektu odpowiadającego w trybie i obiekt odpowiadający w trybie żądającej, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b2594-276">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="b2594-277">Poprzednia prowadzi do następujących wymagań dotyczących `wsa:ReplyTo` nagłówek dla wiadomości żądania:</span><span class="sxs-lookup"><span data-stu-id="b2594-277">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="b2594-278">R3514: Żądanie wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwość nie jest równa "http://www.w3.org/2005/08/addressing/anonymous" Jeśli punkt końcowy używa 1.x HTTP powiązania WSDL 1.1 SOAP i ma stanowi alternatywę zasad z `wsap10:UsingAddressing` lub `wsap:UsingAddressing` Potwierdzenie połączone z `cdp:CompositeDuplex` dołączony.</span><span class="sxs-lookup"><span data-stu-id="b2594-278">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="b2594-279">R3515: Żądanie wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwości jest równa "http://www.w3.org/2005/08/addressing/anonymous", lub nie ma `ReplyTo` nagłówka gwarancja, jeśli punkt końcowy używa 1.x HTTP powiązania WSDL 1.1 SOAP i ma alternatywna zasad z `wsap10:UsingAddressing` potwierdzenia i nie `cdp:CompositeDuplex` potwierdzenia dołączony.</span><span class="sxs-lookup"><span data-stu-id="b2594-279">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="b2594-280">R3516: Żądania wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwości jest równa "http://www.w3.org/2005/08/addressing/anonymous" Jeśli punkt końcowy używa 1.x HTTP powiązania WSDL 1.1 SOAP i ma stanowi alternatywę zasad z `wsap:UsingAddressing` Potwierdzanie i nie `cdp:CompositeDuplex`potwierdzenia dołączony.</span><span class="sxs-lookup"><span data-stu-id="b2594-280">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="b2594-281">Specyfikacja WS-addressing WSDL próbuje opisano podobnymi powiązaniami protokołu, wprowadzając element `<wsaw:Anonymous/>` z trzech wartości tekstowej (wymagane, opcjonalne i zabronionych) wskazująca wymagania na `wsa:ReplyTo` nagłówka (sekcji 3.2).</span><span class="sxs-lookup"><span data-stu-id="b2594-281">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="b2594-282">Niestety taka definicja elementu nie jest szczególnie użyteczne jako potwierdzenia w ramach usługi WS-Policy, ponieważ wymaga rozszerzenia specyficznego dla domeny do obsługi przecięcie alternatyw za pomocą takiego elementu jako potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="b2594-282">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="b2594-283">Wartość wskazuje także takie definicji elementu `ReplyTo` nagłówka, w przeciwieństwie do zachowania punktu końcowego przesyłania, dzięki czemu określonego transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2594-283">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="b2594-284">Definicja akcji</span><span class="sxs-lookup"><span data-stu-id="b2594-284">Action Definition</span></span>  
 <span data-ttu-id="b2594-285">Definiuje WS-Addressing 2004/08 `wsa:Action` atrybutu dla `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementów.</span><span class="sxs-lookup"><span data-stu-id="b2594-285">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="b2594-286">WS-Addressing powiązania WSDL 1.0 (WS-ADDR10 WSDL) definiuje atrybut podobne `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="b2594-286">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="b2594-287">Jedyną różnicą między tymi dwoma jest opisanych w 3.3.2 WS-ADDR i sekcji 4.4.4 WS-ADDR10-WSDL, odpowiednio semantykę wzorzec domyślnej akcji.</span><span class="sxs-lookup"><span data-stu-id="b2594-287">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="b2594-288">Jest uzasadnione ma dwa punkty końcowe, które mają taki sam `portType` (lub kontraktu w terminologii usługi WCF), ale przy użyciu różnych wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b2594-288">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="b2594-289">Ale biorąc pod uwagę, że akcja jest definiowana za pomocą `portType` i nie należy zmieniać w obrębie punktów końcowych, które implementują `portType`, staje się niemożliwe do obsługi oba wzorce akcji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="b2594-289">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="b2594-290">Aby rozwiązać ten rozbieżność, WCF obsługuje jednej wersji `Action` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b2594-290">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="b2594-291">B3521: Używa WCF `wsaw10:Action` atrybutu `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy zgodnie z definicją w WS ADDR10 WSDL ustalenie `Action` identyfikator URI dla odpowiednich komunikatów niezależnie od wersji WS-Addressing używany przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="b2594-291">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="b2594-292">Punkt końcowy odwołanie wewnątrz WSDL portów</span><span class="sxs-lookup"><span data-stu-id="b2594-292">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="b2594-293">Rozszerza WS ADDR10 WSDL sekcji 4.1 `wsdl:port` element, aby uwzględnić `<wsa10:EndpointReference…/>` elementu podrzędnego do opisywania punktu końcowego usługi WS-Addressing warunków.</span><span class="sxs-lookup"><span data-stu-id="b2594-293">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="b2594-294">WCF rozszerza tego narzędzia na WS-Addressing 2004/08, dzięki czemu `<wsa:EndpointReference…/>` były wyświetlane jako elementu podrzędnego `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="b2594-294">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="b2594-295">R3531: Jeśli punkt końcowy ma zamiast dołączonych zasad z `<wsaw10:UsingAddressing/>` potwierdzenia zasad, odpowiadającego `wsdl:port` element może zawierać elementu podrzędnego `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="b2594-295">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="b2594-296">R3532: Jeśli `wsdl:port` zawiera element podrzędny `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` wartość elementu podrzędnego musi być zgodna z wartością `@address` atrybutu elementu równorzędnego `wsdl:port` / `wsdl:location` elementu.</span><span class="sxs-lookup"><span data-stu-id="b2594-296">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="b2594-297">R3533: Jeśli punkt końcowy ma zamiast dołączonych zasad z `<wsap:UsingAddressing/>` potwierdzenia zasad, odpowiadającego `wsdl:port` element może zawierać elementu podrzędnego `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="b2594-297">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="b2594-298">R3534: Jeśli `wsdl:port` zawiera element podrzędny `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` wartość elementu podrzędnego musi być zgodna z wartością `@address` atrybutu elementu równorzędnego `wsdl:port` / `wsdl:location` elementu.</span><span class="sxs-lookup"><span data-stu-id="b2594-298">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="b2594-299">Kompozycja z zabezpieczenia WS</span><span class="sxs-lookup"><span data-stu-id="b2594-299">Composition with WS-Security</span></span>  
 <span data-ttu-id="b2594-300">Zgodnie z zabezpieczeń sekcje brany pod uwagę WS-ADDR i WS-ADDR10 zaleca się wszystkie nagłówki komunikatów adresowania podpisywane wraz z treści wiadomości powiązać je razem.</span><span class="sxs-lookup"><span data-stu-id="b2594-300">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="b2594-301">Gdy WS-Security jest używany na potrzeby ochrony integralności komunikatu, WS-Addressing wiadomości nagłówków, a także nagłówki wynika z parametrów odwołania (i właściwości) muszą być podpisane wraz z treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b2594-301">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b2594-302">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b2594-302">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="b2594-303">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="b2594-303">One-Way Message</span></span>  
 <span data-ttu-id="b2594-304">W tym scenariuszu nadawca wysyła komunikat jednokierunkowy do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="b2594-304">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="b2594-305">Są używane SOAP 1.2, protokołu HTTP 1.1 i 1.0 W3C WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b2594-305">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="b2594-306">Struktura komunikatu żądania: Nagłówki komunikatów obejmują `wsa10:To` i `wsa10:Action` elementy.</span><span class="sxs-lookup"><span data-stu-id="b2594-306">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="b2594-307">Treść wiadomości zawiera określony `<app:Ping>` element z przestrzeni nazw aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2594-307">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="b2594-308">Nagłówki HTTP: Odpowiada docelowego w POST identyfikator URI w `wsa10:To` elementu.</span><span class="sxs-lookup"><span data-stu-id="b2594-308">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="b2594-309">Nagłówek Content-Type ma wartość `application/soap+xml` zgodnie z żądaniem protokołu SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="b2594-309">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="b2594-310">Parametry `charset` i `action` są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="b2594-310">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="b2594-311">`action` Parametr nagłówka Content-Type jest zgodna z wartością elementu `wsa10:Action` nagłówka wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b2594-311">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
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
  
 <span data-ttu-id="b2594-312">Odbiornik odpowiada pustą odpowiedź HTTP i stan 202.</span><span class="sxs-lookup"><span data-stu-id="b2594-312">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="b2594-313">Przykład odpowiedzi HTTP:</span><span class="sxs-lookup"><span data-stu-id="b2594-313">An example of the HTTP response:</span></span>  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="b2594-314">Mechanizmu optymalizacji transmisji wiadomości SOAP</span><span class="sxs-lookup"><span data-stu-id="b2594-314">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="b2594-315">W tej sekcji opisano szczegóły implementacji WCF dla MTOM SOAP protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2594-315">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="b2594-316">Technologia MTOM jest mechanizm kodowania wiadomości SOAP do tej samej klasy jako kodowania tradycyjnych tekstu/XML lub kodowanie binarne WCF.</span><span class="sxs-lookup"><span data-stu-id="b2594-316">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="b2594-317">MTOM obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="b2594-317">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="b2594-318">Kodowanie XML i mechanizmu pakowania opisanego przez [XOP] który optymalizuje elementów informacji XML zawierający dane binarne algorytmem base64 na oddzielnych części binarnej.</span><span class="sxs-lookup"><span data-stu-id="b2594-318">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="b2594-319">Hermetyzacja protokołu MIME pakietu XOP, który serializuje XML typu infoset sprawdzonych i każdej części binarnej pakietu XOP w oddzielnych części MIME.</span><span class="sxs-lookup"><span data-stu-id="b2594-319">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="b2594-320">MIME XOP kodowanie stosowane do SOAP 1.x koperty.</span><span class="sxs-lookup"><span data-stu-id="b2594-320">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="b2594-321">HTTP powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="b2594-321">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="b2594-322">Istnieje możliwość MTOM za pomocą transportu innego niż HTTP z programem WCF.</span><span class="sxs-lookup"><span data-stu-id="b2594-322">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="b2594-323">Jednak w tym temacie firma Microsoft koncentruje się na HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2594-323">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="b2594-324">MTOM format wykorzystuje dużego zestawu specyfikacji obejmujące MTOM samego, XOP i MIME.</span><span class="sxs-lookup"><span data-stu-id="b2594-324">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="b2594-325">Modułowość tego zestawu specyfikacji utrudnia nieco rekonstrukcji dokładnych wymaganiach na format i przetwarzania semantyki.</span><span class="sxs-lookup"><span data-stu-id="b2594-325">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="b2594-326">W tej sekcji opisano wymagania formatu i przetwarzania dla wiązania MTOM HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2594-326">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="b2594-327">Kodowanie komunikatu MTOM</span><span class="sxs-lookup"><span data-stu-id="b2594-327">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="b2594-328">Komunikaty mechanizmu MTOM generowania</span><span class="sxs-lookup"><span data-stu-id="b2594-328">Generating MTOM messages</span></span>  
 <span data-ttu-id="b2594-329">[XOP] 3.1 sekcji opisano proces kodowania XML z elementu informacji elementów, które zawierają wartości base64 w zdefiniowanych abstrakcyjnie pakiet XOP.</span><span class="sxs-lookup"><span data-stu-id="b2594-329">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="b2594-330">Następująca sekwencja kroków opisano proces kodowania MTOM specyficzne:</span><span class="sxs-lookup"><span data-stu-id="b2594-330">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="b2594-331">Sprawdź, czy koperty protokołu SOAP ma być zdekodowany, zawiera żadnego elementu elementu informacji z `[namespace name]` z "http://www.w3.org/2004/08/xop/include" i `[local name]` z `Include`.</span><span class="sxs-lookup"><span data-stu-id="b2594-331">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="b2594-332">Utwórz pusty pakiet MIME.</span><span class="sxs-lookup"><span data-stu-id="b2594-332">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="b2594-333">Zidentyfikuj w oryginalnym XML typu infoset sprawdzonych elementów informacji elementu Optymalizacja.</span><span class="sxs-lookup"><span data-stu-id="b2594-333">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="b2594-334">Dla elementów Optymalizacja znaki które tworzą `[children]` informacje o elementach elementu musi być w formie kanonicznej `xs:base64Binary` (zobacz XSD-2, 3.2.16 base64Binary) i nie może zawierać białych znaków poprzedzających wbudowany, lub po zawartości odstępem.</span><span class="sxs-lookup"><span data-stu-id="b2594-334">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any whitespace characters preceding, inline with, or following the non-whitespace content.</span></span>  
  
4.  <span data-ttu-id="b2594-335">Utwórz XOP koperty protokołu SOAP, który jest kopią oryginalnego koperty protokołu SOAP, ale z elementów informacje o poszczególnych elementach podrzędnych elementu w poprzednim kroku zastępuje `xop:Include` elementu informacji elementu następującą postać:</span><span class="sxs-lookup"><span data-stu-id="b2594-335">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="b2594-336">Przekształć zastąpionego znaków w danych binarnych przez przetwarzanie je jako dane zakodowane w formacie base64.</span><span class="sxs-lookup"><span data-stu-id="b2594-336">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="b2594-337">Generuj unikatowy wartość nagłówka Content-ID, który spełnia wymagania R3133 i R3134.</span><span class="sxs-lookup"><span data-stu-id="b2594-337">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="b2594-338">Wygeneruj nagłówek MIME Content-Transfer-Encoding o wartości binarnej.</span><span class="sxs-lookup"><span data-stu-id="b2594-338">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="b2594-339">Jeśli element elementu informacje są optymalizowane ([nadrzędny] nowo wstawionej `xop:Include` elementu informacji element) ma `xmime:contentType` atrybutu elementu informacji, wygeneruj nagłówek MIME Content-Type o wartości `xmime:contentType` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b2594-339">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="b2594-340">Generowanie nowej części MIME binarnego z zawartością utworzone przez dane binarne odczytany z zastąpionego znaki przetwarzane jako base64, nagłówek Content-ID z 4b, nagłówek Content-Transfer-Encoding z 4c nagłówka Content-Type, jeśli generowany w kroku 4d.</span><span class="sxs-lookup"><span data-stu-id="b2594-340">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="b2594-341">Dodaj `href` atrybutu `xop:Include` elementu o wartości cid: identyfikator uri pochodzące z wartość nagłówka Content-ID wygenerowany w kroku 4b.</span><span class="sxs-lookup"><span data-stu-id="b2594-341">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="b2594-342">Usuń otaczający "\<" i ">" znaki ucieczki adresu URL pozostałe ciąg i Dodaj prefiks `cid:`.</span><span class="sxs-lookup"><span data-stu-id="b2594-342">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="b2594-343">Następujący zestaw znaków minimalna jest wymagany do ucieczkę można zastosować RFC1738 i specyfikacja RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="b2594-343">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="b2594-344">Można użyć znaków ucieczki innych znaków.</span><span class="sxs-lookup"><span data-stu-id="b2594-344">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="b2594-345">Utwórz głównej części MIME o XOP koperty protokołu SOAP z kroku 4.</span><span class="sxs-lookup"><span data-stu-id="b2594-345">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="b2594-346">Zapisać nagłówków HTTP, w tym nagłówka HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="b2594-346">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="b2594-347">Należy zapisać pakiet MIME.</span><span class="sxs-lookup"><span data-stu-id="b2594-347">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="b2594-348">Komunikaty mechanizmu MTOM przetwarzania</span><span class="sxs-lookup"><span data-stu-id="b2594-348">Processing MTOM messages</span></span>  
 <span data-ttu-id="b2594-349">Przetwarzanie MTOM wiadomość jest dokładną odwrotnością proces opisany w poprzednim "Generowanie MTOM wiadomości" sekcji:</span><span class="sxs-lookup"><span data-stu-id="b2594-349">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="b2594-350">Upewnij się, głównej części MIME ma typ zawartości `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="b2594-350">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="b2594-351">Konstruować koperty protokołu SOAP, analizując głównej części MIME pakietu jako dokument XML.</span><span class="sxs-lookup"><span data-stu-id="b2594-351">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="b2594-352">Kodowanie znaków jest określany przez `charset` parametru Content-Type dla głównej części MIME.</span><span class="sxs-lookup"><span data-stu-id="b2594-352">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="b2594-353">Dla każdego elementu informacji elementu skonstruowane koperty protokołu SOAP, który ma, jedynym członkiem właściwości [dzieci] `xop:Include` elementu informacji elementu:</span><span class="sxs-lookup"><span data-stu-id="b2594-353">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="b2594-354">Usuń `cid:` prefiks i unescape wszystkie sekwencje ucieczki identyfikatora URI (RFC 2396) w wartości `@href` atrybutu `xop:Include` elementu.</span><span class="sxs-lookup"><span data-stu-id="b2594-354">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="b2594-355">Umieść ciąg wyniku w "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="b2594-355">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="b2594-356">Znajdź części MIME o pasującej do ciągu uzyskane w kroku 3a wartość nagłówka Content-ID.</span><span class="sxs-lookup"><span data-stu-id="b2594-356">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="b2594-357">Zastąp `xop:Include` element informacji elementu z `children` właściwości każdego elementu z elementami informacji znak reprezentujących kodowania base64 kanoniczny (zobacz XSD-2, 3.2.16 base64Binary) z treści jednostki części MIME zidentyfikowany w kroku 3b (skutecznie zastępują `xop:Include` elementu element informacji o danych odtworzone z części pakietu).</span><span class="sxs-lookup"><span data-stu-id="b2594-357">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="b2594-358">Nagłówek Content-Type protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="b2594-358">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="b2594-359">Poniżej znajduje się lista wyjaśnienia WCF dla formatu nagłówka HTTP Content-Type protokołu SOAP 1.x kodowany w formacie MTOM komunikatu pochodzi od wymagania określone w specyfikacji MTOM sam i pochodne MTOM i dokument RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="b2594-359">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="b2594-360">R4131: Nagłówek HTTP Content-Type musi mieć wartość multipart/powiązane (bez uwzględniania wielkości liter) i jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="b2594-360">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="b2594-361">Nazwa parametru jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="b2594-361">Parameter names are case-insensitive.</span></span> <span data-ttu-id="b2594-362">Kolejność parametrów nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="b2594-362">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="b2594-363">Pełna formularz Backus-Naur formularza (BNF) nagłówka Content-Type dla wiadomości MIME ma na liście 2045 RFC, sekcji 5.1.</span><span class="sxs-lookup"><span data-stu-id="b2594-363">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="b2594-364">R4132: Nagłówek HTTP Content-Type musi mieć parametr typu o wartości `application/xop+xml` ujęta w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="b2594-364">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="b2594-365">Podczas wymaganie, aby użyć podwójnego cudzysłowu nie jest jawną w dokumencie RFC 2387, tekst przestrzega, wszystkie parametry typu multipart/związane z nośnika najprawdopodobniej zawierać znaków zastrzeżonych, takich jak "\@" lub "/" i w związku z tym wymagają cudzysłowu Znaczniki.</span><span class="sxs-lookup"><span data-stu-id="b2594-365">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="b2594-366">R4133: Nagłówek HTTP Content-Type musi mieć parametr start o wartości nagłówka Identyfikatora zawartości części MIME, który zawiera SOAP 1.x koperty ujęta w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="b2594-366">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="b2594-367">W przypadku pominięcia początkowa pierwsza część MIME musi zawierać SOAP 1.x koperty.</span><span class="sxs-lookup"><span data-stu-id="b2594-367">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="b2594-368">R4134: Nagłówek HTTP Content-Type dla komunikatu SOAP 1.1 MTOM zakodowane musi zawierać informacje o uruchomieniu parametru z wartością tekstu/xml, ujęta w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="b2594-368">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="b2594-369">R4135: Nagłówka HTTP Content-Type komunikatu kodowany w formacie protokołu SOAP 1.2 MTOM muszą zawierać informacje o uruchomieniu parametru z wartością `application/soap+xml`, ujęty w podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="b2594-369">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="b2594-370">R4136: Nagłówek HTTP Content-Type dla komunikatu MTOM zakodowane w formacie 1.x SOAP musi mieć parametr granic o wartości (ujęta w znaki podwójnego cudzysłowu) odpowiadający granicą MIME, zdefiniowanych w specyfikacji RFC 2046 sekcji 5.1.1 BNF</span><span class="sxs-lookup"><span data-stu-id="b2594-370">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="b2594-371">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="b2594-371">Examples:</span></span>  
  
     <span data-ttu-id="b2594-372">POPRAW</span><span class="sxs-lookup"><span data-stu-id="b2594-372">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="b2594-373">POPRAW</span><span class="sxs-lookup"><span data-stu-id="b2594-373">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="b2594-374">NIEPOPRAWNE</span><span class="sxs-lookup"><span data-stu-id="b2594-374">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="b2594-375">Obiekt typu infoset części MIME</span><span class="sxs-lookup"><span data-stu-id="b2594-375">Infoset MIME Part</span></span>  
 <span data-ttu-id="b2594-376">SOAP 1.x koperty jest hermetyzowany jako część pakietu XOP MIME głównym i jest często nazywana `infoset` części.</span><span class="sxs-lookup"><span data-stu-id="b2594-376">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="b2594-377">R4141: SOAP 1.x koperty musi hermetyzowany jako część pakietu XOP MIME o nazwie głównego `infoset` należą i do którego istnieje odwołanie z HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="b2594-377">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="b2594-378">R4142: SOAP `Infoset` części musi zawierać następujące nagłówki MIME: `Content-ID`, `Content-Transfer-Encoding`, i `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="b2594-378">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="b2594-379">Format nagłówka Content-ID jest zdefiniowany w dokumencie RFC 2045 jako</span><span class="sxs-lookup"><span data-stu-id="b2594-379">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="b2594-380">gdzie `msg-id` jest zdefiniowana w dokumencie RFC 2822, (zastępującym RFC 822, do którego odwołuje się RFC 2045) jako:</span><span class="sxs-lookup"><span data-stu-id="b2594-380">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="b2594-381">i jest efektywne adres e-mail ujętą w nawiasy klamrowe "\<" i ">".</span><span class="sxs-lookup"><span data-stu-id="b2594-381">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="b2594-382">`[CFWS]` Prefiksu i sufiksu dodano RFC 2822 do przenoszenia komentarze i nie powinna być używana w celu zachowania współdziałania.</span><span class="sxs-lookup"><span data-stu-id="b2594-382">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="b2594-383">R4143: Wartość nagłówka Content-ID części MIME typu Infoset wykonaj `msg-id` produkcyjnych z RFC 2822 z `[CFWS]` części prefiksu i sufiksu pominięty.</span><span class="sxs-lookup"><span data-stu-id="b2594-383">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="b2594-384">Liczba wdrożeń MIME rozluźnić, wymagania dotyczące wartości ujętych w nawiasy klamrowe "\<" i ">" jako adres e-mail i użyć `absoluteURI` ujęta w "\<", ">" oprócz adresu e-mail.</span><span class="sxs-lookup"><span data-stu-id="b2594-384">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="b2594-385">Ta wersja programu WCF używa wartości nagłówek MIME Content-ID w postaci:</span><span class="sxs-lookup"><span data-stu-id="b2594-385">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="b2594-386">R4144: Procesorów MTOM powinna obsługiwać zgodnych rozluźnić, poniżej wartości nagłówka Content-ID `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="b2594-386">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="b2594-387">MIME (RFC 2045) zawiera nagłówek Content-Transfer-Encoding do komunikacji, kodowania zawartości części MIME.</span><span class="sxs-lookup"><span data-stu-id="b2594-387">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="b2594-388">Domyślnie zdefiniowane dla Content-Transfer-Encoding jest 7-bitowym, który nie jest odpowiedni dla większości wiadomości SOAP, więc nagłówka Content-Transfer-Encoding jest potrzebny większy współdziałania:</span><span class="sxs-lookup"><span data-stu-id="b2594-388">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="b2594-389">R4145: Część obiektu typu Infoset SOAP musi zawierać nagłówek Content-Transfer-Encoding.</span><span class="sxs-lookup"><span data-stu-id="b2594-389">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="b2594-390">R4146: W przypadku koperty protokołu SOAP kodowania znaków UTF-8, wartość nagłówka Content-Transfer-Encoding musi być 8-bitową.</span><span class="sxs-lookup"><span data-stu-id="b2594-390">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="b2594-391">R4147: W przypadku koperty protokołu SOAP kodowania znaków UTF-16, wartość nagłówka Content-Transfer-Encoding musi być binarny.</span><span class="sxs-lookup"><span data-stu-id="b2594-391">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="b2594-392">Zgodnie z [XOP] sekcji 5,</span><span class="sxs-lookup"><span data-stu-id="b2594-392">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="b2594-393">R4148: Część obiektu typu Infoset SOAP1.1 musi zawierać nagłówek Content-Type o typ nośnika application/xop + xml i parametry typu = "text/xml" i zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="b2594-393">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="b2594-394">R4149: Część obiektu typu Infoset SOAP 1.2 musi zawierać nagłówek Content-Type z typem nośnika `application/xop+xml` i parametry type = "`application/soap+xml`" i `charset`.</span><span class="sxs-lookup"><span data-stu-id="b2594-394">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="b2594-395">Gdy definiuje XOP `charset` parametr `application/xop+xml` jako opcjonalną, wymagana jest podobne do wymagań BP 1.1 na współdziałanie `charset` parametr `text/xml` typu nośnika.</span><span class="sxs-lookup"><span data-stu-id="b2594-395">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="b2594-396">R41410: `type` i `charset` parametry muszą być obecne w nagłówku Content-Type części typu Infoset 1.x protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b2594-396">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="b2594-397">Obsługa punktu końcowego WCF MTOM</span><span class="sxs-lookup"><span data-stu-id="b2594-397">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="b2594-398">MTOM ma na celu kodowania komunikatu protokołu SOAP, aby zoptymalizować dane zakodowane w formacie base64.</span><span class="sxs-lookup"><span data-stu-id="b2594-398">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="b2594-399">Poniżej znajduje się lista warunków ograniczających:</span><span class="sxs-lookup"><span data-stu-id="b2594-399">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="b2594-400">R4151: Może zostać zoptymalizowany dowolny element informacji elementu zawierającego dane zakodowane w formacie base64.</span><span class="sxs-lookup"><span data-stu-id="b2594-400">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="b2594-401">B4152: WCF optymalizuje element informacji elementy, które zawierają dane zakodowane w formacie base64 i przekracza 1024 bajtów długości.</span><span class="sxs-lookup"><span data-stu-id="b2594-401">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="b2594-402">Punkt końcowy usługi WCF skonfigurowana do używania MTOM będą zawsze wysyłały wiadomości w formacie MTOM.</span><span class="sxs-lookup"><span data-stu-id="b2594-402">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="b2594-403">Nawet jeśli żadne części spełniają kryteria wymagane, wiadomość jest nadal MTOM kodowany w formacie (serializowany jako pakiet MIME z jednej części MIME zawierającej koperty protokołu SOAP).</span><span class="sxs-lookup"><span data-stu-id="b2594-403">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="b2594-404">Potwierdzenie WS-Policy dla MTOM</span><span class="sxs-lookup"><span data-stu-id="b2594-404">WS-Policy Assertion for MTOM</span></span>  
 <span data-ttu-id="b2594-405">Usługi WCF używa następujących potwierdzenia zasad w celu wskazania MTOM użycia przez punkt końcowy:</span><span class="sxs-lookup"><span data-stu-id="b2594-405">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="b2594-406">R4211: Poprzedniego potwierdzenia zasad ma temat zasady punktu końcowego i określa, że wszystkie wiadomości wysyłane do i odbierane z punktu końcowego musi być zoptymalizowany przy użyciu mechanizmu MTOM.</span><span class="sxs-lookup"><span data-stu-id="b2594-406">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="b2594-407">B4212: Gdy skonfigurowany do używania MTOM optymalizacji, punkt końcowy usługi WCF dodaje potwierdzenia zasad MTOM zasady dołączone do odpowiedniej `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="b2594-407">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="b2594-408">Kompozycja z zabezpieczenia WS</span><span class="sxs-lookup"><span data-stu-id="b2594-408">Composition with WS-Security</span></span>  
 <span data-ttu-id="b2594-409">MTOM jest mechanizmem kodowania, która jest podobna do `text/xml` i WCF Binarny XML.</span><span class="sxs-lookup"><span data-stu-id="b2594-409">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="b2594-410">MTOM oferuje fizycznych kompozycji WS-Security i inne usługi WS-\* protokoły: wiadomości uwierzytelnionej za pomocą usługi WS-Security mogą być optymalizowane za pomocą mechanizmu MTOM.</span><span class="sxs-lookup"><span data-stu-id="b2594-410">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b2594-411">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b2594-411">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="b2594-412">Usługi WCF SOAP 1.1 komunikat zakodowane przy użyciu mechanizmu MTOM</span><span class="sxs-lookup"><span data-stu-id="b2594-412">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="b2594-413">Usługi WCF bezpiecznego protokołu SOAP 1.2 komunikat zakodowane przy użyciu mechanizmu MTOM</span><span class="sxs-lookup"><span data-stu-id="b2594-413">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="b2594-414">W tym przykładzie wiadomość jest zakodowany przy użyciu mechanizmu MTOM i SOAP 1.2, która jest chroniona za pomocą usługi WS-Security.</span><span class="sxs-lookup"><span data-stu-id="b2594-414">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="b2594-415">Części binarnej zidentyfikowane dla kodowania zawartości `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpowiedniego podpisu zaszyfrowanego i zaszyfrowanej treści.</span><span class="sxs-lookup"><span data-stu-id="b2594-415">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="b2594-416">Należy pamiętać, że `CipherValue` z `EncryptedKey` nie została zidentyfikowana optymalizacji przez usługi WCF, ponieważ jego długość jest mniej następnie 1024 bajty.</span><span class="sxs-lookup"><span data-stu-id="b2594-416">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>  
  
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
