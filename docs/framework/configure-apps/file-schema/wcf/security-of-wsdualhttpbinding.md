---
title: <security> dla <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: bed7f4ce325e0d5e387e310ca15a3b72ac93f18e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936544"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="db467-102">\<zabezpieczenia > \<WSDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="db467-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="db467-103">Definiuje możliwości [ \<zabezpieczeń > WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="db467-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="db467-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="db467-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="db467-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="db467-105">\<bindings></span></span>  
<span data-ttu-id="db467-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="db467-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="db467-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="db467-107">\<binding></span></span>  
<span data-ttu-id="db467-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="db467-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db467-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="db467-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db467-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="db467-110">Attributes and Elements</span></span>  
 <span data-ttu-id="db467-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="db467-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db467-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="db467-112">Attributes</span></span>  
  
|<span data-ttu-id="db467-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="db467-113">Attribute</span></span>|<span data-ttu-id="db467-114">Opis</span><span class="sxs-lookup"><span data-stu-id="db467-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db467-115">tryb</span><span class="sxs-lookup"><span data-stu-id="db467-115">mode</span></span>|<span data-ttu-id="db467-116">Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="db467-116">-   Optional.</span></span> <span data-ttu-id="db467-117">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="db467-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="db467-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="db467-118">The default value is `Message`.</span></span> <span data-ttu-id="db467-119">Ten atrybut jest typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="db467-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="db467-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="db467-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="db467-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="db467-121">Value</span></span>|<span data-ttu-id="db467-122">Opis</span><span class="sxs-lookup"><span data-stu-id="db467-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db467-123">Brak</span><span class="sxs-lookup"><span data-stu-id="db467-123">None</span></span>|<span data-ttu-id="db467-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="db467-124">Security is disabled.</span></span>|  
|<span data-ttu-id="db467-125">Message</span><span class="sxs-lookup"><span data-stu-id="db467-125">Message</span></span>|<span data-ttu-id="db467-126">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="db467-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db467-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="db467-127">Child Elements</span></span>  
  
|<span data-ttu-id="db467-128">Element</span><span class="sxs-lookup"><span data-stu-id="db467-128">Element</span></span>|<span data-ttu-id="db467-129">Opis</span><span class="sxs-lookup"><span data-stu-id="db467-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db467-130">\<message></span><span class="sxs-lookup"><span data-stu-id="db467-130">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="db467-131">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="db467-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="db467-132">Ten element jest typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="db467-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db467-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="db467-133">Parent Elements</span></span>  
  
|<span data-ttu-id="db467-134">Element</span><span class="sxs-lookup"><span data-stu-id="db467-134">Element</span></span>|<span data-ttu-id="db467-135">Opis</span><span class="sxs-lookup"><span data-stu-id="db467-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db467-136">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="db467-136">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="db467-137">Definiuje wszystkie możliwości [ \<powiązań WSDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="db467-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db467-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db467-138">Remarks</span></span>  
 <span data-ttu-id="db467-139">Podwójne powiązanie uwidacznia adres IP klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="db467-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="db467-140">Klient powinien korzystać z zabezpieczeń, aby upewnić się, że tylko nawiązuje połączenie z usługami, które ufają.</span><span class="sxs-lookup"><span data-stu-id="db467-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db467-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db467-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="db467-142">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="db467-142">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="db467-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="db467-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="db467-144">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="db467-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="db467-145">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="db467-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="db467-146">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="db467-146">\<binding></span></span>](../../../misc/binding.md)
