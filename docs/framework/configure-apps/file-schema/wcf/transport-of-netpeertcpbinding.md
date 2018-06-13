---
title: '&lt;transport&gt; w &lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: c94336413424542f6fc6c0ef5b400b10ae715cd8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750703"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="88434-102">&lt;transport&gt; w &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="88434-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="88434-103">Określa ustawienia zabezpieczeń na poziomie transportu, korzystając z [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="88434-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="88434-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="88434-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="88434-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="88434-105">\<bindings></span></span>  
<span data-ttu-id="88434-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="88434-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="88434-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="88434-107">\<binding></span></span>  
<span data-ttu-id="88434-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="88434-108">\<security></span></span>  
<span data-ttu-id="88434-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="88434-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88434-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="88434-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88434-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="88434-111">Attributes and Elements</span></span>  
 <span data-ttu-id="88434-112">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="88434-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88434-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="88434-113">Attributes</span></span>  
  
|<span data-ttu-id="88434-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="88434-114">Attribute</span></span>|<span data-ttu-id="88434-115">Opis</span><span class="sxs-lookup"><span data-stu-id="88434-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88434-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="88434-116">credentialType</span></span>|<span data-ttu-id="88434-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="88434-117">Optional.</span></span> <span data-ttu-id="88434-118">Określa poświadczenia używane do weryfikowania wiadomości wysyłane z transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="88434-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="88434-119">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="88434-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="88434-120">credentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="88434-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="88434-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="88434-121">Value</span></span>|<span data-ttu-id="88434-122">Opis</span><span class="sxs-lookup"><span data-stu-id="88434-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="88434-123">certyfikat</span><span class="sxs-lookup"><span data-stu-id="88434-123">Certificate</span></span>|<span data-ttu-id="88434-124">Uwierzytelnianie kanał transportowy peer wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="88434-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="88434-125">Hasło</span><span class="sxs-lookup"><span data-stu-id="88434-125">Password</span></span>|<span data-ttu-id="88434-126">Uwierzytelnianie kanał transportowy peer wymaga poprawne hasło.</span><span class="sxs-lookup"><span data-stu-id="88434-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88434-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="88434-127">Child Elements</span></span>  
 <span data-ttu-id="88434-128">Brak</span><span class="sxs-lookup"><span data-stu-id="88434-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88434-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="88434-129">Parent Elements</span></span>  
  
|<span data-ttu-id="88434-130">Element</span><span class="sxs-lookup"><span data-stu-id="88434-130">Element</span></span>|<span data-ttu-id="88434-131">Opis</span><span class="sxs-lookup"><span data-stu-id="88434-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88434-132">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="88434-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="88434-133">Definiuje ustawienia zabezpieczeń dla [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="88434-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88434-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88434-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="88434-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="88434-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="88434-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="88434-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="88434-137">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="88434-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="88434-138">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="88434-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="88434-139">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="88434-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
