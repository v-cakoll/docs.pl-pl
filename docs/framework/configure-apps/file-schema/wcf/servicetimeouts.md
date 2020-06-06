---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399547"
---
# \<serviceTimeouts>
<span data-ttu-id="201d5-101">Określa limit czasu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="201d5-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="201d5-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="201d5-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="201d5-103">Typ</span><span class="sxs-lookup"><span data-stu-id="201d5-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="201d5-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="201d5-104">Attributes and Elements</span></span>  
 <span data-ttu-id="201d5-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="201d5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="201d5-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="201d5-106">Attributes</span></span>  
  
|<span data-ttu-id="201d5-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="201d5-107">Attribute</span></span>|<span data-ttu-id="201d5-108">Opis</span><span class="sxs-lookup"><span data-stu-id="201d5-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="201d5-109"><xref:System.TimeSpan>Wartość, która określa przedział czasu, przez który transakcja musi przepływać z klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="201d5-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="201d5-110">Wartość domyślna to "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="201d5-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="201d5-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="201d5-111">Child Elements</span></span>  
 <span data-ttu-id="201d5-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="201d5-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="201d5-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="201d5-113">Parent Elements</span></span>  
  
|<span data-ttu-id="201d5-114">Element</span><span class="sxs-lookup"><span data-stu-id="201d5-114">Element</span></span>|<span data-ttu-id="201d5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="201d5-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="201d5-116">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="201d5-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="201d5-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="201d5-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
