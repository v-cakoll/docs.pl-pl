---
title: <security> dla <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738659"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="8d8d6-102">\<security> dla \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="8d8d6-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="8d8d6-103">Definiuje ustawienia zabezpieczeń [\<netPeerTcpBinding>](netpeertcpbinding.md) , w tym typ używanego uwierzytelniania i zabezpieczenia używane do transportu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="8d8d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d8d6-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d8d6-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8d8d6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8d8d6-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d8d6-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8d8d6-107">Attributes</span></span>  
  
|<span data-ttu-id="8d8d6-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8d8d6-108">Attribute</span></span>|<span data-ttu-id="8d8d6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8d8d6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d8d6-110">tryb</span><span class="sxs-lookup"><span data-stu-id="8d8d6-110">mode</span></span>|<span data-ttu-id="8d8d6-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-111">Optional.</span></span> <span data-ttu-id="8d8d6-112">Określa typ zabezpieczeń używanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="8d8d6-113">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-113">The default value is `Message`.</span></span> <span data-ttu-id="8d8d6-114">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="8d8d6-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8d8d6-115">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="8d8d6-115">mode Attribute</span></span>  
  
|<span data-ttu-id="8d8d6-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="8d8d6-116">Value</span></span>|<span data-ttu-id="8d8d6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8d8d6-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d8d6-118">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8d8d6-118">Message</span></span>|<span data-ttu-id="8d8d6-119">Zabezpieczenia protokołu SOAP zapewniają uwierzytelnianie, integralność i poufność.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="8d8d6-120">Brak</span><span class="sxs-lookup"><span data-stu-id="8d8d6-120">None</span></span>|<span data-ttu-id="8d8d6-121">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-121">Security is disabled.</span></span>|  
|<span data-ttu-id="8d8d6-122">Transport</span><span class="sxs-lookup"><span data-stu-id="8d8d6-122">Transport</span></span>|<span data-ttu-id="8d8d6-123">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="8d8d6-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8d8d6-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="8d8d6-125">Protokół HTTPS zapewnia uwierzytelnianie i poufność.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="8d8d6-126">Komunikaty protokołu SOAP zapewniają zaawansowane typy poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d8d6-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8d8d6-127">Child Elements</span></span>  
  
|<span data-ttu-id="8d8d6-128">Element</span><span class="sxs-lookup"><span data-stu-id="8d8d6-128">Element</span></span>|<span data-ttu-id="8d8d6-129">Opis</span><span class="sxs-lookup"><span data-stu-id="8d8d6-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="8d8d6-130">Definiuje typ transportu dla zabezpieczonych komunikatów wysyłanych przez elementy równorzędne skonfigurowane przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="8d8d6-131">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="8d8d6-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d8d6-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8d8d6-132">Parent Elements</span></span>  
  
|<span data-ttu-id="8d8d6-133">Element</span><span class="sxs-lookup"><span data-stu-id="8d8d6-133">Element</span></span>|<span data-ttu-id="8d8d6-134">Opis</span><span class="sxs-lookup"><span data-stu-id="8d8d6-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8d8d6-135">Definiuje wszystkie możliwości powiązań [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8d8d6-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d8d6-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d8d6-136">Remarks</span></span>  
 <span data-ttu-id="8d8d6-137">Zabezpieczenia mogą dotyczyć zarówno komunikatów, jak i związanych z transportem.</span><span class="sxs-lookup"><span data-stu-id="8d8d6-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8d6-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d8d6-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="8d8d6-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8d8d6-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8d8d6-140">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="8d8d6-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="8d8d6-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8d8d6-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8d8d6-142">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="8d8d6-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8d8d6-143">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="8d8d6-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
