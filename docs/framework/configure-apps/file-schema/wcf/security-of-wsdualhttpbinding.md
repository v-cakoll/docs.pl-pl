---
title: '&lt;security&gt; w &lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 5759e8a3618cd959605b139577bae24c35490ea8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150217"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="5c48f-102">&lt;security&gt; w &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5c48f-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="5c48f-103">Definiuje możliwości zabezpieczeń [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5c48f-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="5c48f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5c48f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5c48f-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5c48f-105">\<bindings></span></span>  
<span data-ttu-id="5c48f-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5c48f-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="5c48f-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5c48f-107">\<binding></span></span>  
<span data-ttu-id="5c48f-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="5c48f-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c48f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c48f-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c48f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5c48f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5c48f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5c48f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c48f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5c48f-112">Attributes</span></span>  
  
|<span data-ttu-id="5c48f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5c48f-113">Attribute</span></span>|<span data-ttu-id="5c48f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5c48f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c48f-115">tryb</span><span class="sxs-lookup"><span data-stu-id="5c48f-115">mode</span></span>|<span data-ttu-id="5c48f-116">— Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5c48f-116">-   Optional.</span></span> <span data-ttu-id="5c48f-117">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="5c48f-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="5c48f-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="5c48f-118">The default value is `Message`.</span></span> <span data-ttu-id="5c48f-119">Ten atrybut jest typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5c48f-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5c48f-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="5c48f-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="5c48f-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="5c48f-121">Value</span></span>|<span data-ttu-id="5c48f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5c48f-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c48f-123">Brak</span><span class="sxs-lookup"><span data-stu-id="5c48f-123">None</span></span>|<span data-ttu-id="5c48f-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5c48f-124">Security is disabled.</span></span>|  
|<span data-ttu-id="5c48f-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="5c48f-125">Message</span></span>|<span data-ttu-id="5c48f-126">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5c48f-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c48f-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5c48f-127">Child Elements</span></span>  
  
|<span data-ttu-id="5c48f-128">Element</span><span class="sxs-lookup"><span data-stu-id="5c48f-128">Element</span></span>|<span data-ttu-id="5c48f-129">Opis</span><span class="sxs-lookup"><span data-stu-id="5c48f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c48f-130">\<message></span><span class="sxs-lookup"><span data-stu-id="5c48f-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="5c48f-131">Definiuje ustawienia zabezpieczeń na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5c48f-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="5c48f-132">Ten element jest typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="5c48f-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c48f-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5c48f-133">Parent Elements</span></span>  
  
|<span data-ttu-id="5c48f-134">Element</span><span class="sxs-lookup"><span data-stu-id="5c48f-134">Element</span></span>|<span data-ttu-id="5c48f-135">Opis</span><span class="sxs-lookup"><span data-stu-id="5c48f-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c48f-136">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5c48f-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5c48f-137">Definiuje wszystkie możliwości wiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5c48f-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c48f-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c48f-138">Remarks</span></span>  
 <span data-ttu-id="5c48f-139">Podwójna powiązania udostępnia adres IP klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="5c48f-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="5c48f-140">Klienta należy użyć zabezpieczeń, aby upewnić się, że tylko nawiązuje połączenie z usługi ona relacje zaufania.</span><span class="sxs-lookup"><span data-stu-id="5c48f-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c48f-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c48f-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="5c48f-142">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="5c48f-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5c48f-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5c48f-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5c48f-144">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="5c48f-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5c48f-145">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="5c48f-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="5c48f-146">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5c48f-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
