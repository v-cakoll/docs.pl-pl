---
title: '&lt;security&gt; w &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 0079cb9e62abed42a36b67fed935f883473ebbb8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147827"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="92fc5-102">&lt;security&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="92fc5-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="92fc5-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="92fc5-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="92fc5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="92fc5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="92fc5-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="92fc5-105">\<bindings></span></span>  
<span data-ttu-id="92fc5-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="92fc5-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="92fc5-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="92fc5-107">\<binding></span></span>  
<span data-ttu-id="92fc5-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="92fc5-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92fc5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="92fc5-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92fc5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92fc5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="92fc5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="92fc5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92fc5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92fc5-112">Attributes</span></span>  
  
|<span data-ttu-id="92fc5-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="92fc5-113">Attribute</span></span>|<span data-ttu-id="92fc5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="92fc5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92fc5-115">tryb</span><span class="sxs-lookup"><span data-stu-id="92fc5-115">mode</span></span>|<span data-ttu-id="92fc5-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="92fc5-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="92fc5-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="92fc5-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92fc5-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="92fc5-118">-   None: This disables security.</span></span><br /><span data-ttu-id="92fc5-119">-Transport: Zabezpieczenia przy użyciu podstawowych zabezpieczeń transportu na podstawie.</span><span class="sxs-lookup"><span data-stu-id="92fc5-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="92fc5-120">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="92fc5-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="92fc5-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="92fc5-121">-   The default value is Transport.</span></span> <span data-ttu-id="92fc5-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="92fc5-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92fc5-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92fc5-123">Child Elements</span></span>  
  
|<span data-ttu-id="92fc5-124">Element</span><span class="sxs-lookup"><span data-stu-id="92fc5-124">Element</span></span>|<span data-ttu-id="92fc5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="92fc5-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92fc5-126">transport</span><span class="sxs-lookup"><span data-stu-id="92fc5-126">transport</span></span>|<span data-ttu-id="92fc5-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="92fc5-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="92fc5-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="92fc5-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92fc5-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92fc5-129">Parent Elements</span></span>  
  
|<span data-ttu-id="92fc5-130">Element</span><span class="sxs-lookup"><span data-stu-id="92fc5-130">Element</span></span>|<span data-ttu-id="92fc5-131">Opis</span><span class="sxs-lookup"><span data-stu-id="92fc5-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92fc5-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="92fc5-132">binding</span></span>|<span data-ttu-id="92fc5-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="92fc5-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92fc5-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92fc5-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="92fc5-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="92fc5-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="92fc5-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="92fc5-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="92fc5-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="92fc5-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="92fc5-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="92fc5-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="92fc5-139">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="92fc5-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="92fc5-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="92fc5-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
