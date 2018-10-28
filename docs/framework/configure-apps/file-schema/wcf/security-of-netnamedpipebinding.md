---
title: '&lt;security&gt; w &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 4a80a8337a5b98ff30de60afbe4438e0d91b946b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185683"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="3d653-102">&lt;security&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3d653-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="3d653-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="3d653-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="3d653-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3d653-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3d653-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="3d653-105">\<bindings></span></span>  
<span data-ttu-id="3d653-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="3d653-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="3d653-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3d653-107">\<binding></span></span>  
<span data-ttu-id="3d653-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="3d653-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d653-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d653-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d653-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3d653-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d653-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3d653-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d653-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3d653-112">Attributes</span></span>  
  
|<span data-ttu-id="3d653-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3d653-113">Attribute</span></span>|<span data-ttu-id="3d653-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3d653-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d653-115">tryb</span><span class="sxs-lookup"><span data-stu-id="3d653-115">mode</span></span>|<span data-ttu-id="3d653-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3d653-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="3d653-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="3d653-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3d653-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3d653-118">-   None: This disables security.</span></span><br /><span data-ttu-id="3d653-119">-Transport: Zabezpieczenia przy użyciu podstawowych zabezpieczeń transportu na podstawie.</span><span class="sxs-lookup"><span data-stu-id="3d653-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="3d653-120">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="3d653-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="3d653-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="3d653-121">-   The default value is Transport.</span></span> <span data-ttu-id="3d653-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3d653-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d653-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3d653-123">Child Elements</span></span>  
  
|<span data-ttu-id="3d653-124">Element</span><span class="sxs-lookup"><span data-stu-id="3d653-124">Element</span></span>|<span data-ttu-id="3d653-125">Opis</span><span class="sxs-lookup"><span data-stu-id="3d653-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d653-126">transport</span><span class="sxs-lookup"><span data-stu-id="3d653-126">transport</span></span>|<span data-ttu-id="3d653-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="3d653-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="3d653-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3d653-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d653-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3d653-129">Parent Elements</span></span>  
  
|<span data-ttu-id="3d653-130">Element</span><span class="sxs-lookup"><span data-stu-id="3d653-130">Element</span></span>|<span data-ttu-id="3d653-131">Opis</span><span class="sxs-lookup"><span data-stu-id="3d653-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d653-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="3d653-132">binding</span></span>|<span data-ttu-id="3d653-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="3d653-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d653-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d653-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="3d653-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="3d653-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3d653-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="3d653-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="3d653-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3d653-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3d653-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="3d653-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3d653-139">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="3d653-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="3d653-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3d653-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
