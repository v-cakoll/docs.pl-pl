---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 595970a56e05c4fc1c9b2c0eb669ec3b3a120fe1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262395"
---
# <a name="defaultports"></a><span data-ttu-id="23d24-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="23d24-101">\<defaultPorts></span></span>
<span data-ttu-id="23d24-102">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="23d24-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="23d24-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="23d24-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="23d24-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="23d24-104">\<behaviors></span></span>  
<span data-ttu-id="23d24-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="23d24-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="23d24-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="23d24-106">\<behavior></span></span>  
<span data-ttu-id="23d24-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="23d24-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="23d24-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="23d24-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d24-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="23d24-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23d24-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23d24-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23d24-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23d24-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23d24-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23d24-112">Attributes</span></span>  
 <span data-ttu-id="23d24-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="23d24-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23d24-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23d24-114">Child Elements</span></span>  
  
|<span data-ttu-id="23d24-115">Element</span><span class="sxs-lookup"><span data-stu-id="23d24-115">Element</span></span>|<span data-ttu-id="23d24-116">Opis</span><span class="sxs-lookup"><span data-stu-id="23d24-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23d24-117">\<Dodaj > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="23d24-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="23d24-118">Domyślny punkt końcowy komunikacji, aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="23d24-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23d24-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23d24-119">Parent Elements</span></span>  
  
|<span data-ttu-id="23d24-120">Element</span><span class="sxs-lookup"><span data-stu-id="23d24-120">Element</span></span>|<span data-ttu-id="23d24-121">Opis</span><span class="sxs-lookup"><span data-stu-id="23d24-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23d24-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="23d24-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="23d24-123">Lista domyślnych portów.</span><span class="sxs-lookup"><span data-stu-id="23d24-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23d24-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23d24-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
