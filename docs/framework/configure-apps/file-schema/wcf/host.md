---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 8a8f9db96281d8d775ff5c2923018228b3a9c1e5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269032"
---
# <a name="host"></a><span data-ttu-id="554f1-101">\<host></span><span class="sxs-lookup"><span data-stu-id="554f1-101">\<host></span></span>
<span data-ttu-id="554f1-102">Określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="554f1-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="554f1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="554f1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="554f1-104">\<services></span><span class="sxs-lookup"><span data-stu-id="554f1-104">\<services></span></span>  
<span data-ttu-id="554f1-105">\<service></span><span class="sxs-lookup"><span data-stu-id="554f1-105">\<service></span></span>  
<span data-ttu-id="554f1-106">\<host></span><span class="sxs-lookup"><span data-stu-id="554f1-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="554f1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="554f1-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="554f1-108">Typ</span><span class="sxs-lookup"><span data-stu-id="554f1-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="554f1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="554f1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="554f1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="554f1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="554f1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="554f1-111">Attributes</span></span>  
 <span data-ttu-id="554f1-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="554f1-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="554f1-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="554f1-113">Child Elements</span></span>  
  
|<span data-ttu-id="554f1-114">Element</span><span class="sxs-lookup"><span data-stu-id="554f1-114">Element</span></span>|<span data-ttu-id="554f1-115">Opis</span><span class="sxs-lookup"><span data-stu-id="554f1-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="554f1-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="554f1-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="554f1-117">Kolekcja `baseAddress` elementy, które określa adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="554f1-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="554f1-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="554f1-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="554f1-119">Element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.</span><span class="sxs-lookup"><span data-stu-id="554f1-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="554f1-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="554f1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="554f1-121">Element</span><span class="sxs-lookup"><span data-stu-id="554f1-121">Element</span></span>|<span data-ttu-id="554f1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="554f1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="554f1-123">\<service></span><span class="sxs-lookup"><span data-stu-id="554f1-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="554f1-124">Określa ustawienia usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="554f1-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="554f1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="554f1-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="554f1-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="554f1-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
