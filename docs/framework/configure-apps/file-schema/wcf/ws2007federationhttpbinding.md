---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 20ba643fddbac8a488e5457f0195cc253d4d23f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139313"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="08c50-101">Bezpieczne i interoperacyjne powiązanie, które wynika z [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) i obsługuje zabezpieczenia federacyjne.</span><span class="sxs-lookup"><span data-stu-id="08c50-101">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="08c50-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="08c50-102">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08c50-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="08c50-103">Attributes and Elements</span></span>

<span data-ttu-id="08c50-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="08c50-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="08c50-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="08c50-105">Attributes</span></span>

|<span data-ttu-id="08c50-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="08c50-106">Attribute</span></span>|<span data-ttu-id="08c50-107">Opis</span><span class="sxs-lookup"><span data-stu-id="08c50-107">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="08c50-108">Wartość wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="08c50-108">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="08c50-109">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="08c50-109">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="08c50-110"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="08c50-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="08c50-111">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="08c50-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08c50-112">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="08c50-112">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="08c50-113">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="08c50-113">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="08c50-114">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> , który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="08c50-114">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="08c50-115">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="08c50-115">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="08c50-116">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="08c50-116">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="08c50-117">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="08c50-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="08c50-118">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="08c50-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="08c50-119">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="08c50-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="08c50-120">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="08c50-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="08c50-121">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="08c50-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="08c50-122">Maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które można odbierać w kanale skonfigurowanym za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="08c50-122">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="08c50-123">Nadawca komunikatu, który przekracza ten limit, odbiera błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="08c50-123">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="08c50-124">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="08c50-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="08c50-125">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="08c50-125">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="08c50-126">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="08c50-126">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="08c50-127">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="08c50-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="08c50-128">-Text: Użyj kodera wiadomości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="08c50-128">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="08c50-129">-MTOM: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="08c50-129">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="08c50-130">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="08c50-130">The default is Text.</span></span><br /><br /> <span data-ttu-id="08c50-131">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="08c50-131">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="08c50-132">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="08c50-132">The configuration name of the binding.</span></span> <span data-ttu-id="08c50-133">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="08c50-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="08c50-134">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="08c50-134">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="08c50-135">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="08c50-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="08c50-136"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="08c50-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="08c50-137">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="08c50-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08c50-138">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="08c50-138">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="08c50-139">Identyfikator URI, w którym znajduje się powiadomienie dotyczące zachowania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="08c50-139">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="08c50-140">Wersja bieżącego powiadomienia o ochronie prywatności.</span><span class="sxs-lookup"><span data-stu-id="08c50-140">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="08c50-141">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="08c50-141">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="08c50-142">Jeśli `useDefaultWebProxy` jest `true` , to ustawienie musi być `null` .</span><span class="sxs-lookup"><span data-stu-id="08c50-142">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="08c50-143">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="08c50-143">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="08c50-144">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="08c50-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="08c50-145">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="08c50-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08c50-146">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="08c50-146">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="08c50-147"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="08c50-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="08c50-148">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="08c50-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08c50-149">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="08c50-149">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="08c50-150">Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="08c50-150">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="08c50-151">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="08c50-151">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="08c50-152">-BigEndianUnicode: kodowanie Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="08c50-152">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="08c50-153">-Unicode: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="08c50-153">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="08c50-154">-UTF8: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="08c50-154">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="08c50-155">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="08c50-155">The default is UTF8.</span></span> <span data-ttu-id="08c50-156">Ten atrybut jest typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="08c50-156">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="08c50-157">Wartość określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="08c50-157">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="08c50-158">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="08c50-158">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="08c50-159">Wartość wskazująca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="08c50-159">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="08c50-160">Jeśli ten atrybut ma wartość, adres serwera proxy musi mieć `null` wartość (czyli nie jest ustawiony) `true` .</span><span class="sxs-lookup"><span data-stu-id="08c50-160">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="08c50-161">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="08c50-161">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="08c50-162">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="08c50-162">Child Elements</span></span>

|<span data-ttu-id="08c50-163">Element</span><span class="sxs-lookup"><span data-stu-id="08c50-163">Element</span></span>|<span data-ttu-id="08c50-164">Opis</span><span class="sxs-lookup"><span data-stu-id="08c50-164">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="08c50-165">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="08c50-165">Defines the security settings for the message.</span></span> <span data-ttu-id="08c50-166">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="08c50-166">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="08c50-167">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="08c50-167">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="08c50-168">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="08c50-168">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="08c50-169">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="08c50-169">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="08c50-170">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="08c50-170">Parent Elements</span></span>

|<span data-ttu-id="08c50-171">Element</span><span class="sxs-lookup"><span data-stu-id="08c50-171">Element</span></span>|<span data-ttu-id="08c50-172">Opis</span><span class="sxs-lookup"><span data-stu-id="08c50-172">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="08c50-173">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="08c50-173">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="08c50-174">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08c50-174">Remarks</span></span>

<span data-ttu-id="08c50-175">Federacja jest możliwością udostępniania tożsamości w wielu przedsiębiorstwach lub domenach zaufania na potrzeby uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="08c50-175">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="08c50-176">Używa protokołu WS-Trust, aby zamapować reprezentację tożsamości z jednej domeny zaufania na inną.</span><span class="sxs-lookup"><span data-stu-id="08c50-176">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="08c50-177">Federacyjne powiązanie HTTP obsługuje zabezpieczenia protokołu SOAP oraz zabezpieczenia w trybie mieszanym, ale nie obsługuje zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="08c50-177">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="08c50-178">Usługi skonfigurowane przy użyciu tego powiązania muszą korzystać z transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="08c50-178">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="08c50-179">Aby uzyskać więcej informacji, zobacz [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="08c50-179">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="08c50-180">Przykład</span><span class="sxs-lookup"><span data-stu-id="08c50-180">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="08c50-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08c50-181">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="08c50-182">Powiązania</span><span class="sxs-lookup"><span data-stu-id="08c50-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="08c50-183">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="08c50-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="08c50-184">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="08c50-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
