---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 4e5c7d56e35afe3001f4c70064adbfef7702c720
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229280"
---
# <a name="filtertable"></a><span data-ttu-id="7ba5f-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="7ba5f-101">\<filterTable></span></span>
<span data-ttu-id="7ba5f-102">Reprezentuje tabelę routingu, który zawiera listę filtrów do oszacowania wiadomości i punktu końcowego klienta do wyznaczania tras, jeśli filtr zwróci wartość true.</span><span class="sxs-lookup"><span data-stu-id="7ba5f-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="7ba5f-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7ba5f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7ba5f-104">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="7ba5f-104">\<routing></span></span>  
<span data-ttu-id="7ba5f-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="7ba5f-105">\<routingTables></span></span>  
<span data-ttu-id="7ba5f-106">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="7ba5f-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ba5f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ba5f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ba5f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7ba5f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7ba5f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7ba5f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ba5f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7ba5f-110">Attributes</span></span>  
  
|<span data-ttu-id="7ba5f-111">Element</span><span class="sxs-lookup"><span data-stu-id="7ba5f-111">Element</span></span>|<span data-ttu-id="7ba5f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7ba5f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ba5f-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="7ba5f-113">name</span></span>|<span data-ttu-id="7ba5f-114">Ciąg, który zawiera unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7ba5f-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ba5f-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7ba5f-115">Child Elements</span></span>  
  
|<span data-ttu-id="7ba5f-116">Element</span><span class="sxs-lookup"><span data-stu-id="7ba5f-116">Element</span></span>|<span data-ttu-id="7ba5f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7ba5f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ba5f-118">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="7ba5f-118">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="7ba5f-119">Mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="7ba5f-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ba5f-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7ba5f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7ba5f-121">Element</span><span class="sxs-lookup"><span data-stu-id="7ba5f-121">Element</span></span>|<span data-ttu-id="7ba5f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="7ba5f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ba5f-123">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="7ba5f-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7ba5f-124">Sekcja konfiguracji, który zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="7ba5f-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ba5f-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ba5f-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
