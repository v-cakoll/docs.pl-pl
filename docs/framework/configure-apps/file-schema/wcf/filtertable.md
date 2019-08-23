---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f9e64e667befb70d617574b2a03c3e6bebb2a143
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925601"
---
# <a name="filtertable"></a><span data-ttu-id="2bdb3-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="2bdb3-101">\<filterTable></span></span>
<span data-ttu-id="2bdb3-102">Reprezentuje tabelę routingu zawierającą listę filtrów służących do szacowania komunikatów oraz punkt końcowy klienta, do którego mają być kierowane komunikaty, jeśli filtr ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="2bdb3-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="2bdb3-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2bdb3-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2bdb3-104">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="2bdb3-104">\<routing></span></span>  
<span data-ttu-id="2bdb3-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="2bdb3-105">\<routingTables></span></span>  
<span data-ttu-id="2bdb3-106">\<> tabeli</span><span class="sxs-lookup"><span data-stu-id="2bdb3-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bdb3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bdb3-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bdb3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2bdb3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2bdb3-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2bdb3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bdb3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2bdb3-110">Attributes</span></span>  
  
|<span data-ttu-id="2bdb3-111">Element</span><span class="sxs-lookup"><span data-stu-id="2bdb3-111">Element</span></span>|<span data-ttu-id="2bdb3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2bdb3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2bdb3-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="2bdb3-113">name</span></span>|<span data-ttu-id="2bdb3-114">Ciąg zawierający unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2bdb3-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bdb3-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2bdb3-115">Child Elements</span></span>  
  
|<span data-ttu-id="2bdb3-116">Element</span><span class="sxs-lookup"><span data-stu-id="2bdb3-116">Element</span></span>|<span data-ttu-id="2bdb3-117">Opis</span><span class="sxs-lookup"><span data-stu-id="2bdb3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bdb3-118">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="2bdb3-118">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="2bdb3-119">Mapowania między filtrami routingu i docelowymi punktami końcowymi do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="2bdb3-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bdb3-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2bdb3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2bdb3-121">Element</span><span class="sxs-lookup"><span data-stu-id="2bdb3-121">Element</span></span>|<span data-ttu-id="2bdb3-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2bdb3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bdb3-123">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="2bdb3-123">\<routing></span></span>](routing.md)|<span data-ttu-id="2bdb3-124">Sekcja konfiguracji, która zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="2bdb3-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bdb3-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bdb3-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
