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
ms.openlocfilehash: 96425604fab8f70456ea1e0d97efb2c3bf843224
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="7c3f8-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="7c3f8-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="7c3f8-103">Reprezentuje tabelę routingu zawierającą listę filtrów do oszacowania wiadomości i punktu końcowego klienta do wyznaczania tras wiadomościom, jeśli filtr zwróci wartość true.</span><span class="sxs-lookup"><span data-stu-id="7c3f8-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="7c3f8-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7c3f8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7c3f8-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="7c3f8-105">\<routing></span></span>  
<span data-ttu-id="7c3f8-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="7c3f8-106">\<routingTables></span></span>  
<span data-ttu-id="7c3f8-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="7c3f8-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c3f8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c3f8-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c3f8-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7c3f8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7c3f8-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7c3f8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c3f8-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7c3f8-111">Attributes</span></span>  
  
|<span data-ttu-id="7c3f8-112">Element</span><span class="sxs-lookup"><span data-stu-id="7c3f8-112">Element</span></span>|<span data-ttu-id="7c3f8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7c3f8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c3f8-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="7c3f8-114">name</span></span>|<span data-ttu-id="7c3f8-115">Ciąg zawierający unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7c3f8-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c3f8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7c3f8-116">Child Elements</span></span>  
  
|<span data-ttu-id="7c3f8-117">Element</span><span class="sxs-lookup"><span data-stu-id="7c3f8-117">Element</span></span>|<span data-ttu-id="7c3f8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7c3f8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c3f8-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="7c3f8-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="7c3f8-120">Mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="7c3f8-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c3f8-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7c3f8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7c3f8-122">Element</span><span class="sxs-lookup"><span data-stu-id="7c3f8-122">Element</span></span>|<span data-ttu-id="7c3f8-123">Opis</span><span class="sxs-lookup"><span data-stu-id="7c3f8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c3f8-124">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="7c3f8-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7c3f8-125">Sekcja konfiguracyjna, który zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="7c3f8-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c3f8-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c3f8-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
