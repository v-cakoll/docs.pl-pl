---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f790e294b832f43a595d0636c60a8a67da5ad56a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147892"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="9c030-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="9c030-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="9c030-103">Reprezentuje tabelę routingu, który zawiera listę filtrów do oszacowania wiadomości i punktu końcowego klienta do wyznaczania tras, jeśli filtr zwróci wartość true.</span><span class="sxs-lookup"><span data-stu-id="9c030-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="9c030-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9c030-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9c030-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="9c030-105">\<routing></span></span>  
<span data-ttu-id="9c030-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="9c030-106">\<routingTables></span></span>  
<span data-ttu-id="9c030-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="9c030-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c030-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c030-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c030-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c030-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9c030-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9c030-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c030-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c030-111">Attributes</span></span>  
  
|<span data-ttu-id="9c030-112">Element</span><span class="sxs-lookup"><span data-stu-id="9c030-112">Element</span></span>|<span data-ttu-id="9c030-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9c030-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c030-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="9c030-114">name</span></span>|<span data-ttu-id="9c030-115">Ciąg, który zawiera unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9c030-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c030-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c030-116">Child Elements</span></span>  
  
|<span data-ttu-id="9c030-117">Element</span><span class="sxs-lookup"><span data-stu-id="9c030-117">Element</span></span>|<span data-ttu-id="9c030-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9c030-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c030-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="9c030-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="9c030-120">Mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="9c030-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c030-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c030-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9c030-122">Element</span><span class="sxs-lookup"><span data-stu-id="9c030-122">Element</span></span>|<span data-ttu-id="9c030-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9c030-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c030-124">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="9c030-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="9c030-125">Sekcja konfiguracji, który zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="9c030-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c030-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c030-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
