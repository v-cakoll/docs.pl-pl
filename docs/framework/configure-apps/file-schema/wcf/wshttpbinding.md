---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: fc86a97ebae160f5bf2c8fcb2df9295ed7803963
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399013"
---
# <a name="wshttpbinding"></a><span data-ttu-id="49fdc-101">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="49fdc-101">\<wsHttpBinding></span></span>
<span data-ttu-id="49fdc-102">Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie odpowiednie dla kontraktów usługi non-Duplex.</span><span class="sxs-lookup"><span data-stu-id="49fdc-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="49fdc-103">Powiązanie implementuje następujące specyfikacje: Niezawodna obsługa komunikatów w usłudze WS i zabezpieczeniach WS-Security na potrzeby zabezpieczeń i uwierzytelniania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="49fdc-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="49fdc-104">Transport to HTTP, a kodowanie wiadomości to kodowanie Text/XML.</span><span class="sxs-lookup"><span data-stu-id="49fdc-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
<span data-ttu-id="49fdc-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="49fdc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="49fdc-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="49fdc-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="49fdc-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="49fdc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="49fdc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="49fdc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49fdc-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="49fdc-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49fdc-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="49fdc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="49fdc-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="49fdc-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49fdc-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="49fdc-112">Attributes</span></span>  
  
|<span data-ttu-id="49fdc-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="49fdc-113">Attribute</span></span>|<span data-ttu-id="49fdc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="49fdc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49fdc-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="49fdc-115">allowCookies</span></span>|<span data-ttu-id="49fdc-116">Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="49fdc-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="49fdc-117">Wartością domyślną jest false.</span><span class="sxs-lookup"><span data-stu-id="49fdc-117">The default is false.</span></span><br /><br /> <span data-ttu-id="49fdc-118">Tej właściwości można użyć podczas współpracy z usługami sieci Web ASMX, które korzystają z plików cookie.</span><span class="sxs-lookup"><span data-stu-id="49fdc-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="49fdc-119">W ten sposób można mieć pewność, że pliki cookie zwrócone z serwera są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="49fdc-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="49fdc-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="49fdc-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="49fdc-121">Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="49fdc-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="49fdc-122">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="49fdc-122">The default is `false`.</span></span>|  
|<span data-ttu-id="49fdc-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="49fdc-123">closeTimeout</span></span>|<span data-ttu-id="49fdc-124"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="49fdc-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="49fdc-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="49fdc-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="49fdc-126">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="49fdc-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="49fdc-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="49fdc-127">hostnameComparisonMode</span></span>|<span data-ttu-id="49fdc-128">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="49fdc-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="49fdc-129">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="49fdc-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="49fdc-130">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="49fdc-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="49fdc-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="49fdc-131">maxBufferPoolSize</span></span>|<span data-ttu-id="49fdc-132">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="49fdc-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="49fdc-133">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="49fdc-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="49fdc-134">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="49fdc-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="49fdc-135">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="49fdc-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="49fdc-136">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="49fdc-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="49fdc-137">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="49fdc-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="49fdc-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="49fdc-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="49fdc-139">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="49fdc-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="49fdc-140">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="49fdc-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="49fdc-141">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="49fdc-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="49fdc-142">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="49fdc-142">The default is 65536.</span></span>|  
|<span data-ttu-id="49fdc-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="49fdc-143">messageEncoding</span></span>|<span data-ttu-id="49fdc-144">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="49fdc-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="49fdc-145">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="49fdc-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="49fdc-146">Opis Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="49fdc-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="49fdc-147">MTOM Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="49fdc-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="49fdc-148">-Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="49fdc-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="49fdc-149">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="49fdc-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="49fdc-150">nazwa</span><span class="sxs-lookup"><span data-stu-id="49fdc-150">name</span></span>|<span data-ttu-id="49fdc-151">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="49fdc-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="49fdc-152">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="49fdc-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="49fdc-153">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="49fdc-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="49fdc-154">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="49fdc-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="49fdc-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="49fdc-155">openTimeout</span></span>|<span data-ttu-id="49fdc-156"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="49fdc-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="49fdc-157">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="49fdc-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="49fdc-158">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="49fdc-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="49fdc-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="49fdc-159">proxyAddress</span></span>|<span data-ttu-id="49fdc-160">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="49fdc-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="49fdc-161">Jeśli `useSystemWebProxy` `null`jest `true`, to ustawienie musi być.</span><span class="sxs-lookup"><span data-stu-id="49fdc-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="49fdc-162">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="49fdc-162">The default is `null`.</span></span>|  
|<span data-ttu-id="49fdc-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="49fdc-163">receiveTimeout</span></span>|<span data-ttu-id="49fdc-164"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="49fdc-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="49fdc-165">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="49fdc-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="49fdc-166">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="49fdc-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="49fdc-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="49fdc-167">sendTimeout</span></span>|<span data-ttu-id="49fdc-168"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="49fdc-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="49fdc-169">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="49fdc-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="49fdc-170">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="49fdc-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="49fdc-171">TextEncoding</span><span class="sxs-lookup"><span data-stu-id="49fdc-171">textEncoding</span></span>|<span data-ttu-id="49fdc-172">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="49fdc-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="49fdc-173">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="49fdc-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="49fdc-174">- UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="49fdc-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="49fdc-175">- Utf16TextEncoding: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="49fdc-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="49fdc-176">-   Utf8TextEncoding: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="49fdc-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="49fdc-177">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="49fdc-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="49fdc-178">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="49fdc-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="49fdc-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="49fdc-179">transactionFlow</span></span>|<span data-ttu-id="49fdc-180">Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="49fdc-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="49fdc-181">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="49fdc-181">The default is `false`.</span></span>|  
|<span data-ttu-id="49fdc-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="49fdc-182">useDefaultWebProxy</span></span>|<span data-ttu-id="49fdc-183">Wartość logiczna określająca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="49fdc-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="49fdc-184">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="49fdc-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49fdc-185">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="49fdc-185">Child Elements</span></span>  
  
|<span data-ttu-id="49fdc-186">Element</span><span class="sxs-lookup"><span data-stu-id="49fdc-186">Element</span></span>|<span data-ttu-id="49fdc-187">Opis</span><span class="sxs-lookup"><span data-stu-id="49fdc-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49fdc-188">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="49fdc-188">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="49fdc-189">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="49fdc-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="49fdc-190">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="49fdc-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="49fdc-191">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49fdc-191">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="49fdc-192">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="49fdc-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="49fdc-193">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="49fdc-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="49fdc-194">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="49fdc-194">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="49fdc-195">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="49fdc-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49fdc-196">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="49fdc-196">Parent Elements</span></span>  
  
|<span data-ttu-id="49fdc-197">Element</span><span class="sxs-lookup"><span data-stu-id="49fdc-197">Element</span></span>|<span data-ttu-id="49fdc-198">Opis</span><span class="sxs-lookup"><span data-stu-id="49fdc-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49fdc-199">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="49fdc-199">\<bindings></span></span>](bindings.md)|<span data-ttu-id="49fdc-200">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="49fdc-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49fdc-201">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49fdc-201">Remarks</span></span>  
 <span data-ttu-id="49fdc-202">Jest podobna do, `BasicHttpBinding` ale udostępnia więcej funkcji usługi sieci Web. `WSHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="49fdc-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="49fdc-203">Korzysta ona z transportu HTTP i zapewnia zabezpieczenia komunikatów, jak BasicHttpBinding, ale udostępnia również transakcje, niezawodne komunikaty i adresy WS-Addressing, które są domyślnie włączone lub dostępne za pośrednictwem jednego ustawienia formantu.</span><span class="sxs-lookup"><span data-stu-id="49fdc-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49fdc-204">Przykład</span><span class="sxs-lookup"><span data-stu-id="49fdc-204">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49fdc-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49fdc-205">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="49fdc-206">Powiązania</span><span class="sxs-lookup"><span data-stu-id="49fdc-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="49fdc-207">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="49fdc-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="49fdc-208">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="49fdc-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="49fdc-209">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="49fdc-209">\<binding></span></span>](../../../misc/binding.md)
