---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 81f0101ce1dc2195cfc2f556e38a8551f674d13b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941511"
---
# <a name="wshttpbinding"></a><span data-ttu-id="c541a-101">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c541a-101">\<wsHttpBinding></span></span>
<span data-ttu-id="c541a-102">Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie odpowiednie dla kontraktów usługi non-Duplex.</span><span class="sxs-lookup"><span data-stu-id="c541a-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="c541a-103">Powiązanie implementuje następujące specyfikacje: Niezawodna obsługa komunikatów w usłudze WS i zabezpieczeniach WS-Security na potrzeby zabezpieczeń i uwierzytelniania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c541a-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="c541a-104">Transport to HTTP, a kodowanie wiadomości to kodowanie Text/XML.</span><span class="sxs-lookup"><span data-stu-id="c541a-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="c541a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c541a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c541a-106">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="c541a-106">\<bindings></span></span>  
<span data-ttu-id="c541a-107">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c541a-107">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c541a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c541a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c541a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c541a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c541a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c541a-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c541a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c541a-111">Attributes</span></span>  
  
|<span data-ttu-id="c541a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c541a-112">Attribute</span></span>|<span data-ttu-id="c541a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c541a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c541a-114">allowCookies</span><span class="sxs-lookup"><span data-stu-id="c541a-114">allowCookies</span></span>|<span data-ttu-id="c541a-115">Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="c541a-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="c541a-116">Wartością domyślną jest false.</span><span class="sxs-lookup"><span data-stu-id="c541a-116">The default is false.</span></span><br /><br /> <span data-ttu-id="c541a-117">Tej właściwości można użyć podczas współpracy z usługami sieci Web ASMX, które korzystają z plików cookie.</span><span class="sxs-lookup"><span data-stu-id="c541a-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="c541a-118">W ten sposób można mieć pewność, że pliki cookie zwrócone z serwera są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c541a-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="c541a-119">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="c541a-119">bypassProxyOnLocal</span></span>|<span data-ttu-id="c541a-120">Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="c541a-120">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="c541a-121">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c541a-121">The default is `false`.</span></span>|  
|<span data-ttu-id="c541a-122">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="c541a-122">closeTimeout</span></span>|<span data-ttu-id="c541a-123"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="c541a-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c541a-124">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c541a-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c541a-125">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c541a-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c541a-126">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c541a-126">hostnameComparisonMode</span></span>|<span data-ttu-id="c541a-127">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="c541a-127">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="c541a-128">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="c541a-128">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="c541a-129">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="c541a-129">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="c541a-130">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c541a-130">maxBufferPoolSize</span></span>|<span data-ttu-id="c541a-131">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c541a-131">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="c541a-132">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="c541a-132">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="c541a-133">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="c541a-133">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="c541a-134">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="c541a-134">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="c541a-135">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="c541a-135">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="c541a-136">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="c541a-136">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="c541a-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c541a-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="c541a-138">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c541a-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="c541a-139">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c541a-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="c541a-140">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c541a-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="c541a-141">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="c541a-141">The default is 65536.</span></span>|  
|<span data-ttu-id="c541a-142">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="c541a-142">messageEncoding</span></span>|<span data-ttu-id="c541a-143">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c541a-143">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="c541a-144">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="c541a-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c541a-145">Opis Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="c541a-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="c541a-146">MTOM Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="c541a-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="c541a-147">-Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="c541a-147">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="c541a-148">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="c541a-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="c541a-149">nazwa</span><span class="sxs-lookup"><span data-stu-id="c541a-149">name</span></span>|<span data-ttu-id="c541a-150">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="c541a-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c541a-151">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="c541a-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c541a-152">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="c541a-152">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c541a-153">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c541a-153">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="c541a-154">openTimeout</span><span class="sxs-lookup"><span data-stu-id="c541a-154">openTimeout</span></span>|<span data-ttu-id="c541a-155"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="c541a-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c541a-156">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c541a-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c541a-157">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c541a-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c541a-158">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="c541a-158">proxyAddress</span></span>|<span data-ttu-id="c541a-159">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="c541a-159">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="c541a-160">Jeśli `useSystemWebProxy` `null`jest `true`, to ustawienie musi być.</span><span class="sxs-lookup"><span data-stu-id="c541a-160">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="c541a-161">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="c541a-161">The default is `null`.</span></span>|  
|<span data-ttu-id="c541a-162">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c541a-162">receiveTimeout</span></span>|<span data-ttu-id="c541a-163"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="c541a-163">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c541a-164">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c541a-164">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c541a-165">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c541a-165">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c541a-166">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="c541a-166">sendTimeout</span></span>|<span data-ttu-id="c541a-167"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="c541a-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c541a-168">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c541a-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c541a-169">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c541a-169">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c541a-170">TextEncoding</span><span class="sxs-lookup"><span data-stu-id="c541a-170">textEncoding</span></span>|<span data-ttu-id="c541a-171">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="c541a-171">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="c541a-172">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="c541a-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c541a-173">- UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="c541a-173">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="c541a-174">- Utf16TextEncoding: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="c541a-174">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="c541a-175">-   Utf8TextEncoding: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="c541a-175">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="c541a-176">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="c541a-176">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="c541a-177">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="c541a-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="c541a-178">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="c541a-178">transactionFlow</span></span>|<span data-ttu-id="c541a-179">Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="c541a-179">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="c541a-180">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c541a-180">The default is `false`.</span></span>|  
|<span data-ttu-id="c541a-181">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="c541a-181">useDefaultWebProxy</span></span>|<span data-ttu-id="c541a-182">Wartość logiczna określająca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="c541a-182">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="c541a-183">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="c541a-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c541a-184">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c541a-184">Child Elements</span></span>  
  
|<span data-ttu-id="c541a-185">Element</span><span class="sxs-lookup"><span data-stu-id="c541a-185">Element</span></span>|<span data-ttu-id="c541a-186">Opis</span><span class="sxs-lookup"><span data-stu-id="c541a-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c541a-187">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c541a-187">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="c541a-188">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="c541a-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="c541a-189">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c541a-189">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="c541a-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c541a-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="c541a-191">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c541a-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c541a-192">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c541a-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="c541a-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c541a-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="c541a-194">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="c541a-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c541a-195">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c541a-195">Parent Elements</span></span>  
  
|<span data-ttu-id="c541a-196">Element</span><span class="sxs-lookup"><span data-stu-id="c541a-196">Element</span></span>|<span data-ttu-id="c541a-197">Opis</span><span class="sxs-lookup"><span data-stu-id="c541a-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c541a-198">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="c541a-198">\<bindings></span></span>](bindings.md)|<span data-ttu-id="c541a-199">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c541a-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c541a-200">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c541a-200">Remarks</span></span>  
 <span data-ttu-id="c541a-201">Jest podobna do, `BasicHttpBinding` ale udostępnia więcej funkcji usługi sieci Web. `WSHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="c541a-201">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="c541a-202">Korzysta ona z transportu HTTP i zapewnia zabezpieczenia komunikatów, jak BasicHttpBinding, ale udostępnia również transakcje, niezawodne komunikaty i adresy WS-Addressing, które są domyślnie włączone lub dostępne za pośrednictwem jednego ustawienia formantu.</span><span class="sxs-lookup"><span data-stu-id="c541a-202">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c541a-203">Przykład</span><span class="sxs-lookup"><span data-stu-id="c541a-203">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c541a-204">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c541a-204">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="c541a-205">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c541a-205">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c541a-206">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c541a-206">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c541a-207">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c541a-207">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c541a-208">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="c541a-208">\<binding></span></span>](../../../misc/binding.md)
