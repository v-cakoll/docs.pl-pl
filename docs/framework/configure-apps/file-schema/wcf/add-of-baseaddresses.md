---
title: <add> dla <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: a94c5144d907c26e6f5eef09b1a17b17eb6c9e0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920219"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="3e1aa-102">\<Dodawanie > \<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="3e1aa-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="3e1aa-103">Reprezentuje element konfiguracji, który określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="3e1aa-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="3e1aa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3e1aa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3e1aa-105">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="3e1aa-105">\<client></span></span>  
<span data-ttu-id="3e1aa-106">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="3e1aa-106">\<endpoint></span></span>  
<span data-ttu-id="3e1aa-107">\<host></span><span class="sxs-lookup"><span data-stu-id="3e1aa-107">\<host></span></span>  
<span data-ttu-id="3e1aa-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="3e1aa-108">\<baseAddresses></span></span>  
<span data-ttu-id="3e1aa-109">\<baseAddress></span><span class="sxs-lookup"><span data-stu-id="3e1aa-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1aa-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e1aa-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="3e1aa-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3e1aa-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e1aa-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e1aa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3e1aa-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e1aa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e1aa-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e1aa-114">Attributes</span></span>  
  
|<span data-ttu-id="3e1aa-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3e1aa-115">Attribute</span></span>|<span data-ttu-id="3e1aa-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3e1aa-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="3e1aa-117">Ciąg określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="3e1aa-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e1aa-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e1aa-118">Child Elements</span></span>  
 <span data-ttu-id="3e1aa-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="3e1aa-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e1aa-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e1aa-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3e1aa-121">Element</span><span class="sxs-lookup"><span data-stu-id="3e1aa-121">Element</span></span>|<span data-ttu-id="3e1aa-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3e1aa-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e1aa-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="3e1aa-123">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="3e1aa-124">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="3e1aa-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e1aa-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e1aa-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="3e1aa-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="3e1aa-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
