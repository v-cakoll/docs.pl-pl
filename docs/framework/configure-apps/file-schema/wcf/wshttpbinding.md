---
title: <wsHttpBinding>
description: Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie HTTP odpowiednie dla kontraktów usługi non-Duplex, które implementują obsługę protokołu WS-niezawodny i usługi WS-Security.
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: d603f699145622cb1b70ecf99ea542572e841eac
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243987"
---
# \<wsHttpBinding>
<span data-ttu-id="d2438-102">Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie odpowiednie dla kontraktów usługi non-Duplex.</span><span class="sxs-lookup"><span data-stu-id="d2438-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="d2438-103">Powiązanie implementuje następujące specyfikacje: niezawodna obsługa komunikatów w usłudze WS i zabezpieczeniach WS-Security na potrzeby zabezpieczeń i uwierzytelniania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d2438-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="d2438-104">Transport to HTTP, a kodowanie wiadomości to kodowanie Text/XML.</span><span class="sxs-lookup"><span data-stu-id="d2438-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="d2438-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2438-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2438-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2438-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d2438-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2438-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2438-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2438-108">Attributes</span></span>  
  
|<span data-ttu-id="d2438-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d2438-109">Attribute</span></span>|<span data-ttu-id="d2438-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d2438-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2438-111">allowCookies</span><span class="sxs-lookup"><span data-stu-id="d2438-111">allowCookies</span></span>|<span data-ttu-id="d2438-112">Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="d2438-112">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="d2438-113">Wartością domyślną jest false.</span><span class="sxs-lookup"><span data-stu-id="d2438-113">The default is false.</span></span><br /><br /> <span data-ttu-id="d2438-114">Tej właściwości można użyć podczas współpracy z usługami sieci Web ASMX, które korzystają z plików cookie.</span><span class="sxs-lookup"><span data-stu-id="d2438-114">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="d2438-115">W ten sposób można mieć pewność, że pliki cookie zwrócone z serwera są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="d2438-115">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="d2438-116">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="d2438-116">bypassProxyOnLocal</span></span>|<span data-ttu-id="d2438-117">Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="d2438-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="d2438-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="d2438-118">The default is `false`.</span></span>|  
|<span data-ttu-id="d2438-119">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="d2438-119">closeTimeout</span></span>|<span data-ttu-id="d2438-120"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="d2438-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d2438-121">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d2438-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d2438-122">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d2438-122">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d2438-123">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="d2438-123">hostnameComparisonMode</span></span>|<span data-ttu-id="d2438-124">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="d2438-124">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="d2438-125">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> , który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d2438-125">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="d2438-126">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="d2438-126">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="d2438-127">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="d2438-127">maxBufferPoolSize</span></span>|<span data-ttu-id="d2438-128">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2438-128">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="d2438-129">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="d2438-129">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="d2438-130">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="d2438-130">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="d2438-131">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="d2438-131">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="d2438-132">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="d2438-132">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="d2438-133">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="d2438-133">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="d2438-134">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="d2438-134">maxReceivedMessageSize</span></span>|<span data-ttu-id="d2438-135">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2438-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="d2438-136">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d2438-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="d2438-137">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d2438-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d2438-138">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="d2438-138">The default is 65536.</span></span>|  
|<span data-ttu-id="d2438-139">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="d2438-139">messageEncoding</span></span>|<span data-ttu-id="d2438-140">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d2438-140">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="d2438-141">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="d2438-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d2438-142">-Text: Użyj kodera wiadomości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="d2438-142">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="d2438-143">-MTOM: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="d2438-143">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="d2438-144">-Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="d2438-144">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="d2438-145">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="d2438-145">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="d2438-146">name</span><span class="sxs-lookup"><span data-stu-id="d2438-146">name</span></span>|<span data-ttu-id="d2438-147">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2438-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d2438-148">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2438-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d2438-149">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="d2438-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d2438-150">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d2438-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="d2438-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="d2438-151">openTimeout</span></span>|<span data-ttu-id="d2438-152"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="d2438-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d2438-153">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d2438-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d2438-154">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d2438-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d2438-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="d2438-155">proxyAddress</span></span>|<span data-ttu-id="d2438-156">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2438-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="d2438-157">Jeśli `useSystemWebProxy` jest `true` , to ustawienie musi być `null` .</span><span class="sxs-lookup"><span data-stu-id="d2438-157">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="d2438-158">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="d2438-158">The default is `null`.</span></span>|  
|<span data-ttu-id="d2438-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="d2438-159">receiveTimeout</span></span>|<span data-ttu-id="d2438-160">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="d2438-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d2438-161">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d2438-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d2438-162">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d2438-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d2438-163">Właściwości SendTimeout</span><span class="sxs-lookup"><span data-stu-id="d2438-163">sendTimeout</span></span>|<span data-ttu-id="d2438-164"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="d2438-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d2438-165">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d2438-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d2438-166">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d2438-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d2438-167">TextEncoding</span><span class="sxs-lookup"><span data-stu-id="d2438-167">textEncoding</span></span>|<span data-ttu-id="d2438-168">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="d2438-168">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d2438-169">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="d2438-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d2438-170">-UnicodeFffeTextEncoding: kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="d2438-170">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="d2438-171">-Utf16TextEncoding: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="d2438-171">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="d2438-172">-Utf8TextEncoding: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="d2438-172">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="d2438-173">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="d2438-173">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="d2438-174">Ten atrybut jest typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="d2438-174">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="d2438-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="d2438-175">transactionFlow</span></span>|<span data-ttu-id="d2438-176">Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="d2438-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="d2438-177">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="d2438-177">The default is `false`.</span></span>|  
|<span data-ttu-id="d2438-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="d2438-178">useDefaultWebProxy</span></span>|<span data-ttu-id="d2438-179">Wartość logiczna określająca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2438-179">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="d2438-180">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="d2438-180">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2438-181">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2438-181">Child Elements</span></span>  
  
|<span data-ttu-id="d2438-182">Element</span><span class="sxs-lookup"><span data-stu-id="d2438-182">Element</span></span>|<span data-ttu-id="d2438-183">Opis</span><span class="sxs-lookup"><span data-stu-id="d2438-183">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="d2438-184">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2438-184">Defines the security settings for the binding.</span></span> <span data-ttu-id="d2438-185">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="d2438-185">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="d2438-186">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2438-186">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d2438-187">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="d2438-187">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="d2438-188">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="d2438-188">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2438-189">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2438-189">Parent Elements</span></span>  
  
|<span data-ttu-id="d2438-190">Element</span><span class="sxs-lookup"><span data-stu-id="d2438-190">Element</span></span>|<span data-ttu-id="d2438-191">Opis</span><span class="sxs-lookup"><span data-stu-id="d2438-191">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="d2438-192">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d2438-192">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2438-193">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2438-193">Remarks</span></span>  
 <span data-ttu-id="d2438-194">`WSHttpBinding`Jest podobna do, `BasicHttpBinding` ale udostępnia więcej funkcji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d2438-194">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="d2438-195">Korzysta ona z transportu HTTP i zapewnia zabezpieczenia komunikatów, jak BasicHttpBinding, ale udostępnia również transakcje, niezawodne komunikaty i adresy WS-Addressing, które są domyślnie włączone lub dostępne za pośrednictwem jednego ustawienia formantu.</span><span class="sxs-lookup"><span data-stu-id="d2438-195">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2438-196">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2438-196">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2438-197">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2438-197">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="d2438-198">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d2438-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d2438-199">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d2438-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d2438-200">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d2438-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
