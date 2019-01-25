---
title: '&lt;add&gt; w &lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: 31edf570a7374a4b4fe31760d35ec196ecfcb3c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553571"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="f46d7-102">&lt;add&gt; w &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="f46d7-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="f46d7-103">Reprezentuje element konfiguracji określający adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="f46d7-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="f46d7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f46d7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f46d7-105">\<client></span><span class="sxs-lookup"><span data-stu-id="f46d7-105">\<client></span></span>  
<span data-ttu-id="f46d7-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="f46d7-106">\<endpoint></span></span>  
<span data-ttu-id="f46d7-107">\<host></span><span class="sxs-lookup"><span data-stu-id="f46d7-107">\<host></span></span>  
<span data-ttu-id="f46d7-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="f46d7-108">\<baseAddresses></span></span>  
<span data-ttu-id="f46d7-109">\<baseAddress></span><span class="sxs-lookup"><span data-stu-id="f46d7-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f46d7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f46d7-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="f46d7-111">Typ</span><span class="sxs-lookup"><span data-stu-id="f46d7-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f46d7-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f46d7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f46d7-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f46d7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f46d7-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f46d7-114">Attributes</span></span>  
  
|<span data-ttu-id="f46d7-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f46d7-115">Attribute</span></span>|<span data-ttu-id="f46d7-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f46d7-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="f46d7-117">Ciąg, który określa adres bazowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="f46d7-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f46d7-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f46d7-118">Child Elements</span></span>  
 <span data-ttu-id="f46d7-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="f46d7-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f46d7-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f46d7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f46d7-121">Element</span><span class="sxs-lookup"><span data-stu-id="f46d7-121">Element</span></span>|<span data-ttu-id="f46d7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f46d7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f46d7-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="f46d7-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="f46d7-124">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="f46d7-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f46d7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f46d7-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="f46d7-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="f46d7-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
