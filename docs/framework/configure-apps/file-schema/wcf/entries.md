---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855277"
---
# <a name="entries"></a><span data-ttu-id="7a830-101">\<> wpisów</span><span class="sxs-lookup"><span data-stu-id="7a830-101">\<entries></span></span>
<span data-ttu-id="7a830-102">Wpis routingu zawierający mapowania między filtrami routingu i docelowymi punktami końcowymi, do których mają być wysyłane komunikaty, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="7a830-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="7a830-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a830-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a830-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7a830-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7a830-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="7a830-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="7a830-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="7a830-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="7a830-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtrowania**](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="7a830-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="7a830-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> wpisów**</span><span class="sxs-lookup"><span data-stu-id="7a830-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a830-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a830-109">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a830-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a830-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7a830-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a830-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a830-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a830-112">Attributes</span></span>  
 <span data-ttu-id="7a830-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="7a830-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7a830-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a830-114">Child Elements</span></span>  
  
|<span data-ttu-id="7a830-115">Element</span><span class="sxs-lookup"><span data-stu-id="7a830-115">Element</span></span>|<span data-ttu-id="7a830-116">Opis</span><span class="sxs-lookup"><span data-stu-id="7a830-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a830-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="7a830-117">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="7a830-118">Mapuje filtr do punktu końcowego klienta, który został wcześniej zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="7a830-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="7a830-119">Komunikaty pasujące do tego filtru zostaną wysłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="7a830-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a830-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a830-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7a830-121">Element</span><span class="sxs-lookup"><span data-stu-id="7a830-121">Element</span></span>|<span data-ttu-id="7a830-122">Opis</span><span class="sxs-lookup"><span data-stu-id="7a830-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a830-123">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="7a830-123">\<routing></span></span>](routing.md)|<span data-ttu-id="7a830-124">Sekcja konfiguracji, która zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="7a830-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a830-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a830-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
