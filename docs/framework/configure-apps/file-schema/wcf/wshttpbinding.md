---
title: '&lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 480e10b9667712fbd2a3ffa95e1373d72ee1a9df
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516399"
---
# <a name="ltwshttpbindinggt"></a><span data-ttu-id="fd09e-102">&lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="fd09e-102">&lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="fd09e-103">Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie odpowiednie dla kontraktów na usługę non-duplex.</span><span class="sxs-lookup"><span data-stu-id="fd09e-103">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="fd09e-104">Powiązanie implementuje następujące specyfikacje: WS-Reliable Messaging w zakresie niezawodności i WS-Security do uwierzytelniania i zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fd09e-104">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="fd09e-105">Transport, jest protokół HTTP i kodowanie komunikatu jest Text/XML kodowania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-105">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="fd09e-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fd09e-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="fd09e-107">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="fd09e-107">\<bindings></span></span>  
<span data-ttu-id="fd09e-108">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="fd09e-108">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd09e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd09e-109">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
                textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string" />  
          <message   
             algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                          clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
             establishSecurityContext="Boolean"  
             negotiateServiceCredential="Boolean" />  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd09e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd09e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fd09e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd09e-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd09e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd09e-112">Attributes</span></span>  
  
|<span data-ttu-id="fd09e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd09e-113">Attribute</span></span>|<span data-ttu-id="fd09e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fd09e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd09e-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="fd09e-115">allowCookies</span></span>|<span data-ttu-id="fd09e-116">Wartość logiczna, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="fd09e-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="fd09e-117">Wartością domyślną jest false.</span><span class="sxs-lookup"><span data-stu-id="fd09e-117">The default is false.</span></span><br /><br /> <span data-ttu-id="fd09e-118">Podczas interakcji z usługami sieci Web ASMX, które używają plików cookie, można użyć tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd09e-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="fd09e-119">W ten sposób można się upewnić, że pliki cookie, zwrócona z serwera są automatycznie kopiowane do wszystkich przyszłych żądań za daną usługę.</span><span class="sxs-lookup"><span data-stu-id="fd09e-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="fd09e-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="fd09e-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="fd09e-121">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="fd09e-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="fd09e-122">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="fd09e-122">The default is `false`.</span></span>|  
|<span data-ttu-id="fd09e-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="fd09e-123">closeTimeout</span></span>|<span data-ttu-id="fd09e-124">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="fd09e-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="fd09e-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fd09e-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fd09e-126">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fd09e-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fd09e-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="fd09e-127">hostnameComparisonMode</span></span>|<span data-ttu-id="fd09e-128">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="fd09e-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="fd09e-129">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="fd09e-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="fd09e-130">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="fd09e-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="fd09e-131">maxBufferPoolSize</span></span>|<span data-ttu-id="fd09e-132">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="fd09e-133">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="fd09e-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="fd09e-134">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="fd09e-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="fd09e-135">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="fd09e-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="fd09e-136">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="fd09e-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="fd09e-137">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="fd09e-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="fd09e-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="fd09e-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="fd09e-139">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="fd09e-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="fd09e-140">Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="fd09e-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="fd09e-141">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fd09e-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="fd09e-142">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="fd09e-142">The default is 65536.</span></span>|  
|<span data-ttu-id="fd09e-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="fd09e-143">messageEncoding</span></span>|<span data-ttu-id="fd09e-144">Definiuje encoder umożliwia kodowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fd09e-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="fd09e-145">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="fd09e-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd09e-146">-Text: Użyj koder komunikatu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="fd09e-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="fd09e-147">-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="fd09e-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="fd09e-148">— Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="fd09e-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="fd09e-149">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="fd09e-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="fd09e-150">nazwa</span><span class="sxs-lookup"><span data-stu-id="fd09e-150">name</span></span>|<span data-ttu-id="fd09e-151">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="fd09e-152">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="fd09e-153">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="fd09e-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="fd09e-154">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fd09e-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="fd09e-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="fd09e-155">openTimeout</span></span>|<span data-ttu-id="fd09e-156">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="fd09e-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="fd09e-157">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fd09e-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fd09e-158">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fd09e-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fd09e-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="fd09e-159">proxyAddress</span></span>|<span data-ttu-id="fd09e-160">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd09e-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="fd09e-161">Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="fd09e-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="fd09e-162">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="fd09e-162">The default is `null`.</span></span>|  
|<span data-ttu-id="fd09e-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="fd09e-163">receiveTimeout</span></span>|<span data-ttu-id="fd09e-164">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="fd09e-165">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fd09e-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fd09e-166">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fd09e-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fd09e-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="fd09e-167">sendTimeout</span></span>|<span data-ttu-id="fd09e-168">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="fd09e-169">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fd09e-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fd09e-170">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fd09e-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fd09e-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="fd09e-171">textEncoding</span></span>|<span data-ttu-id="fd09e-172">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="fd09e-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="fd09e-173">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="fd09e-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd09e-174">-UnicodeFffeTextEncoding: Unicode BigEndian kodowanie.</span><span class="sxs-lookup"><span data-stu-id="fd09e-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="fd09e-175">-Utf16TextEncoding: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="fd09e-176">-Utf8TextEncoding: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="fd09e-177">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="fd09e-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="fd09e-178">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="fd09e-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="fd09e-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="fd09e-179">transactionFlow</span></span>|<span data-ttu-id="fd09e-180">Wartość logiczna określająca, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="fd09e-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="fd09e-181">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="fd09e-181">The default is `false`.</span></span>|  
|<span data-ttu-id="fd09e-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="fd09e-182">useDefaultWebProxy</span></span>|<span data-ttu-id="fd09e-183">Wartość logiczna określająca, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="fd09e-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="fd09e-184">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="fd09e-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd09e-185">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd09e-185">Child Elements</span></span>  
  
|<span data-ttu-id="fd09e-186">Element</span><span class="sxs-lookup"><span data-stu-id="fd09e-186">Element</span></span>|<span data-ttu-id="fd09e-187">Opis</span><span class="sxs-lookup"><span data-stu-id="fd09e-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd09e-188">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="fd09e-188">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="fd09e-189">Definiuje ustawienia zabezpieczeń dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="fd09e-190">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="fd09e-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="fd09e-191">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="fd09e-191">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="fd09e-192">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="fd09e-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="fd09e-193">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="fd09e-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="fd09e-194">reliableSession</span><span class="sxs-lookup"><span data-stu-id="fd09e-194">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="fd09e-195">Określa, jeśli niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="fd09e-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd09e-196">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd09e-196">Parent Elements</span></span>  
  
|<span data-ttu-id="fd09e-197">Element</span><span class="sxs-lookup"><span data-stu-id="fd09e-197">Element</span></span>|<span data-ttu-id="fd09e-198">Opis</span><span class="sxs-lookup"><span data-stu-id="fd09e-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd09e-199">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="fd09e-199">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="fd09e-200">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fd09e-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd09e-201">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd09e-201">Remarks</span></span>  
 <span data-ttu-id="fd09e-202">`WSHttpBinding` Przypomina `BasicHttpBinding` , ale zapewnia więcej funkcji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fd09e-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="fd09e-203">Używa protokołu HTTP i zapewnia zabezpieczenia komunikatów, tak jak BasicHttpBinding, ale zapewnia także transakcji, niezawodnej obsługi komunikatów i WS-Addressing, albo włączone domyślnie dostępne za pomocą ustawienia jednego formantu.</span><span class="sxs-lookup"><span data-stu-id="fd09e-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd09e-204">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd09e-204">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://foo/bar"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </wsHttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd09e-205">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd09e-205">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement>  
 [<span data-ttu-id="fd09e-206">Powiązania</span><span class="sxs-lookup"><span data-stu-id="fd09e-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fd09e-207">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="fd09e-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fd09e-208">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="fd09e-208">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="fd09e-209">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fd09e-209">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
