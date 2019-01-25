---
title: '&lt;timeOuts&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 42f4db1d954834cbfa3c526328cca45443751506
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629661"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="b0625-102">&lt;timeOuts&gt;</span><span class="sxs-lookup"><span data-stu-id="b0625-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="b0625-103">Reprezentuje element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.</span><span class="sxs-lookup"><span data-stu-id="b0625-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="b0625-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b0625-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b0625-105">\<client></span><span class="sxs-lookup"><span data-stu-id="b0625-105">\<client></span></span>  
<span data-ttu-id="b0625-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="b0625-106">\<endpoint></span></span>  
<span data-ttu-id="b0625-107">\<host></span><span class="sxs-lookup"><span data-stu-id="b0625-107">\<host></span></span>  
<span data-ttu-id="b0625-108">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="b0625-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0625-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0625-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0625-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b0625-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b0625-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b0625-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0625-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b0625-112">Attributes</span></span>  
  
|<span data-ttu-id="b0625-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b0625-113">Attribute</span></span>|<span data-ttu-id="b0625-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b0625-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="b0625-115">A <xref:System.TimeSpan> wartość, która określa przedział czasu dozwolony na zamknięcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="b0625-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="b0625-116">A <xref:System.TimeSpan> wartość, która określa okres czasu dozwolony dla otwarcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="b0625-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0625-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b0625-117">Child Elements</span></span>  
 <span data-ttu-id="b0625-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="b0625-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0625-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b0625-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b0625-120">Element</span><span class="sxs-lookup"><span data-stu-id="b0625-120">Element</span></span>|<span data-ttu-id="b0625-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b0625-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0625-122">\<host></span><span class="sxs-lookup"><span data-stu-id="b0625-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="b0625-123">Element konfiguracji, który określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="b0625-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0625-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0625-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="b0625-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="b0625-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
