---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 48e56b79f47e84122ddd4d7f55d50044510bfa66
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149062"
---
# <a name="ltclientviagt"></a><span data-ttu-id="85b78-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="85b78-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="85b78-103">Określa identyfikator URI, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="85b78-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="85b78-104">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="85b78-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="85b78-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="85b78-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="85b78-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="85b78-106">\<behaviors></span></span>  
<span data-ttu-id="85b78-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="85b78-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="85b78-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="85b78-108">\<behavior></span></span>  
<span data-ttu-id="85b78-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="85b78-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85b78-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="85b78-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85b78-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="85b78-111">Attributes and Elements</span></span>  
 <span data-ttu-id="85b78-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="85b78-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85b78-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="85b78-113">Attributes</span></span>  
  
|<span data-ttu-id="85b78-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="85b78-114">Attribute</span></span>|<span data-ttu-id="85b78-115">Opis</span><span class="sxs-lookup"><span data-stu-id="85b78-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="85b78-116">Ciąg, który określa identyfikator URI wskazujący trasę wyznaczoną dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="85b78-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85b78-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="85b78-117">Child Elements</span></span>  
 <span data-ttu-id="85b78-118">Brak</span><span class="sxs-lookup"><span data-stu-id="85b78-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85b78-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="85b78-119">Parent Elements</span></span>  
  
|<span data-ttu-id="85b78-120">Element</span><span class="sxs-lookup"><span data-stu-id="85b78-120">Element</span></span>|<span data-ttu-id="85b78-121">Opis</span><span class="sxs-lookup"><span data-stu-id="85b78-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85b78-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="85b78-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="85b78-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="85b78-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85b78-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85b78-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
