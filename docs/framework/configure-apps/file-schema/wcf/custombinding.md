---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 0b6f26c7b9e9d02b3ff20b53f42b09d671699ea5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919390"
---
# <a name="custombinding"></a><span data-ttu-id="f2468-101">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f2468-101">\<customBinding></span></span>

<span data-ttu-id="f2468-102">Zapewnia pełną kontrolę nad stosem obsługi komunikatów dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f2468-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="f2468-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f2468-103">\<system.serviceModel></span></span>\
<span data-ttu-id="f2468-104">\<powiązania > </span><span class="sxs-lookup"><span data-stu-id="f2468-104">\<bindings></span></span>\
<span data-ttu-id="f2468-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f2468-105">\<customBinding></span></span>

## <a name="syntax"></a><span data-ttu-id="f2468-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2468-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="f2468-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f2468-107">Attributes and Elements</span></span>

<span data-ttu-id="f2468-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f2468-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="f2468-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f2468-109">Attributes</span></span>

|<span data-ttu-id="f2468-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f2468-110">Attribute</span></span>|<span data-ttu-id="f2468-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f2468-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f2468-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="f2468-112">closeTimeout</span></span>|<span data-ttu-id="f2468-113"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="f2468-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f2468-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f2468-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f2468-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f2468-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="f2468-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="f2468-116">name</span></span>|<span data-ttu-id="f2468-117">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="f2468-117">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f2468-118">Ta wartość jest ciągiem zdefiniowanym przez użytkownika, który działa jako ciąg identyfikacyjny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f2468-118">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="f2468-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="f2468-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f2468-120">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f2468-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="f2468-121">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f2468-121">openTimeout</span></span>|<span data-ttu-id="f2468-122"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="f2468-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f2468-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f2468-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f2468-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f2468-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="f2468-125">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f2468-125">receiveTimeout</span></span>|<span data-ttu-id="f2468-126"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="f2468-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f2468-127">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f2468-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f2468-128">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f2468-128">The default is 00:01:00.</span></span>|
|<span data-ttu-id="f2468-129">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="f2468-129">sendTimeout</span></span>|<span data-ttu-id="f2468-130"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="f2468-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f2468-131">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f2468-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f2468-132">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f2468-132">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f2468-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f2468-133">Child Elements</span></span>

|<span data-ttu-id="f2468-134">Element</span><span class="sxs-lookup"><span data-stu-id="f2468-134">Element</span></span>|<span data-ttu-id="f2468-135">Opis</span><span class="sxs-lookup"><span data-stu-id="f2468-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2468-136">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="f2468-136">\<compositeDuplex></span></span>](compositeduplex.md)|<span data-ttu-id="f2468-137">Określa komunikat dwukierunkowy dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f2468-137">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="f2468-138">Jest on używany z transportami, które nie zezwalają na natywną komunikację bezstronną, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="f2468-138">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="f2468-139">Protokół TCP, w przeciwieństwie, umożliwia natywną komunikację bezstronną i nie wymaga użycia tego elementu powiązania dla usługi do wysyłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="f2468-139">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="f2468-140">Klient musi uwidocznić adres usługi, aby nawiązać kontakt i nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f2468-140">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="f2468-141">Ten adres klienta jest dostarczany przez `ClientBaseAddress` atrybut.</span><span class="sxs-lookup"><span data-stu-id="f2468-141">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="f2468-142">Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="f2468-142">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="f2468-143">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="f2468-143">\<pnrpPeerResolver></span></span>](pnrppeerresolver.md)|<span data-ttu-id="f2468-144">Określa program rozpoznawania nazw elementów równorzędnych protokołu PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="f2468-144">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="f2468-145">Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="f2468-145">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="f2468-146">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="f2468-146">\<reliableSession></span></span>](reliablesession.md)|<span data-ttu-id="f2468-147">Określa ustawienie dla obsługi komunikatów w usłudze WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="f2468-147">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="f2468-148">Gdy ten element zostanie dodany do niestandardowego powiązania, otrzymany kanał może obsługiwać tylko jednokrotne gwarancje dostarczania.</span><span class="sxs-lookup"><span data-stu-id="f2468-148">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="f2468-149">Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="f2468-149">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="f2468-150">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f2468-150">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="f2468-151">Określa opcje zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f2468-151">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="f2468-152">Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f2468-152">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="f2468-153">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="f2468-153">\<sslStreamSecurity></span></span>](sslstreamsecurity.md)|<span data-ttu-id="f2468-154">Określa ustawienia zabezpieczeń dla powiązania strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="f2468-154">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="f2468-155">Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f2468-155">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="f2468-156">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="f2468-156">\<transactionFlow></span></span>](transactionflow.md)|<span data-ttu-id="f2468-157">Określa, że powiązanie obsługuje przepływ transakcji, oraz protokołu, który ma być używany przez `transactionProtocol` atrybut.</span><span class="sxs-lookup"><span data-stu-id="f2468-157">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="f2468-158">Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="f2468-158">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="f2468-159">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="f2468-159">\<windowsStreamSecurity></span></span>](windowsstreamsecurity.md)|<span data-ttu-id="f2468-160">Określa opcje zabezpieczeń przesyłania strumieniowego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f2468-160">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="f2468-161">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f2468-161">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2468-162">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f2468-162">Parent Elements</span></span>

|<span data-ttu-id="f2468-163">Element</span><span class="sxs-lookup"><span data-stu-id="f2468-163">Element</span></span>|<span data-ttu-id="f2468-164">Opis</span><span class="sxs-lookup"><span data-stu-id="f2468-164">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="f2468-165">powiązania</span><span class="sxs-lookup"><span data-stu-id="f2468-165">bindings</span></span>|<span data-ttu-id="f2468-166">Zawiera wszystkie powiązania dla Windows Communication Foundation aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2468-166">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2468-167">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2468-167">Remarks</span></span>

<span data-ttu-id="f2468-168">Niestandardowe powiązania zapewniają pełną kontrolę nad stosem obsługi komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="f2468-168">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="f2468-169">Można utworzyć specjalne powiązania dostosowane, dodając elementy konfiguracji dla określonych jednostek.</span><span class="sxs-lookup"><span data-stu-id="f2468-169">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="f2468-170">Na przykład użytkownik może połączyć `httpsTransport` sekcję, sekcję i `security` sekcję `reliableSession` , aby utworzyć niezawodne i bezpieczne powiązanie https.</span><span class="sxs-lookup"><span data-stu-id="f2468-170">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="f2468-171">Pojedyncze powiązanie definiuje stos komunikatów przez określenie elementów konfiguracji dla elementów stosu w kolejności, w jakiej występują na stosie.</span><span class="sxs-lookup"><span data-stu-id="f2468-171">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="f2468-172">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="f2468-172">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="f2468-173">W każdym powiązaniu niestandardowym musi istnieć jeden i tylko jeden element transportu.</span><span class="sxs-lookup"><span data-stu-id="f2468-173">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="f2468-174">Bez tego elementu stos komunikatów jest niekompletny.</span><span class="sxs-lookup"><span data-stu-id="f2468-174">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="f2468-175">Kolejność, w której elementy pojawiają się w kwestiach stosu, ponieważ jest to kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f2468-175">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="f2468-176">Zalecana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="f2468-176">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="f2468-177">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f2468-177">Transactions (optional)</span></span>

2. <span data-ttu-id="f2468-178">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f2468-178">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="f2468-179">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f2468-179">Security (optional)</span></span>

4. <span data-ttu-id="f2468-180">Transportu</span><span class="sxs-lookup"><span data-stu-id="f2468-180">Transport</span></span>

5. <span data-ttu-id="f2468-181">Koder (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f2468-181">Encoder (optional)</span></span>

<span data-ttu-id="f2468-182">Użyj niestandardowego powiązania, gdy jedno z powiązań dostarczonych przez system nie spełnia wymagań usługi.</span><span class="sxs-lookup"><span data-stu-id="f2468-182">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="f2468-183">Można na przykład użyć niestandardowego powiązania, aby umożliwić korzystanie z nowego lub nowego kodera w punkcie końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="f2468-183">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="f2468-184">Niestandardowe powiązanie jest konstruowane przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> kolekcji elementów powiązania, które są "ułożone" w określonej kolejności:</span><span class="sxs-lookup"><span data-stu-id="f2468-184">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="f2468-185">U góry jest opcjonalne <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , które umożliwia przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2468-185">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="f2468-186">Następnie jest opcjonalne <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> , które udostępnia mechanizm sesji i kolejności, zgodnie z definicją w specyfikacji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="f2468-186">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="f2468-187">To pojęcie sesji może przekroczyć pośredniki SOAP i transportu.</span><span class="sxs-lookup"><span data-stu-id="f2468-187">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="f2468-188">Dalej jest opcjonalny element powiązania zabezpieczeń, który zapewnia funkcje zabezpieczeń, takie jak autoryzacja, uwierzytelnianie, ochrona i poufność.</span><span class="sxs-lookup"><span data-stu-id="f2468-188">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="f2468-189">Następujące elementy powiązań zabezpieczeń są udostępniane przez Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="f2468-189">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="f2468-190">Następnie są opcjonalne wzorce komunikatów określone przez elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="f2468-190">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="f2468-191">Poniżej przedstawiono opcjonalne elementy powiązania uaktualnienia/pomocnika transportu:</span><span class="sxs-lookup"><span data-stu-id="f2468-191">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="f2468-192">Następnie jest wymagany element powiązania kodowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f2468-192">Next is a required message encoding binding element.</span></span> <span data-ttu-id="f2468-193">Możesz użyć własnego transportu lub użyć jednego z następujących powiązań kodowania komunikatów:</span><span class="sxs-lookup"><span data-stu-id="f2468-193">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="f2468-194">U dołu jest wymagany element transportu.</span><span class="sxs-lookup"><span data-stu-id="f2468-194">At the bottom is a required transport element.</span></span> <span data-ttu-id="f2468-195">Możesz użyć własnego transportu lub użyć jednego z elementów powiązania transportowego dostarczonych przez Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="f2468-195">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="f2468-196">Poniższa tabela zawiera podsumowanie opcji dla każdej warstwy.</span><span class="sxs-lookup"><span data-stu-id="f2468-196">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="f2468-197">Warstwa</span><span class="sxs-lookup"><span data-stu-id="f2468-197">Layer</span></span>|<span data-ttu-id="f2468-198">Opcje</span><span class="sxs-lookup"><span data-stu-id="f2468-198">Options</span></span>|<span data-ttu-id="f2468-199">Wymagane</span><span class="sxs-lookup"><span data-stu-id="f2468-199">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="f2468-200">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="f2468-200">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="f2468-201">Nie</span><span class="sxs-lookup"><span data-stu-id="f2468-201">No</span></span>|
|<span data-ttu-id="f2468-202">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="f2468-202">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="f2468-203">Nie</span><span class="sxs-lookup"><span data-stu-id="f2468-203">No</span></span>|
|<span data-ttu-id="f2468-204">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="f2468-204">Security</span></span>|<span data-ttu-id="f2468-205">Symetryczne, asymetryczne, na poziomie transportu</span><span class="sxs-lookup"><span data-stu-id="f2468-205">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="f2468-206">Nie</span><span class="sxs-lookup"><span data-stu-id="f2468-206">No</span></span>|
|<span data-ttu-id="f2468-207">Zmiana kształtu</span><span class="sxs-lookup"><span data-stu-id="f2468-207">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="f2468-208">Nie</span><span class="sxs-lookup"><span data-stu-id="f2468-208">No</span></span>|
|<span data-ttu-id="f2468-209">Uaktualnienia transportu</span><span class="sxs-lookup"><span data-stu-id="f2468-209">Transport Upgrades</span></span>|<span data-ttu-id="f2468-210">Strumień SSL, strumień systemu Windows, program rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="f2468-210">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="f2468-211">Nie</span><span class="sxs-lookup"><span data-stu-id="f2468-211">No</span></span>|
|<span data-ttu-id="f2468-212">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="f2468-212">Encoding</span></span>|<span data-ttu-id="f2468-213">Tekst, dane binarne, MTOM, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f2468-213">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="f2468-214">Tak</span><span class="sxs-lookup"><span data-stu-id="f2468-214">Yes</span></span>|
|<span data-ttu-id="f2468-215">Transportu</span><span class="sxs-lookup"><span data-stu-id="f2468-215">Transport</span></span>|<span data-ttu-id="f2468-216">TCP, nazwane potoki, HTTP, HTTPS, typy usługi MSMQ, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f2468-216">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="f2468-217">Tak</span><span class="sxs-lookup"><span data-stu-id="f2468-217">Yes</span></span>|

<span data-ttu-id="f2468-218">Ponadto można definiować własne elementy powiązania i wstawiać je między wszystkimi wcześniej zdefiniowanymi warstwami.</span><span class="sxs-lookup"><span data-stu-id="f2468-218">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="f2468-219">Aby uzyskać informacje na temat sposobu użycia niestandardowego powiązania do modyfikacji powiązania dostarczonego przez system, zobacz [How to: Dostosuj powiązanie](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)dostarczone przez system.</span><span class="sxs-lookup"><span data-stu-id="f2468-219">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2468-220">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2468-220">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f2468-221">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f2468-221">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="f2468-222">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f2468-222">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f2468-223">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f2468-223">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f2468-224">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f2468-224">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f2468-225">CustomBinding — element</span><span class="sxs-lookup"><span data-stu-id="f2468-225">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="f2468-226">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f2468-226">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f2468-227">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f2468-227">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f2468-228">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f2468-228">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
