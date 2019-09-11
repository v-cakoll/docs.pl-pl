---
title: <add> dla <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850582"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="06ebe-102">\<Dodawanie > \<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="06ebe-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="06ebe-103">Reprezentuje element konfiguracji, który określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="06ebe-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
<span data-ttu-id="06ebe-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06ebe-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06ebe-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="06ebe-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="06ebe-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usług**](services.md)</span><span class="sxs-lookup"><span data-stu-id="06ebe-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="06ebe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usługi**](service.md)</span><span class="sxs-lookup"><span data-stu-id="06ebe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="06ebe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hosta**](host.md)</span><span class="sxs-lookup"><span data-stu-id="06ebe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="06ebe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<baseAddresses >** ](baseaddresses.md)</span><span class="sxs-lookup"><span data-stu-id="06ebe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)</span></span>\
<span data-ttu-id="06ebe-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="06ebe-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06ebe-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="06ebe-111">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="06ebe-112">Typ</span><span class="sxs-lookup"><span data-stu-id="06ebe-112">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06ebe-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06ebe-113">Attributes and Elements</span></span>  
 <span data-ttu-id="06ebe-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="06ebe-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06ebe-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06ebe-115">Attributes</span></span>  
  
|<span data-ttu-id="06ebe-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="06ebe-116">Attribute</span></span>|<span data-ttu-id="06ebe-117">Opis</span><span class="sxs-lookup"><span data-stu-id="06ebe-117">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="06ebe-118">Ciąg określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="06ebe-118">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06ebe-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06ebe-119">Child Elements</span></span>  
 <span data-ttu-id="06ebe-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="06ebe-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06ebe-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06ebe-121">Parent Elements</span></span>  
  
|<span data-ttu-id="06ebe-122">Element</span><span class="sxs-lookup"><span data-stu-id="06ebe-122">Element</span></span>|<span data-ttu-id="06ebe-123">Opis</span><span class="sxs-lookup"><span data-stu-id="06ebe-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06ebe-124">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="06ebe-124">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="06ebe-125">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="06ebe-125">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06ebe-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06ebe-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="06ebe-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="06ebe-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
