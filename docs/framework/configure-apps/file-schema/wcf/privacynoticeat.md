---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: e2ce2111e4bb26cc6a51b4a772b1d8a4d3238c70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200769"
---
# <a name="privacynoticeat"></a><span data-ttu-id="f6cca-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="f6cca-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="f6cca-102">Reprezentuje element konfiguracji, który określa zachowania poufności, używane w `wsFederationHttp` powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6cca-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="f6cca-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f6cca-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f6cca-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f6cca-104">\<bindings></span></span>  
<span data-ttu-id="f6cca-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f6cca-105">\<customBinding></span></span>  
<span data-ttu-id="f6cca-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f6cca-106">\<binding></span></span>  
<span data-ttu-id="f6cca-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="f6cca-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6cca-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6cca-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f6cca-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f6cca-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6cca-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6cca-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f6cca-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f6cca-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6cca-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6cca-112">Attributes</span></span>  
  
|<span data-ttu-id="f6cca-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6cca-113">Attribute</span></span>|<span data-ttu-id="f6cca-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f6cca-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="f6cca-115">Ciąg określający URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="f6cca-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="f6cca-116">Liczba całkowita określająca wersję tego zawiadomienia o prywatności.</span><span class="sxs-lookup"><span data-stu-id="f6cca-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6cca-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6cca-117">Child Elements</span></span>  
 <span data-ttu-id="f6cca-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="f6cca-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6cca-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6cca-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f6cca-120">Element</span><span class="sxs-lookup"><span data-stu-id="f6cca-120">Element</span></span>|<span data-ttu-id="f6cca-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f6cca-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6cca-122">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f6cca-122">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f6cca-123">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6cca-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6cca-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6cca-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f6cca-125">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f6cca-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f6cca-126">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f6cca-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f6cca-127">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f6cca-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f6cca-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f6cca-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
