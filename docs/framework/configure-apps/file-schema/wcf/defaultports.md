---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398071"
---
# \<defaultPorts>
<span data-ttu-id="44a06-101">Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="44a06-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="44a06-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="44a06-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44a06-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44a06-103">Attributes and Elements</span></span>  
 <span data-ttu-id="44a06-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44a06-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44a06-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44a06-105">Attributes</span></span>  
 <span data-ttu-id="44a06-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="44a06-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44a06-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44a06-107">Child Elements</span></span>  
  
|<span data-ttu-id="44a06-108">Element</span><span class="sxs-lookup"><span data-stu-id="44a06-108">Element</span></span>|<span data-ttu-id="44a06-109">Opis</span><span class="sxs-lookup"><span data-stu-id="44a06-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44a06-110">\<add>z\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="44a06-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="44a06-111">Domyślny punkt końcowy komunikacji, do którego nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="44a06-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44a06-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44a06-112">Parent Elements</span></span>  
  
|<span data-ttu-id="44a06-113">Element</span><span class="sxs-lookup"><span data-stu-id="44a06-113">Element</span></span>|<span data-ttu-id="44a06-114">Opis</span><span class="sxs-lookup"><span data-stu-id="44a06-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="44a06-115">Lista domyślnych portów.</span><span class="sxs-lookup"><span data-stu-id="44a06-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44a06-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44a06-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
