---
title: '&lt;Obiekt windowsStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5a0d3b61f473b49abdb2470a9fa5381dc9929274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="62c56-102">&lt;Obiekt windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="62c56-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="62c56-103">Określ ustawienia zabezpieczenia strumienia systemu Windows niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="62c56-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="62c56-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="62c56-104">\<system.serviceModel></span></span>  
<span data-ttu-id="62c56-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="62c56-105">\<bindings></span></span>  
<span data-ttu-id="62c56-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="62c56-106">\<customBinding></span></span>  
<span data-ttu-id="62c56-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="62c56-107">\<binding></span></span>  
<span data-ttu-id="62c56-108">\<Obiekt windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="62c56-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c56-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="62c56-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62c56-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="62c56-110">Attributes and Elements</span></span>  
 <span data-ttu-id="62c56-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="62c56-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62c56-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="62c56-112">Attributes</span></span>  
  
|<span data-ttu-id="62c56-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="62c56-113">Attribute</span></span>|<span data-ttu-id="62c56-114">Opis</span><span class="sxs-lookup"><span data-stu-id="62c56-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62c56-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="62c56-115">protectionLevel</span></span>|<span data-ttu-id="62c56-116">Definiuje zabezpieczenia na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="62c56-116">Defines message-level security.</span></span> <span data-ttu-id="62c56-117">Podpisywanie wiadomości zmniejsza ryzyko innych firm, manipulowanie wiadomości, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="62c56-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="62c56-118">Szyfrowanie zapewnia ochronę poufności poziom danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="62c56-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="62c56-119">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="62c56-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62c56-120">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="62c56-120">-   None: No protection.</span></span><br /><span data-ttu-id="62c56-121">-Znak: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="62c56-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="62c56-122">-EncryptAndSign: Komunikaty są podpisane i zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="62c56-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="62c56-123">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="62c56-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="62c56-124">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="62c56-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62c56-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62c56-125">Child Elements</span></span>  
 <span data-ttu-id="62c56-126">Brak</span><span class="sxs-lookup"><span data-stu-id="62c56-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62c56-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="62c56-127">Parent Elements</span></span>  
  
|<span data-ttu-id="62c56-128">Element</span><span class="sxs-lookup"><span data-stu-id="62c56-128">Element</span></span>|<span data-ttu-id="62c56-129">Opis</span><span class="sxs-lookup"><span data-stu-id="62c56-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62c56-130">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="62c56-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="62c56-131">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="62c56-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62c56-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62c56-132">Remarks</span></span>  
 <span data-ttu-id="62c56-133">Transporty Użyj protokołu zorientowanych strumieniowo np. TCP i nazwane potoki obsługują uaktualnienia transportu na podstawie strumienia.</span><span class="sxs-lookup"><span data-stu-id="62c56-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="62c56-134">W szczególności WCF udostępnia aktualizacje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="62c56-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="62c56-135">Konfiguracja zabezpieczeń transportu jest hermetyzowany przez ten element konfiguracji za pomocą [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), które można konfigurować i dodane do powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="62c56-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c56-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62c56-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="62c56-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="62c56-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="62c56-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="62c56-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="62c56-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="62c56-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="62c56-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="62c56-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
