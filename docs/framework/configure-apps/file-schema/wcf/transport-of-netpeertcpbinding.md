---
title: <transport> dla <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 157637615abafbd5913e4d90b702bb0224d5f121
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204877"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="f89c3-102">\<transport > z \<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="f89c3-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="f89c3-103">Określa ustawienia zabezpieczenia na poziomie transportu, korzystając z [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f89c3-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="f89c3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f89c3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f89c3-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f89c3-105">\<bindings></span></span>  
<span data-ttu-id="f89c3-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f89c3-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="f89c3-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f89c3-107">\<binding></span></span>  
<span data-ttu-id="f89c3-108">\<security></span><span class="sxs-lookup"><span data-stu-id="f89c3-108">\<security></span></span>  
<span data-ttu-id="f89c3-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="f89c3-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89c3-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f89c3-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f89c3-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f89c3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f89c3-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f89c3-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f89c3-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f89c3-113">Attributes</span></span>  
  
|<span data-ttu-id="f89c3-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f89c3-114">Attribute</span></span>|<span data-ttu-id="f89c3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f89c3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f89c3-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="f89c3-116">credentialType</span></span>|<span data-ttu-id="f89c3-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f89c3-117">Optional.</span></span> <span data-ttu-id="f89c3-118">Określa typ poświadczenia używane do weryfikowania komunikaty wysyłane za pomocą transportu elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="f89c3-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="f89c3-119">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f89c3-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="f89c3-120">credentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="f89c3-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="f89c3-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="f89c3-121">Value</span></span>|<span data-ttu-id="f89c3-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f89c3-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f89c3-123">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="f89c3-123">Certificate</span></span>|<span data-ttu-id="f89c3-124">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f89c3-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="f89c3-125">Hasło</span><span class="sxs-lookup"><span data-stu-id="f89c3-125">Password</span></span>|<span data-ttu-id="f89c3-126">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga prawidłowego hasła.</span><span class="sxs-lookup"><span data-stu-id="f89c3-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f89c3-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f89c3-127">Child Elements</span></span>  
 <span data-ttu-id="f89c3-128">Brak</span><span class="sxs-lookup"><span data-stu-id="f89c3-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f89c3-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f89c3-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f89c3-130">Element</span><span class="sxs-lookup"><span data-stu-id="f89c3-130">Element</span></span>|<span data-ttu-id="f89c3-131">Opis</span><span class="sxs-lookup"><span data-stu-id="f89c3-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f89c3-132">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f89c3-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="f89c3-133">Definiuje ustawienia zabezpieczeń dla [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f89c3-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f89c3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f89c3-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="f89c3-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f89c3-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f89c3-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f89c3-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f89c3-137">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f89c3-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f89c3-138">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f89c3-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f89c3-139">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f89c3-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
