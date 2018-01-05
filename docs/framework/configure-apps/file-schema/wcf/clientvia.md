---
title: '&lt;clientVia&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a1870a8c331aae16ab14da62c64d6fb15ecd3bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="ba6f2-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="ba6f2-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="ba6f2-103">Określa identyfikator URI, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="ba6f2-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="ba6f2-104">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ba6f2-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="ba6f2-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ba6f2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba6f2-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ba6f2-106">\<behaviors></span></span>  
<span data-ttu-id="ba6f2-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ba6f2-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="ba6f2-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ba6f2-108">\<behavior></span></span>  
<span data-ttu-id="ba6f2-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="ba6f2-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba6f2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba6f2-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba6f2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ba6f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ba6f2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ba6f2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba6f2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ba6f2-113">Attributes</span></span>  
  
|<span data-ttu-id="ba6f2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ba6f2-114">Attribute</span></span>|<span data-ttu-id="ba6f2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ba6f2-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="ba6f2-116">Ciąg określający identyfikator URI wskazujący trasę wyznaczoną dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ba6f2-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba6f2-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ba6f2-117">Child Elements</span></span>  
 <span data-ttu-id="ba6f2-118">Brak</span><span class="sxs-lookup"><span data-stu-id="ba6f2-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba6f2-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ba6f2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ba6f2-120">Element</span><span class="sxs-lookup"><span data-stu-id="ba6f2-120">Element</span></span>|<span data-ttu-id="ba6f2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ba6f2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba6f2-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ba6f2-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ba6f2-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ba6f2-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba6f2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba6f2-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
