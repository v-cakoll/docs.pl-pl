---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b159488efa2a80a9dea625e4c6dfe2f215dfc457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939186"
---
# <a name="timeouts"></a><span data-ttu-id="bacf3-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="bacf3-101">\<timeOuts></span></span>
<span data-ttu-id="bacf3-102">Reprezentuje element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="bacf3-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="bacf3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bacf3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bacf3-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="bacf3-104">\<client></span></span>  
<span data-ttu-id="bacf3-105">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="bacf3-105">\<endpoint></span></span>  
<span data-ttu-id="bacf3-106">\<host></span><span class="sxs-lookup"><span data-stu-id="bacf3-106">\<host></span></span>  
<span data-ttu-id="bacf3-107">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="bacf3-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bacf3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="bacf3-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bacf3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bacf3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bacf3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bacf3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bacf3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bacf3-111">Attributes</span></span>  
  
|<span data-ttu-id="bacf3-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bacf3-112">Attribute</span></span>|<span data-ttu-id="bacf3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bacf3-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bacf3-114"><xref:System.TimeSpan> Wartość, która określa przedział czasu, jaki może być zamknięty dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="bacf3-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="bacf3-115"><xref:System.TimeSpan> Wartość, która określa przedział czasu, jaki może otworzyć Host usługi.</span><span class="sxs-lookup"><span data-stu-id="bacf3-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bacf3-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bacf3-116">Child Elements</span></span>  
 <span data-ttu-id="bacf3-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="bacf3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bacf3-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bacf3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bacf3-119">Element</span><span class="sxs-lookup"><span data-stu-id="bacf3-119">Element</span></span>|<span data-ttu-id="bacf3-120">Opis</span><span class="sxs-lookup"><span data-stu-id="bacf3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bacf3-121">\<host></span><span class="sxs-lookup"><span data-stu-id="bacf3-121">\<host></span></span>](host.md)|<span data-ttu-id="bacf3-122">Element konfiguracji, który określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="bacf3-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bacf3-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bacf3-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="bacf3-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="bacf3-124">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
