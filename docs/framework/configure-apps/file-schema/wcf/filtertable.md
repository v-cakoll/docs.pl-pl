---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855191"
---
# \<filterTable>
<span data-ttu-id="25c8c-101">Reprezentuje tabelę routingu zawierającą listę filtrów służących do szacowania komunikatów oraz punkt końcowy klienta, do którego mają być kierowane komunikaty, jeśli filtr ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="25c8c-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="25c8c-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="25c8c-102">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25c8c-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="25c8c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="25c8c-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25c8c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25c8c-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="25c8c-105">Attributes</span></span>  
  
|<span data-ttu-id="25c8c-106">Element</span><span class="sxs-lookup"><span data-stu-id="25c8c-106">Element</span></span>|<span data-ttu-id="25c8c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="25c8c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25c8c-108">name</span><span class="sxs-lookup"><span data-stu-id="25c8c-108">name</span></span>|<span data-ttu-id="25c8c-109">Ciąg zawierający unikatową nazwę tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="25c8c-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25c8c-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="25c8c-110">Child Elements</span></span>  
  
|<span data-ttu-id="25c8c-111">Element</span><span class="sxs-lookup"><span data-stu-id="25c8c-111">Element</span></span>|<span data-ttu-id="25c8c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="25c8c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="25c8c-113">Mapowania między filtrami routingu i docelowymi punktami końcowymi do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="25c8c-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25c8c-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="25c8c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="25c8c-115">Element</span><span class="sxs-lookup"><span data-stu-id="25c8c-115">Element</span></span>|<span data-ttu-id="25c8c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="25c8c-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="25c8c-117">Sekcja konfiguracji, która zawiera tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="25c8c-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25c8c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25c8c-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
