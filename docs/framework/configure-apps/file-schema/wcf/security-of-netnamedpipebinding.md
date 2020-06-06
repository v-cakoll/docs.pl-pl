---
title: <security> dla <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736434"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="37384-102">\<security> dla \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="37384-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="37384-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="37384-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="37384-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37384-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37384-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37384-105">Attributes and Elements</span></span>  
 <span data-ttu-id="37384-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37384-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37384-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37384-107">Attributes</span></span>  
  
|<span data-ttu-id="37384-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37384-108">Attribute</span></span>|<span data-ttu-id="37384-109">Opis</span><span class="sxs-lookup"><span data-stu-id="37384-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37384-110">tryb</span><span class="sxs-lookup"><span data-stu-id="37384-110">mode</span></span>|<span data-ttu-id="37384-111">Określa typ zabezpieczeń, które są stosowane do tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="37384-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="37384-112">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="37384-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="37384-113">-Brak: spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="37384-113">-   None: This disables security.</span></span><br /><span data-ttu-id="37384-114">-Transport: zabezpieczenia są udostępniane przy użyciu podstawowych zabezpieczeń opartych na transportach.</span><span class="sxs-lookup"><span data-stu-id="37384-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="37384-115">Istnieje możliwość kontrolowania poziomu ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="37384-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="37384-116">— Wartość domyślna to transport.</span><span class="sxs-lookup"><span data-stu-id="37384-116">-   The default value is Transport.</span></span> <span data-ttu-id="37384-117">Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="37384-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37384-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37384-118">Child Elements</span></span>  
  
|<span data-ttu-id="37384-119">Element</span><span class="sxs-lookup"><span data-stu-id="37384-119">Element</span></span>|<span data-ttu-id="37384-120">Opis</span><span class="sxs-lookup"><span data-stu-id="37384-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37384-121">transport</span><span class="sxs-lookup"><span data-stu-id="37384-121">transport</span></span>|<span data-ttu-id="37384-122">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="37384-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="37384-123">Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="37384-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37384-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37384-124">Parent Elements</span></span>  
  
|<span data-ttu-id="37384-125">Element</span><span class="sxs-lookup"><span data-stu-id="37384-125">Element</span></span>|<span data-ttu-id="37384-126">Opis</span><span class="sxs-lookup"><span data-stu-id="37384-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37384-127">powiązanie</span><span class="sxs-lookup"><span data-stu-id="37384-127">binding</span></span>|<span data-ttu-id="37384-128">Element Binding elementu [\<netNamedPipeBinding>](netnamedpipebinding.md) .</span><span class="sxs-lookup"><span data-stu-id="37384-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37384-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37384-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="37384-130">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="37384-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="37384-131">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="37384-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="37384-132">Powiązania</span><span class="sxs-lookup"><span data-stu-id="37384-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="37384-133">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="37384-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="37384-134">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="37384-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
