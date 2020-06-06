---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855201"
---
# \<filterTables>
<span data-ttu-id="4688b-101">Reprezentuje sekcję konfiguracji definiującą tabele routingu, które zawierają mapowania między filtrami routingu i docelowymi punktami końcowymi, do których mają być wysyłane komunikaty, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="4688b-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="4688b-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="4688b-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4688b-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4688b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4688b-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4688b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4688b-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4688b-105">Attributes</span></span>  
 <span data-ttu-id="4688b-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="4688b-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4688b-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4688b-107">Child Elements</span></span>  
  
|<span data-ttu-id="4688b-108">Element</span><span class="sxs-lookup"><span data-stu-id="4688b-108">Element</span></span>|<span data-ttu-id="4688b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4688b-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="4688b-110">Tabela routingu, która zawiera mapowania między filtrami routingu i docelowymi punktami końcowymi do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="4688b-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4688b-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4688b-111">Parent Elements</span></span>  
  
|<span data-ttu-id="4688b-112">Element</span><span class="sxs-lookup"><span data-stu-id="4688b-112">Element</span></span>|<span data-ttu-id="4688b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4688b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="4688b-114">Sekcja konfiguracji, która zawiera filtry routingu i tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="4688b-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4688b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4688b-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
