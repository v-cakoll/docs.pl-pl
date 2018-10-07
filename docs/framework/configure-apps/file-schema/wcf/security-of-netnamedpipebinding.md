---
title: '&lt;security&gt; w &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
ms.openlocfilehash: e1c93fc344ea4c7dd3b801c876d59c9a799baf44
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835820"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="d928e-102">&lt;security&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d928e-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="d928e-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="d928e-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="d928e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d928e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d928e-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d928e-105">\<bindings></span></span>  
<span data-ttu-id="d928e-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="d928e-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="d928e-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d928e-107">\<binding></span></span>  
<span data-ttu-id="d928e-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d928e-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d928e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d928e-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d928e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d928e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d928e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d928e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d928e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d928e-112">Attributes</span></span>  
  
|<span data-ttu-id="d928e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d928e-113">Attribute</span></span>|<span data-ttu-id="d928e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d928e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d928e-115">tryb</span><span class="sxs-lookup"><span data-stu-id="d928e-115">mode</span></span>|<span data-ttu-id="d928e-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d928e-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="d928e-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="d928e-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d928e-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d928e-118">-   None: This disables security.</span></span><br /><span data-ttu-id="d928e-119">-Transport: Zabezpieczenia przy użyciu podstawowych zabezpieczeń transportu na podstawie.</span><span class="sxs-lookup"><span data-stu-id="d928e-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="d928e-120">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="d928e-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="d928e-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="d928e-121">-   The default value is Transport.</span></span> <span data-ttu-id="d928e-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d928e-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d928e-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d928e-123">Child Elements</span></span>  
  
|<span data-ttu-id="d928e-124">Element</span><span class="sxs-lookup"><span data-stu-id="d928e-124">Element</span></span>|<span data-ttu-id="d928e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d928e-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d928e-126">transport</span><span class="sxs-lookup"><span data-stu-id="d928e-126">transport</span></span>|<span data-ttu-id="d928e-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="d928e-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="d928e-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d928e-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d928e-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d928e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d928e-130">Element</span><span class="sxs-lookup"><span data-stu-id="d928e-130">Element</span></span>|<span data-ttu-id="d928e-131">Opis</span><span class="sxs-lookup"><span data-stu-id="d928e-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d928e-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="d928e-132">binding</span></span>|<span data-ttu-id="d928e-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="d928e-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d928e-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d928e-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="d928e-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d928e-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d928e-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="d928e-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="d928e-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d928e-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d928e-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d928e-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d928e-139">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d928e-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="d928e-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d928e-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
