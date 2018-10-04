---
title: '&lt;transport&gt; w &lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 62ba3b27b10afe182623f3be0f6738940e194579
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579793"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="aa5c7-102">&lt;transport&gt; w &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="aa5c7-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="aa5c7-103">Określa ustawienia zabezpieczenia na poziomie transportu, korzystając z [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="aa5c7-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="aa5c7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aa5c7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aa5c7-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="aa5c7-105">\<bindings></span></span>  
<span data-ttu-id="aa5c7-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="aa5c7-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="aa5c7-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="aa5c7-107">\<binding></span></span>  
<span data-ttu-id="aa5c7-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="aa5c7-108">\<security></span></span>  
<span data-ttu-id="aa5c7-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="aa5c7-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa5c7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa5c7-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa5c7-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aa5c7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aa5c7-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aa5c7-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa5c7-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aa5c7-113">Attributes</span></span>  
  
|<span data-ttu-id="aa5c7-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aa5c7-114">Attribute</span></span>|<span data-ttu-id="aa5c7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="aa5c7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa5c7-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="aa5c7-116">credentialType</span></span>|<span data-ttu-id="aa5c7-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-117">Optional.</span></span> <span data-ttu-id="aa5c7-118">Określa typ poświadczenia używane do weryfikowania komunikaty wysyłane za pomocą transportu elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="aa5c7-119">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="aa5c7-120">credentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="aa5c7-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="aa5c7-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="aa5c7-121">Value</span></span>|<span data-ttu-id="aa5c7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="aa5c7-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa5c7-123">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="aa5c7-123">Certificate</span></span>|<span data-ttu-id="aa5c7-124">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="aa5c7-125">Hasło</span><span class="sxs-lookup"><span data-stu-id="aa5c7-125">Password</span></span>|<span data-ttu-id="aa5c7-126">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga prawidłowego hasła.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa5c7-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aa5c7-127">Child Elements</span></span>  
 <span data-ttu-id="aa5c7-128">Brak</span><span class="sxs-lookup"><span data-stu-id="aa5c7-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa5c7-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aa5c7-129">Parent Elements</span></span>  
  
|<span data-ttu-id="aa5c7-130">Element</span><span class="sxs-lookup"><span data-stu-id="aa5c7-130">Element</span></span>|<span data-ttu-id="aa5c7-131">Opis</span><span class="sxs-lookup"><span data-stu-id="aa5c7-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa5c7-132">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="aa5c7-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="aa5c7-133">Definiuje ustawienia zabezpieczeń dla [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="aa5c7-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa5c7-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa5c7-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="aa5c7-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="aa5c7-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="aa5c7-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="aa5c7-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="aa5c7-137">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="aa5c7-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="aa5c7-138">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="aa5c7-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="aa5c7-139">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="aa5c7-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
