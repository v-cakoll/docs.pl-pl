---
title: <security> z <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 8bc35b3bc8f0cbe1a51ceab63d876d5859d6b325
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270867"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="b6589-102">\<Zabezpieczenia > z \<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b6589-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="b6589-103">Definiuje możliwości zabezpieczeń [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b6589-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="b6589-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b6589-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b6589-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b6589-105">\<bindings></span></span>  
<span data-ttu-id="b6589-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b6589-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="b6589-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b6589-107">\<binding></span></span>  
<span data-ttu-id="b6589-108">\<security></span><span class="sxs-lookup"><span data-stu-id="b6589-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6589-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6589-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6589-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6589-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b6589-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b6589-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6589-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6589-112">Attributes</span></span>  
  
|<span data-ttu-id="b6589-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6589-113">Attribute</span></span>|<span data-ttu-id="b6589-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b6589-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6589-115">tryb</span><span class="sxs-lookup"><span data-stu-id="b6589-115">mode</span></span>|<span data-ttu-id="b6589-116">— Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b6589-116">-   Optional.</span></span> <span data-ttu-id="b6589-117">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="b6589-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b6589-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="b6589-118">The default value is `Message`.</span></span> <span data-ttu-id="b6589-119">Ten atrybut jest typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b6589-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b6589-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="b6589-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="b6589-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="b6589-121">Value</span></span>|<span data-ttu-id="b6589-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b6589-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b6589-123">Brak</span><span class="sxs-lookup"><span data-stu-id="b6589-123">None</span></span>|<span data-ttu-id="b6589-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="b6589-124">Security is disabled.</span></span>|  
|<span data-ttu-id="b6589-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b6589-125">Message</span></span>|<span data-ttu-id="b6589-126">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b6589-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6589-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6589-127">Child Elements</span></span>  
  
|<span data-ttu-id="b6589-128">Element</span><span class="sxs-lookup"><span data-stu-id="b6589-128">Element</span></span>|<span data-ttu-id="b6589-129">Opis</span><span class="sxs-lookup"><span data-stu-id="b6589-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6589-130">\<message></span><span class="sxs-lookup"><span data-stu-id="b6589-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="b6589-131">Definiuje ustawienia zabezpieczeń na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b6589-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="b6589-132">Ten element jest typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="b6589-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6589-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6589-133">Parent Elements</span></span>  
  
|<span data-ttu-id="b6589-134">Element</span><span class="sxs-lookup"><span data-stu-id="b6589-134">Element</span></span>|<span data-ttu-id="b6589-135">Opis</span><span class="sxs-lookup"><span data-stu-id="b6589-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6589-136">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b6589-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b6589-137">Definiuje wszystkie możliwości wiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b6589-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6589-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6589-138">Remarks</span></span>  
 <span data-ttu-id="b6589-139">Podwójna powiązania udostępnia adres IP klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="b6589-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="b6589-140">Klienta należy użyć zabezpieczeń, aby upewnić się, że tylko nawiązuje połączenie z usługi ona relacje zaufania.</span><span class="sxs-lookup"><span data-stu-id="b6589-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6589-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6589-141">See also</span></span>
- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="b6589-142">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b6589-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b6589-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b6589-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b6589-144">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="b6589-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b6589-145">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="b6589-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b6589-146">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b6589-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
