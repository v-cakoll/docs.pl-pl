---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: ba65d3858cdbdf6b49c50e60f4e3cc9624fef136
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254408"
---
# <a name="filtertable"></a><span data-ttu-id="d57d9-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="d57d9-101">\<filterTable></span></span>
<span data-ttu-id="d57d9-102">Reprezentuje tabelę routingu, który zawiera listę filtrów do oszacowania wiadomości i punktu końcowego klienta do wyznaczania tras, jeśli filtr zwróci wartość true.</span><span class="sxs-lookup"><span data-stu-id="d57d9-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="d57d9-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d57d9-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d57d9-104">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="d57d9-104">\<routing></span></span>  
<span data-ttu-id="d57d9-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="d57d9-105">\<routingTables></span></span>  
<span data-ttu-id="d57d9-106">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="d57d9-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d57d9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d57d9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d57d9-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d57d9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d57d9-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d57d9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d57d9-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d57d9-110">Attributes</span></span>  
  
|<span data-ttu-id="d57d9-111">Element</span><span class="sxs-lookup"><span data-stu-id="d57d9-111">Element</span></span>|<span data-ttu-id="d57d9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d57d9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d57d9-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="d57d9-113">name</span></span>|<span data-ttu-id="d57d9-114">Ciąg, który zawiera unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d57d9-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d57d9-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d57d9-115">Child Elements</span></span>  
  
|<span data-ttu-id="d57d9-116">Element</span><span class="sxs-lookup"><span data-stu-id="d57d9-116">Element</span></span>|<span data-ttu-id="d57d9-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d57d9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d57d9-118">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="d57d9-118">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="d57d9-119">Mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="d57d9-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d57d9-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d57d9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d57d9-121">Element</span><span class="sxs-lookup"><span data-stu-id="d57d9-121">Element</span></span>|<span data-ttu-id="d57d9-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d57d9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d57d9-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="d57d9-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d57d9-124">Sekcja konfiguracji, który zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="d57d9-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d57d9-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d57d9-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
