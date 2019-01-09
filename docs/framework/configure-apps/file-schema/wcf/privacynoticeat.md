---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 104b2b6399ea31273045e43be716947db110715d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147320"
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="c9b31-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="c9b31-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="c9b31-103">Reprezentuje element konfiguracji, który określa zachowania poufności, używane w `wsFederationHttp` powiązania.</span><span class="sxs-lookup"><span data-stu-id="c9b31-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="c9b31-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c9b31-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c9b31-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c9b31-105">\<bindings></span></span>  
<span data-ttu-id="c9b31-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c9b31-106">\<customBinding></span></span>  
<span data-ttu-id="c9b31-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c9b31-107">\<binding></span></span>  
<span data-ttu-id="c9b31-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="c9b31-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b31-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9b31-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="c9b31-110">Typ</span><span class="sxs-lookup"><span data-stu-id="c9b31-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9b31-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c9b31-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c9b31-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c9b31-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9b31-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c9b31-113">Attributes</span></span>  
  
|<span data-ttu-id="c9b31-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c9b31-114">Attribute</span></span>|<span data-ttu-id="c9b31-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c9b31-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="c9b31-116">Ciąg określający URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="c9b31-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="c9b31-117">Liczba całkowita określająca wersję tego zawiadomienia o prywatności.</span><span class="sxs-lookup"><span data-stu-id="c9b31-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9b31-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c9b31-118">Child Elements</span></span>  
 <span data-ttu-id="c9b31-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="c9b31-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9b31-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c9b31-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c9b31-121">Element</span><span class="sxs-lookup"><span data-stu-id="c9b31-121">Element</span></span>|<span data-ttu-id="c9b31-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c9b31-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9b31-123">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c9b31-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c9b31-124">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c9b31-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9b31-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9b31-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c9b31-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c9b31-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c9b31-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c9b31-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c9b31-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c9b31-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c9b31-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c9b31-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
