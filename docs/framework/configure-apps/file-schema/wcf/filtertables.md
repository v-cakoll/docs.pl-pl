---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855201"
---
# <a name="filtertables"></a><span data-ttu-id="72fd7-101">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="72fd7-101">\<filterTables></span></span>
<span data-ttu-id="72fd7-102">Reprezentuje sekcję konfiguracji definiującą tabele routingu, które zawierają mapowania między filtrami routingu i docelowymi punktami końcowymi, do których mają być wysyłane komunikaty, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="72fd7-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="72fd7-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="72fd7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="72fd7-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="72fd7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="72fd7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="72fd7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="72fd7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="72fd7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72fd7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="72fd7-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72fd7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="72fd7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="72fd7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="72fd7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72fd7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="72fd7-110">Attributes</span></span>  
 <span data-ttu-id="72fd7-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="72fd7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="72fd7-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="72fd7-112">Child Elements</span></span>  
  
|<span data-ttu-id="72fd7-113">Element</span><span class="sxs-lookup"><span data-stu-id="72fd7-113">Element</span></span>|<span data-ttu-id="72fd7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="72fd7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72fd7-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="72fd7-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="72fd7-116">Tabela routingu, która zawiera mapowania między filtrami routingu i docelowymi punktami końcowymi do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="72fd7-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72fd7-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="72fd7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="72fd7-118">Element</span><span class="sxs-lookup"><span data-stu-id="72fd7-118">Element</span></span>|<span data-ttu-id="72fd7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="72fd7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72fd7-120">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="72fd7-120">\<routing></span></span>](routing.md)|<span data-ttu-id="72fd7-121">Sekcja konfiguracji, która zawiera filtry routingu i tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="72fd7-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72fd7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72fd7-122">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
