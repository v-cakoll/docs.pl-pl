---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c49c7cf3a196595556c2bf1b4ed4365bfe1e4cbf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704248"
---
# <a name="filtertables"></a><span data-ttu-id="36536-101">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="36536-101">\<filterTables></span></span>
<span data-ttu-id="36536-102">Reprezentuje sekcję konfiguracji określającą tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysłania wiadomości, gdy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="36536-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="36536-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="36536-103">\<system.serviceModel></span></span>  
<span data-ttu-id="36536-104">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="36536-104">\<routing></span></span>  
<span data-ttu-id="36536-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="36536-105">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36536-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="36536-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36536-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="36536-107">Attributes and Elements</span></span>  
 <span data-ttu-id="36536-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="36536-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36536-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="36536-109">Attributes</span></span>  
 <span data-ttu-id="36536-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="36536-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36536-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="36536-111">Child Elements</span></span>  
  
|<span data-ttu-id="36536-112">Element</span><span class="sxs-lookup"><span data-stu-id="36536-112">Element</span></span>|<span data-ttu-id="36536-113">Opis</span><span class="sxs-lookup"><span data-stu-id="36536-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36536-114">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="36536-114">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="36536-115">Tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="36536-115">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36536-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="36536-116">Parent Elements</span></span>  
  
|<span data-ttu-id="36536-117">Element</span><span class="sxs-lookup"><span data-stu-id="36536-117">Element</span></span>|<span data-ttu-id="36536-118">Opis</span><span class="sxs-lookup"><span data-stu-id="36536-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36536-119">\<routing></span><span class="sxs-lookup"><span data-stu-id="36536-119">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="36536-120">Sekcja konfiguracji, zawierający filtrów routingu i tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="36536-120">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36536-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36536-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
