---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: df5e44a0744c08265fcc66dbf97b29d15f4d5e7b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="f89b5-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f89b5-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="f89b5-103">Bezpieczne i interoperacyjne powiązanie, która jest pochodną [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i obsługuje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f89b5-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="f89b5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f89b5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f89b5-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f89b5-105">\<bindings></span></span>  
<span data-ttu-id="f89b5-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f89b5-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89b5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f89b5-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
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
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f89b5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f89b5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f89b5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f89b5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f89b5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f89b5-110">Attributes</span></span>  
  
|<span data-ttu-id="f89b5-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f89b5-111">Attribute</span></span>|<span data-ttu-id="f89b5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f89b5-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="f89b5-113">Wartość, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="f89b5-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="f89b5-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f89b5-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="f89b5-115">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="f89b5-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f89b5-116">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f89b5-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f89b5-117">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f89b5-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="f89b5-118">Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="f89b5-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="f89b5-119">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f89b5-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="f89b5-120">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje nazwy hosta w dopasowania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="f89b5-121">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="f89b5-122">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="f89b5-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="f89b5-123">Bufory za pomocą wielu części programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f89b5-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="f89b5-124">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna.</span><span class="sxs-lookup"><span data-stu-id="f89b5-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="f89b5-125">Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="f89b5-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="f89b5-126">W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="f89b5-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="f89b5-127">Maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f89b5-128">Nadawcy wiadomości, która przekracza ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f89b5-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="f89b5-129">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f89b5-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f89b5-130">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="f89b5-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="f89b5-131">Definiuje koder używany do kodowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f89b5-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="f89b5-132">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="f89b5-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f89b5-133">-Tekst: Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="f89b5-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="f89b5-134">-Mtom: Za pomocą kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="f89b5-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="f89b5-135">Wartość domyślna to tekst.</span><span class="sxs-lookup"><span data-stu-id="f89b5-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="f89b5-136">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="f89b5-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="f89b5-137">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-137">The configuration name of the binding.</span></span> <span data-ttu-id="f89b5-138">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f89b5-139">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="f89b5-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f89b5-140">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f89b5-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f89b5-141">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="f89b5-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f89b5-142">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f89b5-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f89b5-143">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f89b5-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="f89b5-144">Identyfikator URI, w której znajduje się zasadach zachowania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="f89b5-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="f89b5-145">Zasady zachowania poufności informacji w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="f89b5-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="f89b5-146">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="f89b5-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="f89b5-147">Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="f89b5-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="f89b5-148">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="f89b5-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f89b5-149">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="f89b5-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f89b5-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f89b5-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f89b5-151">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f89b5-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f89b5-152">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f89b5-153">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f89b5-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f89b5-154">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f89b5-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="f89b5-155">Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="f89b5-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f89b5-156">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="f89b5-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f89b5-157">-BigEndianUnicode: Big Endian kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="f89b5-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="f89b5-158">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="f89b5-159">-UTF8: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="f89b5-160">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="f89b5-160">The default is UTF8.</span></span> <span data-ttu-id="f89b5-161">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="f89b5-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="f89b5-162">Wartość, która określa, czy wiązanie obsługuje przechodzenia WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="f89b5-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="f89b5-163">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f89b5-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="f89b5-164">Wartość, która wskazuje, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="f89b5-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="f89b5-165">Adres serwera proxy musi być `null` (to znaczy, że nie ustawiono) Jeśli ten atrybut jest `true`.</span><span class="sxs-lookup"><span data-stu-id="f89b5-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="f89b5-166">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="f89b5-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f89b5-167">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f89b5-167">Child Elements</span></span>  
  
|<span data-ttu-id="f89b5-168">Element</span><span class="sxs-lookup"><span data-stu-id="f89b5-168">Element</span></span>|<span data-ttu-id="f89b5-169">Opis</span><span class="sxs-lookup"><span data-stu-id="f89b5-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f89b5-170">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f89b5-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="f89b5-171">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f89b5-171">Defines the security settings for the message.</span></span> <span data-ttu-id="f89b5-172">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f89b5-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="f89b5-173">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="f89b5-173">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f89b5-174">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f89b5-175">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f89b5-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="f89b5-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="f89b5-176">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="f89b5-177">Określa, czy między punktami końcowymi kanału ustanowiono niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="f89b5-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f89b5-178">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f89b5-178">Parent Elements</span></span>  
  
|<span data-ttu-id="f89b5-179">Element</span><span class="sxs-lookup"><span data-stu-id="f89b5-179">Element</span></span>|<span data-ttu-id="f89b5-180">Opis</span><span class="sxs-lookup"><span data-stu-id="f89b5-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f89b5-181">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f89b5-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="f89b5-182">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f89b5-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f89b5-183">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f89b5-183">Remarks</span></span>  
 <span data-ttu-id="f89b5-184">Federacja znajduje się możliwość udostępniania tożsamości wielu przedsiębiorstw lub zaufania domen do uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f89b5-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="f89b5-185">Używa protokołu WS-Trust do reprezentacji tożsamości z jednej relacji zaufania domeny do innego mapowania.</span><span class="sxs-lookup"><span data-stu-id="f89b5-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="f89b5-186">Powiązania federacyjnego HTTP obsługuje zabezpieczeń SOAP, a także trybu mieszanego zabezpieczeń, ale nie obsługuje zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="f89b5-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="f89b5-187">Usługi skonfigurowane dla tego wiązania należy korzystać z transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f89b5-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="f89b5-188">Aby uzyskać więcej informacji, zobacz [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f89b5-188">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f89b5-189">Przykład</span><span class="sxs-lookup"><span data-stu-id="f89b5-189">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
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
  
## <a name="see-also"></a><span data-ttu-id="f89b5-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f89b5-190">See Also</span></span>  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>  
 [<span data-ttu-id="f89b5-191">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f89b5-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
 [<span data-ttu-id="f89b5-192">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f89b5-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f89b5-193">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f89b5-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f89b5-194">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f89b5-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f89b5-195">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f89b5-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
