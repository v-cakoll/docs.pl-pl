---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: cdaaacf0dfa75209d001f6e8d6ac7175816048aa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140793"
---
# \<customBinding>

<span data-ttu-id="1e467-101">Zapewnia pełną kontrolę nad stosem obsługi komunikatów dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1e467-101">Provides full control over the messaging stack for the user.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**  

## <a name="syntax"></a><span data-ttu-id="1e467-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e467-102">Syntax</span></span>

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e467-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1e467-103">Attributes and Elements</span></span>

<span data-ttu-id="1e467-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1e467-104">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="1e467-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1e467-105">Attributes</span></span>

|<span data-ttu-id="1e467-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1e467-106">Attribute</span></span>|<span data-ttu-id="1e467-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1e467-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="1e467-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="1e467-108">closeTimeout</span></span>|<span data-ttu-id="1e467-109"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1e467-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1e467-110">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1e467-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1e467-111">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1e467-111">The default is 00:01:00.</span></span>|
|<span data-ttu-id="1e467-112">name</span><span class="sxs-lookup"><span data-stu-id="1e467-112">name</span></span>|<span data-ttu-id="1e467-113">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="1e467-113">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1e467-114">Ta wartość jest ciągiem zdefiniowanym przez użytkownika, który działa jako ciąg identyfikacyjny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1e467-114">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="1e467-115">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="1e467-115">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1e467-116">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1e467-116">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="1e467-117">openTimeout</span><span class="sxs-lookup"><span data-stu-id="1e467-117">openTimeout</span></span>|<span data-ttu-id="1e467-118"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="1e467-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1e467-119">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1e467-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1e467-120">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1e467-120">The default is 00:01:00.</span></span>|
|<span data-ttu-id="1e467-121">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="1e467-121">receiveTimeout</span></span>|<span data-ttu-id="1e467-122">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="1e467-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1e467-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1e467-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1e467-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1e467-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="1e467-125">Właściwości SendTimeout</span><span class="sxs-lookup"><span data-stu-id="1e467-125">sendTimeout</span></span>|<span data-ttu-id="1e467-126"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1e467-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1e467-127">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1e467-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1e467-128">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1e467-128">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1e467-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1e467-129">Child Elements</span></span>

|<span data-ttu-id="1e467-130">Element</span><span class="sxs-lookup"><span data-stu-id="1e467-130">Element</span></span>|<span data-ttu-id="1e467-131">Opis</span><span class="sxs-lookup"><span data-stu-id="1e467-131">Description</span></span>|
|-------------|-----------------|
|[\<compositeDuplex>](compositeduplex.md)|<span data-ttu-id="1e467-132">Określa komunikat dwukierunkowy dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1e467-132">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="1e467-133">Jest on używany z transportami, które nie zezwalają na natywną komunikację bezstronną, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="1e467-133">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="1e467-134">Protokół TCP, w przeciwieństwie, umożliwia natywną komunikację bezstronną i nie wymaga użycia tego elementu powiązania dla usługi do wysyłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="1e467-134">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="1e467-135">Klient musi uwidocznić adres usługi, aby nawiązać kontakt i nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="1e467-135">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="1e467-136">Ten adres klienta jest dostarczany przez `ClientBaseAddress` atrybut.</span><span class="sxs-lookup"><span data-stu-id="1e467-136">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="1e467-137">Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement> .</span><span class="sxs-lookup"><span data-stu-id="1e467-137">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[\<pnrpPeerResolver>](pnrppeerresolver.md)|<span data-ttu-id="1e467-138">Określa program rozpoznawania nazw elementów równorzędnych protokołu PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="1e467-138">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="1e467-139">Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement> .</span><span class="sxs-lookup"><span data-stu-id="1e467-139">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[\<reliableSession>](reliablesession.md)|<span data-ttu-id="1e467-140">Określa ustawienie dla obsługi komunikatów w usłudze WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="1e467-140">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="1e467-141">Gdy ten element zostanie dodany do niestandardowego powiązania, otrzymany kanał może obsługiwać tylko jednokrotne gwarancje dostarczania.</span><span class="sxs-lookup"><span data-stu-id="1e467-141">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="1e467-142">Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement> .</span><span class="sxs-lookup"><span data-stu-id="1e467-142">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="1e467-143">Określa opcje zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1e467-143">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="1e467-144">Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="1e467-144">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[\<sslStreamSecurity>](sslstreamsecurity.md)|<span data-ttu-id="1e467-145">Określa ustawienia zabezpieczeń dla powiązania strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="1e467-145">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="1e467-146">Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="1e467-146">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[\<transactionFlow>](transactionflow.md)|<span data-ttu-id="1e467-147">Określa, że powiązanie obsługuje przepływ transakcji, oraz protokołu, który ma być używany przez `transactionProtocol` atrybut.</span><span class="sxs-lookup"><span data-stu-id="1e467-147">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="1e467-148">Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement> .</span><span class="sxs-lookup"><span data-stu-id="1e467-148">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[\<windowsStreamSecurity>](windowsstreamsecurity.md)|<span data-ttu-id="1e467-149">Określa opcje zabezpieczeń przesyłania strumieniowego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1e467-149">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="1e467-150">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="1e467-150">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1e467-151">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1e467-151">Parent Elements</span></span>

|<span data-ttu-id="1e467-152">Element</span><span class="sxs-lookup"><span data-stu-id="1e467-152">Element</span></span>|<span data-ttu-id="1e467-153">Opis</span><span class="sxs-lookup"><span data-stu-id="1e467-153">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="1e467-154">powiązania</span><span class="sxs-lookup"><span data-stu-id="1e467-154">bindings</span></span>|<span data-ttu-id="1e467-155">Zawiera wszystkie powiązania dla Windows Communication Foundation aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1e467-155">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1e467-156">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e467-156">Remarks</span></span>

<span data-ttu-id="1e467-157">Niestandardowe powiązania zapewniają pełną kontrolę nad stosem obsługi komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="1e467-157">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="1e467-158">Można utworzyć specjalne powiązania dostosowane, dodając elementy konfiguracji dla określonych jednostek.</span><span class="sxs-lookup"><span data-stu-id="1e467-158">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="1e467-159">Na przykład użytkownik może połączyć `httpsTransport` sekcję, `reliableSession` sekcję i `security` sekcję, aby utworzyć niezawodne i bezpieczne powiązanie https.</span><span class="sxs-lookup"><span data-stu-id="1e467-159">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="1e467-160">Pojedyncze powiązanie definiuje stos komunikatów przez określenie elementów konfiguracji dla elementów stosu w kolejności, w jakiej występują na stosie.</span><span class="sxs-lookup"><span data-stu-id="1e467-160">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="1e467-161">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="1e467-161">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="1e467-162">W każdym powiązaniu niestandardowym musi istnieć jeden i tylko jeden element transportu.</span><span class="sxs-lookup"><span data-stu-id="1e467-162">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="1e467-163">Bez tego elementu stos komunikatów jest niekompletny.</span><span class="sxs-lookup"><span data-stu-id="1e467-163">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="1e467-164">Kolejność, w której elementy pojawiają się w kwestiach stosu, ponieważ jest to kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1e467-164">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="1e467-165">Zalecana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="1e467-165">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="1e467-166">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="1e467-166">Transactions (optional)</span></span>

2. <span data-ttu-id="1e467-167">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="1e467-167">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="1e467-168">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="1e467-168">Security (optional)</span></span>

4. <span data-ttu-id="1e467-169">Transport</span><span class="sxs-lookup"><span data-stu-id="1e467-169">Transport</span></span>

5. <span data-ttu-id="1e467-170">Koder (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="1e467-170">Encoder (optional)</span></span>

<span data-ttu-id="1e467-171">Użyj niestandardowego powiązania, gdy jedno z powiązań dostarczonych przez system nie spełnia wymagań usługi.</span><span class="sxs-lookup"><span data-stu-id="1e467-171">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="1e467-172">Można na przykład użyć niestandardowego powiązania, aby umożliwić korzystanie z nowego lub nowego kodera w punkcie końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="1e467-172">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="1e467-173">Niestandardowe powiązanie jest konstruowane przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> kolekcji elementów powiązania, które są "ułożone" w określonej kolejności:</span><span class="sxs-lookup"><span data-stu-id="1e467-173">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="1e467-174">U góry jest opcjonalne <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , które umożliwia przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="1e467-174">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="1e467-175">Następnie jest opcjonalne <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> , które udostępnia mechanizm sesji i kolejności, zgodnie z definicją w specyfikacji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="1e467-175">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="1e467-176">To pojęcie sesji może przekroczyć pośredniki SOAP i transportu.</span><span class="sxs-lookup"><span data-stu-id="1e467-176">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="1e467-177">Dalej jest opcjonalny element powiązania zabezpieczeń, który zapewnia funkcje zabezpieczeń, takie jak autoryzacja, uwierzytelnianie, ochrona i poufność.</span><span class="sxs-lookup"><span data-stu-id="1e467-177">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="1e467-178">Następujące elementy powiązań zabezpieczeń są udostępniane przez Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="1e467-178">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="1e467-179">Następnie są opcjonalne wzorce komunikatów określone przez elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="1e467-179">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="1e467-180">Poniżej przedstawiono opcjonalne elementy powiązania uaktualnienia/pomocnika transportu:</span><span class="sxs-lookup"><span data-stu-id="1e467-180">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="1e467-181">Następnie jest wymagany element powiązania kodowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1e467-181">Next is a required message encoding binding element.</span></span> <span data-ttu-id="1e467-182">Możesz użyć własnego transportu lub użyć jednego z następujących powiązań kodowania komunikatów:</span><span class="sxs-lookup"><span data-stu-id="1e467-182">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="1e467-183">U dołu jest wymagany element transportu.</span><span class="sxs-lookup"><span data-stu-id="1e467-183">At the bottom is a required transport element.</span></span> <span data-ttu-id="1e467-184">Możesz użyć własnego transportu lub użyć jednego z elementów powiązania transportowego dostarczonych przez Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="1e467-184">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="1e467-185">Poniższa tabela zawiera podsumowanie opcji dla każdej warstwy.</span><span class="sxs-lookup"><span data-stu-id="1e467-185">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="1e467-186">Warstwa</span><span class="sxs-lookup"><span data-stu-id="1e467-186">Layer</span></span>|<span data-ttu-id="1e467-187">Opcje</span><span class="sxs-lookup"><span data-stu-id="1e467-187">Options</span></span>|<span data-ttu-id="1e467-188">Wymagane</span><span class="sxs-lookup"><span data-stu-id="1e467-188">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="1e467-189">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="1e467-189">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="1e467-190">Nie</span><span class="sxs-lookup"><span data-stu-id="1e467-190">No</span></span>|
|<span data-ttu-id="1e467-191">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="1e467-191">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="1e467-192">Nie</span><span class="sxs-lookup"><span data-stu-id="1e467-192">No</span></span>|
|<span data-ttu-id="1e467-193">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="1e467-193">Security</span></span>|<span data-ttu-id="1e467-194">Symetryczne, asymetryczne, na poziomie transportu</span><span class="sxs-lookup"><span data-stu-id="1e467-194">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="1e467-195">Nie</span><span class="sxs-lookup"><span data-stu-id="1e467-195">No</span></span>|
|<span data-ttu-id="1e467-196">Zmiana kształtu</span><span class="sxs-lookup"><span data-stu-id="1e467-196">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="1e467-197">Nie</span><span class="sxs-lookup"><span data-stu-id="1e467-197">No</span></span>|
|<span data-ttu-id="1e467-198">Uaktualnienia transportu</span><span class="sxs-lookup"><span data-stu-id="1e467-198">Transport Upgrades</span></span>|<span data-ttu-id="1e467-199">Strumień SSL, strumień systemu Windows, program rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="1e467-199">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="1e467-200">Nie</span><span class="sxs-lookup"><span data-stu-id="1e467-200">No</span></span>|
|<span data-ttu-id="1e467-201">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="1e467-201">Encoding</span></span>|<span data-ttu-id="1e467-202">Tekst, dane binarne, MTOM, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1e467-202">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="1e467-203">Tak</span><span class="sxs-lookup"><span data-stu-id="1e467-203">Yes</span></span>|
|<span data-ttu-id="1e467-204">Transport</span><span class="sxs-lookup"><span data-stu-id="1e467-204">Transport</span></span>|<span data-ttu-id="1e467-205">TCP, nazwane potoki, HTTP, HTTPS, typy usługi MSMQ, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1e467-205">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="1e467-206">Tak</span><span class="sxs-lookup"><span data-stu-id="1e467-206">Yes</span></span>|

<span data-ttu-id="1e467-207">Ponadto można definiować własne elementy powiązania i wstawiać je między wszystkimi wcześniej zdefiniowanymi warstwami.</span><span class="sxs-lookup"><span data-stu-id="1e467-207">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="1e467-208">Aby uzyskać informacje na temat sposobu użycia niestandardowego powiązania do modyfikacji powiązania dostarczonego przez system, zobacz [How to: Dostosowywanie podanego przez system powiązania](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="1e467-208">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e467-209">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e467-209">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="1e467-210">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1e467-210">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1e467-211">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="1e467-211">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1e467-212">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1e467-212">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1e467-213">CustomBinding — element</span><span class="sxs-lookup"><span data-stu-id="1e467-213">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="1e467-214">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1e467-214">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1e467-215">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="1e467-215">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1e467-216">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1e467-216">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
