---
title: '&lt;limity czasu&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: e39deeb251865b87eb7734e4447088ca2f221d1d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148334"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="2f891-102">&lt;limity czasu&gt;</span><span class="sxs-lookup"><span data-stu-id="2f891-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="2f891-103">Reprezentuje element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.</span><span class="sxs-lookup"><span data-stu-id="2f891-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="2f891-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2f891-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2f891-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="2f891-105">\<client></span></span>  
<span data-ttu-id="2f891-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="2f891-106">\<endpoint></span></span>  
<span data-ttu-id="2f891-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="2f891-107">\<host></span></span>  
<span data-ttu-id="2f891-108">\<limity czasu ></span><span class="sxs-lookup"><span data-stu-id="2f891-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f891-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f891-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f891-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2f891-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2f891-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2f891-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f891-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2f891-112">Attributes</span></span>  
  
|<span data-ttu-id="2f891-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2f891-113">Attribute</span></span>|<span data-ttu-id="2f891-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2f891-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="2f891-115">A <xref:System.TimeSpan> wartość, która określa przedział czasu dozwolony na zamknięcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="2f891-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="2f891-116">A <xref:System.TimeSpan> wartość, która określa okres czasu dozwolony dla otwarcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="2f891-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f891-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2f891-117">Child Elements</span></span>  
 <span data-ttu-id="2f891-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="2f891-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f891-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2f891-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2f891-120">Element</span><span class="sxs-lookup"><span data-stu-id="2f891-120">Element</span></span>|<span data-ttu-id="2f891-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2f891-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f891-122">\<host ></span><span class="sxs-lookup"><span data-stu-id="2f891-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="2f891-123">Element konfiguracji, który określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="2f891-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f891-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f891-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="2f891-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="2f891-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
