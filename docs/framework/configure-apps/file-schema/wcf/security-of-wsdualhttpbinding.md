---
title: '&lt;security&gt; w &lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 023e0dd2a89c005928625cf95f3de61af81c7b6b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514532"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="db6e1-102">&lt;security&gt; w &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="db6e1-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="db6e1-103">Definiuje możliwości zabezpieczeń [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="db6e1-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="db6e1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="db6e1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="db6e1-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="db6e1-105">\<bindings></span></span>  
<span data-ttu-id="db6e1-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="db6e1-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="db6e1-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="db6e1-107">\<binding></span></span>  
<span data-ttu-id="db6e1-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="db6e1-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db6e1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="db6e1-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db6e1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="db6e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="db6e1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="db6e1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db6e1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="db6e1-112">Attributes</span></span>  
  
|<span data-ttu-id="db6e1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="db6e1-113">Attribute</span></span>|<span data-ttu-id="db6e1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="db6e1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db6e1-115">tryb</span><span class="sxs-lookup"><span data-stu-id="db6e1-115">mode</span></span>|<span data-ttu-id="db6e1-116">— Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="db6e1-116">-   Optional.</span></span> <span data-ttu-id="db6e1-117">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="db6e1-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="db6e1-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="db6e1-118">The default value is `Message`.</span></span> <span data-ttu-id="db6e1-119">Ten atrybut jest typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="db6e1-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="db6e1-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="db6e1-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="db6e1-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="db6e1-121">Value</span></span>|<span data-ttu-id="db6e1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="db6e1-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db6e1-123">Brak</span><span class="sxs-lookup"><span data-stu-id="db6e1-123">None</span></span>|<span data-ttu-id="db6e1-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="db6e1-124">Security is disabled.</span></span>|  
|<span data-ttu-id="db6e1-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="db6e1-125">Message</span></span>|<span data-ttu-id="db6e1-126">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="db6e1-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db6e1-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="db6e1-127">Child Elements</span></span>  
  
|<span data-ttu-id="db6e1-128">Element</span><span class="sxs-lookup"><span data-stu-id="db6e1-128">Element</span></span>|<span data-ttu-id="db6e1-129">Opis</span><span class="sxs-lookup"><span data-stu-id="db6e1-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db6e1-130">\<message></span><span class="sxs-lookup"><span data-stu-id="db6e1-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="db6e1-131">Definiuje ustawienia zabezpieczeń na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="db6e1-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="db6e1-132">Ten element jest typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="db6e1-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db6e1-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="db6e1-133">Parent Elements</span></span>  
  
|<span data-ttu-id="db6e1-134">Element</span><span class="sxs-lookup"><span data-stu-id="db6e1-134">Element</span></span>|<span data-ttu-id="db6e1-135">Opis</span><span class="sxs-lookup"><span data-stu-id="db6e1-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db6e1-136">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="db6e1-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="db6e1-137">Definiuje wszystkie możliwości wiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="db6e1-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db6e1-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db6e1-138">Remarks</span></span>  
 <span data-ttu-id="db6e1-139">Podwójna powiązania udostępnia adres IP klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="db6e1-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="db6e1-140">Klienta należy użyć zabezpieczeń, aby upewnić się, że tylko nawiązuje połączenie z usługi ona relacje zaufania.</span><span class="sxs-lookup"><span data-stu-id="db6e1-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6e1-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db6e1-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="db6e1-142">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="db6e1-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="db6e1-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="db6e1-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="db6e1-144">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="db6e1-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="db6e1-145">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="db6e1-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="db6e1-146">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="db6e1-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
