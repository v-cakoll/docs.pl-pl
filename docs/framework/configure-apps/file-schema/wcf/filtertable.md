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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04780d51cfd1d1d0049fc608cf7bd304be382b9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="01888-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="01888-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="01888-103">Reprezentuje tabelę routingu zawierającą listę filtrów do oszacowania wiadomości i punktu końcowego klienta do wyznaczania tras wiadomościom, jeśli filtr zwróci wartość true.</span><span class="sxs-lookup"><span data-stu-id="01888-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="01888-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="01888-104">\<system.serviceModel></span></span>  
<span data-ttu-id="01888-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="01888-105">\<routing></span></span>  
<span data-ttu-id="01888-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="01888-106">\<routingTables></span></span>  
<span data-ttu-id="01888-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="01888-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01888-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="01888-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01888-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="01888-109">Attributes and Elements</span></span>  
 <span data-ttu-id="01888-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="01888-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01888-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="01888-111">Attributes</span></span>  
  
|<span data-ttu-id="01888-112">Element</span><span class="sxs-lookup"><span data-stu-id="01888-112">Element</span></span>|<span data-ttu-id="01888-113">Opis</span><span class="sxs-lookup"><span data-stu-id="01888-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01888-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="01888-114">name</span></span>|<span data-ttu-id="01888-115">Ciąg zawierający unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="01888-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01888-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="01888-116">Child Elements</span></span>  
  
|<span data-ttu-id="01888-117">Element</span><span class="sxs-lookup"><span data-stu-id="01888-117">Element</span></span>|<span data-ttu-id="01888-118">Opis</span><span class="sxs-lookup"><span data-stu-id="01888-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01888-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="01888-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="01888-120">Mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="01888-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01888-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="01888-121">Parent Elements</span></span>  
  
|<span data-ttu-id="01888-122">Element</span><span class="sxs-lookup"><span data-stu-id="01888-122">Element</span></span>|<span data-ttu-id="01888-123">Opis</span><span class="sxs-lookup"><span data-stu-id="01888-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01888-124">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="01888-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="01888-125">Sekcja konfiguracyjna, który zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="01888-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01888-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01888-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
