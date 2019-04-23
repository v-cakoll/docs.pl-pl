---
title: <add> dla <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: fbcb3a07bf40c96a4cd1b2ec87277b6fefdfb89d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164479"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="0d6b1-102">\<Dodaj > z \<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="0d6b1-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="0d6b1-103">Reprezentuje element konfiguracji określający adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="0d6b1-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="0d6b1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0d6b1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0d6b1-105">\<client></span><span class="sxs-lookup"><span data-stu-id="0d6b1-105">\<client></span></span>  
<span data-ttu-id="0d6b1-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="0d6b1-106">\<endpoint></span></span>  
<span data-ttu-id="0d6b1-107">\<host></span><span class="sxs-lookup"><span data-stu-id="0d6b1-107">\<host></span></span>  
<span data-ttu-id="0d6b1-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="0d6b1-108">\<baseAddresses></span></span>  
<span data-ttu-id="0d6b1-109">\<baseAddress></span><span class="sxs-lookup"><span data-stu-id="0d6b1-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d6b1-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d6b1-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="0d6b1-111">Typ</span><span class="sxs-lookup"><span data-stu-id="0d6b1-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d6b1-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0d6b1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0d6b1-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0d6b1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d6b1-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0d6b1-114">Attributes</span></span>  
  
|<span data-ttu-id="0d6b1-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0d6b1-115">Attribute</span></span>|<span data-ttu-id="0d6b1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0d6b1-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="0d6b1-117">Ciąg, który określa adres bazowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="0d6b1-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d6b1-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0d6b1-118">Child Elements</span></span>  
 <span data-ttu-id="0d6b1-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="0d6b1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d6b1-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0d6b1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0d6b1-121">Element</span><span class="sxs-lookup"><span data-stu-id="0d6b1-121">Element</span></span>|<span data-ttu-id="0d6b1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0d6b1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d6b1-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="0d6b1-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="0d6b1-124">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="0d6b1-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d6b1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d6b1-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="0d6b1-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="0d6b1-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
