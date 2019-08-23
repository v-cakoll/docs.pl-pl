---
title: <security> dla <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 0996a98438dc344d96d640abced52ac99709adbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936673"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="7ce02-102">\<zabezpieczenia > \<NetNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="7ce02-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="7ce02-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="7ce02-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="7ce02-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7ce02-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7ce02-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="7ce02-105">\<bindings></span></span>  
<span data-ttu-id="7ce02-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="7ce02-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="7ce02-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="7ce02-107">\<binding></span></span>  
<span data-ttu-id="7ce02-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7ce02-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce02-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ce02-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ce02-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7ce02-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7ce02-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7ce02-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ce02-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7ce02-112">Attributes</span></span>  
  
|<span data-ttu-id="7ce02-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7ce02-113">Attribute</span></span>|<span data-ttu-id="7ce02-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7ce02-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ce02-115">tryb</span><span class="sxs-lookup"><span data-stu-id="7ce02-115">mode</span></span>|<span data-ttu-id="7ce02-116">Określa typ zabezpieczeń, które są stosowane do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7ce02-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="7ce02-117">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="7ce02-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7ce02-118">Dawaj Spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7ce02-118">-   None: This disables security.</span></span><br /><span data-ttu-id="7ce02-119">Transportu Zabezpieczenia są udostępniane przy użyciu podstawowych zabezpieczeń opartych na transportach.</span><span class="sxs-lookup"><span data-stu-id="7ce02-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="7ce02-120">Istnieje możliwość kontrolowania poziomu ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="7ce02-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="7ce02-121">— Wartość domyślna to transport.</span><span class="sxs-lookup"><span data-stu-id="7ce02-121">-   The default value is Transport.</span></span> <span data-ttu-id="7ce02-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7ce02-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ce02-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7ce02-123">Child Elements</span></span>  
  
|<span data-ttu-id="7ce02-124">Element</span><span class="sxs-lookup"><span data-stu-id="7ce02-124">Element</span></span>|<span data-ttu-id="7ce02-125">Opis</span><span class="sxs-lookup"><span data-stu-id="7ce02-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ce02-126">transport</span><span class="sxs-lookup"><span data-stu-id="7ce02-126">transport</span></span>|<span data-ttu-id="7ce02-127">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="7ce02-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="7ce02-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7ce02-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ce02-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7ce02-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7ce02-130">Element</span><span class="sxs-lookup"><span data-stu-id="7ce02-130">Element</span></span>|<span data-ttu-id="7ce02-131">Opis</span><span class="sxs-lookup"><span data-stu-id="7ce02-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ce02-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="7ce02-132">binding</span></span>|<span data-ttu-id="7ce02-133">Element Binding elementu [ \<NetNamedPipeBinding >](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="7ce02-133">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ce02-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ce02-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="7ce02-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7ce02-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7ce02-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="7ce02-136">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="7ce02-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7ce02-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7ce02-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="7ce02-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7ce02-139">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7ce02-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7ce02-140">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="7ce02-140">\<binding></span></span>](../../../misc/binding.md)
