---
title: <security> dla <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: fa31dda3274c9768694bdf5232f31554899e1d82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670524"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="32e48-102">\<Zabezpieczenia > z \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="32e48-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="32e48-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="32e48-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="32e48-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32e48-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32e48-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="32e48-105">\<bindings></span></span>  
<span data-ttu-id="32e48-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="32e48-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="32e48-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="32e48-107">\<binding></span></span>  
<span data-ttu-id="32e48-108">\<security></span><span class="sxs-lookup"><span data-stu-id="32e48-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e48-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="32e48-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32e48-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="32e48-110">Attributes and Elements</span></span>  
 <span data-ttu-id="32e48-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="32e48-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32e48-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="32e48-112">Attributes</span></span>  
  
|<span data-ttu-id="32e48-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="32e48-113">Attribute</span></span>|<span data-ttu-id="32e48-114">Opis</span><span class="sxs-lookup"><span data-stu-id="32e48-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32e48-115">tryb</span><span class="sxs-lookup"><span data-stu-id="32e48-115">mode</span></span>|<span data-ttu-id="32e48-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="32e48-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="32e48-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="32e48-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="32e48-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="32e48-118">-   None: This disables security.</span></span><br /><span data-ttu-id="32e48-119">-Transport: Zabezpieczenia przy użyciu podstawowych zabezpieczeń transportu na podstawie.</span><span class="sxs-lookup"><span data-stu-id="32e48-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="32e48-120">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="32e48-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="32e48-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="32e48-121">-   The default value is Transport.</span></span> <span data-ttu-id="32e48-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="32e48-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32e48-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="32e48-123">Child Elements</span></span>  
  
|<span data-ttu-id="32e48-124">Element</span><span class="sxs-lookup"><span data-stu-id="32e48-124">Element</span></span>|<span data-ttu-id="32e48-125">Opis</span><span class="sxs-lookup"><span data-stu-id="32e48-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32e48-126">transport</span><span class="sxs-lookup"><span data-stu-id="32e48-126">transport</span></span>|<span data-ttu-id="32e48-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="32e48-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="32e48-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="32e48-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32e48-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="32e48-129">Parent Elements</span></span>  
  
|<span data-ttu-id="32e48-130">Element</span><span class="sxs-lookup"><span data-stu-id="32e48-130">Element</span></span>|<span data-ttu-id="32e48-131">Opis</span><span class="sxs-lookup"><span data-stu-id="32e48-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32e48-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="32e48-132">binding</span></span>|<span data-ttu-id="32e48-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="32e48-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32e48-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32e48-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="32e48-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="32e48-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="32e48-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="32e48-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="32e48-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="32e48-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="32e48-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="32e48-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="32e48-139">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="32e48-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="32e48-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="32e48-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
