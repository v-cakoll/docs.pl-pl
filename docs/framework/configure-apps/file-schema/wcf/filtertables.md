---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: d73a3c25dbb4d2de41007149ef5864fcf37ad883
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573062"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="7d3b7-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="7d3b7-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="7d3b7-103">Reprezentuje sekcję konfiguracji określającą tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysłania wiadomości, gdy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="7d3b7-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="7d3b7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7d3b7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7d3b7-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="7d3b7-105">\<routing></span></span>  
<span data-ttu-id="7d3b7-106">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="7d3b7-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d3b7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d3b7-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d3b7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d3b7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7d3b7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d3b7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d3b7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d3b7-110">Attributes</span></span>  
 <span data-ttu-id="7d3b7-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d3b7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d3b7-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d3b7-112">Child Elements</span></span>  
  
|<span data-ttu-id="7d3b7-113">Element</span><span class="sxs-lookup"><span data-stu-id="7d3b7-113">Element</span></span>|<span data-ttu-id="7d3b7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7d3b7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d3b7-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="7d3b7-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="7d3b7-116">Tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="7d3b7-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d3b7-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d3b7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7d3b7-118">Element</span><span class="sxs-lookup"><span data-stu-id="7d3b7-118">Element</span></span>|<span data-ttu-id="7d3b7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7d3b7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d3b7-120">\<routing></span><span class="sxs-lookup"><span data-stu-id="7d3b7-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7d3b7-121">Sekcja konfiguracji, zawierający filtrów routingu i tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="7d3b7-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d3b7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d3b7-122">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
