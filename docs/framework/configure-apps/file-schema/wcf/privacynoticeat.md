---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: f7349bf61082c5d8e5bd4249e01b8835a1861cb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934260"
---
# <a name="privacynoticeat"></a><span data-ttu-id="b800d-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="b800d-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="b800d-102">Reprezentuje element konfiguracji, który określa powiadomienie o prywatności użyte w `wsFederationHttp` powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="b800d-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="b800d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b800d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="b800d-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="b800d-104">\<bindings></span></span>  
<span data-ttu-id="b800d-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b800d-105">\<customBinding></span></span>  
<span data-ttu-id="b800d-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b800d-106">\<binding></span></span>  
<span data-ttu-id="b800d-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="b800d-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b800d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b800d-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="b800d-109">Typ</span><span class="sxs-lookup"><span data-stu-id="b800d-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b800d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b800d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b800d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b800d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b800d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b800d-112">Attributes</span></span>  
  
|<span data-ttu-id="b800d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b800d-113">Attribute</span></span>|<span data-ttu-id="b800d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b800d-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="b800d-115">Ciąg określający identyfikator URI, w którym znajduje się powiadomienie o prywatności.</span><span class="sxs-lookup"><span data-stu-id="b800d-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="b800d-116">Liczba całkowita określająca wersję tego powiadomienia o ochronie prywatności.</span><span class="sxs-lookup"><span data-stu-id="b800d-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b800d-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b800d-117">Child Elements</span></span>  
 <span data-ttu-id="b800d-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="b800d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b800d-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b800d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b800d-120">Element</span><span class="sxs-lookup"><span data-stu-id="b800d-120">Element</span></span>|<span data-ttu-id="b800d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b800d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b800d-122">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b800d-122">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b800d-123">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b800d-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b800d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b800d-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b800d-125">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b800d-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b800d-126">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b800d-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b800d-127">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b800d-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b800d-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b800d-128">\<customBinding></span></span>](custombinding.md)
