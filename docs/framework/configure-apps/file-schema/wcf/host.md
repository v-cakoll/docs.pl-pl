---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855211"
---
# \<host>
<span data-ttu-id="ad6bb-101">Określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ad6bb-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="ad6bb-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad6bb-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="ad6bb-103">Typ</span><span class="sxs-lookup"><span data-stu-id="ad6bb-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad6bb-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ad6bb-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ad6bb-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ad6bb-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad6bb-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ad6bb-106">Attributes</span></span>  
 <span data-ttu-id="ad6bb-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="ad6bb-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ad6bb-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ad6bb-108">Child Elements</span></span>  
  
|<span data-ttu-id="ad6bb-109">Element</span><span class="sxs-lookup"><span data-stu-id="ad6bb-109">Element</span></span>|<span data-ttu-id="ad6bb-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ad6bb-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="ad6bb-111">Kolekcja `baseAddress` elementów, która określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ad6bb-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="ad6bb-112">Element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ad6bb-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad6bb-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ad6bb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ad6bb-114">Element</span><span class="sxs-lookup"><span data-stu-id="ad6bb-114">Element</span></span>|<span data-ttu-id="ad6bb-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ad6bb-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="ad6bb-116">Określa ustawienia dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ad6bb-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad6bb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad6bb-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="ad6bb-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="ad6bb-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
