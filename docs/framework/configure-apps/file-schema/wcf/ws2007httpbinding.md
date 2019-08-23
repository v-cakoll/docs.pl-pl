---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 2fb9f7a16a360ddd61e6f8b935f928ddfdeb6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915255"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="e6f21-101">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="e6f21-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="e6f21-102">Definiuje powiązanie interoperacyjne, które zapewnia obsługę prawidłowych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>elementów, <xref:System.ServiceModel.ReliableSession>i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> .</span><span class="sxs-lookup"><span data-stu-id="e6f21-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="e6f21-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e6f21-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e6f21-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="e6f21-104">\<bindings></span></span>  
<span data-ttu-id="e6f21-105">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="e6f21-105">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f21-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6f21-106">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
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
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6f21-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6f21-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e6f21-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e6f21-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6f21-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6f21-109">Attributes</span></span>  
  
|<span data-ttu-id="e6f21-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e6f21-110">Attribute</span></span>|<span data-ttu-id="e6f21-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e6f21-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="e6f21-112">Wartość wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="e6f21-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="e6f21-113">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="e6f21-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e6f21-114">Tej właściwości można użyć podczas korzystania z usług sieci Web ASP.NET (ASMX), które używają plików cookie.</span><span class="sxs-lookup"><span data-stu-id="e6f21-114">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="e6f21-115">Dzięki temu pliki cookie zwracane przez serwer są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e6f21-115">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="e6f21-116">Wartość wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e6f21-116">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="e6f21-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="e6f21-117">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="e6f21-118"><xref:System.TimeSpan> Wartość, która określa przedział czasu na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="e6f21-118">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="e6f21-119">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e6f21-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e6f21-120">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e6f21-120">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="e6f21-121">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="e6f21-121">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="e6f21-122">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="e6f21-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="e6f21-123">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="e6f21-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="e6f21-124">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6f21-124">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="e6f21-125">Wartość domyślna to 524 288 bajtów (512 × 1 024).</span><span class="sxs-lookup"><span data-stu-id="e6f21-125">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="e6f21-126">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="e6f21-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="e6f21-127">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne, ponieważ wyrzucanie elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="e6f21-127">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="e6f21-128">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="e6f21-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="e6f21-129">Pozwala to uniknąć nakładu pracy podczas tworzenia i niszczenia buforów.</span><span class="sxs-lookup"><span data-stu-id="e6f21-129">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="e6f21-130">Może zostać wyświetlony maksymalny rozmiar komunikatu (w bajtach), łącznie z nagłówkami, które zostały skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6f21-130">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="e6f21-131">Nadawca komunikatu przekraczającego ten limit odbiera błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e6f21-131">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="e6f21-132">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e6f21-132">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e6f21-133">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="e6f21-133">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="e6f21-134">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e6f21-134">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="e6f21-135">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="e6f21-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e6f21-136">-   `Text`: Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="e6f21-136">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="e6f21-137">-   `Mtom`: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="e6f21-137">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="e6f21-138">Wartość domyślna to `Text`.</span><span class="sxs-lookup"><span data-stu-id="e6f21-138">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="e6f21-139">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="e6f21-139">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="e6f21-140">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6f21-140">The configuration name of the binding.</span></span> <span data-ttu-id="e6f21-141">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6f21-141">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e6f21-142">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="e6f21-142">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e6f21-143">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e6f21-143">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e6f21-144"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="e6f21-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e6f21-145">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e6f21-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e6f21-146">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e6f21-146">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="e6f21-147">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="e6f21-147">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="e6f21-148">Jeśli `useSystemWebProxy` `null`jest `true`, to ustawienie musi być.</span><span class="sxs-lookup"><span data-stu-id="e6f21-148">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="e6f21-149">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="e6f21-149">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e6f21-150"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="e6f21-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e6f21-151">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e6f21-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e6f21-152">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e6f21-152">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e6f21-153"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e6f21-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e6f21-154">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e6f21-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e6f21-155">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e6f21-155">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="e6f21-156">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="e6f21-156">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="e6f21-157">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="e6f21-157">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e6f21-158">-   `UnicodeFffeTextEncoding`: Kodowanie Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="e6f21-158">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="e6f21-159">-   `Utf16TextEncoding`: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="e6f21-159">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="e6f21-160">-   `Utf8TextEncoding`: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="e6f21-160">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="e6f21-161">Wartość domyślna to `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="e6f21-161">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="e6f21-162">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e6f21-162">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="e6f21-163">Wartość określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="e6f21-163">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="e6f21-164">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="e6f21-164">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="e6f21-165">Wartość określająca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="e6f21-165">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="e6f21-166">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="e6f21-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6f21-167">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6f21-167">Child Elements</span></span>  
  
|<span data-ttu-id="e6f21-168">Element</span><span class="sxs-lookup"><span data-stu-id="e6f21-168">Element</span></span>|<span data-ttu-id="e6f21-169">Opis</span><span class="sxs-lookup"><span data-stu-id="e6f21-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6f21-170">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e6f21-170">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="e6f21-171">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6f21-171">Defines the security settings for the binding.</span></span> <span data-ttu-id="e6f21-172">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e6f21-172">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="e6f21-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e6f21-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e6f21-174">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które można przetwarzać za pomocą punktów końcowych skonfigurowanych dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6f21-174">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="e6f21-175">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e6f21-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="e6f21-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e6f21-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="e6f21-177">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="e6f21-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6f21-178">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6f21-178">Parent Elements</span></span>  
  
|<span data-ttu-id="e6f21-179">Element</span><span class="sxs-lookup"><span data-stu-id="e6f21-179">Element</span></span>|<span data-ttu-id="e6f21-180">Opis</span><span class="sxs-lookup"><span data-stu-id="e6f21-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6f21-181">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="e6f21-181">\<bindings></span></span>](bindings.md)|<span data-ttu-id="e6f21-182">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e6f21-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6f21-183">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6f21-183">Remarks</span></span>  
 <span data-ttu-id="e6f21-184">Dodaje do programu powiązanie dostarczone z systemem, które `WSHttpBinding` jest podobne do programu, ale używa organizacji do rozwoju standardowych wersji standardu języka Oasis (Structured Information Standards) ReliableSession, Security i TransactionFlow Protocols. `WS2007HttpBinding`</span><span class="sxs-lookup"><span data-stu-id="e6f21-184">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="e6f21-185">W przypadku korzystania z tego powiązania nie są wymagane żadne zmiany w modelu obiektu ani w ustawieniach domyślnych.</span><span class="sxs-lookup"><span data-stu-id="e6f21-185">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6f21-186">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6f21-186">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
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
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e6f21-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6f21-187">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="e6f21-188">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e6f21-188">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6f21-189">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e6f21-189">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e6f21-190">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e6f21-190">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e6f21-191">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="e6f21-191">\<binding></span></span>](../../../misc/binding.md)
