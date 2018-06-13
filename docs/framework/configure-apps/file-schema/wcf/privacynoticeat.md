---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2914a3716b9e2adb6ebc47fd73ccee027a3b65da
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749247"
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="955f1-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="955f1-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="955f1-103">Reprezentuje element konfiguracji, który określa powiadomienie o prywatności użyte w `wsFederationHttp` powiązania.</span><span class="sxs-lookup"><span data-stu-id="955f1-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="955f1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="955f1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="955f1-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="955f1-105">\<bindings></span></span>  
<span data-ttu-id="955f1-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="955f1-106">\<customBinding></span></span>  
<span data-ttu-id="955f1-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="955f1-107">\<binding></span></span>  
<span data-ttu-id="955f1-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="955f1-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="955f1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="955f1-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="955f1-110">Typ</span><span class="sxs-lookup"><span data-stu-id="955f1-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="955f1-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="955f1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="955f1-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="955f1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="955f1-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="955f1-113">Attributes</span></span>  
  
|<span data-ttu-id="955f1-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="955f1-114">Attribute</span></span>|<span data-ttu-id="955f1-115">Opis</span><span class="sxs-lookup"><span data-stu-id="955f1-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="955f1-116">Ciąg określający URI, w której znajduje się zasadach zachowania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="955f1-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="955f1-117">Liczba całkowita określająca wersję tego zawiadomienia o prywatności.</span><span class="sxs-lookup"><span data-stu-id="955f1-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="955f1-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="955f1-118">Child Elements</span></span>  
 <span data-ttu-id="955f1-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="955f1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="955f1-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="955f1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="955f1-121">Element</span><span class="sxs-lookup"><span data-stu-id="955f1-121">Element</span></span>|<span data-ttu-id="955f1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="955f1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="955f1-123">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="955f1-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="955f1-124">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="955f1-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="955f1-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="955f1-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="955f1-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="955f1-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="955f1-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="955f1-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="955f1-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="955f1-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="955f1-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="955f1-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
