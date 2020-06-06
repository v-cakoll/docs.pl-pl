---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854965"
---
# \<timeOuts>
<span data-ttu-id="9b59d-101">Reprezentuje element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="9b59d-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="9b59d-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b59d-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b59d-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9b59d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9b59d-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9b59d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b59d-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9b59d-105">Attributes</span></span>  
  
|<span data-ttu-id="9b59d-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9b59d-106">Attribute</span></span>|<span data-ttu-id="9b59d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9b59d-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="9b59d-108"><xref:System.TimeSpan>Wartość, która określa przedział czasu, jaki może być zamknięty dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="9b59d-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="9b59d-109"><xref:System.TimeSpan>Wartość, która określa przedział czasu, jaki może otworzyć Host usługi.</span><span class="sxs-lookup"><span data-stu-id="9b59d-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b59d-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9b59d-110">Child Elements</span></span>  
 <span data-ttu-id="9b59d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="9b59d-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b59d-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9b59d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="9b59d-113">Element</span><span class="sxs-lookup"><span data-stu-id="9b59d-113">Element</span></span>|<span data-ttu-id="9b59d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9b59d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="9b59d-115">Element konfiguracji, który określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="9b59d-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b59d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b59d-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="9b59d-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="9b59d-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
