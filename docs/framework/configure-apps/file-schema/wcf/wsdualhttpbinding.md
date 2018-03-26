---
title: '&lt;wsDualHttpBinding&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a49b534ba22f4ac422eb26885388e24594b49afd
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="ltwsdualhttpbindinggt"></a><span data-ttu-id="5609b-102">&lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5609b-102">&lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="5609b-103">Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie, które jest odpowiednie dla kontraktów usługi duplex lub komunikacji za pośrednictwem pośredników SOAP.</span><span class="sxs-lookup"><span data-stu-id="5609b-103">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="5609b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5609b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5609b-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5609b-105">\<bindings></span></span>  
<span data-ttu-id="5609b-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5609b-106">\<wsDualHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5609b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5609b-107">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        bypassProxyOnLocal="Boolean"  
        clientBaseAddress="URI"  
        transactionFlow="Boolean"   
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
        proxyAddress="URI"  
  
textEncoding="Unicode/BigEndianUnicode/UTF8"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan" />  
        <security mode="None/Message">  
           <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                negotiateServiceCredential="Boolean"  
                    algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
                </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5609b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5609b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5609b-109">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5609b-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5609b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5609b-110">Attributes</span></span>  
  
|<span data-ttu-id="5609b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5609b-111">Attribute</span></span>|<span data-ttu-id="5609b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5609b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5609b-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="5609b-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="5609b-114">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="5609b-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="5609b-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5609b-115">The default is `false`.</span></span>|  
|<span data-ttu-id="5609b-116">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="5609b-116">clientBaseAddress</span></span>|<span data-ttu-id="5609b-117">Identyfikator URI, który ustawia adres podstawowy nasłuchujący klienta dla wiadomości odpowiedzi z usługi.</span><span class="sxs-lookup"><span data-stu-id="5609b-117">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="5609b-118">Jeśli jest określony, ten adres (oraz na channelGUID) jest używany do nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="5609b-118">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="5609b-119">Jeśli nie określono wartości, adres podstawowy klienta jest generowane w sposób specyficznych dla transportu.</span><span class="sxs-lookup"><span data-stu-id="5609b-119">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="5609b-120">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="5609b-120">The default is `null`.</span></span>|  
|<span data-ttu-id="5609b-121">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="5609b-121">closeTimeout</span></span>|<span data-ttu-id="5609b-122">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="5609b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5609b-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5609b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5609b-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5609b-124">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5609b-125">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="5609b-125">hostnameComparisonMode</span></span>|<span data-ttu-id="5609b-126">Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="5609b-126">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="5609b-127">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="5609b-127">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="5609b-128">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje nazwy hosta w dopasowania.</span><span class="sxs-lookup"><span data-stu-id="5609b-128">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="5609b-129">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="5609b-129">maxBufferPoolSize</span></span>|<span data-ttu-id="5609b-130">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5609b-130">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="5609b-131">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="5609b-131">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="5609b-132">Bufory za pomocą wielu części programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5609b-132">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="5609b-133">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna.</span><span class="sxs-lookup"><span data-stu-id="5609b-133">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="5609b-134">Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="5609b-134">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="5609b-135">W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="5609b-135">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="5609b-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="5609b-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="5609b-137">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="5609b-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="5609b-138">Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5609b-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="5609b-139">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5609b-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5609b-140">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="5609b-140">The default is 65536.</span></span>|  
|<span data-ttu-id="5609b-141">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="5609b-141">messageEncoding</span></span>|<span data-ttu-id="5609b-142">Definiuje koder używany do kodowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5609b-142">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="5609b-143">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="5609b-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5609b-144">-Tekst: Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="5609b-144">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="5609b-145">-Mtom: Za pomocą kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="5609b-145">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="5609b-146">— Wartość domyślna to tekst.</span><span class="sxs-lookup"><span data-stu-id="5609b-146">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="5609b-147">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="5609b-147">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="5609b-148">nazwa</span><span class="sxs-lookup"><span data-stu-id="5609b-148">name</span></span>|<span data-ttu-id="5609b-149">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="5609b-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5609b-150">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5609b-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5609b-151">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="5609b-151">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5609b-152">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5609b-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="5609b-153">openTimeout</span><span class="sxs-lookup"><span data-stu-id="5609b-153">openTimeout</span></span>|<span data-ttu-id="5609b-154">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="5609b-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5609b-155">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5609b-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5609b-156">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5609b-156">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5609b-157">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="5609b-157">proxyAddress</span></span>|<span data-ttu-id="5609b-158">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="5609b-158">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="5609b-159">Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="5609b-159">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="5609b-160">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="5609b-160">The default is `null`.</span></span>|  
|<span data-ttu-id="5609b-161">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="5609b-161">receiveTimeout</span></span>|<span data-ttu-id="5609b-162">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="5609b-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5609b-163">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5609b-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5609b-164">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5609b-164">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5609b-165">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="5609b-165">sendTimeout</span></span>|<span data-ttu-id="5609b-166">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="5609b-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5609b-167">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5609b-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5609b-168">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5609b-168">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5609b-169">textEncoding</span><span class="sxs-lookup"><span data-stu-id="5609b-169">textEncoding</span></span>|<span data-ttu-id="5609b-170">Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="5609b-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="5609b-171">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="5609b-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5609b-172">-BigEndianUnicode: Unicode BigEndian kodowanie.</span><span class="sxs-lookup"><span data-stu-id="5609b-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="5609b-173">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="5609b-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="5609b-174">-UTF8: 8-bitowego kodowania o</span><span class="sxs-lookup"><span data-stu-id="5609b-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="5609b-175">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="5609b-175">The default is UTF8.</span></span> <span data-ttu-id="5609b-176">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="5609b-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="5609b-177">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="5609b-177">transactionFlow</span></span>|<span data-ttu-id="5609b-178">Wartość logiczna określająca, czy wiązanie obsługuje przechodzenia WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="5609b-178">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="5609b-179">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5609b-179">The default is `false`.</span></span>|  
|<span data-ttu-id="5609b-180">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="5609b-180">useDefaultWebProxy</span></span>|<span data-ttu-id="5609b-181">Wartość logiczna wskazująca, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="5609b-181">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="5609b-182">Adres serwera proxy musi być `null` (to znaczy, że nie ustawiono) Jeśli ten atrybut jest `true`.</span><span class="sxs-lookup"><span data-stu-id="5609b-182">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="5609b-183">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="5609b-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5609b-184">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5609b-184">Child Elements</span></span>  
  
|<span data-ttu-id="5609b-185">Element</span><span class="sxs-lookup"><span data-stu-id="5609b-185">Element</span></span>|<span data-ttu-id="5609b-186">Opis</span><span class="sxs-lookup"><span data-stu-id="5609b-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5609b-187">\<security></span><span class="sxs-lookup"><span data-stu-id="5609b-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|<span data-ttu-id="5609b-188">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="5609b-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="5609b-189">Ten element jest typu <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5609b-189">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="5609b-190">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="5609b-190">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="5609b-191">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="5609b-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5609b-192">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="5609b-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="5609b-193">reliableSession</span><span class="sxs-lookup"><span data-stu-id="5609b-193">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="5609b-194">Określa, czy niezawodnej sesji są połączenia między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="5609b-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5609b-195">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5609b-195">Parent Elements</span></span>  
  
|<span data-ttu-id="5609b-196">Element</span><span class="sxs-lookup"><span data-stu-id="5609b-196">Element</span></span>|<span data-ttu-id="5609b-197">Opis</span><span class="sxs-lookup"><span data-stu-id="5609b-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5609b-198">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5609b-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="5609b-199">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5609b-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5609b-200">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5609b-200">Remarks</span></span>  
 <span data-ttu-id="5609b-201">`WSDualHttpBinding` Udostępnia możliwość obsługi tego samego protokoły usług sieci Web jako `WSHttpBinding`, ale do użycia z kontraktów dupleksowych.</span><span class="sxs-lookup"><span data-stu-id="5609b-201">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="5609b-202">`WSDualHttpBinding` obsługuje zabezpieczenia protokołu SOAP i tylko wymaga niezawodnej obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5609b-202">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="5609b-203">To powiązanie wymaga, że klient ma publiczny identyfikator URI, który zawiera punkt końcowy wywołania zwrotnego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5609b-203">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="5609b-204">Jest to obsługiwane przez `clientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5609b-204">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="5609b-205">Dwa powiązania udostępnia adres IP klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="5609b-205">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="5609b-206">Klienta należy użyć zabezpieczeń, aby upewnić się, że go tylko łączy się z usługami go relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="5609b-206">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="5609b-207">To powiązanie może służyć do niezawodnego komunikacji za pośrednictwem pośredników SOAP co najmniej jeden.</span><span class="sxs-lookup"><span data-stu-id="5609b-207">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="5609b-208">Domyślnie to powiązanie generuje stosu środowiska wykonawczego o WS-ReliableMessaging niezawodności, WS-Security komunikat zabezpieczeń i uwierzytelniania HTTP w celu dostarczania komunikatów i kodowanie wiadomości tekstowe i XML.</span><span class="sxs-lookup"><span data-stu-id="5609b-208">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5609b-209">Przykład</span><span class="sxs-lookup"><span data-stu-id="5609b-209">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
        openTimeout="00:00:20"   
        receiveTimeout="00:00:30"  
        sendTimeout="00:00:40"  
        bypassProxyOnLocal="false"   
        clientBaseAddress="http://localhost:8001/client/"  
        transactionFlow="true"   
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="utf-16"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" />  
        <security mode="None">  
            <message clientCredentialType="None"  
                negotiateServiceCredential="false"  
                algorithmSuite="Aes128" />  
        </security>  
    </binding>  
</wsDualHttpBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5609b-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5609b-210">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [<span data-ttu-id="5609b-211">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5609b-211">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5609b-212">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="5609b-212">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5609b-213">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="5609b-213">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5609b-214">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5609b-214">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
