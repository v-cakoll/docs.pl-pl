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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4052971746086061cb2ed091bd13c962318b2d89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="messaging-protocols"></a><span data-ttu-id="f84b6-102">Protokoły obsługi komunikatów</span><span class="sxs-lookup"><span data-stu-id="f84b6-102">Messaging Protocols</span></span>
<span data-ttu-id="f84b6-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Stosu kanału wykorzystuje kanały transportu i kodowanie do transformacji reprezentacji wewnętrznej komunikatu do jego format danych przesyłanych w sieci i wysłać go przy użyciu danego transportu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="f84b6-104">Transport najczęściej używane na współdziałanie usług sieci Web, jest protokół HTTP i są najczęściej używane kodowanie, używane przez usługi sieci Web opartych na języku XML SOAP 1.1 i SOAP 1.2, mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="f84b6-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="f84b6-105">W tym temacie omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji dla następujących protokołów zatrudnieni przez <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f84b6-105">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="f84b6-106">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="f84b6-106">Specification/document</span></span>|<span data-ttu-id="f84b6-107">Łącze</span><span class="sxs-lookup"><span data-stu-id="f84b6-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="f84b6-108">PROTOKOŁU HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="f84b6-108">HTTP 1.1</span></span>|<span data-ttu-id="f84b6-109">http://www.IETF.org/RFC/RFC2616.txt</span><span class="sxs-lookup"><span data-stu-id="f84b6-109">http://www.ietf.org/rfc/rfc2616.txt</span></span>|  
|<span data-ttu-id="f84b6-110">SOAP 1.1 powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="f84b6-110">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="f84b6-111">http://www.w3.org/TR/2000/Note-SOAP-20000508/, sekcji 7</span><span class="sxs-lookup"><span data-stu-id="f84b6-111">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="f84b6-112">SOAP 1.2 powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="f84b6-112">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="f84b6-113">http://www.w3.org/TR/soap12-part2/, sekcji 7</span><span class="sxs-lookup"><span data-stu-id="f84b6-113">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="f84b6-114">W tym temacie omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji dla następujące protokoły <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> fragmentów.</span><span class="sxs-lookup"><span data-stu-id="f84b6-114">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="f84b6-115">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="f84b6-115">Specification/Document</span></span>|<span data-ttu-id="f84b6-116">Łącze</span><span class="sxs-lookup"><span data-stu-id="f84b6-116">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="f84b6-117">XML</span><span class="sxs-lookup"><span data-stu-id="f84b6-117">XML</span></span>|<span data-ttu-id="f84b6-118">http://www.w3.org/TR/REC-XML</span><span class="sxs-lookup"><span data-stu-id="f84b6-118">http://www.w3.org/TR/REC-xml</span></span>|  
|<span data-ttu-id="f84b6-119">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="f84b6-119">SOAP 1.1</span></span>|<span data-ttu-id="f84b6-120">http://www.w3.org/TR/2000/Note-SOAP-20000508/</span><span class="sxs-lookup"><span data-stu-id="f84b6-120">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/</span></span>|  
|<span data-ttu-id="f84b6-121">SOAP 1.2 Core</span><span class="sxs-lookup"><span data-stu-id="f84b6-121">SOAP 1.2 Core</span></span>|<span data-ttu-id="f84b6-122">http://www.w3.org/TR/soap12-Part1/</span><span class="sxs-lookup"><span data-stu-id="f84b6-122">http://www.w3.org/TR/soap12-part1/</span></span>|  
|<span data-ttu-id="f84b6-123">Protokół WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="f84b6-123">WS-Addressing 2004/08</span></span>|<span data-ttu-id="f84b6-124">http://www.w3.org/submission/2004/SUBM-WS-Addressing-20040810/</span><span class="sxs-lookup"><span data-stu-id="f84b6-124">http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/</span></span>|  
|<span data-ttu-id="f84b6-125">Usługi sieci Web W3C adresowania 1.0 — podstawowe</span><span class="sxs-lookup"><span data-stu-id="f84b6-125">W3C Web Services Addressing 1.0 - Core</span></span>|<span data-ttu-id="f84b6-126">http://www.w3.org/TR/2006/rec-ws-addr-Core-20060509</span><span class="sxs-lookup"><span data-stu-id="f84b6-126">http://www.w3.org/TR/2006/REC-ws-addr-core-20060509</span></span>|  
|<span data-ttu-id="f84b6-127">Adresowania 1.0 — wiązanie protokołu SOAP usług sieci Web W3C</span><span class="sxs-lookup"><span data-stu-id="f84b6-127">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|<span data-ttu-id="f84b6-128">http://www.w3.org/TR/2006/rec-ws-addr-SOAP-20060509</span><span class="sxs-lookup"><span data-stu-id="f84b6-128">http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509</span></span>|  
|<span data-ttu-id="f84b6-129">Usługi sieci Web W3C adresowania 1.0 — wiązanie WSDL</span><span class="sxs-lookup"><span data-stu-id="f84b6-129">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|<span data-ttu-id="f84b6-130">http://www.w3.org/TR/2006/CR-ws-addr-WSDL-20060529/</span><span class="sxs-lookup"><span data-stu-id="f84b6-130">http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/</span></span>|  
<span data-ttu-id="f84b6-131">Usługi sieci Web W3C adresowania 1.0 - metadanych</span><span class="sxs-lookup"><span data-stu-id="f84b6-131">W3C Web Services Addressing 1.0 - Metadata</span></span>|<span data-ttu-id="f84b6-132">http://www.w3.org/TR/ws-addr-METADATA/</span><span class="sxs-lookup"><span data-stu-id="f84b6-132">http://www.w3.org/TR/ws-addr-metadata/</span></span>|  
|<span data-ttu-id="f84b6-133">Powiązanie WSDL SOAP1.1</span><span class="sxs-lookup"><span data-stu-id="f84b6-133">WSDL SOAP1.1 Binding</span></span>|<span data-ttu-id="f84b6-134">http://www.w3.org/TR/WSDL/</span><span class="sxs-lookup"><span data-stu-id="f84b6-134">http://www.w3.org/TR/wsdl/</span></span>|  
|<span data-ttu-id="f84b6-135">Powiązanie WSDL SOAP1.2</span><span class="sxs-lookup"><span data-stu-id="f84b6-135">WSDL SOAP1.2 Binding</span></span>|<span data-ttu-id="f84b6-136">http://www.w3.org/submission/wsdl11soap12/</span><span class="sxs-lookup"><span data-stu-id="f84b6-136">http://www.w3.org/Submission/wsdl11soap12/</span></span>|  
  
 <span data-ttu-id="f84b6-137">W tym temacie omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji dla następujące protokoły <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> wykorzystuje.</span><span class="sxs-lookup"><span data-stu-id="f84b6-137">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="f84b6-138">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="f84b6-138">Specification/document</span></span>|<span data-ttu-id="f84b6-139">Łącze</span><span class="sxs-lookup"><span data-stu-id="f84b6-139">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="f84b6-140">ELEMENT XOP</span><span class="sxs-lookup"><span data-stu-id="f84b6-140">XOP</span></span>|<span data-ttu-id="f84b6-141">http://www.w3.org/TR/xop10/</span><span class="sxs-lookup"><span data-stu-id="f84b6-141">http://www.w3.org/TR/xop10/</span></span>|  
|<span data-ttu-id="f84b6-142">MTOM + SOAP 1.2 powiązania</span><span class="sxs-lookup"><span data-stu-id="f84b6-142">MTOM + SOAP 1.2 Binding</span></span>|<span data-ttu-id="f84b6-143">http://www.w3.org/TR/soap12-MTOM/</span><span class="sxs-lookup"><span data-stu-id="f84b6-143">http://www.w3.org/TR/soap12-mtom/</span></span>|  
|<span data-ttu-id="f84b6-144">MTOM SOAP 1.1 powiązania</span><span class="sxs-lookup"><span data-stu-id="f84b6-144">MTOM SOAP 1.1 Binding</span></span>|<span data-ttu-id="f84b6-145">http://www.w3.org/submission/soap11mtom10/</span><span class="sxs-lookup"><span data-stu-id="f84b6-145">http://www.w3.org/Submission/soap11mtom10/</span></span>|  
|<span data-ttu-id="f84b6-146">Potwierdzenie WS-Policy MTOM</span><span class="sxs-lookup"><span data-stu-id="f84b6-146">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="f84b6-147">http://www.w3.org/submission/2006/SUBM-ws-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="f84b6-147">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="f84b6-148">Następujące obszary nazw XML i prefiksy skojarzone są używane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f84b6-148">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="f84b6-149">Prefiks</span><span class="sxs-lookup"><span data-stu-id="f84b6-149">Prefix</span></span>|<span data-ttu-id="f84b6-150">Namespace Uniform Resource Identifier (URI)</span><span class="sxs-lookup"><span data-stu-id="f84b6-150">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="f84b6-151">S11</span><span class="sxs-lookup"><span data-stu-id="f84b6-151">s11</span></span>|<span data-ttu-id="f84b6-152">http://schemas.xmlsoap.org/SOAP/Envelope</span><span class="sxs-lookup"><span data-stu-id="f84b6-152">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="f84b6-153">S12</span><span class="sxs-lookup"><span data-stu-id="f84b6-153">s12</span></span>|<span data-ttu-id="f84b6-154">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="f84b6-154">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="f84b6-155">wsa</span><span class="sxs-lookup"><span data-stu-id="f84b6-155">wsa</span></span>|<span data-ttu-id="f84b6-156">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="f84b6-156">http://www.w3.org/2004/08/addressing</span></span>|  
|<span data-ttu-id="f84b6-157">wsam</span><span class="sxs-lookup"><span data-stu-id="f84b6-157">wsam</span></span>|<span data-ttu-id="f84b6-158">http://www.w3.org/2007/05/Addressing/METADATA</span><span class="sxs-lookup"><span data-stu-id="f84b6-158">http://www.w3.org/2007/05/addressing/metadata</span></span>|  
|<span data-ttu-id="f84b6-159">wsap</span><span class="sxs-lookup"><span data-stu-id="f84b6-159">wsap</span></span>|<span data-ttu-id="f84b6-160">http://schemas.xmlsoap.org/ws/2004/09/Policy/Addressing</span><span class="sxs-lookup"><span data-stu-id="f84b6-160">http://schemas.xmlsoap.org/ws/2004/09/policy/addressing</span></span>|  
|<span data-ttu-id="f84b6-161">wsa10</span><span class="sxs-lookup"><span data-stu-id="f84b6-161">wsa10</span></span>|<span data-ttu-id="f84b6-162">http://www.w3.org/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="f84b6-162">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="f84b6-163">wsaw10</span><span class="sxs-lookup"><span data-stu-id="f84b6-163">wsaw10</span></span>|<span data-ttu-id="f84b6-164">http://www.w3.org/2006/05/Addressing/WSDL</span><span class="sxs-lookup"><span data-stu-id="f84b6-164">http://www.w3.org/2006/05/addressing/wsdl</span></span>|  
|<span data-ttu-id="f84b6-165">Element XOP</span><span class="sxs-lookup"><span data-stu-id="f84b6-165">xop</span></span>|<span data-ttu-id="f84b6-166">http://www.w3.org/2004/08/XOP/Include</span><span class="sxs-lookup"><span data-stu-id="f84b6-166">http://www.w3.org/2004/08/xop/include</span></span>|  
|<span data-ttu-id="f84b6-167">xmime</span><span class="sxs-lookup"><span data-stu-id="f84b6-167">xmime</span></span>|<span data-ttu-id="f84b6-168">http://www.w3.org/2004/06/xmlmime</span><span class="sxs-lookup"><span data-stu-id="f84b6-168">http://www.w3.org/2004/06/xmlmime</span></span><br /><br /> <span data-ttu-id="f84b6-169">http://www.w3.org/2005/05/xmlmime</span><span class="sxs-lookup"><span data-stu-id="f84b6-169">http://www.w3.org/2005/05/xmlmime</span></span>|  
<span data-ttu-id="f84b6-170">punkt dystrybucji</span><span class="sxs-lookup"><span data-stu-id="f84b6-170">dp</span></span>|<span data-ttu-id="f84b6-171">http://schemas.microsoft.com/NET/2006/06/Duplex</span><span class="sxs-lookup"><span data-stu-id="f84b6-171">http://schemas.microsoft.com/net/2006/06/duplex</span></span>|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="f84b6-172">SOAP 1.1 i SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="f84b6-172">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="f84b6-173">Koperty i przetwarzania modelu</span><span class="sxs-lookup"><span data-stu-id="f84b6-173">Envelope and Processing Model</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-174">implementuje przetwarzania koperty protokołu SOAP 1.1 Basic Profile 1.1 (BP11) i Basic Profile 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="f84b6-174"> implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="f84b6-175">SOAP 1.2 koperty przetwarzania jest zaimplementowana po SOAP12 — część 1.</span><span class="sxs-lookup"><span data-stu-id="f84b6-175">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="f84b6-176">W tej sekcji opisano niektóre opcje implementacji wykonywaną przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] BP11 i SOAP12 — część 1.</span><span class="sxs-lookup"><span data-stu-id="f84b6-176">This section explains certain implementation choices taken by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="f84b6-177">Wymagany nagłówek przetwarzania</span><span class="sxs-lookup"><span data-stu-id="f84b6-177">Mandatory Header Processing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-178">następuje reguł do przetwarzania nagłówków oznaczony `mustUnderstand` opisanego w specyfikacji SOAP 1.1 i SOAP 1.2, z następujących zmian.</span><span class="sxs-lookup"><span data-stu-id="f84b6-178"> follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="f84b6-179">Komunikat, który przechodzi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanału stosu jest przetwarzany przez poszczególnych kanałów skonfigurowanych przez powiązanie skojarzone elementy, na przykład, kodowania wiadomości tekstowych, zabezpieczeń, niezawodna obsługa komunikatów i transakcji.</span><span class="sxs-lookup"><span data-stu-id="f84b6-179">A message that enters the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="f84b6-180">Każdy kanał rozpoznaje nagłówków z skojarzona przestrzeń nazw i oznacza je jako rozumiem.</span><span class="sxs-lookup"><span data-stu-id="f84b6-180">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="f84b6-181">W momencie komunikat wejścia dyspozytor, programu formatującego operacji odczytuje nagłówki oczekiwany przez odpowiednie kontraktu komunikatu na operację i znaczniki ich zrozumienie.</span><span class="sxs-lookup"><span data-stu-id="f84b6-181">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="f84b6-182">Następnie Dyspozytor sprawdza, czy wszystkie pozostałe nagłówki nie są rozumieć, ale oznaczenie `mustUnderstand` i zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f84b6-182">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="f84b6-183">Komunikaty, które zawierają `mustUnderstand` nagłówki, które są przeznaczone dla odbiorcy nie są przetwarzane przez kod aplikacji odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="f84b6-183">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="f84b6-184">Takie warstwie przetwarzania umożliwia rozdzielenie warstwy infrastruktury i aplikacji węzła SOAP:</span><span class="sxs-lookup"><span data-stu-id="f84b6-184">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="f84b6-185">B1111: Nagłówki, które nie są zrozumiałe są wykrywane po komunikat jest przetwarzany przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu kanału infrastruktury, ale przetworzenia przez aplikację</span><span class="sxs-lookup"><span data-stu-id="f84b6-185">B1111: Headers that are not understood are detected after the message is processed by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="f84b6-186">`mustUnderstand` Wartość nagłówka różni się między SOAP 1.1 i SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="f84b6-186">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="f84b6-187">Basic Profile 1.1 wymaga, aby `mustUnderstand` wartość wynosić 0 lub 1 dla wiadomości SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="f84b6-187">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="f84b6-188">SOAP 1.2 umożliwia 0, 1, `false`, i `true` jako wartości, ale zaleca emitowanie canonical reprezentację `xs:boolean` wartości (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="f84b6-188">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="f84b6-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emituje `mustUnderstand` wartości 0 i 1 dla wersji zarówno SOAP 1.1 i SOAP 1.2 koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-190">akceptuje miejsce całą wartość `xs:boolean` dla `mustUnderstand` nagłówka (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="f84b6-190"> accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="f84b6-191">Błędach SOAP</span><span class="sxs-lookup"><span data-stu-id="f84b6-191">SOAP Faults</span></span>  
 <span data-ttu-id="f84b6-192">Poniżej przedstawiono listę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-określonej implementacji błędu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-192">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="f84b6-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zwraca następujące kody błędów protokołu SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, i `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="f84b6-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zwraca następujące kody błędów protokołu SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, i `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="f84b6-195">Wiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="f84b6-195">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="f84b6-196">SOAP 1.1 powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="f84b6-196">SOAP 1.1 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-197">implementuje powiązanie SOAP1.1 HTTP po specyfikacji Basic Profile 1.1 sekcji 3.4 o wyjaśnienia następujące:</span><span class="sxs-lookup"><span data-stu-id="f84b6-197"> implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="f84b6-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa nie implementuje przekierowania żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="f84b6-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="f84b6-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów obsługujących pliki cookie HTTP, zgodnie z 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="f84b6-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="f84b6-200">SOAP 1.2 powiązanie HTTP</span><span class="sxs-lookup"><span data-stu-id="f84b6-200">SOAP 1.2 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-201">implementuje powiązania SOAP 1.2 HTTP, zgodnie z opisem w SOAP 1.2, część 2 (SOAP12Part2) specyfikacji z następujących wyjaśnienia.</span><span class="sxs-lookup"><span data-stu-id="f84b6-201"> implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="f84b6-202">Parametr opcjonalny akcji dla wprowadzone SOAP 1.2 `application/soap+xml` typu nośnika.</span><span class="sxs-lookup"><span data-stu-id="f84b6-202">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="f84b6-203">Ten parametr jest przydatne w celu zoptymalizowania wysyłania wiadomości bez konieczności czy treść komunikatu protokołu SOAP można w sytuacji, gdy WS-Addressing nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="f84b6-203">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="f84b6-204">R2221: `application/soap+xml` parametr akcji, jeśli jest obecny w żądaniu SOAP 1.2, muszą być zgodne `soapAction` atrybutu `wsoap12:operation` elementu w odpowiednich Powiązanie WSDL.</span><span class="sxs-lookup"><span data-stu-id="f84b6-204">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="f84b6-205">R2222: `application/soap+xml` parametr akcji, jeśli jest obecny na wiadomości SOAP 1.2, muszą być zgodne `wsa:Action` stosowania WS-Addressing 2004/08 lub 1.0 WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f84b6-205">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="f84b6-206">Gdy WS-Addressing jest wyłączona, a żądanie przychodzące nie zawiera parametr akcji, wiadomości `Action` jest traktowany jako okres bez określonej.</span><span class="sxs-lookup"><span data-stu-id="f84b6-206">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="f84b6-207">Protokół WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="f84b6-207">WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-208">implementuje 3 wersji WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="f84b6-208"> implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="f84b6-209">Protokół WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="f84b6-209">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="f84b6-210">W3C usług sieci Web adresowanie SOAP powiązania (ADDR10 SOAP) i 1.0 Core (ADDR10 RDZENI)</span><span class="sxs-lookup"><span data-stu-id="f84b6-210">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="f84b6-211">Protokół WS-Addressing 1.0 - metadanych</span><span class="sxs-lookup"><span data-stu-id="f84b6-211">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="f84b6-212">Odwołania do punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="f84b6-212">Endpoint References</span></span>  
 <span data-ttu-id="f84b6-213">Wszystkie wersje usługi WS-Addressing który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje używać odwołań do punktu końcowego do opisywania punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="f84b6-213">All versions of WS-Addressing that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="f84b6-214">Odwołania do punktu końcowego i wersji WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="f84b6-214">Endpoint References and WS-Addressing Versions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-215">implementuje wiele protokołów infrastruktury, które używają protokołu WS-Addressing, w szczególności `EndpointReference` elementu i `W3C.WsAddressing.EndpointReferenceType` klasy (na przykład WS-ReliableMessaging, WS-SecureConversation i WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="f84b6-215"> implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-216">obsługuje korzystanie z danej wersji WS-Addressing z innymi protokołami infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f84b6-216"> supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-217">punkty końcowe obsługuje jedną wersję WS-Addressing na punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f84b6-217"> endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="f84b6-218">Dla R3111, w obszarze nazw `EndpointReference` elementu lub typ używany w wiadomościach z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego musi odpowiadać wersji WS-Addressing implementowanych przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f84b6-218">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="f84b6-219">Na przykład jeśli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego implementuje usługi WS-ReliableMessaging `AcksTo` zwrócony przez punkt końcowy, wewnątrz nagłówka `CreateSequenceResponse` korzysta z wersji WS-Addressing który `EncodingBinding` określa element dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f84b6-219">For example, if a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="f84b6-220">Odwołania do punktu końcowego i metadane</span><span class="sxs-lookup"><span data-stu-id="f84b6-220">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="f84b6-221">Liczba scenariuszy wymagają komunikacji metadanych lub odwołanie do metadanych dla danego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f84b6-221">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="f84b6-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wykorzystuje mechanizm opisane w sekcji 6, aby uwzględnić metadanych dla odwołania do punktu końcowego według wartości lub według odwołania specyfikacji WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="f84b6-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="f84b6-223">Rozważmy scenariusz, w którym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa wymaga uwierzytelnienia za pomocą tokenu zabezpieczeń potwierdzenia Markup Language (SAML) wydanego przez emitenta tokenu w http://sts.fabrikam123.com. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Punktu końcowego opisano to wymaganie uwierzytelniania przy użyciu `sp:IssuedToken` asercja z zagnieżdżoną `sp:Issuer` wskazujący emitenta tokenu potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="f84b6-223">Consider a scenario where a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com. The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="f84b6-224">Aplikacje klienckie, które uzyskują dostęp do `sp:Issuer` potwierdzenia trzeba znać sposób komunikacji z punktem końcowym wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="f84b6-224">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="f84b6-225">Klient musi wiedzieć, metadane dotyczące wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="f84b6-225">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="f84b6-226">Korzystanie z rozszerzeń metadanych odwołania punktu końcowego zdefiniowana w punkcie końcowym MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera odwołanie do metadanych wystawca tokenów.</span><span class="sxs-lookup"><span data-stu-id="f84b6-226">Using the endpoint reference metadata extensions defined in MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a reference to the token issuer metadata.</span></span>  
  
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
  
### <a name="message-addressing-headers"></a><span data-ttu-id="f84b6-227">Adresowanie nagłówki komunikatów</span><span class="sxs-lookup"><span data-stu-id="f84b6-227">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="f84b6-228">Nagłówki komunikatów</span><span class="sxs-lookup"><span data-stu-id="f84b6-228">Message Headers</span></span>  
 <span data-ttu-id="f84b6-229">W przypadku obu wersji WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa następujące nagłówki komunikatów według specyfikacji `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, i `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-229">For both WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="f84b6-230">B3211: dla wszystkich wersji WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honoruje, ale nie tworzy fabrycznej nagłówków wiadomości WS-Addressing `wsa:FaultTo` i `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-230">B3211: For all WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="f84b6-231">Aplikacje, które współdziałają z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji można dodać te wiadomości nagłówki i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odpowiednio przetworzy je.</span><span class="sxs-lookup"><span data-stu-id="f84b6-231">Applications that interact with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can add these message headers and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="f84b6-232">Odwołanie do parametrów i właściwości</span><span class="sxs-lookup"><span data-stu-id="f84b6-232">Reference Parameters and Properties</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-233">implementuje przetwarzania parametrów odwołanie do punktu końcowego i odwołanie p</span><span class="sxs-lookup"><span data-stu-id="f84b6-233"> implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="f84b6-234">właściwości zgodnie z odpowiednimi wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="f84b6-234">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="f84b6-235">B3221: Gdy skonfigurowany do używania protokołu WS-Addressing 2004/08 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych nie odróżnienie przetwarzania właściwości odwołania i parametrów odwołania.</span><span class="sxs-lookup"><span data-stu-id="f84b6-235">B3221: When configured to use WS-Addressing 2004/08, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="f84b6-236">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="f84b6-236">Message Exchange Patterns</span></span>  
 <span data-ttu-id="f84b6-237">Sekwencja komunikatów związane z wywołania operacji usługi sieci Web nazywa się *wymiany komunikatów*.</span><span class="sxs-lookup"><span data-stu-id="f84b6-237">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-238">obsługuje jednokierunkowe, żądanie odpowiedź i dupleksu wiadomości wymiany wzorce.</span><span class="sxs-lookup"><span data-stu-id="f84b6-238"> supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="f84b6-239">W tej sekcji wyjaśnia WS-Addressing wymagania dotyczące przetwarzania w zależności od wymiany komunikatów używany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f84b6-239">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="f84b6-240">W tej sekcji żądający wysyła pierwszy komunikat i obiekt odpowiadający odbiera pierwszego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-240">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="f84b6-241">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="f84b6-241">One-Way Message</span></span>  
 <span data-ttu-id="f84b6-242">Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punkt końcowy jest skonfigurowana do obsługi komunikatów z danego `Action` wykonać wzorzec jednokierunkowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego obowiązują następujące zachowania i wymagania.</span><span class="sxs-lookup"><span data-stu-id="f84b6-242">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="f84b6-243">Inaczej, zachowania i zasady mają zastosowanie zarówno wersji WS-Addressing obsługiwane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f84b6-243">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="f84b6-244">R3311: Żądający musi zawierać `wsa:To`, `wsa:Action`, a nagłówki dla wszystkich parametrów odwołanie określone przez odwołanie do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f84b6-244">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="f84b6-245">Po jest używany protokół WS-Addressing 2004/08 i [właściwości odwołania] są określone przez odwołanie do punktu końcowego odpowiednie nagłówki musi zostać dodany do komunikatu za.</span><span class="sxs-lookup"><span data-stu-id="f84b6-245">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="f84b6-246">B3312: Żądający może obejmować `MessageID`, `ReplyTo`, i `FaultTo` nagłówków.</span><span class="sxs-lookup"><span data-stu-id="f84b6-246">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="f84b6-247">Infrastruktura odbiornik, zostaną one zignorowane, a zostaną przekazane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f84b6-247">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="f84b6-248">R3313: Gdy HTTP jest używany, a żaden komunikat jest wysyłany na etap odpowiedzi HTTP, odpowiadający musi wysłać odpowiedź HTTP z pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f84b6-248">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="f84b6-249">Podczas transportu HTTP jest w użyciu i kontrakt operacji deklaruje komunikatu jednokierunkowego, odpowiedź HTTP nadal może być używany do wysyłania wiadomości infrastruktury — na przykład wysłać niezawodna obsługa komunikatów `SequenceAcknowledgement` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-249">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="f84b6-250">B3314: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu odpowiadającego w trybie nie wysyła w odpowiedzi na komunikat jednokierunkowy komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="f84b6-250">B3314: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="f84b6-251">Żądanie i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="f84b6-251">Request-Reply</span></span>  
 <span data-ttu-id="f84b6-252">Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punkt końcowy jest skonfigurowana dla komunikatu o danej `Action` postępuj zgodnie ze wzorcem "żądanie-odpowiedź" [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego następuje zachowania i poniższe wymagania.</span><span class="sxs-lookup"><span data-stu-id="f84b6-252">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="f84b6-253">Chyba że określono inaczej, zachowania i zasady mają zastosowanie zarówno wersji WS-Addressing obsługiwane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f84b6-253">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="f84b6-254">R3321: W żądaniu musi zawierać żądający `wsa:To`, `wsa:Action`, `wsa:MessageID`, a nagłówki dla wszystkich parametrów odwołania odwołania (i właściwości) określone przez odwołanie do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f84b6-254">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="f84b6-255">R3322: W przypadku protokołu WS-Addressing 2004/08 `ReplyTo` muszą także być ujęte w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-255">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="f84b6-256">R3323: Gdy jest używany protokół WS-Addressing 1.0 i `ReplyTo` jest domyślnym odwołaniem punktu końcowego z właściwością [address] równa "http://www.w3.org/2005/08/addressing/anonymous" nie znajduje się w żądaniu, jest używany.</span><span class="sxs-lookup"><span data-stu-id="f84b6-256">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="f84b6-257">R3324: Żądający musi zawierać `wsa:To`, `wsa:Action`, i `wsa:RelatesTo` nagłówków komunikatu odpowiedzi, a także nagłówki dla wszystkich parametrów odwołania odwołania (i właściwości) określone przez `ReplyTo` w odwołaniu do punktu końcowego żądanie.</span><span class="sxs-lookup"><span data-stu-id="f84b6-257">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="f84b6-258">Usługi sieci Web adresowanie błędów</span><span class="sxs-lookup"><span data-stu-id="f84b6-258">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="f84b6-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tworzy następujące błędy, zdefiniowane przez protokół WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="f84b6-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="f84b6-260">Kod</span><span class="sxs-lookup"><span data-stu-id="f84b6-260">Code</span></span>|<span data-ttu-id="f84b6-261">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f84b6-261">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="f84b6-262">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="f84b6-262">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="f84b6-263">Odebrano komunikat z `ReplyTo` innego niż adres dla tego kanału; nie istnieje brak nasłuchującego pod adresem określonym w nagłówku do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f84b6-263">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="f84b6-264">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="f84b6-264">wsa:ActionNotSupported</span></span>|<span data-ttu-id="f84b6-265">kanały infrastruktury lub skojarzone z punktem końcowym Dyspozytor nie rozpoznają z akcją określoną w `Action` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="f84b6-265">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="f84b6-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tworzy następujące błędy, zdefiniowane przez protokół WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="f84b6-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="f84b6-267">Kod</span><span class="sxs-lookup"><span data-stu-id="f84b6-267">Code</span></span>|<span data-ttu-id="f84b6-268">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f84b6-268">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="f84b6-269">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="f84b6-269">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="f84b6-270">Zduplikowana `wsa:To`, `wsa:ReplyTo`, `wsa:From` lub `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-270">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="f84b6-271">Zduplikowana `wsa:RelatesTo` o takiej samej `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-271">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="f84b6-272">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="f84b6-272">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="f84b6-273">Brak wymaganego nagłówka adresowanie.</span><span class="sxs-lookup"><span data-stu-id="f84b6-273">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="f84b6-274">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="f84b6-274">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="f84b6-275">Odebrano komunikat z `ReplyTo` innego niż adres dla tego kanału.</span><span class="sxs-lookup"><span data-stu-id="f84b6-275">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="f84b6-276">Brak nasłuchującego pod adresem określonym w nagłówku do punktu końcowego nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f84b6-276">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="f84b6-277">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="f84b6-277">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="f84b6-278">Action określony w `Action` nagłówka nie jest rozpoznawane przez infrastrukturę kanały lub dyspozytora skojarzonej z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="f84b6-278">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="f84b6-279">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="f84b6-279">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="f84b6-280">Kanał RM wysyła ten błąd, wskazujący punkt końcowy nie będzie przetwarzał sekwencji oparte na badanie `CreateSequence` nagłówków adresowych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f84b6-280">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="f84b6-281">Kod w poprzednich tabelach mapuje `FaultCode` w SOAP 1.1 i `SubCode` (z kodem = nadawca) w SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="f84b6-281">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="f84b6-282">WSDL 1.1 wiązania i protokołu WS-Policy potwierdzeń</span><span class="sxs-lookup"><span data-stu-id="f84b6-282">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="f84b6-283">Używanie protokołu WS-Addressing wskazujący</span><span class="sxs-lookup"><span data-stu-id="f84b6-283">Indicating Use of WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-284">używa potwierdzeń zasad, aby wskazać punkt końcowy obsługę konkretnej wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f84b6-284"> uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="f84b6-285">Następujące potwierdzenia zasad ma punkt końcowy zasad podmiotu [WS-PA] i wskazuje, że komunikaty wysyłane i odbierane z punktem końcowym muszą używać protokołu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="f84b6-285">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="f84b6-286">Potwierdzenie zasad wspomaga specyfikacji WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="f84b6-286">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="f84b6-287">Następujące potwierdzenia zasad, oznacza to, że komunikaty który wysłać/odebrać musi używać protokołu WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="f84b6-287">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="f84b6-288">Następujące potwierdzenia zasad ma punkt końcowy podmiotu zasad [WS-PA] i wskazuje, że komunikaty wysyłane i odbierane z punktu końcowego musi używać protokołu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="f84b6-288">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="f84b6-289">`wsaw10:UsingAddressing` Element jest pobierają z [WS-Addressing-WSDL] i jest używany w ramach usługi WS-Policy zgodnie z tym specyfikacją, sekcja 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="f84b6-289">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="f84b6-290">Użyj adresowanie nie zmienia semantykę wersji 1.1 języka WSDL SOAP 1.1 i SOAP 1.2 HTTP powiązania.</span><span class="sxs-lookup"><span data-stu-id="f84b6-290">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="f84b6-291">Na przykład jeśli odpowiedź ma żądanie, które są wysyłane do punktu końcowego, który używa powiązanie HTTP 1.x adresowanie i WSDL SOAP, odpowiedź należy wysłać przy użyciu odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-291">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="f84b6-292">Odpowiedzi na wysłane za pośrednictwem odpowiedzi http WS-AM potwierdzenia jest:</span><span class="sxs-lookup"><span data-stu-id="f84b6-292">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="f84b6-293">Potwierdzenie pełną zasad może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f84b6-293">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="f84b6-294">Istnieją jednak wzorce wymiany wiadomości, korzystających z o dwa połączenia HTTP niezależne odwrotnej między obiektu żądającego i odpowiadający, na przykład na niechciane komunikaty jednokierunkowe wysyłane przez odpowiadający.</span><span class="sxs-lookup"><span data-stu-id="f84b6-294">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-295">oferuje funkcję za pomocą którego dwa kanały transportu źródłowego utworzenia złożonego dupleksu kanału, gdzie jeden kanał służy do wprowadzania wiadomości, a drugi służy do komunikaty wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="f84b6-295"> offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="f84b6-296">W przypadku transportu HTTP złożonego dupleksu zawiera dwa połączenia HTTP odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="f84b6-296">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="f84b6-297">Żądający używa jednego połączenia do wysyłania komunikatów do udzielenia i udzielenia używa innych wysyłania wiadomości z powrotem do strony żądającej.</span><span class="sxs-lookup"><span data-stu-id="f84b6-297">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="f84b6-298">Odpowiedzi na wysłane za pośrednictwem żądania http oddzielne jest potwierdzenie ws am</span><span class="sxs-lookup"><span data-stu-id="f84b6-298">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="f84b6-299">Potwierdzenie pełną zasad może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f84b6-299">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="f84b6-300">Użyj następujących potwierdzenia o temacie zasady punktu końcowego [WS-PA] dla punktów końcowych używających powiązania HTTP 1.x WSDL 1.1 SOAP wymaga dwóch oddzielnych odwrotnej połączeń HTTP używanego do wiadomości przesyłane od osoby żądającej do obiektu odpowiadającego w trybie i obiekt odpowiadający w trybie żądającej, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f84b6-300">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="f84b6-301">Poprzednia prowadzi do następujących wymagań dotyczących `wsa:ReplyTo` nagłówek dla wiadomości żądania:</span><span class="sxs-lookup"><span data-stu-id="f84b6-301">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="f84b6-302">R3514: Żądanie wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwość nie ma wartości "http://www.w3.org/2005/08/addressing/anonymous" Jeśli punkt końcowy nie używa powiązania WSDL 1.1 SOAP 1.x HTTP i nie ma stanowi alternatywę zasad z `wsap10:UsingAddressing` lub `wsap:UsingAddressing` potwierdzenia połączone z `cdp:CompositeDuplex` dołączony.</span><span class="sxs-lookup"><span data-stu-id="f84b6-302">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="f84b6-303">R3515: Żądanie wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwości równa się "http://www.w3.org/2005/08/addressing/anonymous" lub nie ma `ReplyTo` 1.x HTTP SOAP nagłówka gwarancja, jeśli korzysta z punktu końcowego WSDL 1.1 powiązanie i jest to alternatywa zasad z `wsap10:UsingAddressing` potwierdzenia i nie `cdp:CompositeDuplex` potwierdzenia dołączony.</span><span class="sxs-lookup"><span data-stu-id="f84b6-303">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="f84b6-304">R3516: Żądanie wiadomości wysłane do punktu końcowego musi mieć `ReplyTo` nagłówek o `[address]` właściwości jest równa "http://www.w3.org/2005/08/addressing/anonymous" Jeśli punkt końcowy używa 1.x HTTP powiązania WSDL 1.1 SOAP i ma stanowi alternatywę zasad z `wsap:UsingAddressing` potwierdzenia i nie `cdp:CompositeDuplex` potwierdzenia dołączony.</span><span class="sxs-lookup"><span data-stu-id="f84b6-304">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="f84b6-305">Specyfikacja WS-addressing WSDL próbuje opisano podobnymi powiązaniami protokołu, wprowadzając element `<wsaw:Anonymous/>` z trzech wartości tekstowej (wymagane, opcjonalne i zabronionych) wskazująca wymagania na `wsa:ReplyTo` nagłówka (sekcji 3.2).</span><span class="sxs-lookup"><span data-stu-id="f84b6-305">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="f84b6-306">Niestety taka definicja elementu nie jest szczególnie użyteczne jako potwierdzenia w ramach usługi WS-Policy, ponieważ wymaga rozszerzenia specyficznego dla domeny do obsługi przecięcie alternatyw za pomocą takiego elementu jako potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="f84b6-306">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="f84b6-307">Wartość wskazuje także takie definicji elementu `ReplyTo` nagłówka, w przeciwieństwie do zachowania punktu końcowego przesyłania, dzięki czemu określonego transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-307">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="f84b6-308">Definicja akcji</span><span class="sxs-lookup"><span data-stu-id="f84b6-308">Action Definition</span></span>  
 <span data-ttu-id="f84b6-309">Definiuje WS-Addressing 2004/08 `wsa:Action` atrybutu dla `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementów.</span><span class="sxs-lookup"><span data-stu-id="f84b6-309">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="f84b6-310">WS-Addressing powiązania WSDL 1.0 (WS-ADDR10 WSDL) definiuje atrybut podobne `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-310">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="f84b6-311">Jedyną różnicą między tymi dwoma jest opisanych w 3.3.2 WS-ADDR i sekcji 4.4.4 WS-ADDR10-WSDL, odpowiednio semantykę wzorzec domyślnej akcji.</span><span class="sxs-lookup"><span data-stu-id="f84b6-311">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="f84b6-312">Jest uzasadnione ma dwa punkty końcowe, które mają taki sam `portType` (lub umowy, w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminologii), ale przy użyciu różnych wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f84b6-312">It is a reasonable to have two endpoints that share the same `portType` (or contract, in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="f84b6-313">Ale biorąc pod uwagę, że akcja jest definiowana za pomocą `portType` i nie należy zmieniać w obrębie punktów końcowych, które implementują `portType`, staje się niemożliwe do obsługi oba wzorce akcji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="f84b6-313">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="f84b6-314">Aby rozwiązać ten rozbieżność [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje jednej wersji `Action` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-314">To resolve this controversy, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="f84b6-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa `wsaw10:Action` atrybutu `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy zgodnie z definicją w WS ADDR10 WSDL ustalenie `Action` identyfikator URI dla odpowiednich komunikatów niezależnie od wersji WS-Addressing używany przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f84b6-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="f84b6-316">Punkt końcowy odwołanie wewnątrz WSDL portów</span><span class="sxs-lookup"><span data-stu-id="f84b6-316">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="f84b6-317">Rozszerza WS ADDR10 WSDL sekcji 4.1 `wsdl:port` element, aby uwzględnić `<wsa10:EndpointReference…/>` elementu podrzędnego do opisywania punktu końcowego usługi WS-Addressing warunków.</span><span class="sxs-lookup"><span data-stu-id="f84b6-317">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-318">rozwija tego narzędzia na WS-Addressing 2004/08, umożliwiając `<wsa:EndpointReference…/>` były wyświetlane jako elementu podrzędnego `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-318"> expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="f84b6-319">R3531: Jeśli punkt końcowy ma zamiast dołączonych zasad z `<wsaw10:UsingAddressing/>` potwierdzenia zasad, odpowiadającego `wsdl:port` element może zawierać elementu podrzędnego `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-319">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="f84b6-320">R3532: Jeśli `wsdl:port` zawiera element podrzędny `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` wartość elementu podrzędnego musi być zgodna z wartością `@address` atrybutu elementu równorzędnego `wsdl:port` / `wsdl:location` elementu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-320">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="f84b6-321">R3533: Jeśli punkt końcowy ma zamiast dołączonych zasad z `<wsap:UsingAddressing/>` potwierdzenia zasad, odpowiadającego `wsdl:port` element może zawierać elementu podrzędnego `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-321">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="f84b6-322">R3534: Jeśli `wsdl:port` zawiera element podrzędny `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` wartość elementu podrzędnego musi być zgodna z wartością `@address` atrybutu elementu równorzędnego `wsdl:port` / `wsdl:location` elementu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-322">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="f84b6-323">Kompozycja z zabezpieczenia WS</span><span class="sxs-lookup"><span data-stu-id="f84b6-323">Composition with WS-Security</span></span>  
 <span data-ttu-id="f84b6-324">Zgodnie z zabezpieczeń sekcje brany pod uwagę WS-ADDR i WS-ADDR10 zaleca się wszystkie nagłówki komunikatów adresowania podpisywane wraz z treści wiadomości powiązać je razem.</span><span class="sxs-lookup"><span data-stu-id="f84b6-324">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="f84b6-325">Gdy WS-Security jest używany na potrzeby ochrony integralności komunikatu, WS-Addressing wiadomości nagłówków, a także nagłówki wynika z parametrów odwołania (i właściwości) muszą być podpisane wraz z treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f84b6-325">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="f84b6-326">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f84b6-326">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="f84b6-327">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="f84b6-327">One-Way Message</span></span>  
 <span data-ttu-id="f84b6-328">W tym scenariuszu nadawca wysyła komunikat jednokierunkowy do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="f84b6-328">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="f84b6-329">Są używane SOAP 1.2, protokołu HTTP 1.1 i 1.0 W3C WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f84b6-329">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="f84b6-330">Struktura komunikatu żądania: Nagłówki komunikatów obejmują `wsa10:To` i `wsa10:Action` elementy.</span><span class="sxs-lookup"><span data-stu-id="f84b6-330">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="f84b6-331">Treść wiadomości zawiera określony `<app:Ping>` element z przestrzeni nazw aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f84b6-331">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="f84b6-332">Nagłówki HTTP: Odpowiada docelowego w POST identyfikator URI w `wsa10:To` elementu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-332">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="f84b6-333">Nagłówek Content-Type ma wartość `application/soap+xml` zgodnie z żądaniem protokołu SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="f84b6-333">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="f84b6-334">Parametry `charset` i `action` są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="f84b6-334">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="f84b6-335">`action` Parametr nagłówka Content-Type jest zgodna z wartością elementu `wsa10:Action` nagłówka wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f84b6-335">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
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
  
 <span data-ttu-id="f84b6-336">Odbiornik odpowiada pustą odpowiedź HTTP i stan 202.</span><span class="sxs-lookup"><span data-stu-id="f84b6-336">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="f84b6-337">Przykład odpowiedzi HTTP:</span><span class="sxs-lookup"><span data-stu-id="f84b6-337">An example of the HTTP response:</span></span>  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="f84b6-338">Mechanizmu optymalizacji transmisji wiadomości SOAP</span><span class="sxs-lookup"><span data-stu-id="f84b6-338">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="f84b6-339">W tej sekcji opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji MTOM SOAP protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-339">This section describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="f84b6-340">Technologia MTOM jest mechanizm kodowania wiadomości SOAP do tej samej klasy jako kodowania tradycyjnych tekstu/XML lub [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodowania binarnego.</span><span class="sxs-lookup"><span data-stu-id="f84b6-340">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary encoding.</span></span> <span data-ttu-id="f84b6-341">MTOM obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="f84b6-341">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="f84b6-342">Kodowanie XML i mechanizmu pakowania opisanego przez [XOP] który optymalizuje elementów informacji XML zawierający dane binarne algorytmem base64 na oddzielnych części binarnej.</span><span class="sxs-lookup"><span data-stu-id="f84b6-342">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="f84b6-343">Hermetyzacja protokołu MIME pakietu XOP, który serializuje XML typu infoset sprawdzonych i każdej części binarnej pakietu XOP w oddzielnych części MIME.</span><span class="sxs-lookup"><span data-stu-id="f84b6-343">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="f84b6-344">MIME XOP kodowanie stosowane do SOAP 1.x koperty.</span><span class="sxs-lookup"><span data-stu-id="f84b6-344">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="f84b6-345">HTTP powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-345">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="f84b6-346">Istnieje możliwość MTOM za pomocą transportu innego niż HTTP z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f84b6-346">It is possible to use MTOM with non-HTTP transports with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="f84b6-347">Jednak w tym temacie firma Microsoft koncentruje się na HTTP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-347">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="f84b6-348">MTOM format wykorzystuje dużego zestawu specyfikacji obejmujące MTOM samego, XOP i MIME.</span><span class="sxs-lookup"><span data-stu-id="f84b6-348">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="f84b6-349">Modułowość tego zestawu specyfikacji utrudnia nieco rekonstrukcji dokładnych wymaganiach na format i przetwarzania semantyki.</span><span class="sxs-lookup"><span data-stu-id="f84b6-349">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="f84b6-350">W tej sekcji opisano wymagania formatu i przetwarzania dla wiązania MTOM HTTP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-350">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="f84b6-351">Kodowanie komunikatu MTOM</span><span class="sxs-lookup"><span data-stu-id="f84b6-351">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="f84b6-352">Komunikaty mechanizmu MTOM generowania</span><span class="sxs-lookup"><span data-stu-id="f84b6-352">Generating MTOM messages</span></span>  
 <span data-ttu-id="f84b6-353">[XOP] 3.1 sekcji opisano proces kodowania XML z elementu informacji elementów, które zawierają wartości base64 w zdefiniowanych abstrakcyjnie pakiet XOP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-353">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="f84b6-354">Następująca sekwencja kroków opisano proces kodowania MTOM specyficzne:</span><span class="sxs-lookup"><span data-stu-id="f84b6-354">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="f84b6-355">Sprawdź, czy koperty protokołu SOAP ma być zdekodowany, zawiera żadnego elementu elementu informacji z `[namespace name]` z "http://www.w3.org/2004/08/xop/include" i `[local name]` z `Include`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-355">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="f84b6-356">Utwórz pusty pakiet MIME.</span><span class="sxs-lookup"><span data-stu-id="f84b6-356">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="f84b6-357">Zidentyfikuj w oryginalnym XML typu infoset sprawdzonych elementów informacji elementu Optymalizacja.</span><span class="sxs-lookup"><span data-stu-id="f84b6-357">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="f84b6-358">Dla elementów Optymalizacja znaki które tworzą `[children]` informacje o elementach elementu musi być w formie kanonicznej `xs:base64Binary` (zobacz XSD-2, 3.2.16 base64Binary) i nie może zawierać białych znaków poprzedzających wbudowany, lub po zawartości odstępem.</span><span class="sxs-lookup"><span data-stu-id="f84b6-358">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any whitespace characters preceding, inline with, or following the non-whitespace content.</span></span>  
  
4.  <span data-ttu-id="f84b6-359">Utwórz XOP koperty protokołu SOAP, który jest kopią oryginalnego koperty protokołu SOAP, ale z elementów informacje o poszczególnych elementach podrzędnych elementu w poprzednim kroku zastępuje `xop:Include` elementu informacji elementu następującą postać:</span><span class="sxs-lookup"><span data-stu-id="f84b6-359">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="f84b6-360">Przekształć zastąpionego znaków w danych binarnych przez przetwarzanie je jako dane zakodowane w formacie base64.</span><span class="sxs-lookup"><span data-stu-id="f84b6-360">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="f84b6-361">Generuj unikatowy wartość nagłówka Content-ID, który spełnia wymagania R3133 i R3134.</span><span class="sxs-lookup"><span data-stu-id="f84b6-361">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="f84b6-362">Wygeneruj nagłówek MIME Content-Transfer-Encoding o wartości binarnej.</span><span class="sxs-lookup"><span data-stu-id="f84b6-362">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="f84b6-363">Jeśli element elementu informacje są optymalizowane ([nadrzędny] nowo wstawionej `xop:Include` elementu informacji element) ma `xmime:contentType` atrybutu elementu informacji, wygeneruj nagłówek MIME Content-Type o wartości `xmime:contentType` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-363">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="f84b6-364">Generowanie nowej części MIME binarnego z zawartością utworzone przez dane binarne odczytany z zastąpionego znaki przetwarzane jako base64, nagłówek Content-ID z 4b, nagłówek Content-Transfer-Encoding z 4c nagłówka Content-Type, jeśli generowany w kroku 4d.</span><span class="sxs-lookup"><span data-stu-id="f84b6-364">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="f84b6-365">Dodaj `href` atrybutu `xop:Include` elementu o wartości cid: identyfikator uri pochodzące z wartość nagłówka Content-ID wygenerowany w kroku 4b.</span><span class="sxs-lookup"><span data-stu-id="f84b6-365">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="f84b6-366">Usuń otaczający "\<" i ">" znaki ucieczki adresu URL pozostałe ciąg i Dodaj prefiks `cid:`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-366">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="f84b6-367">Następujący zestaw znaków minimalna jest wymagany do ucieczkę można zastosować RFC1738 i specyfikacja RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="f84b6-367">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="f84b6-368">Można użyć znaków ucieczki innych znaków.</span><span class="sxs-lookup"><span data-stu-id="f84b6-368">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="f84b6-369">Utwórz głównej części MIME o XOP koperty protokołu SOAP z kroku 4.</span><span class="sxs-lookup"><span data-stu-id="f84b6-369">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="f84b6-370">Zapisać nagłówków HTTP, w tym nagłówka HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="f84b6-370">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="f84b6-371">Należy zapisać pakiet MIME.</span><span class="sxs-lookup"><span data-stu-id="f84b6-371">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="f84b6-372">Komunikaty mechanizmu MTOM przetwarzania</span><span class="sxs-lookup"><span data-stu-id="f84b6-372">Processing MTOM messages</span></span>  
 <span data-ttu-id="f84b6-373">Przetwarzanie MTOM wiadomość jest dokładną odwrotnością proces opisany w poprzednim "Generowanie MTOM wiadomości" sekcji:</span><span class="sxs-lookup"><span data-stu-id="f84b6-373">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="f84b6-374">Upewnij się, głównej części MIME ma typ zawartości `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-374">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="f84b6-375">Konstruować koperty protokołu SOAP, analizując głównej części MIME pakietu jako dokument XML.</span><span class="sxs-lookup"><span data-stu-id="f84b6-375">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="f84b6-376">Kodowanie znaków jest określany przez `charset` parametru Content-Type dla głównej części MIME.</span><span class="sxs-lookup"><span data-stu-id="f84b6-376">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="f84b6-377">Dla każdego elementu informacji elementu skonstruowane koperty protokołu SOAP, który ma, jedynym członkiem właściwości [dzieci] `xop:Include` elementu informacji elementu:</span><span class="sxs-lookup"><span data-stu-id="f84b6-377">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="f84b6-378">Usuń `cid:` prefiks i unescape wszystkie sekwencje ucieczki identyfikatora URI (RFC 2396) w wartości `@href` atrybutu `xop:Include` elementu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-378">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="f84b6-379">Umieść ciąg wyniku w "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="f84b6-379">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="f84b6-380">Znajdź części MIME o pasującej do ciągu uzyskane w kroku 3a wartość nagłówka Content-ID.</span><span class="sxs-lookup"><span data-stu-id="f84b6-380">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="f84b6-381">Zastąp `xop:Include` element informacji elementu z `children` właściwości każdego elementu z elementami informacji znak reprezentujących kodowania base64 kanoniczny (zobacz XSD-2, 3.2.16 base64Binary) z treści jednostki części MIME zidentyfikowany w kroku 3b (skutecznie zastępują `xop:Include` elementu element informacji o danych odtworzone z części pakietu).</span><span class="sxs-lookup"><span data-stu-id="f84b6-381">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="f84b6-382">Nagłówek Content-Type protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="f84b6-382">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="f84b6-383">Poniżej przedstawiono listę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wyjaśnienia formatu nagłówka HTTP Content-Type komunikatu MTOM zakodowane w formacie 1.x SOAP pochodzi od wymagania określone w specyfikacji MTOM sam i pochodne MTOM i dokument RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="f84b6-383">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="f84b6-384">R4131: Nagłówek HTTP Content-Type musi mieć wartość multipart/powiązane (bez uwzględniania wielkości liter) i jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="f84b6-384">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="f84b6-385">Nazwa parametru jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="f84b6-385">Parameter names are case-insensitive.</span></span> <span data-ttu-id="f84b6-386">Kolejność parametrów nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="f84b6-386">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="f84b6-387">Pełna formularz Backus-Naur formularza (BNF) nagłówka Content-Type dla wiadomości MIME ma na liście 2045 RFC, sekcji 5.1.</span><span class="sxs-lookup"><span data-stu-id="f84b6-387">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="f84b6-388">R4132: Nagłówek HTTP Content-Type musi mieć parametr typu o wartości `application/xop+xml` ujęta w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-388">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="f84b6-389">Podczas wymaganie, aby użyć podwójnego cudzysłowu nie jest jawną w dokumencie RFC 2387, tekst przestrzega, że wszystkie typu multipart/związane z nośnika, najprawdopodobniej parametrów zawiera zarezerwowanych znaków, takich jak "@" or "/" i w związku z tym należy podwójnych cudzysłowów prostych.</span><span class="sxs-lookup"><span data-stu-id="f84b6-389">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="f84b6-390">R4133: Nagłówek HTTP Content-Type musi mieć parametr start o wartości nagłówka Identyfikatora zawartości części MIME, który zawiera SOAP 1.x koperty ujęta w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-390">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="f84b6-391">W przypadku pominięcia początkowa pierwsza część MIME musi zawierać SOAP 1.x koperty.</span><span class="sxs-lookup"><span data-stu-id="f84b6-391">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="f84b6-392">R4134: Nagłówek HTTP Content-Type dla komunikatu SOAP 1.1 MTOM zakodowane musi zawierać informacje o uruchomieniu parametru z wartością tekstu/xml, ujęta w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="f84b6-392">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="f84b6-393">R4135: Nagłówka HTTP Content-Type komunikatu kodowany w formacie protokołu SOAP 1.2 MTOM muszą zawierać informacje o uruchomieniu parametru z wartością `application/soap+xml`, ujęty w podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="f84b6-393">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="f84b6-394">R4136: Nagłówek HTTP Content-Type dla komunikatu MTOM zakodowane w formacie 1.x SOAP musi mieć parametr granic o wartości (ujęta w znaki podwójnego cudzysłowu) odpowiadający granicą MIME, zdefiniowanych w specyfikacji RFC 2046 sekcji 5.1.1 BNF</span><span class="sxs-lookup"><span data-stu-id="f84b6-394">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="f84b6-395">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="f84b6-395">Examples:</span></span>  
  
     <span data-ttu-id="f84b6-396">POPRAW</span><span class="sxs-lookup"><span data-stu-id="f84b6-396">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="f84b6-397">POPRAW</span><span class="sxs-lookup"><span data-stu-id="f84b6-397">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="f84b6-398">NIEPOPRAWNE</span><span class="sxs-lookup"><span data-stu-id="f84b6-398">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="f84b6-399">Obiekt typu infoset części MIME</span><span class="sxs-lookup"><span data-stu-id="f84b6-399">Infoset MIME Part</span></span>  
 <span data-ttu-id="f84b6-400">SOAP 1.x koperty jest hermetyzowany jako część pakietu XOP MIME głównym i jest często nazywana `infoset` części.</span><span class="sxs-lookup"><span data-stu-id="f84b6-400">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="f84b6-401">R4141: SOAP 1.x koperty musi hermetyzowany jako część pakietu XOP MIME o nazwie głównego `infoset` należą i do którego istnieje odwołanie z HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="f84b6-401">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="f84b6-402">R4142: SOAP `Infoset` części musi zawierać następujące nagłówki MIME: `Content-ID`, `Content-Transfer-Encoding`, i `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-402">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="f84b6-403">Format nagłówka Content-ID jest zdefiniowany w dokumencie RFC 2045 jako</span><span class="sxs-lookup"><span data-stu-id="f84b6-403">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="f84b6-404">gdzie `msg-id` jest zdefiniowana w dokumencie RFC 2822, (zastępującym RFC 822, do którego odwołuje się RFC 2045) jako:</span><span class="sxs-lookup"><span data-stu-id="f84b6-404">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="f84b6-405">i jest efektywne adresu e-mail ujętą w nawiasy klamrowe "\<" i ">".</span><span class="sxs-lookup"><span data-stu-id="f84b6-405">and is effectively an e-mail address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="f84b6-406">`[CFWS]` Prefiksu i sufiksu dodano RFC 2822 do przenoszenia komentarze i nie powinna być używana w celu zachowania współdziałania.</span><span class="sxs-lookup"><span data-stu-id="f84b6-406">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="f84b6-407">R4143: Wartość nagłówka Content-ID części MIME typu Infoset wykonaj `msg-id` produkcyjnych z RFC 2822 z `[CFWS]` części prefiksu i sufiksu pominięty.</span><span class="sxs-lookup"><span data-stu-id="f84b6-407">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="f84b6-408">Liczba wdrożeń MIME rozluźnić, wymagania dotyczące wartości ujętych w nawiasy klamrowe "\<" i ">" jako adres e-mail i użyć `absoluteURI` ujęta w "\<", ">" oprócz adresu e-mail.</span><span class="sxs-lookup"><span data-stu-id="f84b6-408">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an e-mail address and used `absoluteURI` enclosed in "\<" , ">" in addition to the e-mail address.</span></span> <span data-ttu-id="f84b6-409">Ta wersja [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa wartości nagłówek MIME Content-ID w postaci:</span><span class="sxs-lookup"><span data-stu-id="f84b6-409">This version of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="f84b6-410">R4144: Procesorów MTOM powinna obsługiwać zgodnych rozluźnić, poniżej wartości nagłówka Content-ID `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-410">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="f84b6-411">MIME (RFC 2045) zawiera nagłówek Content-Transfer-Encoding do komunikacji, kodowania zawartości części MIME.</span><span class="sxs-lookup"><span data-stu-id="f84b6-411">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="f84b6-412">Domyślnie zdefiniowane dla Content-Transfer-Encoding jest 7-bitowym, który nie jest odpowiedni dla większości wiadomości SOAP, więc nagłówka Content-Transfer-Encoding jest potrzebny większy współdziałania:</span><span class="sxs-lookup"><span data-stu-id="f84b6-412">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="f84b6-413">R4145: Część obiektu typu Infoset SOAP musi zawierać nagłówek Content-Transfer-Encoding.</span><span class="sxs-lookup"><span data-stu-id="f84b6-413">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="f84b6-414">R4146: W przypadku koperty protokołu SOAP kodowania znaków UTF-8, wartość nagłówka Content-Transfer-Encoding musi być 8-bitową.</span><span class="sxs-lookup"><span data-stu-id="f84b6-414">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="f84b6-415">R4147: W przypadku koperty protokołu SOAP kodowania znaków UTF-16, wartość nagłówka Content-Transfer-Encoding musi być binarny.</span><span class="sxs-lookup"><span data-stu-id="f84b6-415">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="f84b6-416">Zgodnie z [XOP] sekcji 5,</span><span class="sxs-lookup"><span data-stu-id="f84b6-416">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="f84b6-417">R4148: Część obiektu typu Infoset SOAP1.1 musi zawierać nagłówek Content-Type o typ nośnika application/xop + xml i parametry typu = "text/xml" i zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="f84b6-417">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="f84b6-418">R4149: Część obiektu typu Infoset SOAP 1.2 musi zawierać nagłówek Content-Type z typem nośnika `application/xop+xml` i parametry type = "`application/soap+xml`" i `charset`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-418">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="f84b6-419">Gdy definiuje XOP `charset` parametr `application/xop+xml` jako opcjonalną, wymagana jest podobne do wymagań BP 1.1 na współdziałanie `charset` parametr `text/xml` typu nośnika.</span><span class="sxs-lookup"><span data-stu-id="f84b6-419">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="f84b6-420">R41410: `type` i `charset` parametry muszą być obecne w nagłówku Content-Type części typu Infoset 1.x protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f84b6-420">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="f84b6-421">Obsługa punktu końcowego WCF MTOM</span><span class="sxs-lookup"><span data-stu-id="f84b6-421">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="f84b6-422">MTOM ma na celu kodowania komunikatu protokołu SOAP, aby zoptymalizować dane zakodowane w formacie base64.</span><span class="sxs-lookup"><span data-stu-id="f84b6-422">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="f84b6-423">Poniżej znajduje się lista warunków ograniczających:</span><span class="sxs-lookup"><span data-stu-id="f84b6-423">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="f84b6-424">R4151: Może zostać zoptymalizowany dowolny element informacji elementu zawierającego dane zakodowane w formacie base64.</span><span class="sxs-lookup"><span data-stu-id="f84b6-424">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="f84b6-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optymalizuje element informacji elementy, które zawierają dane zakodowane w formacie base64 i przekracza 1024 bajtów długości.</span><span class="sxs-lookup"><span data-stu-id="f84b6-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="f84b6-426">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punkt końcowy jest skonfigurowana do używania MTOM zawsze będzie wysyłać wiadomości w formacie MTOM.</span><span class="sxs-lookup"><span data-stu-id="f84b6-426">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="f84b6-427">Nawet jeśli żadne części spełniają kryteria wymagane, wiadomość jest nadal MTOM kodowany w formacie (serializowany jako pakiet MIME z jednej części MIME zawierającej koperty protokołu SOAP).</span><span class="sxs-lookup"><span data-stu-id="f84b6-427">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="f84b6-428">Potwierdzenie WS-Policy dla MTOM</span><span class="sxs-lookup"><span data-stu-id="f84b6-428">WS-Policy Assertion for MTOM</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f84b6-429">używa następujących potwierdzenia zasad w celu wskazania MTOM użycia przez punkt końcowy:</span><span class="sxs-lookup"><span data-stu-id="f84b6-429"> uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="f84b6-430">R4211: Poprzedniego potwierdzenia zasad ma temat zasady punktu końcowego i określa, że wszystkie wiadomości wysyłane do i odbierane z punktu końcowego musi być zoptymalizowany przy użyciu mechanizmu MTOM.</span><span class="sxs-lookup"><span data-stu-id="f84b6-430">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="f84b6-431">B4212: Podczas konfigurowania używania optymalizacji MTOM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego dodaje potwierdzenia zasad MTOM do zasady dołączone do odpowiedniej `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="f84b6-431">B4212: When configured to use MTOM optimization, an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="f84b6-432">Kompozycja z zabezpieczenia WS</span><span class="sxs-lookup"><span data-stu-id="f84b6-432">Composition with WS-Security</span></span>  
 <span data-ttu-id="f84b6-433">MTOM jest mechanizmem kodowania, która jest podobna do `text/xml` i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binarny XML.</span><span class="sxs-lookup"><span data-stu-id="f84b6-433">MTOM is an encoding mechanism that is similar to `text/xml` and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary XML.</span></span> <span data-ttu-id="f84b6-434">MTOM oferuje fizycznych kompozycji WS-Security i inne usługi WS-* protokoły: wiadomości uwierzytelnionej za pomocą usługi WS-Security mogą być optymalizowane za pomocą mechanizmu MTOM.</span><span class="sxs-lookup"><span data-stu-id="f84b6-434">MTOM offers natural composition with WS-Security and other WS-* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="f84b6-435">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f84b6-435">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="f84b6-436">Usługi WCF SOAP 1.1 komunikat zakodowane przy użyciu mechanizmu MTOM</span><span class="sxs-lookup"><span data-stu-id="f84b6-436">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="f84b6-437">Usługi WCF bezpiecznego protokołu SOAP 1.2 komunikat zakodowane przy użyciu mechanizmu MTOM</span><span class="sxs-lookup"><span data-stu-id="f84b6-437">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="f84b6-438">W tym przykładzie wiadomość jest zakodowany przy użyciu mechanizmu MTOM i SOAP 1.2, która jest chroniona za pomocą usługi WS-Security.</span><span class="sxs-lookup"><span data-stu-id="f84b6-438">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="f84b6-439">Części binarnej zidentyfikowane dla kodowania zawartości `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpowiedniego podpisu zaszyfrowanego i zaszyfrowanej treści.</span><span class="sxs-lookup"><span data-stu-id="f84b6-439">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="f84b6-440">Należy pamiętać, że `CipherValue` z `EncryptedKey` nie została zidentyfikowana optymalizacji przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ponieważ jego długość jest mniej następnie 1024 bajty.</span><span class="sxs-lookup"><span data-stu-id="f84b6-440">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because its length is less then 1024 bytes.</span></span>  
  
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
