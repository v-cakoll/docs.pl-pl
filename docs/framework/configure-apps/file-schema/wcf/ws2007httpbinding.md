---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 9caba8dfc848a2463b1fa482ccaf55288d96af29
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182152"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="ccef1-101">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="ccef1-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="ccef1-102">Definiuje interoperacyjne powiązanie, które zapewnia obsługę dla poprawnych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="ccef1-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ccef1-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ccef1-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ccef1-104">\<bindings></span></span>  
<span data-ttu-id="ccef1-105">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="ccef1-105">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccef1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccef1-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccef1-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ccef1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ccef1-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ccef1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccef1-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ccef1-109">Attributes</span></span>  
  
|<span data-ttu-id="ccef1-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ccef1-110">Attribute</span></span>|<span data-ttu-id="ccef1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ccef1-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="ccef1-112">Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="ccef1-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="ccef1-113">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ccef1-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="ccef1-114">Można użyć tej właściwości, gdy wchodzisz w interakcję z usług sieci Web platformy ASP.NET (ASMX), które używają plików cookie.</span><span class="sxs-lookup"><span data-stu-id="ccef1-114">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="ccef1-115">Daje to gwarancję, że pliki cookie, które serwer zwraca są automatycznie kopiowane do wszystkich przyszłych żądań za daną usługę.</span><span class="sxs-lookup"><span data-stu-id="ccef1-115">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="ccef1-116">Wartość, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="ccef1-116">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="ccef1-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ccef1-117">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="ccef1-118">A <xref:System.TimeSpan> wartość, która określa przedział czasu na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="ccef1-118">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="ccef1-119">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ccef1-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ccef1-120">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ccef1-120">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="ccef1-121">Określa tryb porównywania nazwy hosta HTTP używany do analizowania Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="ccef1-121">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="ccef1-122">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="ccef1-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="ccef1-123">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="ccef1-124">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-124">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="ccef1-125">Wartość domyślna to 524,288 bajtów (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="ccef1-125">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="ccef1-126">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="ccef1-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="ccef1-127">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, podobnie jak wyrzucanie elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="ccef1-127">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="ccef1-128">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="ccef1-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="ccef1-129">Umożliwia to uniknięcie obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="ccef1-129">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="ccef1-130">Maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, które mogą odbierać kanał, który został skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="ccef1-130">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="ccef1-131">Nadawca wiadomości przekroczenie tego limitu otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ccef1-131">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="ccef1-132">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ccef1-132">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="ccef1-133">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="ccef1-133">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="ccef1-134">Definiuje encoder umożliwia kodowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ccef1-134">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="ccef1-135">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ccef1-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ccef1-136">-   `Text`: Za pomocą kodera komunikatów tekstu.</span><span class="sxs-lookup"><span data-stu-id="ccef1-136">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="ccef1-137">-   `Mtom`: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="ccef1-137">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="ccef1-138">Wartość domyślna to `Text`.</span><span class="sxs-lookup"><span data-stu-id="ccef1-138">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="ccef1-139">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="ccef1-139">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="ccef1-140">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-140">The configuration name of the binding.</span></span> <span data-ttu-id="ccef1-141">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-141">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ccef1-142">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="ccef1-142">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ccef1-143">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ccef1-143">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="ccef1-144">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="ccef1-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ccef1-145">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ccef1-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ccef1-146">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ccef1-146">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="ccef1-147">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="ccef1-147">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="ccef1-148">Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="ccef1-148">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="ccef1-149">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="ccef1-149">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ccef1-150">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ccef1-151">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ccef1-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ccef1-152">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ccef1-152">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="ccef1-153">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ccef1-154">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ccef1-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ccef1-155">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ccef1-155">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="ccef1-156">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="ccef1-156">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="ccef1-157">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ccef1-157">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ccef1-158">-   `UnicodeFffeTextEncoding`: Big Endian kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="ccef1-158">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="ccef1-159">-   `Utf16TextEncoding`: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-159">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="ccef1-160">-   `Utf8TextEncoding`: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-160">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="ccef1-161">Wartość domyślna to `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="ccef1-161">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="ccef1-162">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="ccef1-162">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="ccef1-163">Wartość, która określa, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="ccef1-163">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="ccef1-164">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ccef1-164">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="ccef1-165">Wartość, która określa, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="ccef1-165">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="ccef1-166">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="ccef1-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccef1-167">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ccef1-167">Child Elements</span></span>  
  
|<span data-ttu-id="ccef1-168">Element</span><span class="sxs-lookup"><span data-stu-id="ccef1-168">Element</span></span>|<span data-ttu-id="ccef1-169">Opis</span><span class="sxs-lookup"><span data-stu-id="ccef1-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccef1-170">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="ccef1-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="ccef1-171">Definiuje ustawienia zabezpieczeń dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-171">Defines the security settings for the binding.</span></span> <span data-ttu-id="ccef1-172">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ccef1-172">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="ccef1-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ccef1-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="ccef1-174">Definiuje ograniczenia złożoności wiadomości SOAP, które może przetworzyć punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-174">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="ccef1-175">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="ccef1-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="ccef1-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ccef1-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="ccef1-177">Określa, czy niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="ccef1-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ccef1-178">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ccef1-178">Parent Elements</span></span>  
  
|<span data-ttu-id="ccef1-179">Element</span><span class="sxs-lookup"><span data-stu-id="ccef1-179">Element</span></span>|<span data-ttu-id="ccef1-180">Opis</span><span class="sxs-lookup"><span data-stu-id="ccef1-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccef1-181">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ccef1-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="ccef1-182">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ccef1-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccef1-183">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ccef1-183">Remarks</span></span>  
 <span data-ttu-id="ccef1-184">`WS2007HttpBinding` Dodaje podobne do powiązania dostarczane przez system `WSHttpBinding` , ale organizacji dla wersji standardowa zawodowego of Structured Information Standards (OASIS) protokołów TransactionFlow, ReliableSession i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ccef1-184">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="ccef1-185">Brak zmian do obiektu modelu lub domyślne ustawienia są wymagane, gdy za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ccef1-185">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccef1-186">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccef1-186">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ccef1-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccef1-187">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="ccef1-188">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ccef1-188">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ccef1-189">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ccef1-189">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ccef1-190">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ccef1-190">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ccef1-191">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ccef1-191">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
