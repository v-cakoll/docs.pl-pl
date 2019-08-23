---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 0f1dfd523e593c82727354db7ce39ffc992bdfb4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932803"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="ebe5d-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="ebe5d-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="ebe5d-102">Określ ustawienia zabezpieczeń strumienia systemu Windows niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="ebe5d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ebe5d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ebe5d-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="ebe5d-104">\<bindings></span></span>  
<span data-ttu-id="ebe5d-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ebe5d-105">\<customBinding></span></span>  
<span data-ttu-id="ebe5d-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="ebe5d-106">\<binding></span></span>  
<span data-ttu-id="ebe5d-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="ebe5d-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe5d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebe5d-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebe5d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ebe5d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ebe5d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebe5d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ebe5d-111">Attributes</span></span>  
  
|<span data-ttu-id="ebe5d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ebe5d-112">Attribute</span></span>|<span data-ttu-id="ebe5d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ebe5d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ebe5d-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="ebe5d-114">protectionLevel</span></span>|<span data-ttu-id="ebe5d-115">Definiuje zabezpieczenia na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-115">Defines message-level security.</span></span> <span data-ttu-id="ebe5d-116">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="ebe5d-117">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="ebe5d-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ebe5d-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ebe5d-119">Dawaj Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-119">-   None: No protection.</span></span><br /><span data-ttu-id="ebe5d-120">Zapis Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="ebe5d-121">EncryptAndSign Komunikaty są podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="ebe5d-122">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="ebe5d-123">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebe5d-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ebe5d-124">Child Elements</span></span>  
 <span data-ttu-id="ebe5d-125">Brak</span><span class="sxs-lookup"><span data-stu-id="ebe5d-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebe5d-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ebe5d-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ebe5d-127">Element</span><span class="sxs-lookup"><span data-stu-id="ebe5d-127">Element</span></span>|<span data-ttu-id="ebe5d-128">Opis</span><span class="sxs-lookup"><span data-stu-id="ebe5d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebe5d-129">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="ebe5d-129">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="ebe5d-130">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebe5d-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebe5d-131">Remarks</span></span>  
 <span data-ttu-id="ebe5d-132">Transporty korzystające z protokołu opartego na strumieniu, takiego jak TCP i nazwane potoki, obsługują uaktualnienia transportu na podstawie strumienia.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="ebe5d-133">W programie WCF dostępne są uaktualnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ebe5d-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="ebe5d-134">Konfiguracja tego zabezpieczenia transportu jest hermetyzowana przez ten element konfiguracji, a także przez [ \<sslStreamSecurity >](sslstreamsecurity.md), który można skonfigurować i dodać do niestandardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="ebe5d-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe5d-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebe5d-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="ebe5d-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ebe5d-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ebe5d-137">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="ebe5d-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ebe5d-138">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ebe5d-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ebe5d-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ebe5d-139">\<customBinding></span></span>](custombinding.md)
