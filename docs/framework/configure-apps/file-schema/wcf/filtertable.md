---
title: '&lt;filterTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cf87cc74c7bb5d495584407c803dacc7b94f195
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="54433-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="54433-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="54433-103">Reprezentuje tabelę routingu zawierającą listę filtrów do oszacowania wiadomości i punktu końcowego klienta do wyznaczania tras wiadomościom, jeśli filtr zwróci wartość true.</span><span class="sxs-lookup"><span data-stu-id="54433-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="54433-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="54433-104">\<system.serviceModel></span></span>  
<span data-ttu-id="54433-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="54433-105">\<routing></span></span>  
<span data-ttu-id="54433-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="54433-106">\<routingTables></span></span>  
<span data-ttu-id="54433-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="54433-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54433-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="54433-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54433-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="54433-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54433-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="54433-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54433-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="54433-111">Attributes</span></span>  
  
|<span data-ttu-id="54433-112">Element</span><span class="sxs-lookup"><span data-stu-id="54433-112">Element</span></span>|<span data-ttu-id="54433-113">Opis</span><span class="sxs-lookup"><span data-stu-id="54433-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54433-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="54433-114">name</span></span>|<span data-ttu-id="54433-115">Ciąg zawierający unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="54433-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54433-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="54433-116">Child Elements</span></span>  
  
|<span data-ttu-id="54433-117">Element</span><span class="sxs-lookup"><span data-stu-id="54433-117">Element</span></span>|<span data-ttu-id="54433-118">Opis</span><span class="sxs-lookup"><span data-stu-id="54433-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54433-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="54433-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="54433-120">Mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="54433-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54433-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="54433-121">Parent Elements</span></span>  
  
|<span data-ttu-id="54433-122">Element</span><span class="sxs-lookup"><span data-stu-id="54433-122">Element</span></span>|<span data-ttu-id="54433-123">Opis</span><span class="sxs-lookup"><span data-stu-id="54433-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54433-124">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="54433-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="54433-125">Sekcja konfiguracyjna, który zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="54433-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54433-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54433-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
