---
title: '&lt;Host&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: afa9d65223ab3a7730a55bc41ed98458707b32db
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145232"
---
# <a name="lthostgt"></a><span data-ttu-id="bcc6d-102">&lt;Host&gt;</span><span class="sxs-lookup"><span data-stu-id="bcc6d-102">&lt;host&gt;</span></span>
<span data-ttu-id="bcc6d-103">Określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="bcc6d-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="bcc6d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bcc6d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bcc6d-105">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="bcc6d-105">\<services></span></span>  
<span data-ttu-id="bcc6d-106">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="bcc6d-106">\<service></span></span>  
<span data-ttu-id="bcc6d-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="bcc6d-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc6d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="bcc6d-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="bcc6d-109">Typ</span><span class="sxs-lookup"><span data-stu-id="bcc6d-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcc6d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bcc6d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bcc6d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bcc6d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcc6d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bcc6d-112">Attributes</span></span>  
 <span data-ttu-id="bcc6d-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="bcc6d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bcc6d-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bcc6d-114">Child Elements</span></span>  
  
|<span data-ttu-id="bcc6d-115">Element</span><span class="sxs-lookup"><span data-stu-id="bcc6d-115">Element</span></span>|<span data-ttu-id="bcc6d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bcc6d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcc6d-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="bcc6d-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="bcc6d-118">Kolekcja `baseAddress` elementy, które określa adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="bcc6d-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="bcc6d-119">\<limity czasu ></span><span class="sxs-lookup"><span data-stu-id="bcc6d-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="bcc6d-120">Element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.</span><span class="sxs-lookup"><span data-stu-id="bcc6d-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bcc6d-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bcc6d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bcc6d-122">Element</span><span class="sxs-lookup"><span data-stu-id="bcc6d-122">Element</span></span>|<span data-ttu-id="bcc6d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="bcc6d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcc6d-124">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="bcc6d-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="bcc6d-125">Określa ustawienia usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bcc6d-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bcc6d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcc6d-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="bcc6d-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="bcc6d-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
