---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 6218bb3f205f2825eb3f10fabf834cfd0396ac87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754135"
---
# <a name="ltclientviagt"></a><span data-ttu-id="696d7-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="696d7-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="696d7-103">Określa identyfikator URI, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="696d7-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="696d7-104">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="696d7-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="696d7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="696d7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="696d7-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="696d7-106">\<behaviors></span></span>  
<span data-ttu-id="696d7-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="696d7-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="696d7-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="696d7-108">\<behavior></span></span>  
<span data-ttu-id="696d7-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="696d7-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696d7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="696d7-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="696d7-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="696d7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="696d7-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="696d7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="696d7-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="696d7-113">Attributes</span></span>  
  
|<span data-ttu-id="696d7-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="696d7-114">Attribute</span></span>|<span data-ttu-id="696d7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="696d7-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="696d7-116">Ciąg określający identyfikator URI wskazujący trasę wyznaczoną dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="696d7-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="696d7-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="696d7-117">Child Elements</span></span>  
 <span data-ttu-id="696d7-118">Brak</span><span class="sxs-lookup"><span data-stu-id="696d7-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="696d7-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="696d7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="696d7-120">Element</span><span class="sxs-lookup"><span data-stu-id="696d7-120">Element</span></span>|<span data-ttu-id="696d7-121">Opis</span><span class="sxs-lookup"><span data-stu-id="696d7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="696d7-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="696d7-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="696d7-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="696d7-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="696d7-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="696d7-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
