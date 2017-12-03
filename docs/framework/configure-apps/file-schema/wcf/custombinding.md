---
title: '&lt;customBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 267bf183e40c8647959e97ae479d78cfe41367b2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustombindinggt"></a><span data-ttu-id="e04c7-102">&lt;customBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e04c7-102">&lt;customBinding&gt;</span></span>
<span data-ttu-id="e04c7-103">Zapewnia użytkownikowi pełną kontrolę nad stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e04c7-103">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="e04c7-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e04c7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e04c7-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e04c7-105">\<bindings></span></span>  
<span data-ttu-id="e04c7-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e04c7-106">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e04c7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e04c7-107">Syntax</span></span>  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e04c7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e04c7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e04c7-109">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e04c7-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e04c7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e04c7-110">Attributes</span></span>  
  
|<span data-ttu-id="e04c7-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e04c7-111">Attribute</span></span>|<span data-ttu-id="e04c7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e04c7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e04c7-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="e04c7-113">closeTimeout</span></span>|<span data-ttu-id="e04c7-114">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="e04c7-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e04c7-115">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e04c7-116">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e04c7-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e04c7-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="e04c7-117">name</span></span>|<span data-ttu-id="e04c7-118">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="e04c7-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e04c7-119">Ta wartość jest ciągiem zdefiniowane przez użytkownika pełniącym rolę ciągu identyfikacyjnego niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e04c7-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="e04c7-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="e04c7-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e04c7-121">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e04c7-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="e04c7-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="e04c7-122">openTimeout</span></span>|<span data-ttu-id="e04c7-123">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="e04c7-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e04c7-124">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e04c7-125">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e04c7-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e04c7-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="e04c7-126">receiveTimeout</span></span>|<span data-ttu-id="e04c7-127">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="e04c7-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e04c7-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e04c7-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e04c7-129">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e04c7-130">właściwości sendTimeout</span><span class="sxs-lookup"><span data-stu-id="e04c7-130">sendTimeout</span></span>|<span data-ttu-id="e04c7-131">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e04c7-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e04c7-132">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e04c7-133">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e04c7-133">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e04c7-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e04c7-134">Child Elements</span></span>  
  
|<span data-ttu-id="e04c7-135">Element</span><span class="sxs-lookup"><span data-stu-id="e04c7-135">Element</span></span>|<span data-ttu-id="e04c7-136">Opis</span><span class="sxs-lookup"><span data-stu-id="e04c7-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e04c7-137">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="e04c7-137">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="e04c7-138">Określa dwukierunkowej wiadomości do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e04c7-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="e04c7-139">Jest ona używana z transportu, które nie zezwalają na komunikacji dupleksowej natywnie, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="e04c7-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="e04c7-140">TCP, natomiast natywnie umożliwia komunikacji dupleksowej i nie wymaga użycia tego elementu powiązania dla usługi wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="e04c7-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="e04c7-141">Klient musi ujawniać adres usługi upewnić się, skontaktuj się z pomocą i nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="e04c7-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="e04c7-142">Ten adres klienta jest zapewniana przez `ClientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e04c7-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="e04c7-143">Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="e04c7-144">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="e04c7-144">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="e04c7-145">Określa nazwę elementu równorzędnego rozpoznawania protokołu PNRP (Peer Name) program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="e04c7-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="e04c7-146">Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="e04c7-147">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="e04c7-147">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="e04c7-148">Określa ustawienie dla WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="e04c7-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="e04c7-149">Gdy ten element jest dodawany do niestandardowego powiązania, wynikowy kanał obsługuje dokładnie — raz gwarancje dostarczenia.</span><span class="sxs-lookup"><span data-stu-id="e04c7-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="e04c7-150">Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="e04c7-151">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="e04c7-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="e04c7-152">Określa opcje zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e04c7-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="e04c7-153">Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="e04c7-154">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="e04c7-154">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="e04c7-155">Określa ustawienia zabezpieczeń dla powiązania strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="e04c7-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="e04c7-156">Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="e04c7-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="e04c7-157">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="e04c7-158">Określa, czy wiązanie obsługuje przepływu transakcji i Protokół do użycia przez `transactionProtocol` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e04c7-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="e04c7-159">Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="e04c7-160">\<Obiekt windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="e04c7-160">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="e04c7-161">Określa opcje do przesyłania strumieniowego zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e04c7-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="e04c7-162">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e04c7-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e04c7-163">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e04c7-163">Parent Elements</span></span>  
  
|<span data-ttu-id="e04c7-164">Element</span><span class="sxs-lookup"><span data-stu-id="e04c7-164">Element</span></span>|<span data-ttu-id="e04c7-165">Opis</span><span class="sxs-lookup"><span data-stu-id="e04c7-165">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e04c7-166">powiązania</span><span class="sxs-lookup"><span data-stu-id="e04c7-166">bindings</span></span>|<span data-ttu-id="e04c7-167">Zawiera wszystkie powiązania dla aplikacji Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="e04c7-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e04c7-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e04c7-168">Remarks</span></span>  
 <span data-ttu-id="e04c7-169">Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości WCF.</span><span class="sxs-lookup"><span data-stu-id="e04c7-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="e04c7-170">Można utworzyć specjalne powiązania dopasowane Moje Dodawanie elementów konfiguracji dla określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="e04c7-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="e04c7-171">Na przykład użytkownik może łączyć `httpsTransport` sekcji `reliableSession` sekcji i `security` sekcji, aby utworzyć https i niezawodności na podstawie powiązania.</span><span class="sxs-lookup"><span data-stu-id="e04c7-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="e04c7-172">Powiązanie poszczególnych definiuje stosu wiadomości, określając elementy konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie.</span><span class="sxs-lookup"><span data-stu-id="e04c7-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="e04c7-173">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="e04c7-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="e04c7-174">W każdym niestandardowego powiązania musi istnieć jeden i tylko jeden element transportu.</span><span class="sxs-lookup"><span data-stu-id="e04c7-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="e04c7-175">Bez tego elementu stosem obsługi wiadomości jest niekompletna.</span><span class="sxs-lookup"><span data-stu-id="e04c7-175">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="e04c7-176">Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacji są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e04c7-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="e04c7-177">Zalecana kolejność elementów stosu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="e04c7-177">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="e04c7-178">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e04c7-178">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="e04c7-179">Niezawodnej obsługi komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e04c7-179">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="e04c7-180">Zabezpieczeń (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e04c7-180">Security (optional)</span></span>  
  
4.  <span data-ttu-id="e04c7-181">Transportu</span><span class="sxs-lookup"><span data-stu-id="e04c7-181">Transport</span></span>  
  
5.  <span data-ttu-id="e04c7-182">Koder (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e04c7-182">Encoder (optional)</span></span>  
  
 <span data-ttu-id="e04c7-183">Jeśli jedno z powiązań dostarczane przez system nie spełnia wymagania dotyczące usługi, należy użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e04c7-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="e04c7-184">Niestandardowego powiązania można, na przykład, aby umożliwić użycie nowego transportu lub nowe koder na punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="e04c7-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="e04c7-185">Wiązanie niestandardowe jest tworzony przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekcji elementów, które są "skumulowany" w określonej kolejności wiązania:</span><span class="sxs-lookup"><span data-stu-id="e04c7-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="e04c7-186">U góry to opcjonalna <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> umożliwiająca przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="e04c7-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="e04c7-187">Następnie to opcjonalna <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> zapewnia sesji i kolejność mechanizmu zgodnie z definicją w specyfikacji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="e04c7-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="e04c7-188">To pojęcie sesji mogą przechodzić pośredników SOAP i transportu.</span><span class="sxs-lookup"><span data-stu-id="e04c7-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="e04c7-189">Następnie jest elementu powiązania zabezpieczeń opcjonalne, która udostępnia funkcje zabezpieczeń, takich jak autoryzacja, uwierzytelnianie, ochrony i poufności.</span><span class="sxs-lookup"><span data-stu-id="e04c7-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="e04c7-190">Następujące elementy powiązania zabezpieczeń są dostarczane przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e04c7-190">The following security binding elements are provided by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="e04c7-191">Obok opcjonalne wzorce wiadomości są określone przez elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="e04c7-191">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="e04c7-192">Obok są opcjonalne transportu uaktualnień/pomocników elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="e04c7-192">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="e04c7-193">Obok jest element powiązania kodowania komunikatu wymagane.</span><span class="sxs-lookup"><span data-stu-id="e04c7-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="e04c7-194">Można użyć własnych transportu lub użyj jednej z poniższych kodowanie powiązań:</span><span class="sxs-lookup"><span data-stu-id="e04c7-194">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="e04c7-195">W dolnej części jest element wymagany transportu.</span><span class="sxs-lookup"><span data-stu-id="e04c7-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="e04c7-196">Można użyć własnych transportu lub użyj jednej z elementami pochodzącymi powiązania transportu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e04c7-196">You can use your own transport or use one of transport binding elements provided by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="e04c7-197">W poniższej tabeli przedstawiono opcje dla każdej warstwy.</span><span class="sxs-lookup"><span data-stu-id="e04c7-197">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="e04c7-198">Warstwy</span><span class="sxs-lookup"><span data-stu-id="e04c7-198">Layer</span></span>|<span data-ttu-id="e04c7-199">Opcje</span><span class="sxs-lookup"><span data-stu-id="e04c7-199">Options</span></span>|<span data-ttu-id="e04c7-200">Wymagane</span><span class="sxs-lookup"><span data-stu-id="e04c7-200">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="e04c7-201">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="e04c7-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="e04c7-202">Nie</span><span class="sxs-lookup"><span data-stu-id="e04c7-202">No</span></span>|  
|<span data-ttu-id="e04c7-203">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="e04c7-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="e04c7-204">Nie</span><span class="sxs-lookup"><span data-stu-id="e04c7-204">No</span></span>|  
|<span data-ttu-id="e04c7-205">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="e04c7-205">Security</span></span>|<span data-ttu-id="e04c7-206">Symetryczne, asymetrycznego, poziomu transportu</span><span class="sxs-lookup"><span data-stu-id="e04c7-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="e04c7-207">Nie</span><span class="sxs-lookup"><span data-stu-id="e04c7-207">No</span></span>|  
|<span data-ttu-id="e04c7-208">Zmiana kształtu</span><span class="sxs-lookup"><span data-stu-id="e04c7-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="e04c7-209">Nie</span><span class="sxs-lookup"><span data-stu-id="e04c7-209">No</span></span>|  
|<span data-ttu-id="e04c7-210">Transport uaktualnień</span><span class="sxs-lookup"><span data-stu-id="e04c7-210">Transport Upgrades</span></span>|<span data-ttu-id="e04c7-211">Strumień protokołu SSL, strumienia systemu Windows, program rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="e04c7-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="e04c7-212">Nie</span><span class="sxs-lookup"><span data-stu-id="e04c7-212">No</span></span>|  
|<span data-ttu-id="e04c7-213">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="e04c7-213">Encoding</span></span>|<span data-ttu-id="e04c7-214">Tekst, Binary, MTOM, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="e04c7-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="e04c7-215">Tak</span><span class="sxs-lookup"><span data-stu-id="e04c7-215">Yes</span></span>|  
|<span data-ttu-id="e04c7-216">Transportu</span><span class="sxs-lookup"><span data-stu-id="e04c7-216">Transport</span></span>|<span data-ttu-id="e04c7-217">TCP i nazwane potoki, HTTP i HTTPS, odmian usługi MSMQ, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="e04c7-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="e04c7-218">Tak</span><span class="sxs-lookup"><span data-stu-id="e04c7-218">Yes</span></span>|  
  
 <span data-ttu-id="e04c7-219">Ponadto można definiować własne elementy powiązania i wstawione między dowolnymi z poprzednim zdefiniowane warstwy.</span><span class="sxs-lookup"><span data-stu-id="e04c7-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="e04c7-220">Aby uzyskać informacje dotyczące sposobu używania niestandardowego powiązania, aby zmodyfikować powiązania dostarczane przez system, zobacz [porady: dostosowywanie powiązania System-Provided](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="e04c7-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
1.  
  
## <a name="see-also"></a><span data-ttu-id="e04c7-221">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e04c7-221">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="e04c7-222">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e04c7-222">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="e04c7-223">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e04c7-223">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e04c7-224">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="e04c7-224">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="e04c7-225">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="e04c7-225">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="e04c7-226">customBinding — Element</span><span class="sxs-lookup"><span data-stu-id="e04c7-226">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="e04c7-227">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e04c7-227">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e04c7-228">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="e04c7-228">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e04c7-229">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e04c7-229">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
