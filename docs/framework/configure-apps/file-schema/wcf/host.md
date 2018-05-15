---
title: '&lt;Host&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 9c48fff7473449192887bfd8cc201dd87cb4e7f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lthostgt"></a><span data-ttu-id="50e2e-102">&lt;Host&gt;</span><span class="sxs-lookup"><span data-stu-id="50e2e-102">&lt;host&gt;</span></span>
<span data-ttu-id="50e2e-103">Określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="50e2e-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="50e2e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="50e2e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="50e2e-105">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="50e2e-105">\<services></span></span>  
<span data-ttu-id="50e2e-106">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="50e2e-106">\<service></span></span>  
<span data-ttu-id="50e2e-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="50e2e-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e2e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="50e2e-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="50e2e-109">Typ</span><span class="sxs-lookup"><span data-stu-id="50e2e-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50e2e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="50e2e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="50e2e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="50e2e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50e2e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="50e2e-112">Attributes</span></span>  
 <span data-ttu-id="50e2e-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="50e2e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="50e2e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="50e2e-114">Child Elements</span></span>  
  
|<span data-ttu-id="50e2e-115">Element</span><span class="sxs-lookup"><span data-stu-id="50e2e-115">Element</span></span>|<span data-ttu-id="50e2e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="50e2e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50e2e-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="50e2e-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="50e2e-118">Kolekcja `baseAddress` elementów, które określa adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="50e2e-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="50e2e-119">\<limity czasu ></span><span class="sxs-lookup"><span data-stu-id="50e2e-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="50e2e-120">Element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="50e2e-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50e2e-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="50e2e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="50e2e-122">Element</span><span class="sxs-lookup"><span data-stu-id="50e2e-122">Element</span></span>|<span data-ttu-id="50e2e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="50e2e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50e2e-124">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="50e2e-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="50e2e-125">Określa ustawienia dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="50e2e-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50e2e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50e2e-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="50e2e-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="50e2e-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
