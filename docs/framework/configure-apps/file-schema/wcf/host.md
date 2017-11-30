---
title: '&lt;Host&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bded8d718259bf4fc84bfe790db069a77fc2a703
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lthostgt"></a><span data-ttu-id="65cb7-102">&lt;Host&gt;</span><span class="sxs-lookup"><span data-stu-id="65cb7-102">&lt;host&gt;</span></span>
<span data-ttu-id="65cb7-103">Określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="65cb7-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="65cb7-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="65cb7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="65cb7-105">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="65cb7-105">\<services></span></span>  
<span data-ttu-id="65cb7-106">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="65cb7-106">\<service></span></span>  
<span data-ttu-id="65cb7-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="65cb7-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65cb7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="65cb7-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="65cb7-109">Typ</span><span class="sxs-lookup"><span data-stu-id="65cb7-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65cb7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="65cb7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="65cb7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="65cb7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65cb7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="65cb7-112">Attributes</span></span>  
 <span data-ttu-id="65cb7-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="65cb7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="65cb7-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65cb7-114">Child Elements</span></span>  
  
|<span data-ttu-id="65cb7-115">Element</span><span class="sxs-lookup"><span data-stu-id="65cb7-115">Element</span></span>|<span data-ttu-id="65cb7-116">Opis</span><span class="sxs-lookup"><span data-stu-id="65cb7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65cb7-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="65cb7-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="65cb7-118">Kolekcja `baseAddress` elementów, które określa adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="65cb7-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="65cb7-119">\<limity czasu ></span><span class="sxs-lookup"><span data-stu-id="65cb7-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="65cb7-120">Element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="65cb7-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65cb7-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65cb7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="65cb7-122">Element</span><span class="sxs-lookup"><span data-stu-id="65cb7-122">Element</span></span>|<span data-ttu-id="65cb7-123">Opis</span><span class="sxs-lookup"><span data-stu-id="65cb7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65cb7-124">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="65cb7-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="65cb7-125">Określa ustawienia dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="65cb7-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65cb7-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65cb7-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="65cb7-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="65cb7-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
