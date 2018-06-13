---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 7bdc76ba7a8e2927b93fa0207f48cc569279482f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747414"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="5fd0e-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="5fd0e-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="5fd0e-103">Reprezentuje tabelę routingu zawierającą listę filtrów do oszacowania wiadomości i punktu końcowego klienta do wyznaczania tras wiadomościom, jeśli filtr zwróci wartość true.</span><span class="sxs-lookup"><span data-stu-id="5fd0e-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="5fd0e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5fd0e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5fd0e-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="5fd0e-105">\<routing></span></span>  
<span data-ttu-id="5fd0e-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="5fd0e-106">\<routingTables></span></span>  
<span data-ttu-id="5fd0e-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="5fd0e-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fd0e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fd0e-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5fd0e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5fd0e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5fd0e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5fd0e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fd0e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5fd0e-111">Attributes</span></span>  
  
|<span data-ttu-id="5fd0e-112">Element</span><span class="sxs-lookup"><span data-stu-id="5fd0e-112">Element</span></span>|<span data-ttu-id="5fd0e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5fd0e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5fd0e-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="5fd0e-114">name</span></span>|<span data-ttu-id="5fd0e-115">Ciąg zawierający unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5fd0e-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fd0e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5fd0e-116">Child Elements</span></span>  
  
|<span data-ttu-id="5fd0e-117">Element</span><span class="sxs-lookup"><span data-stu-id="5fd0e-117">Element</span></span>|<span data-ttu-id="5fd0e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5fd0e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fd0e-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="5fd0e-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="5fd0e-120">Mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="5fd0e-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5fd0e-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5fd0e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5fd0e-122">Element</span><span class="sxs-lookup"><span data-stu-id="5fd0e-122">Element</span></span>|<span data-ttu-id="5fd0e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="5fd0e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fd0e-124">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="5fd0e-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="5fd0e-125">Sekcja konfiguracyjna, który zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="5fd0e-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fd0e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fd0e-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
