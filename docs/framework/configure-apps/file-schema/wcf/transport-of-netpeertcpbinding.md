---
title: <transport> dla <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735976"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="34eb1-102">\<transport> dla \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="34eb1-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="34eb1-103">Określa ustawienia zabezpieczeń na poziomie transportu podczas korzystania z [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="34eb1-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="34eb1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34eb1-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34eb1-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34eb1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="34eb1-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34eb1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34eb1-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34eb1-107">Attributes</span></span>  
  
|<span data-ttu-id="34eb1-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34eb1-108">Attribute</span></span>|<span data-ttu-id="34eb1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="34eb1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34eb1-110">CredentialType</span><span class="sxs-lookup"><span data-stu-id="34eb1-110">credentialType</span></span>|<span data-ttu-id="34eb1-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="34eb1-111">Optional.</span></span> <span data-ttu-id="34eb1-112">Określa typ poświadczeń używanych do weryfikowania komunikatów wysyłanych z transportem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="34eb1-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="34eb1-113">Ten atrybut jest typu <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="34eb1-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="34eb1-114">CredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="34eb1-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="34eb1-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="34eb1-115">Value</span></span>|<span data-ttu-id="34eb1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="34eb1-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="34eb1-117">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="34eb1-117">Certificate</span></span>|<span data-ttu-id="34eb1-118">Uwierzytelnianie w ramach transportu kanału równorzędnego wymaga certyfikatu x509.</span><span class="sxs-lookup"><span data-stu-id="34eb1-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="34eb1-119">Hasło</span><span class="sxs-lookup"><span data-stu-id="34eb1-119">Password</span></span>|<span data-ttu-id="34eb1-120">Uwierzytelnianie transportu kanału równorzędnego wymaga poprawnego hasła.</span><span class="sxs-lookup"><span data-stu-id="34eb1-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34eb1-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34eb1-121">Child Elements</span></span>  
 <span data-ttu-id="34eb1-122">Brak</span><span class="sxs-lookup"><span data-stu-id="34eb1-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34eb1-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34eb1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="34eb1-124">Element</span><span class="sxs-lookup"><span data-stu-id="34eb1-124">Element</span></span>|<span data-ttu-id="34eb1-125">Opis</span><span class="sxs-lookup"><span data-stu-id="34eb1-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="34eb1-126">Definiuje ustawienia zabezpieczeń dla [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="34eb1-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34eb1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34eb1-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="34eb1-128">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="34eb1-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="34eb1-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="34eb1-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="34eb1-130">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="34eb1-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="34eb1-131">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="34eb1-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
