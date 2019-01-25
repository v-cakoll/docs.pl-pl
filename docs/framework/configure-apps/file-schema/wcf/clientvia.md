---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 6491411d8cfe5c7a5a944f3b1cd728c9f0a4b852
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641216"
---
# <a name="ltclientviagt"></a><span data-ttu-id="ad747-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="ad747-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="ad747-103">Określa identyfikator URI, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="ad747-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="ad747-104">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ad747-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="ad747-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ad747-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad747-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ad747-106">\<behaviors></span></span>  
<span data-ttu-id="ad747-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ad747-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="ad747-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ad747-108">\<behavior></span></span>  
<span data-ttu-id="ad747-109">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="ad747-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad747-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad747-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad747-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ad747-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ad747-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ad747-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad747-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ad747-113">Attributes</span></span>  
  
|<span data-ttu-id="ad747-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ad747-114">Attribute</span></span>|<span data-ttu-id="ad747-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ad747-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="ad747-116">Ciąg, który określa identyfikator URI wskazujący trasę wyznaczoną dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ad747-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad747-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ad747-117">Child Elements</span></span>  
 <span data-ttu-id="ad747-118">Brak</span><span class="sxs-lookup"><span data-stu-id="ad747-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad747-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ad747-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ad747-120">Element</span><span class="sxs-lookup"><span data-stu-id="ad747-120">Element</span></span>|<span data-ttu-id="ad747-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ad747-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad747-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ad747-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ad747-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ad747-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad747-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad747-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
