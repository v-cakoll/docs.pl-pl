---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 7869737f1e3d8c7a9ba569991ead6f7f759e6c58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616891"
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="7b84f-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7b84f-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="7b84f-103">Bezpieczne i interoperacyjne powiązanie pochodzi od klasy [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i obsługuje federacyjnego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="7b84f-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="7b84f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b84f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b84f-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="7b84f-105">\<bindings></span></span>  
<span data-ttu-id="7b84f-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7b84f-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b84f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b84f-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b84f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7b84f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7b84f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7b84f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b84f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7b84f-110">Attributes</span></span>  
  
|<span data-ttu-id="7b84f-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7b84f-111">Attribute</span></span>|<span data-ttu-id="7b84f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7b84f-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="7b84f-113">Wartość, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="7b84f-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="7b84f-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="7b84f-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="7b84f-115">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="7b84f-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7b84f-116">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7b84f-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b84f-117">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7b84f-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="7b84f-118">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="7b84f-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="7b84f-119">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="7b84f-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="7b84f-120">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="7b84f-121">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="7b84f-122">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="7b84f-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="7b84f-123">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="7b84f-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="7b84f-124">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="7b84f-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="7b84f-125">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="7b84f-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="7b84f-126">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="7b84f-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="7b84f-127">Maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="7b84f-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7b84f-128">Nadawca wiadomości, która przekracza ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7b84f-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="7b84f-129">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7b84f-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7b84f-130">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="7b84f-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="7b84f-131">Definiuje encoder umożliwia kodowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7b84f-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="7b84f-132">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="7b84f-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7b84f-133">-Tekst: Za pomocą kodera komunikatów tekstu.</span><span class="sxs-lookup"><span data-stu-id="7b84f-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="7b84f-134">-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="7b84f-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="7b84f-135">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="7b84f-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="7b84f-136">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="7b84f-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="7b84f-137">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-137">The configuration name of the binding.</span></span> <span data-ttu-id="7b84f-138">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7b84f-139">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="7b84f-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7b84f-140">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7b84f-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7b84f-141">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="7b84f-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7b84f-142">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7b84f-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b84f-143">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7b84f-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="7b84f-144">Identyfikator URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="7b84f-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="7b84f-145">Wersja bieżąca powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="7b84f-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="7b84f-146">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="7b84f-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="7b84f-147">Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="7b84f-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="7b84f-148">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="7b84f-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7b84f-149">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7b84f-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7b84f-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b84f-151">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="7b84f-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7b84f-152">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7b84f-153">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7b84f-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b84f-154">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7b84f-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="7b84f-155">Określa kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="7b84f-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7b84f-156">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="7b84f-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7b84f-157">-BigEndianUnicode: Big Endian kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="7b84f-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="7b84f-158">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="7b84f-159">-   UTF8: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="7b84f-160">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="7b84f-160">The default is UTF8.</span></span> <span data-ttu-id="7b84f-161">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="7b84f-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="7b84f-162">Wartość, która określa, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="7b84f-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="7b84f-163">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="7b84f-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="7b84f-164">Wartość, która wskazuje, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="7b84f-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="7b84f-165">Adres serwera proxy musi być `null` (czyli nie ustawiono) Jeśli ten atrybut jest `true`.</span><span class="sxs-lookup"><span data-stu-id="7b84f-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="7b84f-166">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="7b84f-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b84f-167">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7b84f-167">Child Elements</span></span>  
  
|<span data-ttu-id="7b84f-168">Element</span><span class="sxs-lookup"><span data-stu-id="7b84f-168">Element</span></span>|<span data-ttu-id="7b84f-169">Opis</span><span class="sxs-lookup"><span data-stu-id="7b84f-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b84f-170">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="7b84f-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="7b84f-171">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7b84f-171">Defines the security settings for the message.</span></span> <span data-ttu-id="7b84f-172">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7b84f-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="7b84f-173">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="7b84f-173">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="7b84f-174">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="7b84f-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7b84f-175">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7b84f-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="7b84f-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="7b84f-176">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="7b84f-177">Określa, czy niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="7b84f-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b84f-178">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7b84f-178">Parent Elements</span></span>  
  
|<span data-ttu-id="7b84f-179">Element</span><span class="sxs-lookup"><span data-stu-id="7b84f-179">Element</span></span>|<span data-ttu-id="7b84f-180">Opis</span><span class="sxs-lookup"><span data-stu-id="7b84f-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b84f-181">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="7b84f-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7b84f-182">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7b84f-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b84f-183">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b84f-183">Remarks</span></span>  
 <span data-ttu-id="7b84f-184">Federacja znajduje się możliwość udostępniania tożsamości w wielu przedsiębiorstwach lub zaufania domen do uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="7b84f-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="7b84f-185">Używa protokołu WS-Trust do mapowania reprezentacji tożsamości z jednej relacji zaufania domeny do innego.</span><span class="sxs-lookup"><span data-stu-id="7b84f-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="7b84f-186">Federacyjnego powiązania HTTP obsługuje zabezpieczenia protokołu SOAP, a także trybu mieszanego zabezpieczeń, ale nie obsługuje zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="7b84f-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="7b84f-187">Skonfigurowano z tym powiązaniem usług, należy użyć protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7b84f-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="7b84f-188">Aby uzyskać więcej informacji, zobacz [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7b84f-188">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b84f-189">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b84f-189">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="7b84f-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b84f-190">See also</span></span>
- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="7b84f-191">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7b84f-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)
- [<span data-ttu-id="7b84f-192">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7b84f-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7b84f-193">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="7b84f-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7b84f-194">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7b84f-194">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7b84f-195">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="7b84f-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
