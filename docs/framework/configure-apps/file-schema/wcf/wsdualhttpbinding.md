---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 01360ae8288b3cb7374597ad77935f634eb0a519
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139270"
---
# \<wsDualHttpBinding>
<span data-ttu-id="191c6-101">Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie, które jest odpowiednie dla kontraktów usługi dupleksowej lub komunikacji za pośrednictwem pośredników SOAP.</span><span class="sxs-lookup"><span data-stu-id="191c6-101">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="191c6-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="191c6-102">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
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
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="191c6-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="191c6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="191c6-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="191c6-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="191c6-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="191c6-105">Attributes</span></span>  
  
|<span data-ttu-id="191c6-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="191c6-106">Attribute</span></span>|<span data-ttu-id="191c6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="191c6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="191c6-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="191c6-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="191c6-109">Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="191c6-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="191c6-110">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="191c6-110">The default is `false`.</span></span>|  
|<span data-ttu-id="191c6-111">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="191c6-111">clientBaseAddress</span></span>|<span data-ttu-id="191c6-112">Identyfikator URI, który ustawia adres bazowy, do którego klient nasłuchuje komunikatów odpowiedzi z usługi.</span><span class="sxs-lookup"><span data-stu-id="191c6-112">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="191c6-113">Jeśli ta wartość jest określona, ten adres (plus channelGUID) jest używany do nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="191c6-113">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="191c6-114">Jeśli wartość nie jest określona, adres podstawowy klienta jest generowany w sposób specyficzny dla transportu.</span><span class="sxs-lookup"><span data-stu-id="191c6-114">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="191c6-115">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="191c6-115">The default is `null`.</span></span>|  
|<span data-ttu-id="191c6-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="191c6-116">closeTimeout</span></span>|<span data-ttu-id="191c6-117"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="191c6-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="191c6-118">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="191c6-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="191c6-119">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="191c6-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="191c6-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="191c6-120">hostnameComparisonMode</span></span>|<span data-ttu-id="191c6-121">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="191c6-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="191c6-122">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> , który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="191c6-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="191c6-123">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="191c6-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="191c6-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="191c6-124">maxBufferPoolSize</span></span>|<span data-ttu-id="191c6-125">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="191c6-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="191c6-126">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="191c6-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="191c6-127">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="191c6-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="191c6-128">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="191c6-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="191c6-129">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="191c6-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="191c6-130">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="191c6-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="191c6-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="191c6-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="191c6-132">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="191c6-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="191c6-133">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="191c6-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="191c6-134">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="191c6-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="191c6-135">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="191c6-135">The default is 65536.</span></span>|  
|<span data-ttu-id="191c6-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="191c6-136">messageEncoding</span></span>|<span data-ttu-id="191c6-137">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="191c6-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="191c6-138">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="191c6-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="191c6-139">-Text: Użyj kodera wiadomości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="191c6-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="191c6-140">-MTOM: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="191c6-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="191c6-141">-Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="191c6-141">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="191c6-142">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="191c6-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="191c6-143">name</span><span class="sxs-lookup"><span data-stu-id="191c6-143">name</span></span>|<span data-ttu-id="191c6-144">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="191c6-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="191c6-145">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="191c6-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="191c6-146">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="191c6-146">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="191c6-147">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="191c6-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="191c6-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="191c6-148">openTimeout</span></span>|<span data-ttu-id="191c6-149"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="191c6-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="191c6-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="191c6-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="191c6-151">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="191c6-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="191c6-152">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="191c6-152">proxyAddress</span></span>|<span data-ttu-id="191c6-153">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="191c6-153">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="191c6-154">Jeśli `useDefaultWebProxy` jest `true` , to ustawienie musi być `null` .</span><span class="sxs-lookup"><span data-stu-id="191c6-154">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="191c6-155">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="191c6-155">The default is `null`.</span></span>|  
|<span data-ttu-id="191c6-156">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="191c6-156">receiveTimeout</span></span>|<span data-ttu-id="191c6-157">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="191c6-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="191c6-158">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="191c6-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="191c6-159">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="191c6-159">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="191c6-160">Właściwości SendTimeout</span><span class="sxs-lookup"><span data-stu-id="191c6-160">sendTimeout</span></span>|<span data-ttu-id="191c6-161"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="191c6-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="191c6-162">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="191c6-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="191c6-163">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="191c6-163">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="191c6-164">TextEncoding</span><span class="sxs-lookup"><span data-stu-id="191c6-164">textEncoding</span></span>|<span data-ttu-id="191c6-165">Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="191c6-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="191c6-166">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="191c6-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="191c6-167">-BigEndianUnicode: kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="191c6-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="191c6-168">-Unicode: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="191c6-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="191c6-169">-UTF8: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="191c6-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="191c6-170">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="191c6-170">The default is UTF8.</span></span> <span data-ttu-id="191c6-171">Ten atrybut jest typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="191c6-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="191c6-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="191c6-172">transactionFlow</span></span>|<span data-ttu-id="191c6-173">Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="191c6-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="191c6-174">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="191c6-174">The default is `false`.</span></span>|  
|<span data-ttu-id="191c6-175">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="191c6-175">useDefaultWebProxy</span></span>|<span data-ttu-id="191c6-176">Wartość logiczna wskazująca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="191c6-176">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="191c6-177">Jeśli ten atrybut ma wartość, adres serwera proxy musi mieć `null` wartość (czyli nie jest ustawiony) `true` .</span><span class="sxs-lookup"><span data-stu-id="191c6-177">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="191c6-178">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="191c6-178">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="191c6-179">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="191c6-179">Child Elements</span></span>  
  
|<span data-ttu-id="191c6-180">Element</span><span class="sxs-lookup"><span data-stu-id="191c6-180">Element</span></span>|<span data-ttu-id="191c6-181">Opis</span><span class="sxs-lookup"><span data-stu-id="191c6-181">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="191c6-182">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="191c6-182">Defines the security settings for the binding.</span></span> <span data-ttu-id="191c6-183">Ten element jest typu <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="191c6-183">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="191c6-184">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="191c6-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="191c6-185">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="191c6-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="191c6-186">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="191c6-186">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="191c6-187">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="191c6-187">Parent Elements</span></span>  
  
|<span data-ttu-id="191c6-188">Element</span><span class="sxs-lookup"><span data-stu-id="191c6-188">Element</span></span>|<span data-ttu-id="191c6-189">Opis</span><span class="sxs-lookup"><span data-stu-id="191c6-189">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="191c6-190">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="191c6-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="191c6-191">Uwagi</span><span class="sxs-lookup"><span data-stu-id="191c6-191">Remarks</span></span>  
 <span data-ttu-id="191c6-192">`WSDualHttpBinding`Zapewnia taką samą obsługę protokołów usługi sieci Web jak `WSHttpBinding` , ale w przypadku kontraktów dupleksowych.</span><span class="sxs-lookup"><span data-stu-id="191c6-192">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="191c6-193">`WSDualHttpBinding`obsługuje tylko zabezpieczenia protokołu SOAP i wymaga niezawodnej obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="191c6-193">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="191c6-194">To powiązanie wymaga, aby klient miał publiczny identyfikator URI, który udostępnia punkt końcowy wywołania zwrotnego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="191c6-194">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="191c6-195">Jest to zapewniane przez `clientBaseAddress` atrybut.</span><span class="sxs-lookup"><span data-stu-id="191c6-195">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="191c6-196">Podwójne powiązanie uwidacznia adres IP klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="191c6-196">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="191c6-197">Klient powinien korzystać z zabezpieczeń, aby upewnić się, że tylko nawiązuje połączenie z usługami, które ufają.</span><span class="sxs-lookup"><span data-stu-id="191c6-197">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="191c6-198">To powiązanie może służyć do niezawodnego komunikowania się przez jeden lub więcej pośredników SOAP.</span><span class="sxs-lookup"><span data-stu-id="191c6-198">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="191c6-199">Domyślnie to powiązanie generuje stos środowiska uruchomieniowego z protokołem WS-ReliableMessaging w celu zapewnienia niezawodności, protokołu WS-Security na potrzeby zabezpieczeń i uwierzytelniania wiadomości, protokołu HTTP na potrzeby dostarczania komunikatów oraz kodowania wiadomości tekstowych/XML.</span><span class="sxs-lookup"><span data-stu-id="191c6-199">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="191c6-200">Przykład</span><span class="sxs-lookup"><span data-stu-id="191c6-200">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
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
  
## <a name="see-also"></a><span data-ttu-id="191c6-201">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="191c6-201">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="191c6-202">Powiązania</span><span class="sxs-lookup"><span data-stu-id="191c6-202">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="191c6-203">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="191c6-203">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="191c6-204">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="191c6-204">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
