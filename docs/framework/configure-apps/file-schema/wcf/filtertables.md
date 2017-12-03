---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 028681acffcd93633807bdb1c6fa78aab98011c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="8c1a7-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="8c1a7-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="8c1a7-103">Reprezentuje sekcję konfiguracji określającą tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysłania wiadomości, gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="8c1a7-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="8c1a7-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8c1a7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8c1a7-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="8c1a7-105">\<routing></span></span>  
<span data-ttu-id="8c1a7-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="8c1a7-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c1a7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c1a7-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8c1a7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8c1a7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8c1a7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8c1a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c1a7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8c1a7-110">Attributes</span></span>  
 <span data-ttu-id="8c1a7-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="8c1a7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8c1a7-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8c1a7-112">Child Elements</span></span>  
  
|<span data-ttu-id="8c1a7-113">Element</span><span class="sxs-lookup"><span data-stu-id="8c1a7-113">Element</span></span>|<span data-ttu-id="8c1a7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8c1a7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c1a7-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="8c1a7-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="8c1a7-116">Tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="8c1a7-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c1a7-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8c1a7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8c1a7-118">Element</span><span class="sxs-lookup"><span data-stu-id="8c1a7-118">Element</span></span>|<span data-ttu-id="8c1a7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8c1a7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c1a7-120">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="8c1a7-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="8c1a7-121">Sekcja konfiguracyjna zawierający filtrów routingu i tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="8c1a7-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c1a7-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c1a7-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
