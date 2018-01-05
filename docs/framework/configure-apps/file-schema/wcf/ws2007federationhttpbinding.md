---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28e4cc9189c144404bcfe2b7f8e255a74eef76c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="72ee2-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="72ee2-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="72ee2-103">Bezpieczne i interoperacyjne powiązanie, która jest pochodną [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i obsługuje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="72ee2-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="72ee2-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="72ee2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="72ee2-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="72ee2-105">\<bindings></span></span>  
<span data-ttu-id="72ee2-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="72ee2-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ee2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="72ee2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72ee2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="72ee2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="72ee2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="72ee2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72ee2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="72ee2-110">Attributes</span></span>  
  
|<span data-ttu-id="72ee2-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="72ee2-111">Attribute</span></span>|<span data-ttu-id="72ee2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="72ee2-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="72ee2-113">Wartość, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="72ee2-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="72ee2-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="72ee2-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="72ee2-115">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="72ee2-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="72ee2-116">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72ee2-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72ee2-117">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="72ee2-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="72ee2-118">Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="72ee2-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="72ee2-119">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="72ee2-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="72ee2-120">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje nazwy hosta w dopasowania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="72ee2-121">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="72ee2-122">Wartość domyślna to 524,288 bajtów (512 * 1024).</span><span class="sxs-lookup"><span data-stu-id="72ee2-122">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="72ee2-123">Wiele elementów [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] użyć buforów.</span><span class="sxs-lookup"><span data-stu-id="72ee2-123">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="72ee2-124">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna.</span><span class="sxs-lookup"><span data-stu-id="72ee2-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="72ee2-125">Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="72ee2-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="72ee2-126">W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="72ee2-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="72ee2-127">Maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="72ee2-128">Nadawcy wiadomości, która przekracza ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="72ee2-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="72ee2-129">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="72ee2-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="72ee2-130">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="72ee2-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="72ee2-131">Definiuje koder używany do kodowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="72ee2-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="72ee2-132">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="72ee2-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="72ee2-133">-Tekst: Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="72ee2-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="72ee2-134">-Mtom: Za pomocą kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="72ee2-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="72ee2-135">Wartość domyślna to tekst.</span><span class="sxs-lookup"><span data-stu-id="72ee2-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="72ee2-136">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="72ee2-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="72ee2-137">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-137">The configuration name of the binding.</span></span> <span data-ttu-id="72ee2-138">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="72ee2-139">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="72ee2-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="72ee2-140">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="72ee2-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="72ee2-141">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="72ee2-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="72ee2-142">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72ee2-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72ee2-143">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="72ee2-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="72ee2-144">Identyfikator URI, w której znajduje się zasadach zachowania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="72ee2-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="72ee2-145">Zasady zachowania poufności informacji w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="72ee2-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="72ee2-146">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="72ee2-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="72ee2-147">Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="72ee2-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="72ee2-148">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="72ee2-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="72ee2-149">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="72ee2-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="72ee2-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72ee2-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72ee2-151">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="72ee2-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="72ee2-152">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="72ee2-153">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72ee2-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72ee2-154">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="72ee2-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="72ee2-155">Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="72ee2-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="72ee2-156">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="72ee2-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="72ee2-157">-BigEndianUnicode: Big Endian kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="72ee2-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="72ee2-158">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="72ee2-159">-UTF8: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="72ee2-160">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="72ee2-160">The default is UTF8.</span></span> <span data-ttu-id="72ee2-161">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="72ee2-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="72ee2-162">Wartość, która określa, czy wiązanie obsługuje przechodzenia WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="72ee2-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="72ee2-163">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="72ee2-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="72ee2-164">Wartość, która wskazuje, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="72ee2-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="72ee2-165">Adres serwera proxy musi być `null` (to znaczy, że nie ustawiono) Jeśli ten atrybut jest `true`.</span><span class="sxs-lookup"><span data-stu-id="72ee2-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="72ee2-166">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="72ee2-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72ee2-167">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="72ee2-167">Child Elements</span></span>  
  
|<span data-ttu-id="72ee2-168">Element</span><span class="sxs-lookup"><span data-stu-id="72ee2-168">Element</span></span>|<span data-ttu-id="72ee2-169">Opis</span><span class="sxs-lookup"><span data-stu-id="72ee2-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72ee2-170">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="72ee2-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="72ee2-171">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="72ee2-171">Defines the security settings for the message.</span></span> <span data-ttu-id="72ee2-172">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="72ee2-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="72ee2-173">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="72ee2-173">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="72ee2-174">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="72ee2-175">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="72ee2-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="72ee2-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="72ee2-176">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="72ee2-177">Określa, czy między punktami końcowymi kanału ustanowiono niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="72ee2-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72ee2-178">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="72ee2-178">Parent Elements</span></span>  
  
|<span data-ttu-id="72ee2-179">Element</span><span class="sxs-lookup"><span data-stu-id="72ee2-179">Element</span></span>|<span data-ttu-id="72ee2-180">Opis</span><span class="sxs-lookup"><span data-stu-id="72ee2-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72ee2-181">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="72ee2-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="72ee2-182">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="72ee2-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72ee2-183">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72ee2-183">Remarks</span></span>  
 <span data-ttu-id="72ee2-184">Federacja znajduje się możliwość udostępniania tożsamości wielu przedsiębiorstw lub zaufania domen do uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="72ee2-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="72ee2-185">Używa protokołu WS-Trust do reprezentacji tożsamości z jednej relacji zaufania domeny do innego mapowania.</span><span class="sxs-lookup"><span data-stu-id="72ee2-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="72ee2-186">Powiązania federacyjnego HTTP obsługuje zabezpieczeń SOAP, a także trybu mieszanego zabezpieczeń, ale nie obsługuje zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="72ee2-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="72ee2-187">Usługi skonfigurowane dla tego wiązania należy korzystać z transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="72ee2-187">Services configured with this binding must use the HTTP transport.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="72ee2-188">[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="72ee2-188"> [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72ee2-189">Przykład</span><span class="sxs-lookup"><span data-stu-id="72ee2-189">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72ee2-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72ee2-190">See Also</span></span>  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>  
 [<span data-ttu-id="72ee2-191">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="72ee2-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
 [<span data-ttu-id="72ee2-192">Powiązania</span><span class="sxs-lookup"><span data-stu-id="72ee2-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="72ee2-193">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="72ee2-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="72ee2-194">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="72ee2-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="72ee2-195">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="72ee2-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
