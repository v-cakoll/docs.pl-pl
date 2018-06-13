---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 966556a1a8bde72e33640dcc6fd37ae7a044ceef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753417"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="58098-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="58098-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="58098-103">Reprezentuje sekcję konfiguracji określającą tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysłania wiadomości, gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="58098-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="58098-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="58098-104">\<system.serviceModel></span></span>  
<span data-ttu-id="58098-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="58098-105">\<routing></span></span>  
<span data-ttu-id="58098-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="58098-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58098-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="58098-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="58098-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="58098-108">Attributes and Elements</span></span>  
 <span data-ttu-id="58098-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="58098-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58098-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="58098-110">Attributes</span></span>  
 <span data-ttu-id="58098-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="58098-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58098-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="58098-112">Child Elements</span></span>  
  
|<span data-ttu-id="58098-113">Element</span><span class="sxs-lookup"><span data-stu-id="58098-113">Element</span></span>|<span data-ttu-id="58098-114">Opis</span><span class="sxs-lookup"><span data-stu-id="58098-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58098-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="58098-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="58098-116">Tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="58098-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58098-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="58098-117">Parent Elements</span></span>  
  
|<span data-ttu-id="58098-118">Element</span><span class="sxs-lookup"><span data-stu-id="58098-118">Element</span></span>|<span data-ttu-id="58098-119">Opis</span><span class="sxs-lookup"><span data-stu-id="58098-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58098-120">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="58098-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="58098-121">Sekcja konfiguracyjna zawierający filtrów routingu i tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="58098-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58098-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58098-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
