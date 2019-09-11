---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855211"
---
# <a name="host"></a><span data-ttu-id="eef21-101">\<host></span><span class="sxs-lookup"><span data-stu-id="eef21-101">\<host></span></span>
<span data-ttu-id="eef21-102">Określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="eef21-102">Specifies settings for a service host.</span></span>  
  
<span data-ttu-id="eef21-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eef21-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eef21-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="eef21-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="eef21-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usług**](services.md)</span><span class="sxs-lookup"><span data-stu-id="eef21-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="eef21-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usługi**](service.md)</span><span class="sxs-lookup"><span data-stu-id="eef21-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="eef21-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> hosta**</span><span class="sxs-lookup"><span data-stu-id="eef21-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef21-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="eef21-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="eef21-109">Typ</span><span class="sxs-lookup"><span data-stu-id="eef21-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eef21-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eef21-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eef21-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eef21-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eef21-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eef21-112">Attributes</span></span>  
 <span data-ttu-id="eef21-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="eef21-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eef21-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eef21-114">Child Elements</span></span>  
  
|<span data-ttu-id="eef21-115">Element</span><span class="sxs-lookup"><span data-stu-id="eef21-115">Element</span></span>|<span data-ttu-id="eef21-116">Opis</span><span class="sxs-lookup"><span data-stu-id="eef21-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eef21-117">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="eef21-117">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="eef21-118">Kolekcja `baseAddress` elementów, która określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="eef21-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="eef21-119">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="eef21-119">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="eef21-120">Element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="eef21-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eef21-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eef21-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eef21-122">Element</span><span class="sxs-lookup"><span data-stu-id="eef21-122">Element</span></span>|<span data-ttu-id="eef21-123">Opis</span><span class="sxs-lookup"><span data-stu-id="eef21-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eef21-124">\<> usługi</span><span class="sxs-lookup"><span data-stu-id="eef21-124">\<service></span></span>](service.md)|<span data-ttu-id="eef21-125">Określa ustawienia dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="eef21-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eef21-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eef21-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="eef21-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="eef21-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
