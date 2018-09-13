---
title: '&lt;transport&gt; w &lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 2b89ae090d24ff6aad1aae1b39a0a18961bd2537
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44704556"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="f1a97-102">&lt;transport&gt; w &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f1a97-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="f1a97-103">Określa ustawienia zabezpieczenia na poziomie transportu, korzystając z [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f1a97-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="f1a97-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1a97-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1a97-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f1a97-105">\<bindings></span></span>  
<span data-ttu-id="f1a97-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f1a97-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="f1a97-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f1a97-107">\<binding></span></span>  
<span data-ttu-id="f1a97-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f1a97-108">\<security></span></span>  
<span data-ttu-id="f1a97-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="f1a97-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a97-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1a97-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1a97-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f1a97-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f1a97-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1a97-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1a97-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f1a97-113">Attributes</span></span>  
  
|<span data-ttu-id="f1a97-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f1a97-114">Attribute</span></span>|<span data-ttu-id="f1a97-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f1a97-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1a97-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="f1a97-116">credentialType</span></span>|<span data-ttu-id="f1a97-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f1a97-117">Optional.</span></span> <span data-ttu-id="f1a97-118">Określa typ poświadczenia używane do weryfikowania komunikaty wysyłane za pomocą transportu elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="f1a97-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="f1a97-119">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f1a97-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="f1a97-120">credentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="f1a97-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="f1a97-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="f1a97-121">Value</span></span>|<span data-ttu-id="f1a97-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f1a97-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1a97-123">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="f1a97-123">Certificate</span></span>|<span data-ttu-id="f1a97-124">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f1a97-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="f1a97-125">Hasło</span><span class="sxs-lookup"><span data-stu-id="f1a97-125">Password</span></span>|<span data-ttu-id="f1a97-126">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga prawidłowego hasła.</span><span class="sxs-lookup"><span data-stu-id="f1a97-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1a97-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f1a97-127">Child Elements</span></span>  
 <span data-ttu-id="f1a97-128">Brak</span><span class="sxs-lookup"><span data-stu-id="f1a97-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1a97-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1a97-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f1a97-130">Element</span><span class="sxs-lookup"><span data-stu-id="f1a97-130">Element</span></span>|<span data-ttu-id="f1a97-131">Opis</span><span class="sxs-lookup"><span data-stu-id="f1a97-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1a97-132">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f1a97-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="f1a97-133">Definiuje ustawienia zabezpieczeń dla [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f1a97-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1a97-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1a97-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="f1a97-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f1a97-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f1a97-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f1a97-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f1a97-137">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f1a97-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f1a97-138">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f1a97-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f1a97-139">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f1a97-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
