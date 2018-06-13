---
title: '&lt;security&gt; w &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 74bf0d14b0acfd8a5382575d2ee1e51174b6b6b8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752796"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="9ffb6-102">&lt;security&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="9ffb6-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="9ffb6-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="9ffb6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9ffb6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9ffb6-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="9ffb6-105">\<bindings></span></span>  
<span data-ttu-id="9ffb6-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="9ffb6-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="9ffb6-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9ffb6-107">\<binding></span></span>  
<span data-ttu-id="9ffb6-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="9ffb6-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ffb6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ffb6-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ffb6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9ffb6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9ffb6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ffb6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ffb6-112">Attributes</span></span>  
  
|<span data-ttu-id="9ffb6-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9ffb6-113">Attribute</span></span>|<span data-ttu-id="9ffb6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9ffb6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ffb6-115">tryb</span><span class="sxs-lookup"><span data-stu-id="9ffb6-115">mode</span></span>|<span data-ttu-id="9ffb6-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="9ffb6-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="9ffb6-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9ffb6-118">-Brak: Powoduje wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-118">-   None: This disables security.</span></span><br /><span data-ttu-id="9ffb6-119">-Transport: Zabezpieczenia za pomocą zabezpieczeń transportu na podstawie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="9ffb6-120">Jest możliwe kontrolowanie poziomu ochrony, w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="9ffb6-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-121">-   The default value is Transport.</span></span> <span data-ttu-id="9ffb6-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ffb6-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9ffb6-123">Child Elements</span></span>  
  
|<span data-ttu-id="9ffb6-124">Element</span><span class="sxs-lookup"><span data-stu-id="9ffb6-124">Element</span></span>|<span data-ttu-id="9ffb6-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9ffb6-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ffb6-126">transport</span><span class="sxs-lookup"><span data-stu-id="9ffb6-126">transport</span></span>|<span data-ttu-id="9ffb6-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="9ffb6-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9ffb6-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ffb6-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9ffb6-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9ffb6-130">Element</span><span class="sxs-lookup"><span data-stu-id="9ffb6-130">Element</span></span>|<span data-ttu-id="9ffb6-131">Opis</span><span class="sxs-lookup"><span data-stu-id="9ffb6-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ffb6-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="9ffb6-132">binding</span></span>|<span data-ttu-id="9ffb6-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="9ffb6-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ffb6-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ffb6-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="9ffb6-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="9ffb6-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="9ffb6-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="9ffb6-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="9ffb6-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9ffb6-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9ffb6-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="9ffb6-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="9ffb6-139">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="9ffb6-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="9ffb6-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9ffb6-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
