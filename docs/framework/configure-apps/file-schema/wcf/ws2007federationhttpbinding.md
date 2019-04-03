---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: e6215465acbf9bb94298d282d15f8735a0e20c8c
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890257"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="870de-101">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="870de-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="870de-102">Bezpieczne i interoperacyjne powiązanie pochodzi od klasy [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i obsługuje federacyjnego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="870de-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <ws2007FederationHttpBinding>
```

## <a name="syntax"></a><span data-ttu-id="870de-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="870de-103">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="870de-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="870de-104">Attributes and Elements</span></span>

<span data-ttu-id="870de-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="870de-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="870de-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="870de-106">Attributes</span></span>

|<span data-ttu-id="870de-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="870de-107">Attribute</span></span>|<span data-ttu-id="870de-108">Opis</span><span class="sxs-lookup"><span data-stu-id="870de-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="870de-109">Wartość, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="870de-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="870de-110">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="870de-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="870de-111">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="870de-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="870de-112">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="870de-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="870de-113">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="870de-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="870de-114">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="870de-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="870de-115">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="870de-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="870de-116">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="870de-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="870de-117">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="870de-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="870de-118">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="870de-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="870de-119">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="870de-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="870de-120">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="870de-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="870de-121">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="870de-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="870de-122">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="870de-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="870de-123">Maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="870de-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="870de-124">Nadawca wiadomości, która przekracza ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="870de-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="870de-125">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="870de-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="870de-126">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="870de-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="870de-127">Definiuje encoder umożliwia kodowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="870de-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="870de-128">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="870de-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="870de-129">-Tekst: Za pomocą kodera komunikatów tekstu.</span><span class="sxs-lookup"><span data-stu-id="870de-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="870de-130">-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="870de-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="870de-131">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="870de-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="870de-132">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="870de-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="870de-133">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="870de-133">The configuration name of the binding.</span></span> <span data-ttu-id="870de-134">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="870de-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="870de-135">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="870de-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="870de-136">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="870de-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="870de-137">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="870de-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="870de-138">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="870de-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="870de-139">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="870de-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="870de-140">Identyfikator URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="870de-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="870de-141">Wersja bieżąca powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="870de-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="870de-142">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="870de-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="870de-143">Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="870de-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="870de-144">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="870de-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="870de-145">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="870de-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="870de-146">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="870de-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="870de-147">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="870de-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="870de-148">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="870de-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="870de-149">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="870de-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="870de-150">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="870de-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="870de-151">Określa kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="870de-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="870de-152">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="870de-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="870de-153">-BigEndianUnicode: Big Endian kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="870de-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="870de-154">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="870de-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="870de-155">-   UTF8: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="870de-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="870de-156">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="870de-156">The default is UTF8.</span></span> <span data-ttu-id="870de-157">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="870de-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="870de-158">Wartość, która określa, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="870de-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="870de-159">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="870de-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="870de-160">Wartość, która wskazuje, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="870de-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="870de-161">Adres serwera proxy musi być `null` (czyli nie ustawiono) Jeśli ten atrybut jest `true`.</span><span class="sxs-lookup"><span data-stu-id="870de-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="870de-162">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="870de-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="870de-163">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="870de-163">Child Elements</span></span>

|<span data-ttu-id="870de-164">Element</span><span class="sxs-lookup"><span data-stu-id="870de-164">Element</span></span>|<span data-ttu-id="870de-165">Opis</span><span class="sxs-lookup"><span data-stu-id="870de-165">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="870de-166">\<security></span><span class="sxs-lookup"><span data-stu-id="870de-166">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="870de-167">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="870de-167">Defines the security settings for the message.</span></span> <span data-ttu-id="870de-168">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="870de-168">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[<span data-ttu-id="870de-169">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="870de-169">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="870de-170">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="870de-170">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="870de-171">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="870de-171">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[<span data-ttu-id="870de-172">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="870de-172">\<reliableSession></span></span>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="870de-173">Określa, czy niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="870de-173">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="870de-174">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="870de-174">Parent Elements</span></span>

|<span data-ttu-id="870de-175">Element</span><span class="sxs-lookup"><span data-stu-id="870de-175">Element</span></span>|<span data-ttu-id="870de-176">Opis</span><span class="sxs-lookup"><span data-stu-id="870de-176">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="870de-177">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="870de-177">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="870de-178">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="870de-178">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="870de-179">Uwagi</span><span class="sxs-lookup"><span data-stu-id="870de-179">Remarks</span></span>

<span data-ttu-id="870de-180">Federacja znajduje się możliwość udostępniania tożsamości w wielu przedsiębiorstwach lub zaufania domen do uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="870de-180">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="870de-181">Używa protokołu WS-Trust do mapowania reprezentacji tożsamości z jednej relacji zaufania domeny do innego.</span><span class="sxs-lookup"><span data-stu-id="870de-181">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="870de-182">Federacyjnego powiązania HTTP obsługuje zabezpieczenia protokołu SOAP, a także trybu mieszanego zabezpieczeń, ale nie obsługuje zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="870de-182">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="870de-183">Skonfigurowano z tym powiązaniem usług, należy użyć protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="870de-183">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="870de-184">Aby uzyskać więcej informacji, zobacz [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="870de-184">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="870de-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="870de-185">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="870de-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="870de-186">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="870de-187">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="870de-187">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)
- [<span data-ttu-id="870de-188">Powiązania</span><span class="sxs-lookup"><span data-stu-id="870de-188">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="870de-189">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="870de-189">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="870de-190">Konfigurowanie usług i klientów za pomocą wiązań</span><span class="sxs-lookup"><span data-stu-id="870de-190">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="870de-191">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="870de-191">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
