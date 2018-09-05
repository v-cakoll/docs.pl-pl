---
title: '&lt;security&gt; w &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0e5a22d6e517bc7a05f74089b7c8ece8c8a4bd39
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558675"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="a7617-102">&lt;security&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a7617-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="a7617-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="a7617-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="a7617-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7617-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7617-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a7617-105">\<bindings></span></span>  
<span data-ttu-id="a7617-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="a7617-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="a7617-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a7617-107">\<binding></span></span>  
<span data-ttu-id="a7617-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="a7617-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7617-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7617-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7617-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a7617-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a7617-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a7617-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7617-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a7617-112">Attributes</span></span>  
  
|<span data-ttu-id="a7617-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a7617-113">Attribute</span></span>|<span data-ttu-id="a7617-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a7617-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7617-115">tryb</span><span class="sxs-lookup"><span data-stu-id="a7617-115">mode</span></span>|<span data-ttu-id="a7617-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a7617-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="a7617-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="a7617-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a7617-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="a7617-118">-   None: This disables security.</span></span><br /><span data-ttu-id="a7617-119">-Transport: Zabezpieczenia przy użyciu podstawowych zabezpieczeń transportu na podstawie.</span><span class="sxs-lookup"><span data-stu-id="a7617-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="a7617-120">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="a7617-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="a7617-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="a7617-121">-   The default value is Transport.</span></span> <span data-ttu-id="a7617-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a7617-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7617-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a7617-123">Child Elements</span></span>  
  
|<span data-ttu-id="a7617-124">Element</span><span class="sxs-lookup"><span data-stu-id="a7617-124">Element</span></span>|<span data-ttu-id="a7617-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a7617-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7617-126">transport</span><span class="sxs-lookup"><span data-stu-id="a7617-126">transport</span></span>|<span data-ttu-id="a7617-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="a7617-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="a7617-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a7617-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7617-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a7617-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a7617-130">Element</span><span class="sxs-lookup"><span data-stu-id="a7617-130">Element</span></span>|<span data-ttu-id="a7617-131">Opis</span><span class="sxs-lookup"><span data-stu-id="a7617-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7617-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="a7617-132">binding</span></span>|<span data-ttu-id="a7617-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="a7617-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7617-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7617-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="a7617-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="a7617-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a7617-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="a7617-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="a7617-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a7617-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a7617-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="a7617-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a7617-139">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="a7617-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a7617-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a7617-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
