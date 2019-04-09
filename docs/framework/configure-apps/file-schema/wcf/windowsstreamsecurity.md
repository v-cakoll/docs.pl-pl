---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 32e8ed6b70a23462fac3c53d1bc353167ff67560
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113636"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="1afa6-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="1afa6-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="1afa6-102">Określ ustawienia zabezpieczenia strumienia Windows niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1afa6-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="1afa6-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1afa6-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1afa6-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1afa6-104">\<bindings></span></span>  
<span data-ttu-id="1afa6-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1afa6-105">\<customBinding></span></span>  
<span data-ttu-id="1afa6-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1afa6-106">\<binding></span></span>  
<span data-ttu-id="1afa6-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="1afa6-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1afa6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1afa6-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1afa6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1afa6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1afa6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1afa6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1afa6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1afa6-111">Attributes</span></span>  
  
|<span data-ttu-id="1afa6-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1afa6-112">Attribute</span></span>|<span data-ttu-id="1afa6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1afa6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1afa6-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1afa6-114">protectionLevel</span></span>|<span data-ttu-id="1afa6-115">Definiuje zabezpieczenia na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1afa6-115">Defines message-level security.</span></span> <span data-ttu-id="1afa6-116">Podpisywania wiadomości zmniejsza ryzyko związane z innej naruszeniu komunikat, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="1afa6-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1afa6-117">Szyfrowanie zapewnia ochronę poufności poziom danych, podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="1afa6-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="1afa6-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="1afa6-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1afa6-119">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="1afa6-119">-   None: No protection.</span></span><br /><span data-ttu-id="1afa6-120">— Logowanie: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="1afa6-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1afa6-121">-EncryptAndSign: Komunikaty są podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="1afa6-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="1afa6-122">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="1afa6-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="1afa6-123">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="1afa6-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1afa6-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1afa6-124">Child Elements</span></span>  
 <span data-ttu-id="1afa6-125">Brak</span><span class="sxs-lookup"><span data-stu-id="1afa6-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1afa6-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1afa6-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1afa6-127">Element</span><span class="sxs-lookup"><span data-stu-id="1afa6-127">Element</span></span>|<span data-ttu-id="1afa6-128">Opis</span><span class="sxs-lookup"><span data-stu-id="1afa6-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1afa6-129">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1afa6-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1afa6-130">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1afa6-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1afa6-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1afa6-131">Remarks</span></span>  
 <span data-ttu-id="1afa6-132">Transport, które używają protokołem zorientowane na strumień, takich jak TCP i nazwane potoki obsługują uaktualnienia na podstawie strumienia transportu.</span><span class="sxs-lookup"><span data-stu-id="1afa6-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="1afa6-133">W szczególności WCF zapewnia bezpieczeństwo uaktualnień.</span><span class="sxs-lookup"><span data-stu-id="1afa6-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="1afa6-134">Konfiguracja zabezpieczeń transportu jest hermetyzowany przez ten element konfiguracji, za pomocą [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), które można konfigurować i dodane do powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1afa6-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1afa6-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1afa6-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="1afa6-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1afa6-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1afa6-137">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="1afa6-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1afa6-138">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1afa6-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1afa6-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1afa6-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
