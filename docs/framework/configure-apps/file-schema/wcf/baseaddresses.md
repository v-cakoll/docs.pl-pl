---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850210"
---
# \<baseAddresses>
<span data-ttu-id="34f80-101">Reprezentuje kolekcję `baseAddress` elementów, które są adresami podstawowymi dla hosta usługi w środowisku własnym.</span><span class="sxs-lookup"><span data-stu-id="34f80-101">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="34f80-102">W przypadku obecności adresu podstawowego punkty końcowe można skonfigurować przy użyciu adresów względnych dla adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="34f80-102">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="34f80-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="34f80-103">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="34f80-104">Typ</span><span class="sxs-lookup"><span data-stu-id="34f80-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34f80-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34f80-105">Attributes and Elements</span></span>  
 <span data-ttu-id="34f80-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34f80-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34f80-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34f80-107">Attributes</span></span>  
 <span data-ttu-id="34f80-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="34f80-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="34f80-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34f80-109">Child Elements</span></span>  
  
|<span data-ttu-id="34f80-110">Element</span><span class="sxs-lookup"><span data-stu-id="34f80-110">Element</span></span>|<span data-ttu-id="34f80-111">Opis</span><span class="sxs-lookup"><span data-stu-id="34f80-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="34f80-112">Element konfiguracji, który określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="34f80-112">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34f80-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34f80-113">Parent Elements</span></span>  
  
|<span data-ttu-id="34f80-114">Element</span><span class="sxs-lookup"><span data-stu-id="34f80-114">Element</span></span>|<span data-ttu-id="34f80-115">Opis</span><span class="sxs-lookup"><span data-stu-id="34f80-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="34f80-116">Element konfiguracji, który określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="34f80-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34f80-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34f80-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="34f80-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="34f80-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
