---
title: <add> z <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: fbcb3a07bf40c96a4cd1b2ec87277b6fefdfb89d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164479"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="8faea-102">\<Dodaj > z \<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="8faea-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="8faea-103">Reprezentuje element konfiguracji określający adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="8faea-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="8faea-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8faea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8faea-105">\<client></span><span class="sxs-lookup"><span data-stu-id="8faea-105">\<client></span></span>  
<span data-ttu-id="8faea-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="8faea-106">\<endpoint></span></span>  
<span data-ttu-id="8faea-107">\<host></span><span class="sxs-lookup"><span data-stu-id="8faea-107">\<host></span></span>  
<span data-ttu-id="8faea-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="8faea-108">\<baseAddresses></span></span>  
<span data-ttu-id="8faea-109">\<baseAddress></span><span class="sxs-lookup"><span data-stu-id="8faea-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8faea-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8faea-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="8faea-111">Typ</span><span class="sxs-lookup"><span data-stu-id="8faea-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8faea-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8faea-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8faea-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8faea-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8faea-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8faea-114">Attributes</span></span>  
  
|<span data-ttu-id="8faea-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8faea-115">Attribute</span></span>|<span data-ttu-id="8faea-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8faea-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="8faea-117">Ciąg, który określa adres bazowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="8faea-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8faea-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8faea-118">Child Elements</span></span>  
 <span data-ttu-id="8faea-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="8faea-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8faea-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8faea-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8faea-121">Element</span><span class="sxs-lookup"><span data-stu-id="8faea-121">Element</span></span>|<span data-ttu-id="8faea-122">Opis</span><span class="sxs-lookup"><span data-stu-id="8faea-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8faea-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="8faea-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="8faea-124">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="8faea-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8faea-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8faea-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="8faea-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="8faea-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
