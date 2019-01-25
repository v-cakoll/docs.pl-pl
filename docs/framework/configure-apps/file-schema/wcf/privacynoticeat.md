---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: bf694911e0715275991084604ce44535d9183eff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683719"
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="4da8c-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="4da8c-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="4da8c-103">Reprezentuje element konfiguracji, który określa zachowania poufności, używane w `wsFederationHttp` powiązania.</span><span class="sxs-lookup"><span data-stu-id="4da8c-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="4da8c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4da8c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4da8c-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4da8c-105">\<bindings></span></span>  
<span data-ttu-id="4da8c-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4da8c-106">\<customBinding></span></span>  
<span data-ttu-id="4da8c-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4da8c-107">\<binding></span></span>  
<span data-ttu-id="4da8c-108">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="4da8c-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da8c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4da8c-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="4da8c-110">Typ</span><span class="sxs-lookup"><span data-stu-id="4da8c-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4da8c-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4da8c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4da8c-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4da8c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4da8c-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4da8c-113">Attributes</span></span>  
  
|<span data-ttu-id="4da8c-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4da8c-114">Attribute</span></span>|<span data-ttu-id="4da8c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4da8c-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="4da8c-116">Ciąg określający URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="4da8c-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="4da8c-117">Liczba całkowita określająca wersję tego zawiadomienia o prywatności.</span><span class="sxs-lookup"><span data-stu-id="4da8c-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4da8c-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4da8c-118">Child Elements</span></span>  
 <span data-ttu-id="4da8c-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="4da8c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4da8c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4da8c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4da8c-121">Element</span><span class="sxs-lookup"><span data-stu-id="4da8c-121">Element</span></span>|<span data-ttu-id="4da8c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4da8c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4da8c-123">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4da8c-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4da8c-124">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4da8c-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4da8c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4da8c-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4da8c-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4da8c-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4da8c-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="4da8c-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4da8c-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="4da8c-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4da8c-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4da8c-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
