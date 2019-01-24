---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 83339eebef9a4f1b7f69e0bd1dd16b8278a68258
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534608"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="eab8d-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="eab8d-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="eab8d-103">Reprezentuje tabelę routingu, który zawiera listę filtrów do oszacowania wiadomości i punktu końcowego klienta do wyznaczania tras, jeśli filtr zwróci wartość true.</span><span class="sxs-lookup"><span data-stu-id="eab8d-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="eab8d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eab8d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="eab8d-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="eab8d-105">\<routing></span></span>  
<span data-ttu-id="eab8d-106">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="eab8d-106">\<routingTables></span></span>  
<span data-ttu-id="eab8d-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="eab8d-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab8d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="eab8d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eab8d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eab8d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eab8d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eab8d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eab8d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eab8d-111">Attributes</span></span>  
  
|<span data-ttu-id="eab8d-112">Element</span><span class="sxs-lookup"><span data-stu-id="eab8d-112">Element</span></span>|<span data-ttu-id="eab8d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="eab8d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eab8d-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="eab8d-114">name</span></span>|<span data-ttu-id="eab8d-115">Ciąg, który zawiera unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="eab8d-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eab8d-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eab8d-116">Child Elements</span></span>  
  
|<span data-ttu-id="eab8d-117">Element</span><span class="sxs-lookup"><span data-stu-id="eab8d-117">Element</span></span>|<span data-ttu-id="eab8d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="eab8d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eab8d-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="eab8d-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="eab8d-120">Mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="eab8d-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eab8d-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eab8d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eab8d-122">Element</span><span class="sxs-lookup"><span data-stu-id="eab8d-122">Element</span></span>|<span data-ttu-id="eab8d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="eab8d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eab8d-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="eab8d-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="eab8d-125">Sekcja konfiguracji, który zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="eab8d-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eab8d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eab8d-126">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
