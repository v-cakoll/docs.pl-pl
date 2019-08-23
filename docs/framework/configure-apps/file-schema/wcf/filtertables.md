---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: b0a344aa69085d50087eefc746236bc8ceacadaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918855"
---
# <a name="filtertables"></a><span data-ttu-id="7886e-101">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="7886e-101">\<filterTables></span></span>
<span data-ttu-id="7886e-102">Reprezentuje sekcję konfiguracji definiującą tabele routingu, które zawierają mapowania między filtrami routingu i docelowymi punktami końcowymi, do których mają być wysyłane komunikaty, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="7886e-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="7886e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7886e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7886e-104">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="7886e-104">\<routing></span></span>  
<span data-ttu-id="7886e-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="7886e-105">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7886e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7886e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7886e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7886e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7886e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7886e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7886e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7886e-109">Attributes</span></span>  
 <span data-ttu-id="7886e-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="7886e-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7886e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7886e-111">Child Elements</span></span>  
  
|<span data-ttu-id="7886e-112">Element</span><span class="sxs-lookup"><span data-stu-id="7886e-112">Element</span></span>|<span data-ttu-id="7886e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7886e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7886e-114">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="7886e-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="7886e-115">Tabela routingu, która zawiera mapowania między filtrami routingu i docelowymi punktami końcowymi do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="7886e-115">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7886e-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7886e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7886e-117">Element</span><span class="sxs-lookup"><span data-stu-id="7886e-117">Element</span></span>|<span data-ttu-id="7886e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7886e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7886e-119">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="7886e-119">\<routing></span></span>](routing.md)|<span data-ttu-id="7886e-120">Sekcja konfiguracji, która zawiera filtry routingu i tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="7886e-120">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7886e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7886e-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
