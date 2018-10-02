---
title: '&lt;security&gt; w &lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
ms.openlocfilehash: c817ea6faf5229a8d372a06b866c75e0f40af3b3
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863120"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="c1c54-102">&lt;security&gt; w &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="c1c54-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="c1c54-103">Definiuje możliwości zabezpieczeń [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c1c54-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="c1c54-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c1c54-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c1c54-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c1c54-105">\<bindings></span></span>  
<span data-ttu-id="c1c54-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c1c54-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="c1c54-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c1c54-107">\<binding></span></span>  
<span data-ttu-id="c1c54-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="c1c54-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1c54-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1c54-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1c54-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c1c54-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c1c54-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c1c54-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1c54-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c1c54-112">Attributes</span></span>  
  
|<span data-ttu-id="c1c54-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c1c54-113">Attribute</span></span>|<span data-ttu-id="c1c54-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c1c54-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1c54-115">tryb</span><span class="sxs-lookup"><span data-stu-id="c1c54-115">mode</span></span>|<span data-ttu-id="c1c54-116">— Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c1c54-116">-   Optional.</span></span> <span data-ttu-id="c1c54-117">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="c1c54-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="c1c54-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="c1c54-118">The default value is `Message`.</span></span> <span data-ttu-id="c1c54-119">Ten atrybut jest typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="c1c54-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c1c54-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="c1c54-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="c1c54-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="c1c54-121">Value</span></span>|<span data-ttu-id="c1c54-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c1c54-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1c54-123">Brak</span><span class="sxs-lookup"><span data-stu-id="c1c54-123">None</span></span>|<span data-ttu-id="c1c54-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c1c54-124">Security is disabled.</span></span>|  
|<span data-ttu-id="c1c54-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c1c54-125">Message</span></span>|<span data-ttu-id="c1c54-126">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c1c54-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1c54-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c1c54-127">Child Elements</span></span>  
  
|<span data-ttu-id="c1c54-128">Element</span><span class="sxs-lookup"><span data-stu-id="c1c54-128">Element</span></span>|<span data-ttu-id="c1c54-129">Opis</span><span class="sxs-lookup"><span data-stu-id="c1c54-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1c54-130">\<message></span><span class="sxs-lookup"><span data-stu-id="c1c54-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="c1c54-131">Definiuje ustawienia zabezpieczeń na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c1c54-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="c1c54-132">Ten element jest typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="c1c54-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1c54-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c1c54-133">Parent Elements</span></span>  
  
|<span data-ttu-id="c1c54-134">Element</span><span class="sxs-lookup"><span data-stu-id="c1c54-134">Element</span></span>|<span data-ttu-id="c1c54-135">Opis</span><span class="sxs-lookup"><span data-stu-id="c1c54-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1c54-136">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c1c54-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c1c54-137">Definiuje wszystkie możliwości wiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c1c54-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1c54-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1c54-138">Remarks</span></span>  
 <span data-ttu-id="c1c54-139">Podwójna powiązania udostępnia adres IP klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="c1c54-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="c1c54-140">Klienta należy użyć zabezpieczeń, aby upewnić się, że tylko nawiązuje połączenie z usługi ona relacje zaufania.</span><span class="sxs-lookup"><span data-stu-id="c1c54-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c54-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1c54-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="c1c54-142">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c1c54-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="c1c54-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c1c54-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c1c54-144">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c1c54-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c1c54-145">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c1c54-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="c1c54-146">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c1c54-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
