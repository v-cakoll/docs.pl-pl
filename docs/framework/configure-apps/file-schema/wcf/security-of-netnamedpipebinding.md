---
title: <security> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: fa31dda3274c9768694bdf5232f31554899e1d82
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203395"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="2930d-102">\<Zabezpieczenia > z \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="2930d-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="2930d-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="2930d-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="2930d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2930d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2930d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="2930d-105">\<bindings></span></span>  
<span data-ttu-id="2930d-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="2930d-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="2930d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2930d-107">\<binding></span></span>  
<span data-ttu-id="2930d-108">\<security></span><span class="sxs-lookup"><span data-stu-id="2930d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2930d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2930d-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2930d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2930d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2930d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2930d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2930d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2930d-112">Attributes</span></span>  
  
|<span data-ttu-id="2930d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2930d-113">Attribute</span></span>|<span data-ttu-id="2930d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2930d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2930d-115">tryb</span><span class="sxs-lookup"><span data-stu-id="2930d-115">mode</span></span>|<span data-ttu-id="2930d-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2930d-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="2930d-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="2930d-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2930d-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2930d-118">-   None: This disables security.</span></span><br /><span data-ttu-id="2930d-119">-Transport: Zabezpieczenia przy użyciu podstawowych zabezpieczeń transportu na podstawie.</span><span class="sxs-lookup"><span data-stu-id="2930d-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="2930d-120">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="2930d-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="2930d-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="2930d-121">-   The default value is Transport.</span></span> <span data-ttu-id="2930d-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2930d-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2930d-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2930d-123">Child Elements</span></span>  
  
|<span data-ttu-id="2930d-124">Element</span><span class="sxs-lookup"><span data-stu-id="2930d-124">Element</span></span>|<span data-ttu-id="2930d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2930d-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2930d-126">transport</span><span class="sxs-lookup"><span data-stu-id="2930d-126">transport</span></span>|<span data-ttu-id="2930d-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="2930d-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="2930d-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2930d-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2930d-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2930d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2930d-130">Element</span><span class="sxs-lookup"><span data-stu-id="2930d-130">Element</span></span>|<span data-ttu-id="2930d-131">Opis</span><span class="sxs-lookup"><span data-stu-id="2930d-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2930d-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="2930d-132">binding</span></span>|<span data-ttu-id="2930d-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="2930d-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2930d-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2930d-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="2930d-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="2930d-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2930d-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="2930d-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="2930d-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2930d-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="2930d-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="2930d-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2930d-139">Konfigurowanie usług i klientów za pomocą wiązań</span><span class="sxs-lookup"><span data-stu-id="2930d-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2930d-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2930d-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
