---
title: <security> dla <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: b6a1c952b1ae65c8fb6f17237b5c15f3a8d4844a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399748"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="f4a5c-102">\<zabezpieczenia > \<WSDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f4a5c-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="f4a5c-103">Definiuje możliwości [ \<zabezpieczeń > WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f4a5c-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
<span data-ttu-id="f4a5c-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4a5c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f4a5c-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f4a5c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f4a5c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f4a5c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f4a5c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f4a5c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)</span></span>\
<span data-ttu-id="f4a5c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="f4a5c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f4a5c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="f4a5c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a5c-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4a5c-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4a5c-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f4a5c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f4a5c-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4a5c-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f4a5c-113">Attributes</span></span>  
  
|<span data-ttu-id="f4a5c-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f4a5c-114">Attribute</span></span>|<span data-ttu-id="f4a5c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f4a5c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4a5c-116">tryb</span><span class="sxs-lookup"><span data-stu-id="f4a5c-116">mode</span></span>|<span data-ttu-id="f4a5c-117">Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-117">-   Optional.</span></span> <span data-ttu-id="f4a5c-118">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="f4a5c-119">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-119">The default value is `Message`.</span></span> <span data-ttu-id="f4a5c-120">Ten atrybut jest typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-120">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f4a5c-121">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="f4a5c-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="f4a5c-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="f4a5c-122">Value</span></span>|<span data-ttu-id="f4a5c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f4a5c-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4a5c-124">Brak</span><span class="sxs-lookup"><span data-stu-id="f4a5c-124">None</span></span>|<span data-ttu-id="f4a5c-125">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-125">Security is disabled.</span></span>|  
|<span data-ttu-id="f4a5c-126">Message</span><span class="sxs-lookup"><span data-stu-id="f4a5c-126">Message</span></span>|<span data-ttu-id="f4a5c-127">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-127">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4a5c-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f4a5c-128">Child Elements</span></span>  
  
|<span data-ttu-id="f4a5c-129">Element</span><span class="sxs-lookup"><span data-stu-id="f4a5c-129">Element</span></span>|<span data-ttu-id="f4a5c-130">Opis</span><span class="sxs-lookup"><span data-stu-id="f4a5c-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4a5c-131">\<message></span><span class="sxs-lookup"><span data-stu-id="f4a5c-131">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="f4a5c-132">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="f4a5c-133">Ten element jest typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-133">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4a5c-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f4a5c-134">Parent Elements</span></span>  
  
|<span data-ttu-id="f4a5c-135">Element</span><span class="sxs-lookup"><span data-stu-id="f4a5c-135">Element</span></span>|<span data-ttu-id="f4a5c-136">Opis</span><span class="sxs-lookup"><span data-stu-id="f4a5c-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4a5c-137">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f4a5c-137">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="f4a5c-138">Definiuje wszystkie możliwości [ \<powiązań WSDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f4a5c-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4a5c-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4a5c-139">Remarks</span></span>  
 <span data-ttu-id="f4a5c-140">Podwójne powiązanie uwidacznia adres IP klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-140">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="f4a5c-141">Klient powinien korzystać z zabezpieczeń, aby upewnić się, że tylko nawiązuje połączenie z usługami, które ufają.</span><span class="sxs-lookup"><span data-stu-id="f4a5c-141">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a5c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4a5c-142">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="f4a5c-143">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f4a5c-143">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f4a5c-144">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f4a5c-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f4a5c-145">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f4a5c-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f4a5c-146">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f4a5c-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f4a5c-147">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f4a5c-147">\<binding></span></span>](../../../misc/binding.md)
