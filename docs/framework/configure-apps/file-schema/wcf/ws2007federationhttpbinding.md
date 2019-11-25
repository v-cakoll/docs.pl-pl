---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 20ba643fddbac8a488e5457f0195cc253d4d23f7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139313"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="881c9-101">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="881c9-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="881c9-102">Bezpieczne i interoperacyjne powiązanie, które wynikają z [\<wsFederationHttpBinding >](wsfederationhttpbinding.md) i obsługuje zabezpieczenia federacyjne.</span><span class="sxs-lookup"><span data-stu-id="881c9-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

<span data-ttu-id="881c9-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="881c9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="881c9-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="881c9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="881c9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="881c9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="881c9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007FederationHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="881c9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="881c9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="881c9-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="881c9-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="881c9-108">Attributes and Elements</span></span>

<span data-ttu-id="881c9-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="881c9-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="881c9-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="881c9-110">Attributes</span></span>

|<span data-ttu-id="881c9-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="881c9-111">Attribute</span></span>|<span data-ttu-id="881c9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="881c9-112">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="881c9-113">Wartość wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="881c9-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="881c9-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="881c9-114">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="881c9-115">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="881c9-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="881c9-116">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="881c9-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="881c9-117">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="881c9-117">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="881c9-118">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="881c9-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="881c9-119">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="881c9-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="881c9-120">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="881c9-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="881c9-121">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="881c9-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="881c9-122">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="881c9-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="881c9-123">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="881c9-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="881c9-124">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="881c9-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="881c9-125">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="881c9-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="881c9-126">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="881c9-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="881c9-127">Maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które można odbierać w kanale skonfigurowanym za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="881c9-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="881c9-128">Nadawca komunikatu, który przekracza ten limit, odbiera błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="881c9-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="881c9-129">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="881c9-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="881c9-130">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="881c9-130">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="881c9-131">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="881c9-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="881c9-132">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="881c9-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="881c9-133">-Text: Użyj kodera wiadomości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="881c9-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="881c9-134">-MTOM: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="881c9-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="881c9-135">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="881c9-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="881c9-136">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="881c9-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="881c9-137">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="881c9-137">The configuration name of the binding.</span></span> <span data-ttu-id="881c9-138">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="881c9-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="881c9-139">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="881c9-139">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="881c9-140">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="881c9-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="881c9-141">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="881c9-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="881c9-142">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="881c9-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="881c9-143">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="881c9-143">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="881c9-144">Identyfikator URI, w którym znajduje się powiadomienie dotyczące zachowania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="881c9-144">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="881c9-145">Wersja bieżącego powiadomienia o ochronie prywatności.</span><span class="sxs-lookup"><span data-stu-id="881c9-145">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="881c9-146">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="881c9-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="881c9-147">Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="881c9-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="881c9-148">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="881c9-148">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="881c9-149">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="881c9-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="881c9-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="881c9-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="881c9-151">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="881c9-151">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="881c9-152">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="881c9-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="881c9-153">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="881c9-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="881c9-154">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="881c9-154">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="881c9-155">Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="881c9-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="881c9-156">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="881c9-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="881c9-157">-BigEndianUnicode: kodowanie Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="881c9-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="881c9-158">-Unicode: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="881c9-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="881c9-159">-UTF8: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="881c9-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="881c9-160">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="881c9-160">The default is UTF8.</span></span> <span data-ttu-id="881c9-161">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="881c9-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="881c9-162">Wartość określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="881c9-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="881c9-163">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="881c9-163">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="881c9-164">Wartość wskazująca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="881c9-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="881c9-165">Jeśli ten atrybut jest `true`, adres serwera proxy musi być `null` (to nie jest ustawione).</span><span class="sxs-lookup"><span data-stu-id="881c9-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="881c9-166">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="881c9-166">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="881c9-167">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="881c9-167">Child Elements</span></span>

|<span data-ttu-id="881c9-168">Element</span><span class="sxs-lookup"><span data-stu-id="881c9-168">Element</span></span>|<span data-ttu-id="881c9-169">Opis</span><span class="sxs-lookup"><span data-stu-id="881c9-169">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="881c9-170">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="881c9-170">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="881c9-171">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="881c9-171">Defines the security settings for the message.</span></span> <span data-ttu-id="881c9-172">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="881c9-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="881c9-173">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="881c9-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="881c9-174">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="881c9-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="881c9-175">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="881c9-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="881c9-176">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="881c9-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="881c9-177">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="881c9-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="881c9-178">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="881c9-178">Parent Elements</span></span>

|<span data-ttu-id="881c9-179">Element</span><span class="sxs-lookup"><span data-stu-id="881c9-179">Element</span></span>|<span data-ttu-id="881c9-180">Opis</span><span class="sxs-lookup"><span data-stu-id="881c9-180">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="881c9-181">> powiązań\<</span><span class="sxs-lookup"><span data-stu-id="881c9-181">\<bindings></span></span>](bindings.md)|<span data-ttu-id="881c9-182">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="881c9-182">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="881c9-183">Uwagi</span><span class="sxs-lookup"><span data-stu-id="881c9-183">Remarks</span></span>

<span data-ttu-id="881c9-184">Federacja jest możliwością udostępniania tożsamości w wielu przedsiębiorstwach lub domenach zaufania na potrzeby uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="881c9-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="881c9-185">Używa protokołu WS-Trust, aby zamapować reprezentację tożsamości z jednej domeny zaufania na inną.</span><span class="sxs-lookup"><span data-stu-id="881c9-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="881c9-186">Federacyjne powiązanie HTTP obsługuje zabezpieczenia protokołu SOAP oraz zabezpieczenia w trybie mieszanym, ale nie obsługuje zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="881c9-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="881c9-187">Usługi skonfigurowane przy użyciu tego powiązania muszą korzystać z transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="881c9-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="881c9-188">Aby uzyskać więcej informacji, zobacz [\<wsFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="881c9-188">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="881c9-189">Przykład</span><span class="sxs-lookup"><span data-stu-id="881c9-189">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="881c9-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="881c9-190">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="881c9-191">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="881c9-191">\<wsFederationHttpBinding></span></span>](wsfederationhttpbinding.md)
- [<span data-ttu-id="881c9-192">Powiązania</span><span class="sxs-lookup"><span data-stu-id="881c9-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="881c9-193">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="881c9-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="881c9-194">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="881c9-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="881c9-195">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="881c9-195">\<binding></span></span>](bindings.md)
