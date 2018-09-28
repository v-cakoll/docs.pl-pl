---
title: '&lt;security&gt; w &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
ms.openlocfilehash: eee4cc13b5181caa4449c3ad6ebc5247cc7e0f1a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47424262"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="693af-102">&lt;security&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="693af-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="693af-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="693af-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="693af-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="693af-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="693af-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="693af-105">\<bindings></span></span>  
<span data-ttu-id="693af-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="693af-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="693af-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="693af-107">\<binding></span></span>  
<span data-ttu-id="693af-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="693af-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="693af-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="693af-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="693af-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="693af-110">Attributes and Elements</span></span>  
 <span data-ttu-id="693af-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="693af-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="693af-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="693af-112">Attributes</span></span>  
  
|<span data-ttu-id="693af-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="693af-113">Attribute</span></span>|<span data-ttu-id="693af-114">Opis</span><span class="sxs-lookup"><span data-stu-id="693af-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="693af-115">tryb</span><span class="sxs-lookup"><span data-stu-id="693af-115">mode</span></span>|<span data-ttu-id="693af-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="693af-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="693af-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="693af-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="693af-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="693af-118">-   None: This disables security.</span></span><br /><span data-ttu-id="693af-119">-Transport: Zabezpieczenia przy użyciu podstawowych zabezpieczeń transportu na podstawie.</span><span class="sxs-lookup"><span data-stu-id="693af-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="693af-120">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="693af-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="693af-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="693af-121">-   The default value is Transport.</span></span> <span data-ttu-id="693af-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="693af-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="693af-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="693af-123">Child Elements</span></span>  
  
|<span data-ttu-id="693af-124">Element</span><span class="sxs-lookup"><span data-stu-id="693af-124">Element</span></span>|<span data-ttu-id="693af-125">Opis</span><span class="sxs-lookup"><span data-stu-id="693af-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="693af-126">transport</span><span class="sxs-lookup"><span data-stu-id="693af-126">transport</span></span>|<span data-ttu-id="693af-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="693af-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="693af-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="693af-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="693af-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="693af-129">Parent Elements</span></span>  
  
|<span data-ttu-id="693af-130">Element</span><span class="sxs-lookup"><span data-stu-id="693af-130">Element</span></span>|<span data-ttu-id="693af-131">Opis</span><span class="sxs-lookup"><span data-stu-id="693af-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="693af-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="693af-132">binding</span></span>|<span data-ttu-id="693af-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="693af-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="693af-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="693af-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="693af-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="693af-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="693af-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="693af-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="693af-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="693af-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="693af-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="693af-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="693af-139">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="693af-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="693af-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="693af-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
