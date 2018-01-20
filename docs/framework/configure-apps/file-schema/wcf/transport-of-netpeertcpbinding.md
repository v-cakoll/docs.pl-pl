---
title: '&lt;transport&gt; w &lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cc5e0b2aa52c8fa37e6148f66dc24fca273a640
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="f6d86-102">&lt;transport&gt; w &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f6d86-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="f6d86-103">Określa ustawienia zabezpieczeń na poziomie transportu, korzystając z [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f6d86-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="f6d86-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f6d86-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6d86-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f6d86-105">\<bindings></span></span>  
<span data-ttu-id="f6d86-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f6d86-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="f6d86-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f6d86-107">\<binding></span></span>  
<span data-ttu-id="f6d86-108">\<security></span><span class="sxs-lookup"><span data-stu-id="f6d86-108">\<security></span></span>  
<span data-ttu-id="f6d86-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="f6d86-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6d86-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6d86-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6d86-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6d86-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f6d86-112">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6d86-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6d86-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6d86-113">Attributes</span></span>  
  
|<span data-ttu-id="f6d86-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6d86-114">Attribute</span></span>|<span data-ttu-id="f6d86-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d86-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6d86-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="f6d86-116">credentialType</span></span>|<span data-ttu-id="f6d86-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f6d86-117">Optional.</span></span> <span data-ttu-id="f6d86-118">Określa poświadczenia używane do weryfikowania wiadomości wysyłane z transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="f6d86-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="f6d86-119">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f6d86-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="f6d86-120">credentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="f6d86-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="f6d86-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="f6d86-121">Value</span></span>|<span data-ttu-id="f6d86-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d86-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f6d86-123">certyfikat</span><span class="sxs-lookup"><span data-stu-id="f6d86-123">Certificate</span></span>|<span data-ttu-id="f6d86-124">Uwierzytelnianie kanał transportowy peer wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f6d86-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="f6d86-125">Hasło</span><span class="sxs-lookup"><span data-stu-id="f6d86-125">Password</span></span>|<span data-ttu-id="f6d86-126">Uwierzytelnianie kanał transportowy peer wymaga poprawne hasło.</span><span class="sxs-lookup"><span data-stu-id="f6d86-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6d86-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6d86-127">Child Elements</span></span>  
 <span data-ttu-id="f6d86-128">Brak</span><span class="sxs-lookup"><span data-stu-id="f6d86-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6d86-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6d86-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f6d86-130">Element</span><span class="sxs-lookup"><span data-stu-id="f6d86-130">Element</span></span>|<span data-ttu-id="f6d86-131">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d86-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6d86-132">\<security></span><span class="sxs-lookup"><span data-stu-id="f6d86-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="f6d86-133">Definiuje ustawienia zabezpieczeń dla [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f6d86-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6d86-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6d86-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="f6d86-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f6d86-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f6d86-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f6d86-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f6d86-137">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f6d86-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f6d86-138">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f6d86-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f6d86-139">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f6d86-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
