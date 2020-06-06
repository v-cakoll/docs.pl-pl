---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399202"
---
# \<useRequestHeadersForMetadataAddress>
<span data-ttu-id="eea02-101">Umożliwia pobieranie informacji o adresie metadanych z nagłówków komunikatów żądania.</span><span class="sxs-lookup"><span data-stu-id="eea02-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="eea02-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="eea02-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eea02-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eea02-103">Attributes and Elements</span></span>  
 <span data-ttu-id="eea02-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eea02-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eea02-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eea02-105">Attributes</span></span>  
 <span data-ttu-id="eea02-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="eea02-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eea02-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eea02-107">Child Elements</span></span>  
  
|<span data-ttu-id="eea02-108">Element</span><span class="sxs-lookup"><span data-stu-id="eea02-108">Element</span></span>|<span data-ttu-id="eea02-109">Opis</span><span class="sxs-lookup"><span data-stu-id="eea02-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="eea02-110">Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="eea02-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eea02-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eea02-111">Parent Elements</span></span>  
  
|<span data-ttu-id="eea02-112">Element</span><span class="sxs-lookup"><span data-stu-id="eea02-112">Element</span></span>|<span data-ttu-id="eea02-113">Opis</span><span class="sxs-lookup"><span data-stu-id="eea02-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="eea02-114">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="eea02-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eea02-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eea02-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
