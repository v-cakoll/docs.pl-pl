---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 0f0dc3ebe34ea45c1b464ff4fe437694ff4761f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399064"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="2be04-101">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="2be04-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="2be04-102">Definiuje powiązanie interoperacyjne, które zapewnia obsługę prawidłowych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>elementów, <xref:System.ServiceModel.ReliableSession>i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> .</span><span class="sxs-lookup"><span data-stu-id="2be04-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
<span data-ttu-id="2be04-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2be04-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2be04-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2be04-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2be04-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2be04-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2be04-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007HttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="2be04-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be04-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2be04-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2be04-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2be04-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2be04-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2be04-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2be04-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2be04-110">Attributes</span></span>  
  
|<span data-ttu-id="2be04-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2be04-111">Attribute</span></span>|<span data-ttu-id="2be04-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2be04-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="2be04-113">Wartość wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="2be04-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="2be04-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2be04-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="2be04-115">Tej właściwości można użyć podczas korzystania z usług sieci Web ASP.NET (ASMX), które używają plików cookie.</span><span class="sxs-lookup"><span data-stu-id="2be04-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="2be04-116">Dzięki temu pliki cookie zwracane przez serwer są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2be04-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="2be04-117">Wartość wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2be04-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="2be04-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2be04-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="2be04-119"><xref:System.TimeSpan> Wartość, która określa przedział czasu na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="2be04-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="2be04-120">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2be04-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2be04-121">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2be04-121">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="2be04-122">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="2be04-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="2be04-123">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="2be04-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="2be04-124">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="2be04-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="2be04-125">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2be04-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="2be04-126">Wartość domyślna to 524 288 bajtów (512 × 1 024).</span><span class="sxs-lookup"><span data-stu-id="2be04-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="2be04-127">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="2be04-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="2be04-128">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne, ponieważ wyrzucanie elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="2be04-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="2be04-129">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="2be04-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="2be04-130">Pozwala to uniknąć nakładu pracy podczas tworzenia i niszczenia buforów.</span><span class="sxs-lookup"><span data-stu-id="2be04-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="2be04-131">Może zostać wyświetlony maksymalny rozmiar komunikatu (w bajtach), łącznie z nagłówkami, które zostały skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2be04-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="2be04-132">Nadawca komunikatu przekraczającego ten limit odbiera błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="2be04-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="2be04-133">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2be04-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="2be04-134">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="2be04-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="2be04-135">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2be04-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="2be04-136">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2be04-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2be04-137">-   `Text`: Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="2be04-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="2be04-138">-   `Mtom`: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="2be04-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="2be04-139">Wartość domyślna to `Text`.</span><span class="sxs-lookup"><span data-stu-id="2be04-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="2be04-140">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="2be04-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="2be04-141">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="2be04-141">The configuration name of the binding.</span></span> <span data-ttu-id="2be04-142">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="2be04-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="2be04-143">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="2be04-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2be04-144">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2be04-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="2be04-145"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="2be04-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2be04-146">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2be04-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2be04-147">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2be04-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="2be04-148">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="2be04-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="2be04-149">Jeśli `useSystemWebProxy` `null`jest `true`, to ustawienie musi być.</span><span class="sxs-lookup"><span data-stu-id="2be04-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="2be04-150">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="2be04-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="2be04-151"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="2be04-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2be04-152">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2be04-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2be04-153">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2be04-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="2be04-154"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="2be04-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2be04-155">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2be04-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2be04-156">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2be04-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="2be04-157">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="2be04-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="2be04-158">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2be04-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2be04-159">-   `UnicodeFffeTextEncoding`: Kodowanie Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="2be04-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="2be04-160">-   `Utf16TextEncoding`: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="2be04-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="2be04-161">-   `Utf8TextEncoding`: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="2be04-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="2be04-162">Wartość domyślna to `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="2be04-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="2be04-163">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="2be04-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="2be04-164">Wartość określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="2be04-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="2be04-165">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2be04-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="2be04-166">Wartość określająca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="2be04-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="2be04-167">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2be04-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2be04-168">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2be04-168">Child Elements</span></span>  
  
|<span data-ttu-id="2be04-169">Element</span><span class="sxs-lookup"><span data-stu-id="2be04-169">Element</span></span>|<span data-ttu-id="2be04-170">Opis</span><span class="sxs-lookup"><span data-stu-id="2be04-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2be04-171">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2be04-171">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="2be04-172">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="2be04-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="2be04-173">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2be04-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="2be04-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2be04-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="2be04-175">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które można przetwarzać za pomocą punktów końcowych skonfigurowanych dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2be04-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="2be04-176">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="2be04-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="2be04-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2be04-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="2be04-178">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="2be04-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2be04-179">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2be04-179">Parent Elements</span></span>  
  
|<span data-ttu-id="2be04-180">Element</span><span class="sxs-lookup"><span data-stu-id="2be04-180">Element</span></span>|<span data-ttu-id="2be04-181">Opis</span><span class="sxs-lookup"><span data-stu-id="2be04-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2be04-182">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="2be04-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="2be04-183">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2be04-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2be04-184">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2be04-184">Remarks</span></span>  
 <span data-ttu-id="2be04-185">Dodaje do programu powiązanie dostarczone z systemem, które `WSHttpBinding` jest podobne do programu, ale używa organizacji do rozwoju standardowych wersji standardu języka Oasis (Structured Information Standards) ReliableSession, Security i TransactionFlow Protocols. `WS2007HttpBinding`</span><span class="sxs-lookup"><span data-stu-id="2be04-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="2be04-186">W przypadku korzystania z tego powiązania nie są wymagane żadne zmiany w modelu obiektu ani w ustawieniach domyślnych.</span><span class="sxs-lookup"><span data-stu-id="2be04-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2be04-187">Przykład</span><span class="sxs-lookup"><span data-stu-id="2be04-187">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2be04-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2be04-188">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="2be04-189">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2be04-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2be04-190">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="2be04-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2be04-191">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="2be04-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2be04-192">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="2be04-192">\<binding></span></span>](../../../misc/binding.md)
