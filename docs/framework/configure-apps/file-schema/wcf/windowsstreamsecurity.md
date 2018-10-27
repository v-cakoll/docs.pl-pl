---
title: '&lt;windowsStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: e117c30ba2583158ee21fd11ff4a38b094c18fd9
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50045931"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="0d532-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="0d532-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="0d532-103">Określ ustawienia zabezpieczenia strumienia Windows niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0d532-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="0d532-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0d532-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0d532-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0d532-105">\<bindings></span></span>  
<span data-ttu-id="0d532-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0d532-106">\<customBinding></span></span>  
<span data-ttu-id="0d532-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0d532-107">\<binding></span></span>  
<span data-ttu-id="0d532-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="0d532-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d532-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d532-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d532-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0d532-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0d532-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0d532-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d532-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0d532-112">Attributes</span></span>  
  
|<span data-ttu-id="0d532-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0d532-113">Attribute</span></span>|<span data-ttu-id="0d532-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0d532-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d532-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="0d532-115">protectionLevel</span></span>|<span data-ttu-id="0d532-116">Definiuje zabezpieczenia na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="0d532-116">Defines message-level security.</span></span> <span data-ttu-id="0d532-117">Podpisywania wiadomości zmniejsza ryzyko związane z innej naruszeniu komunikat, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="0d532-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="0d532-118">Szyfrowanie zapewnia ochronę poufności poziom danych, podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="0d532-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="0d532-119">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="0d532-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0d532-120">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="0d532-120">-   None: No protection.</span></span><br /><span data-ttu-id="0d532-121">— Logowanie: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="0d532-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="0d532-122">-EncryptAndSign: Komunikaty są podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="0d532-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="0d532-123">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="0d532-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="0d532-124">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="0d532-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d532-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0d532-125">Child Elements</span></span>  
 <span data-ttu-id="0d532-126">Brak</span><span class="sxs-lookup"><span data-stu-id="0d532-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d532-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0d532-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0d532-128">Element</span><span class="sxs-lookup"><span data-stu-id="0d532-128">Element</span></span>|<span data-ttu-id="0d532-129">Opis</span><span class="sxs-lookup"><span data-stu-id="0d532-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d532-130">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0d532-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0d532-131">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0d532-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d532-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d532-132">Remarks</span></span>  
 <span data-ttu-id="0d532-133">Transport, które używają protokołem zorientowane na strumień, takich jak TCP i nazwane potoki obsługują uaktualnienia na podstawie strumienia transportu.</span><span class="sxs-lookup"><span data-stu-id="0d532-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="0d532-134">W szczególności WCF zapewnia bezpieczeństwo uaktualnień.</span><span class="sxs-lookup"><span data-stu-id="0d532-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="0d532-135">Konfiguracja zabezpieczeń transportu jest hermetyzowany przez ten element konfiguracji, za pomocą [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), które można konfigurować i dodane do powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="0d532-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d532-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d532-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="0d532-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0d532-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0d532-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="0d532-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="0d532-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0d532-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="0d532-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0d532-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
