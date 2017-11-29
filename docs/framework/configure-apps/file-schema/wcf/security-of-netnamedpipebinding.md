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
ms.openlocfilehash: efb6289c63cdc98402336949ef5916e7568775a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="4733a-102">&lt;security&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="4733a-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="4733a-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="4733a-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="4733a-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4733a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4733a-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4733a-105">\<bindings></span></span>  
<span data-ttu-id="4733a-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="4733a-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="4733a-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4733a-107">\<binding></span></span>  
<span data-ttu-id="4733a-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="4733a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4733a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4733a-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4733a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4733a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4733a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4733a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4733a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4733a-112">Attributes</span></span>  
  
|<span data-ttu-id="4733a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4733a-113">Attribute</span></span>|<span data-ttu-id="4733a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4733a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4733a-115">tryb</span><span class="sxs-lookup"><span data-stu-id="4733a-115">mode</span></span>|<span data-ttu-id="4733a-116">Określa typ zabezpieczeń, która jest stosowana do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4733a-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="4733a-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="4733a-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4733a-118">-Brak: Powoduje wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4733a-118">-   None: This disables security.</span></span><br /><span data-ttu-id="4733a-119">-Transport: Zabezpieczenia za pomocą zabezpieczeń transportu na podstawie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4733a-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="4733a-120">Jest możliwe kontrolowanie poziomu ochrony, w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="4733a-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="4733a-121">— Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="4733a-121">-   The default value is Transport.</span></span> <span data-ttu-id="4733a-122">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="4733a-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4733a-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4733a-123">Child Elements</span></span>  
  
|<span data-ttu-id="4733a-124">Element</span><span class="sxs-lookup"><span data-stu-id="4733a-124">Element</span></span>|<span data-ttu-id="4733a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="4733a-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4733a-126">transport</span><span class="sxs-lookup"><span data-stu-id="4733a-126">transport</span></span>|<span data-ttu-id="4733a-127">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="4733a-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="4733a-128">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4733a-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4733a-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4733a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="4733a-130">Element</span><span class="sxs-lookup"><span data-stu-id="4733a-130">Element</span></span>|<span data-ttu-id="4733a-131">Opis</span><span class="sxs-lookup"><span data-stu-id="4733a-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4733a-132">powiązanie</span><span class="sxs-lookup"><span data-stu-id="4733a-132">binding</span></span>|<span data-ttu-id="4733a-133">Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="4733a-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4733a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4733a-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="4733a-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="4733a-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="4733a-136">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="4733a-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="4733a-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4733a-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4733a-138">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="4733a-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="4733a-139">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4733a-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="4733a-140">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4733a-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
