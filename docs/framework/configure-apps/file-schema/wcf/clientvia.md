---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398113"
---
# <a name="clientvia"></a><span data-ttu-id="fd8df-101">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="fd8df-101">\<clientVia></span></span>
<span data-ttu-id="fd8df-102">Określa identyfikator URI, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="fd8df-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="fd8df-103">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fd8df-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
<span data-ttu-id="fd8df-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd8df-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fd8df-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fd8df-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fd8df-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd8df-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fd8df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd8df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="fd8df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd8df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="fd8df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientVia >**</span><span class="sxs-lookup"><span data-stu-id="fd8df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8df-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd8df-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd8df-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd8df-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fd8df-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fd8df-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd8df-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd8df-113">Attributes</span></span>  
  
|<span data-ttu-id="fd8df-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd8df-114">Attribute</span></span>|<span data-ttu-id="fd8df-115">Opis</span><span class="sxs-lookup"><span data-stu-id="fd8df-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="fd8df-116">Ciąg określający identyfikator URI, który wskazuje trasę, którą powinien wykonać komunikat.</span><span class="sxs-lookup"><span data-stu-id="fd8df-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd8df-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd8df-117">Child Elements</span></span>  
 <span data-ttu-id="fd8df-118">Brak</span><span class="sxs-lookup"><span data-stu-id="fd8df-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd8df-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd8df-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fd8df-120">Element</span><span class="sxs-lookup"><span data-stu-id="fd8df-120">Element</span></span>|<span data-ttu-id="fd8df-121">Opis</span><span class="sxs-lookup"><span data-stu-id="fd8df-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd8df-122">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="fd8df-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fd8df-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fd8df-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd8df-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd8df-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
