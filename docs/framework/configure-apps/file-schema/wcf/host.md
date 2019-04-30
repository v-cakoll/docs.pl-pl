---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 3d1f7774f61060880a5c3b0327bdd6c2cc4dd74e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746747"
---
# <a name="host"></a><span data-ttu-id="dc7c6-101">\<host></span><span class="sxs-lookup"><span data-stu-id="dc7c6-101">\<host></span></span>
<span data-ttu-id="dc7c6-102">Określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="dc7c6-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="dc7c6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dc7c6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="dc7c6-104">\<services></span><span class="sxs-lookup"><span data-stu-id="dc7c6-104">\<services></span></span>  
<span data-ttu-id="dc7c6-105">\<service></span><span class="sxs-lookup"><span data-stu-id="dc7c6-105">\<service></span></span>  
<span data-ttu-id="dc7c6-106">\<host></span><span class="sxs-lookup"><span data-stu-id="dc7c6-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc7c6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc7c6-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="dc7c6-108">Typ</span><span class="sxs-lookup"><span data-stu-id="dc7c6-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc7c6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dc7c6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dc7c6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dc7c6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc7c6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dc7c6-111">Attributes</span></span>  
 <span data-ttu-id="dc7c6-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="dc7c6-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc7c6-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dc7c6-113">Child Elements</span></span>  
  
|<span data-ttu-id="dc7c6-114">Element</span><span class="sxs-lookup"><span data-stu-id="dc7c6-114">Element</span></span>|<span data-ttu-id="dc7c6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="dc7c6-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc7c6-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="dc7c6-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="dc7c6-117">Kolekcja `baseAddress` elementy, które określa adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="dc7c6-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="dc7c6-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="dc7c6-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="dc7c6-119">Element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.</span><span class="sxs-lookup"><span data-stu-id="dc7c6-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc7c6-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dc7c6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="dc7c6-121">Element</span><span class="sxs-lookup"><span data-stu-id="dc7c6-121">Element</span></span>|<span data-ttu-id="dc7c6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="dc7c6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc7c6-123">\<service></span><span class="sxs-lookup"><span data-stu-id="dc7c6-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="dc7c6-124">Określa ustawienia usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dc7c6-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc7c6-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc7c6-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="dc7c6-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="dc7c6-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
