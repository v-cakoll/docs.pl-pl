---
title: '&lt;privacyNoticeAt&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30b3f0bdd1aa02473470c354a730bcfa450f0264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="5200a-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="5200a-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="5200a-103">Reprezentuje element konfiguracji, który określa powiadomienie o prywatności użyte w `wsFederationHttp` powiązania.</span><span class="sxs-lookup"><span data-stu-id="5200a-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="5200a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5200a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5200a-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5200a-105">\<bindings></span></span>  
<span data-ttu-id="5200a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5200a-106">\<customBinding></span></span>  
<span data-ttu-id="5200a-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5200a-107">\<binding></span></span>  
<span data-ttu-id="5200a-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="5200a-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5200a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5200a-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="5200a-110">Typ</span><span class="sxs-lookup"><span data-stu-id="5200a-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5200a-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5200a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5200a-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5200a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5200a-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5200a-113">Attributes</span></span>  
  
|<span data-ttu-id="5200a-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5200a-114">Attribute</span></span>|<span data-ttu-id="5200a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5200a-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="5200a-116">Ciąg określający URI, w której znajduje się zasadach zachowania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="5200a-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="5200a-117">Liczba całkowita określająca wersję tego zawiadomienia o prywatności.</span><span class="sxs-lookup"><span data-stu-id="5200a-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5200a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5200a-118">Child Elements</span></span>  
 <span data-ttu-id="5200a-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="5200a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5200a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5200a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5200a-121">Element</span><span class="sxs-lookup"><span data-stu-id="5200a-121">Element</span></span>|<span data-ttu-id="5200a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5200a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5200a-123">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5200a-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5200a-124">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5200a-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5200a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5200a-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="5200a-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5200a-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5200a-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="5200a-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="5200a-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="5200a-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="5200a-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5200a-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
