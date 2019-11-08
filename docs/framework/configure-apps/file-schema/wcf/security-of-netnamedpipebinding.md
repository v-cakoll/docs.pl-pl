---
title: <security> dla <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736434"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="7aa87-102">\<> zabezpieczeń \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="7aa87-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="7aa87-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="7aa87-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="7aa87-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7aa87-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7aa87-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7aa87-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7aa87-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="7aa87-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7aa87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetNamedPipeBinding**](netnamedpipebinding.md) ></span><span class="sxs-lookup"><span data-stu-id="7aa87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="7aa87-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="7aa87-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7aa87-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpieczenia >**</span><span class="sxs-lookup"><span data-stu-id="7aa87-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aa87-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="7aa87-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7aa87-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7aa87-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7aa87-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7aa87-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7aa87-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7aa87-113">Attributes</span></span>  
  
|<span data-ttu-id="7aa87-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7aa87-114">Attribute</span></span>|<span data-ttu-id="7aa87-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7aa87-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7aa87-116">tryb</span><span class="sxs-lookup"><span data-stu-id="7aa87-116">mode</span></span>|<span data-ttu-id="7aa87-117">Określa typ zabezpieczeń, które są stosowane do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7aa87-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="7aa87-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="7aa87-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7aa87-119">-Brak: spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7aa87-119">-   None: This disables security.</span></span><br /><span data-ttu-id="7aa87-120">-Transport: zabezpieczenia są udostępniane przy użyciu podstawowych zabezpieczeń opartych na transportach.</span><span class="sxs-lookup"><span data-stu-id="7aa87-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="7aa87-121">Istnieje możliwość kontrolowania poziomu ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="7aa87-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="7aa87-122">— Wartość domyślna to transport.</span><span class="sxs-lookup"><span data-stu-id="7aa87-122">-   The default value is Transport.</span></span> <span data-ttu-id="7aa87-123">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7aa87-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7aa87-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7aa87-124">Child Elements</span></span>  
  
|<span data-ttu-id="7aa87-125">Element</span><span class="sxs-lookup"><span data-stu-id="7aa87-125">Element</span></span>|<span data-ttu-id="7aa87-126">Opis</span><span class="sxs-lookup"><span data-stu-id="7aa87-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7aa87-127">transport</span><span class="sxs-lookup"><span data-stu-id="7aa87-127">transport</span></span>|<span data-ttu-id="7aa87-128">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="7aa87-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="7aa87-129">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7aa87-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7aa87-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7aa87-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7aa87-131">Element</span><span class="sxs-lookup"><span data-stu-id="7aa87-131">Element</span></span>|<span data-ttu-id="7aa87-132">Opis</span><span class="sxs-lookup"><span data-stu-id="7aa87-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7aa87-133">powiązanie</span><span class="sxs-lookup"><span data-stu-id="7aa87-133">binding</span></span>|<span data-ttu-id="7aa87-134">Element powiązania [\<netNamedPipeBinding >](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="7aa87-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7aa87-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7aa87-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="7aa87-136">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7aa87-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7aa87-137">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="7aa87-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="7aa87-138">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7aa87-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7aa87-139">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="7aa87-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7aa87-140">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7aa87-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7aa87-141">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="7aa87-141">\<binding></span></span>](bindings.md)
