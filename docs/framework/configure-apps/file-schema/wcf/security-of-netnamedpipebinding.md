---
title: <security> dla <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: cd3ff5d3983283f9b4783912b4b9525c5000df61
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399830"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="35c54-102">\<zabezpieczenia > \<NetNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="35c54-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="35c54-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="35c54-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="35c54-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="35c54-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="35c54-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="35c54-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="35c54-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="35c54-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="35c54-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="35c54-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="35c54-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="35c54-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="35c54-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="35c54-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c54-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="35c54-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35c54-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35c54-111">Attributes and Elements</span></span>  
 <span data-ttu-id="35c54-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35c54-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35c54-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35c54-113">Attributes</span></span>  
  
|<span data-ttu-id="35c54-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="35c54-114">Attribute</span></span>|<span data-ttu-id="35c54-115">Opis</span><span class="sxs-lookup"><span data-stu-id="35c54-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35c54-116">tryb</span><span class="sxs-lookup"><span data-stu-id="35c54-116">mode</span></span>|<span data-ttu-id="35c54-117">Określa typ zabezpieczeń, które są stosowane do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="35c54-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="35c54-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="35c54-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="35c54-119">Dawaj Spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="35c54-119">-   None: This disables security.</span></span><br /><span data-ttu-id="35c54-120">Transportu Zabezpieczenia są udostępniane przy użyciu podstawowych zabezpieczeń opartych na transportach.</span><span class="sxs-lookup"><span data-stu-id="35c54-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="35c54-121">Istnieje możliwość kontrolowania poziomu ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="35c54-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="35c54-122">— Wartość domyślna to transport.</span><span class="sxs-lookup"><span data-stu-id="35c54-122">-   The default value is Transport.</span></span> <span data-ttu-id="35c54-123">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="35c54-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35c54-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35c54-124">Child Elements</span></span>  
  
|<span data-ttu-id="35c54-125">Element</span><span class="sxs-lookup"><span data-stu-id="35c54-125">Element</span></span>|<span data-ttu-id="35c54-126">Opis</span><span class="sxs-lookup"><span data-stu-id="35c54-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35c54-127">transport</span><span class="sxs-lookup"><span data-stu-id="35c54-127">transport</span></span>|<span data-ttu-id="35c54-128">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="35c54-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="35c54-129">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="35c54-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35c54-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35c54-130">Parent Elements</span></span>  
  
|<span data-ttu-id="35c54-131">Element</span><span class="sxs-lookup"><span data-stu-id="35c54-131">Element</span></span>|<span data-ttu-id="35c54-132">Opis</span><span class="sxs-lookup"><span data-stu-id="35c54-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35c54-133">powiązanie</span><span class="sxs-lookup"><span data-stu-id="35c54-133">binding</span></span>|<span data-ttu-id="35c54-134">Element Binding elementu [ \<NetNamedPipeBinding >](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="35c54-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35c54-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35c54-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="35c54-136">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="35c54-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="35c54-137">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="35c54-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="35c54-138">Powiązania</span><span class="sxs-lookup"><span data-stu-id="35c54-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="35c54-139">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="35c54-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="35c54-140">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="35c54-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="35c54-141">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="35c54-141">\<binding></span></span>](../../../misc/binding.md)
