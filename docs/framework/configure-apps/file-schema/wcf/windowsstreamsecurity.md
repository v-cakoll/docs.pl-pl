---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 32e8ed6b70a23462fac3c53d1bc353167ff67560
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113636"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="57f53-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="57f53-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="57f53-102">Określ ustawienia zabezpieczenia strumienia Windows niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="57f53-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="57f53-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="57f53-103">\<system.serviceModel></span></span>  
<span data-ttu-id="57f53-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="57f53-104">\<bindings></span></span>  
<span data-ttu-id="57f53-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="57f53-105">\<customBinding></span></span>  
<span data-ttu-id="57f53-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="57f53-106">\<binding></span></span>  
<span data-ttu-id="57f53-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="57f53-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f53-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="57f53-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57f53-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="57f53-109">Attributes and Elements</span></span>  
 <span data-ttu-id="57f53-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="57f53-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57f53-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="57f53-111">Attributes</span></span>  
  
|<span data-ttu-id="57f53-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="57f53-112">Attribute</span></span>|<span data-ttu-id="57f53-113">Opis</span><span class="sxs-lookup"><span data-stu-id="57f53-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57f53-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="57f53-114">protectionLevel</span></span>|<span data-ttu-id="57f53-115">Definiuje zabezpieczenia na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="57f53-115">Defines message-level security.</span></span> <span data-ttu-id="57f53-116">Podpisywania wiadomości zmniejsza ryzyko związane z innej naruszeniu komunikat, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="57f53-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="57f53-117">Szyfrowanie zapewnia ochronę poufności poziom danych, podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="57f53-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="57f53-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="57f53-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="57f53-119">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="57f53-119">-   None: No protection.</span></span><br /><span data-ttu-id="57f53-120">— Logowanie: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="57f53-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="57f53-121">-EncryptAndSign: Komunikaty są podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="57f53-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="57f53-122">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="57f53-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="57f53-123">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="57f53-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57f53-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="57f53-124">Child Elements</span></span>  
 <span data-ttu-id="57f53-125">Brak</span><span class="sxs-lookup"><span data-stu-id="57f53-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57f53-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="57f53-126">Parent Elements</span></span>  
  
|<span data-ttu-id="57f53-127">Element</span><span class="sxs-lookup"><span data-stu-id="57f53-127">Element</span></span>|<span data-ttu-id="57f53-128">Opis</span><span class="sxs-lookup"><span data-stu-id="57f53-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57f53-129">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="57f53-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="57f53-130">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="57f53-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57f53-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57f53-131">Remarks</span></span>  
 <span data-ttu-id="57f53-132">Transport, które używają protokołem zorientowane na strumień, takich jak TCP i nazwane potoki obsługują uaktualnienia na podstawie strumienia transportu.</span><span class="sxs-lookup"><span data-stu-id="57f53-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="57f53-133">W szczególności WCF zapewnia bezpieczeństwo uaktualnień.</span><span class="sxs-lookup"><span data-stu-id="57f53-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="57f53-134">Konfiguracja zabezpieczeń transportu jest hermetyzowany przez ten element konfiguracji, za pomocą [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), które można konfigurować i dodane do powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="57f53-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f53-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57f53-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="57f53-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="57f53-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="57f53-137">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="57f53-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="57f53-138">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="57f53-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="57f53-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="57f53-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
