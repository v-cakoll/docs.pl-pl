---
title: '&lt;security&gt; w &lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3a018c502aead84eb6936001acb5bc24c59188f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="cf9c3-102">&lt;security&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="cf9c3-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="cf9c3-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="cf9c3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cf9c3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf9c3-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="cf9c3-105">\<bindings></span></span>  
<span data-ttu-id="cf9c3-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="cf9c3-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="cf9c3-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="cf9c3-107">\<binding></span></span>  
<span data-ttu-id="cf9c3-108">\<security></span><span class="sxs-lookup"><span data-stu-id="cf9c3-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9c3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf9c3-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf9c3-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cf9c3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cf9c3-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf9c3-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cf9c3-112">Attributes</span></span>  
  
|<span data-ttu-id="cf9c3-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cf9c3-113">Attribute</span></span>|<span data-ttu-id="cf9c3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cf9c3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf9c3-115">tryb</span><span class="sxs-lookup"><span data-stu-id="cf9c3-115">mode</span></span>|<span data-ttu-id="cf9c3-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="cf9c3-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="cf9c3-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cf9c3-118">-Brak: Powoduje wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-118">-   None: This disables security.</span></span><br /><span data-ttu-id="cf9c3-119">-Transport: Zabezpieczenia za pomocą zabezpieczeń transportu na podstawie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="cf9c3-120">Jest możliwe kontrolowanie poziomu ochrony, w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="cf9c3-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-121">-   The default value is Transport.</span></span> <span data-ttu-id="cf9c3-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf9c3-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cf9c3-123">Child Elements</span></span>  
  
|<span data-ttu-id="cf9c3-124">Element</span><span class="sxs-lookup"><span data-stu-id="cf9c3-124">Element</span></span>|<span data-ttu-id="cf9c3-125">Opis</span><span class="sxs-lookup"><span data-stu-id="cf9c3-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf9c3-126">transport</span><span class="sxs-lookup"><span data-stu-id="cf9c3-126">transport</span></span>|<span data-ttu-id="cf9c3-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="cf9c3-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="cf9c3-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf9c3-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cf9c3-129">Parent Elements</span></span>  
  
|<span data-ttu-id="cf9c3-130">Element</span><span class="sxs-lookup"><span data-stu-id="cf9c3-130">Element</span></span>|<span data-ttu-id="cf9c3-131">Opis</span><span class="sxs-lookup"><span data-stu-id="cf9c3-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf9c3-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="cf9c3-132">binding</span></span>|<span data-ttu-id="cf9c3-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="cf9c3-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf9c3-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf9c3-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="cf9c3-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="cf9c3-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cf9c3-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="cf9c3-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="cf9c3-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="cf9c3-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cf9c3-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="cf9c3-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="cf9c3-139">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="cf9c3-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="cf9c3-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="cf9c3-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
