---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 6059bc91588492afdd1f205398e6cdfdba0be7ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177466"
---
# <a name="wshttpbinding"></a><span data-ttu-id="4439d-101">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4439d-101">\<wsHttpBinding></span></span>
<span data-ttu-id="4439d-102">Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie odpowiednie dla kontraktów na usługę non-duplex.</span><span class="sxs-lookup"><span data-stu-id="4439d-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="4439d-103">Powiązanie implementuje następujące specyfikacje: WS-Reliable Messaging w zakresie niezawodności i WS-Security do uwierzytelniania i zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4439d-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="4439d-104">Transport, jest protokół HTTP i kodowanie komunikatu jest Text/XML kodowania.</span><span class="sxs-lookup"><span data-stu-id="4439d-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="4439d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4439d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="4439d-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4439d-106">\<bindings></span></span>  
<span data-ttu-id="4439d-107">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4439d-107">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4439d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4439d-108">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding allowCookies="Boolean"
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
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4439d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4439d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4439d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4439d-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4439d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4439d-111">Attributes</span></span>  
  
|<span data-ttu-id="4439d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4439d-112">Attribute</span></span>|<span data-ttu-id="4439d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4439d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4439d-114">allowCookies</span><span class="sxs-lookup"><span data-stu-id="4439d-114">allowCookies</span></span>|<span data-ttu-id="4439d-115">Wartość logiczna, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="4439d-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="4439d-116">Wartością domyślną jest false.</span><span class="sxs-lookup"><span data-stu-id="4439d-116">The default is false.</span></span><br /><br /> <span data-ttu-id="4439d-117">Podczas interakcji z usługami sieci Web ASMX, które używają plików cookie, można użyć tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="4439d-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="4439d-118">W ten sposób można się upewnić, że pliki cookie, zwrócona z serwera są automatycznie kopiowane do wszystkich przyszłych żądań za daną usługę.</span><span class="sxs-lookup"><span data-stu-id="4439d-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="4439d-119">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="4439d-119">bypassProxyOnLocal</span></span>|<span data-ttu-id="4439d-120">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="4439d-120">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="4439d-121">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="4439d-121">The default is `false`.</span></span>|  
|<span data-ttu-id="4439d-122">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="4439d-122">closeTimeout</span></span>|<span data-ttu-id="4439d-123">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="4439d-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4439d-124">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4439d-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4439d-125">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4439d-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4439d-126">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="4439d-126">hostnameComparisonMode</span></span>|<span data-ttu-id="4439d-127">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="4439d-127">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="4439d-128">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="4439d-128">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="4439d-129">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="4439d-129">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="4439d-130">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4439d-130">maxBufferPoolSize</span></span>|<span data-ttu-id="4439d-131">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4439d-131">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="4439d-132">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="4439d-132">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="4439d-133">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="4439d-133">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="4439d-134">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="4439d-134">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4439d-135">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="4439d-135">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4439d-136">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="4439d-136">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4439d-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4439d-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="4439d-138">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4439d-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4439d-139">Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4439d-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="4439d-140">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4439d-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4439d-141">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="4439d-141">The default is 65536.</span></span>|  
|<span data-ttu-id="4439d-142">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="4439d-142">messageEncoding</span></span>|<span data-ttu-id="4439d-143">Definiuje encoder umożliwia kodowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4439d-143">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="4439d-144">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="4439d-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4439d-145">-Tekst: Za pomocą kodera komunikatów tekstu.</span><span class="sxs-lookup"><span data-stu-id="4439d-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="4439d-146">-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4439d-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="4439d-147">— Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="4439d-147">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="4439d-148">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="4439d-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="4439d-149">nazwa</span><span class="sxs-lookup"><span data-stu-id="4439d-149">name</span></span>|<span data-ttu-id="4439d-150">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="4439d-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4439d-151">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="4439d-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4439d-152">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="4439d-152">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4439d-153">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4439d-153">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="4439d-154">openTimeout</span><span class="sxs-lookup"><span data-stu-id="4439d-154">openTimeout</span></span>|<span data-ttu-id="4439d-155">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="4439d-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4439d-156">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4439d-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4439d-157">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4439d-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4439d-158">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="4439d-158">proxyAddress</span></span>|<span data-ttu-id="4439d-159">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="4439d-159">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="4439d-160">Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="4439d-160">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="4439d-161">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="4439d-161">The default is `null`.</span></span>|  
|<span data-ttu-id="4439d-162">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="4439d-162">receiveTimeout</span></span>|<span data-ttu-id="4439d-163">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="4439d-163">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4439d-164">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4439d-164">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4439d-165">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4439d-165">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4439d-166">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="4439d-166">sendTimeout</span></span>|<span data-ttu-id="4439d-167">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="4439d-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4439d-168">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4439d-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4439d-169">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4439d-169">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4439d-170">textEncoding</span><span class="sxs-lookup"><span data-stu-id="4439d-170">textEncoding</span></span>|<span data-ttu-id="4439d-171">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="4439d-171">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4439d-172">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="4439d-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4439d-173">-   UnicodeFffeTextEncoding: Unicode BigEndian kodowania.</span><span class="sxs-lookup"><span data-stu-id="4439d-173">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="4439d-174">-   Utf16TextEncoding: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="4439d-174">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="4439d-175">-   Utf8TextEncoding: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="4439d-175">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="4439d-176">The default is Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="4439d-176">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="4439d-177">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4439d-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="4439d-178">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="4439d-178">transactionFlow</span></span>|<span data-ttu-id="4439d-179">Wartość logiczna określająca, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="4439d-179">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="4439d-180">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="4439d-180">The default is `false`.</span></span>|  
|<span data-ttu-id="4439d-181">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="4439d-181">useDefaultWebProxy</span></span>|<span data-ttu-id="4439d-182">Wartość logiczna określająca, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4439d-182">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="4439d-183">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="4439d-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4439d-184">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4439d-184">Child Elements</span></span>  
  
|<span data-ttu-id="4439d-185">Element</span><span class="sxs-lookup"><span data-stu-id="4439d-185">Element</span></span>|<span data-ttu-id="4439d-186">Opis</span><span class="sxs-lookup"><span data-stu-id="4439d-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4439d-187">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="4439d-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="4439d-188">Definiuje ustawienia zabezpieczeń dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="4439d-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="4439d-189">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4439d-189">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="4439d-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4439d-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="4439d-191">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="4439d-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4439d-192">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4439d-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="4439d-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4439d-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="4439d-194">Określa, jeśli niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="4439d-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4439d-195">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4439d-195">Parent Elements</span></span>  
  
|<span data-ttu-id="4439d-196">Element</span><span class="sxs-lookup"><span data-stu-id="4439d-196">Element</span></span>|<span data-ttu-id="4439d-197">Opis</span><span class="sxs-lookup"><span data-stu-id="4439d-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4439d-198">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4439d-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="4439d-199">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4439d-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4439d-200">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4439d-200">Remarks</span></span>  
 <span data-ttu-id="4439d-201">`WSHttpBinding` Przypomina `BasicHttpBinding` , ale zapewnia więcej funkcji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4439d-201">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="4439d-202">Używa protokołu HTTP i zapewnia zabezpieczenia komunikatów, tak jak BasicHttpBinding, ale zapewnia także transakcji, niezawodnej obsługi komunikatów i WS-Addressing, albo włączone domyślnie dostępne za pomocą ustawienia jednego formantu.</span><span class="sxs-lookup"><span data-stu-id="4439d-202">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4439d-203">Przykład</span><span class="sxs-lookup"><span data-stu-id="4439d-203">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
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
  
## <a name="see-also"></a><span data-ttu-id="4439d-204">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4439d-204">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="4439d-205">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4439d-205">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4439d-206">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="4439d-206">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4439d-207">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4439d-207">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4439d-208">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4439d-208">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
