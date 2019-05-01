---
title: <transport> dla <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 157637615abafbd5913e4d90b702bb0224d5f121
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788326"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="aebcd-102">\<transport > z \<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="aebcd-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="aebcd-103">Określa ustawienia zabezpieczenia na poziomie transportu, korzystając z [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="aebcd-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="aebcd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aebcd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aebcd-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="aebcd-105">\<bindings></span></span>  
<span data-ttu-id="aebcd-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="aebcd-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="aebcd-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="aebcd-107">\<binding></span></span>  
<span data-ttu-id="aebcd-108">\<security></span><span class="sxs-lookup"><span data-stu-id="aebcd-108">\<security></span></span>  
<span data-ttu-id="aebcd-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="aebcd-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebcd-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="aebcd-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aebcd-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aebcd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aebcd-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aebcd-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aebcd-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aebcd-113">Attributes</span></span>  
  
|<span data-ttu-id="aebcd-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aebcd-114">Attribute</span></span>|<span data-ttu-id="aebcd-115">Opis</span><span class="sxs-lookup"><span data-stu-id="aebcd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aebcd-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="aebcd-116">credentialType</span></span>|<span data-ttu-id="aebcd-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="aebcd-117">Optional.</span></span> <span data-ttu-id="aebcd-118">Określa typ poświadczenia używane do weryfikowania komunikaty wysyłane za pomocą transportu elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="aebcd-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="aebcd-119">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="aebcd-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="aebcd-120">credentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="aebcd-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="aebcd-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="aebcd-121">Value</span></span>|<span data-ttu-id="aebcd-122">Opis</span><span class="sxs-lookup"><span data-stu-id="aebcd-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aebcd-123">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="aebcd-123">Certificate</span></span>|<span data-ttu-id="aebcd-124">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga X509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="aebcd-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="aebcd-125">Hasło</span><span class="sxs-lookup"><span data-stu-id="aebcd-125">Password</span></span>|<span data-ttu-id="aebcd-126">Uwierzytelnianie transportu kanał elementu równorzędnego wymaga prawidłowego hasła.</span><span class="sxs-lookup"><span data-stu-id="aebcd-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aebcd-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aebcd-127">Child Elements</span></span>  
 <span data-ttu-id="aebcd-128">Brak</span><span class="sxs-lookup"><span data-stu-id="aebcd-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aebcd-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aebcd-129">Parent Elements</span></span>  
  
|<span data-ttu-id="aebcd-130">Element</span><span class="sxs-lookup"><span data-stu-id="aebcd-130">Element</span></span>|<span data-ttu-id="aebcd-131">Opis</span><span class="sxs-lookup"><span data-stu-id="aebcd-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aebcd-132">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="aebcd-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="aebcd-133">Definiuje ustawienia zabezpieczeń dla [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="aebcd-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aebcd-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aebcd-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="aebcd-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="aebcd-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="aebcd-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="aebcd-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="aebcd-137">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="aebcd-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="aebcd-138">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="aebcd-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="aebcd-139">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="aebcd-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
