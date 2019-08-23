---
title: <transport> dla <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 837d01540fa63579877ab4085bd8034c78f2fbe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915561"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="69e20-102">\<Transport > \<NetPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="69e20-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="69e20-103">Określa ustawienia zabezpieczeń na poziomie transportu podczas korzystania z [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="69e20-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="69e20-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="69e20-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="69e20-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="69e20-105">\<bindings></span></span>  
<span data-ttu-id="69e20-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="69e20-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="69e20-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="69e20-107">\<binding></span></span>  
<span data-ttu-id="69e20-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="69e20-108">\<security></span></span>  
<span data-ttu-id="69e20-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="69e20-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69e20-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="69e20-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69e20-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69e20-111">Attributes and Elements</span></span>  
 <span data-ttu-id="69e20-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69e20-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69e20-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69e20-113">Attributes</span></span>  
  
|<span data-ttu-id="69e20-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="69e20-114">Attribute</span></span>|<span data-ttu-id="69e20-115">Opis</span><span class="sxs-lookup"><span data-stu-id="69e20-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69e20-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="69e20-116">credentialType</span></span>|<span data-ttu-id="69e20-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="69e20-117">Optional.</span></span> <span data-ttu-id="69e20-118">Określa typ poświadczeń używanych do weryfikowania komunikatów wysyłanych z transportem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="69e20-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="69e20-119">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="69e20-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="69e20-120">CredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="69e20-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="69e20-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="69e20-121">Value</span></span>|<span data-ttu-id="69e20-122">Opis</span><span class="sxs-lookup"><span data-stu-id="69e20-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="69e20-123">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="69e20-123">Certificate</span></span>|<span data-ttu-id="69e20-124">Uwierzytelnianie w ramach transportu kanału równorzędnego wymaga certyfikatu x509.</span><span class="sxs-lookup"><span data-stu-id="69e20-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="69e20-125">Hasło</span><span class="sxs-lookup"><span data-stu-id="69e20-125">Password</span></span>|<span data-ttu-id="69e20-126">Uwierzytelnianie transportu kanału równorzędnego wymaga poprawnego hasła.</span><span class="sxs-lookup"><span data-stu-id="69e20-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69e20-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69e20-127">Child Elements</span></span>  
 <span data-ttu-id="69e20-128">Brak</span><span class="sxs-lookup"><span data-stu-id="69e20-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69e20-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69e20-129">Parent Elements</span></span>  
  
|<span data-ttu-id="69e20-130">Element</span><span class="sxs-lookup"><span data-stu-id="69e20-130">Element</span></span>|<span data-ttu-id="69e20-131">Opis</span><span class="sxs-lookup"><span data-stu-id="69e20-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69e20-132">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="69e20-132">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="69e20-133">Definiuje ustawienia [ \<zabezpieczeń > NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="69e20-133">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69e20-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69e20-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="69e20-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="69e20-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="69e20-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="69e20-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="69e20-137">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="69e20-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="69e20-138">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="69e20-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="69e20-139">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="69e20-139">\<binding></span></span>](../../../misc/binding.md)
