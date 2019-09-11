---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855191"
---
# <a name="filtertable"></a><span data-ttu-id="4b27d-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="4b27d-101">\<filterTable></span></span>
<span data-ttu-id="4b27d-102">Reprezentuje tabelę routingu zawierającą listę filtrów służących do szacowania komunikatów oraz punkt końcowy klienta, do którego mają być kierowane komunikaty, jeśli filtr ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="4b27d-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
<span data-ttu-id="4b27d-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b27d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4b27d-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4b27d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4b27d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="4b27d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="4b27d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="4b27d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="4b27d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> filtrowania**</span><span class="sxs-lookup"><span data-stu-id="4b27d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b27d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b27d-108">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b27d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4b27d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4b27d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4b27d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b27d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b27d-111">Attributes</span></span>  
  
|<span data-ttu-id="4b27d-112">Element</span><span class="sxs-lookup"><span data-stu-id="4b27d-112">Element</span></span>|<span data-ttu-id="4b27d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4b27d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b27d-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="4b27d-114">name</span></span>|<span data-ttu-id="4b27d-115">Ciąg zawierający unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4b27d-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b27d-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4b27d-116">Child Elements</span></span>  
  
|<span data-ttu-id="4b27d-117">Element</span><span class="sxs-lookup"><span data-stu-id="4b27d-117">Element</span></span>|<span data-ttu-id="4b27d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4b27d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b27d-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="4b27d-119">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="4b27d-120">Mapowania między filtrami routingu i docelowymi punktami końcowymi do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="4b27d-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b27d-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4b27d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4b27d-122">Element</span><span class="sxs-lookup"><span data-stu-id="4b27d-122">Element</span></span>|<span data-ttu-id="4b27d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4b27d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b27d-124">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="4b27d-124">\<routing></span></span>](routing.md)|<span data-ttu-id="4b27d-125">Sekcja konfiguracji, która zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="4b27d-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b27d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b27d-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
