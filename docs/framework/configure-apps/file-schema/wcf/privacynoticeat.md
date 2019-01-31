---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: b1de2a304a5dc4295497ea1f3b395240cb5ca9bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254923"
---
# <a name="privacynoticeat"></a><span data-ttu-id="77417-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="77417-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="77417-102">Reprezentuje element konfiguracji, który określa zachowania poufności, używane w `wsFederationHttp` powiązania.</span><span class="sxs-lookup"><span data-stu-id="77417-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="77417-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="77417-103">\<system.serviceModel></span></span>  
<span data-ttu-id="77417-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="77417-104">\<bindings></span></span>  
<span data-ttu-id="77417-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="77417-105">\<customBinding></span></span>  
<span data-ttu-id="77417-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="77417-106">\<binding></span></span>  
<span data-ttu-id="77417-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="77417-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77417-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="77417-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="77417-109">Typ</span><span class="sxs-lookup"><span data-stu-id="77417-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77417-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="77417-110">Attributes and Elements</span></span>  
 <span data-ttu-id="77417-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="77417-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77417-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="77417-112">Attributes</span></span>  
  
|<span data-ttu-id="77417-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="77417-113">Attribute</span></span>|<span data-ttu-id="77417-114">Opis</span><span class="sxs-lookup"><span data-stu-id="77417-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="77417-115">Ciąg określający URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="77417-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="77417-116">Liczba całkowita określająca wersję tego zawiadomienia o prywatności.</span><span class="sxs-lookup"><span data-stu-id="77417-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77417-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="77417-117">Child Elements</span></span>  
 <span data-ttu-id="77417-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="77417-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77417-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="77417-119">Parent Elements</span></span>  
  
|<span data-ttu-id="77417-120">Element</span><span class="sxs-lookup"><span data-stu-id="77417-120">Element</span></span>|<span data-ttu-id="77417-121">Opis</span><span class="sxs-lookup"><span data-stu-id="77417-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77417-122">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="77417-122">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="77417-123">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="77417-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77417-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77417-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="77417-125">Powiązania</span><span class="sxs-lookup"><span data-stu-id="77417-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="77417-126">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="77417-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="77417-127">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="77417-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="77417-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="77417-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
