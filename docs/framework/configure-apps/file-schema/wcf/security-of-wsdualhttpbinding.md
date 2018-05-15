---
title: '&lt;security&gt; w &lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 734b6d0625cfda79b600a0920ab39bda25ee2e8b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="06e41-102">&lt;security&gt; w &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="06e41-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="06e41-103">Możliwości zabezpieczeń definiuje [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="06e41-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="06e41-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="06e41-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="06e41-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="06e41-105">\<bindings></span></span>  
<span data-ttu-id="06e41-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="06e41-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="06e41-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="06e41-107">\<binding></span></span>  
<span data-ttu-id="06e41-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="06e41-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e41-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="06e41-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06e41-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06e41-110">Attributes and Elements</span></span>  
 <span data-ttu-id="06e41-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="06e41-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06e41-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06e41-112">Attributes</span></span>  
  
|<span data-ttu-id="06e41-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="06e41-113">Attribute</span></span>|<span data-ttu-id="06e41-114">Opis</span><span class="sxs-lookup"><span data-stu-id="06e41-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06e41-115">tryb</span><span class="sxs-lookup"><span data-stu-id="06e41-115">mode</span></span>|<span data-ttu-id="06e41-116">-Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="06e41-116">-   Optional.</span></span> <span data-ttu-id="06e41-117">Określa typ zabezpieczeń, która została zastosowana.</span><span class="sxs-lookup"><span data-stu-id="06e41-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="06e41-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="06e41-118">The default value is `Message`.</span></span> <span data-ttu-id="06e41-119">Ten atrybut jest typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="06e41-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="06e41-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="06e41-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="06e41-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="06e41-121">Value</span></span>|<span data-ttu-id="06e41-122">Opis</span><span class="sxs-lookup"><span data-stu-id="06e41-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06e41-123">Brak</span><span class="sxs-lookup"><span data-stu-id="06e41-123">None</span></span>|<span data-ttu-id="06e41-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="06e41-124">Security is disabled.</span></span>|  
|<span data-ttu-id="06e41-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="06e41-125">Message</span></span>|<span data-ttu-id="06e41-126">Zabezpieczenia korzystanie z zabezpieczeń komunikatów SOAP.</span><span class="sxs-lookup"><span data-stu-id="06e41-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06e41-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06e41-127">Child Elements</span></span>  
  
|<span data-ttu-id="06e41-128">Element</span><span class="sxs-lookup"><span data-stu-id="06e41-128">Element</span></span>|<span data-ttu-id="06e41-129">Opis</span><span class="sxs-lookup"><span data-stu-id="06e41-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06e41-130">\<message></span><span class="sxs-lookup"><span data-stu-id="06e41-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="06e41-131">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="06e41-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="06e41-132">Ten element jest typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="06e41-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06e41-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06e41-133">Parent Elements</span></span>  
  
|<span data-ttu-id="06e41-134">Element</span><span class="sxs-lookup"><span data-stu-id="06e41-134">Element</span></span>|<span data-ttu-id="06e41-135">Opis</span><span class="sxs-lookup"><span data-stu-id="06e41-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06e41-136">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="06e41-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="06e41-137">Definiuje wszystkie możliwości powiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="06e41-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06e41-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06e41-138">Remarks</span></span>  
 <span data-ttu-id="06e41-139">Dwa powiązania udostępnia adres IP klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="06e41-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="06e41-140">Klienta należy użyć zabezpieczeń, aby upewnić się, że go tylko łączy się z usługami go relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="06e41-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e41-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06e41-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="06e41-142">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="06e41-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="06e41-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="06e41-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="06e41-144">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="06e41-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="06e41-145">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="06e41-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="06e41-146">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="06e41-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
