---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b6ae5faa2dd2ffef9669a0245a75227b0f669cf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118069"
---
# <a name="timeouts"></a><span data-ttu-id="09da2-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="09da2-101">\<timeOuts></span></span>
<span data-ttu-id="09da2-102">Reprezentuje element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.</span><span class="sxs-lookup"><span data-stu-id="09da2-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="09da2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="09da2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="09da2-104">\<client></span><span class="sxs-lookup"><span data-stu-id="09da2-104">\<client></span></span>  
<span data-ttu-id="09da2-105">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="09da2-105">\<endpoint></span></span>  
<span data-ttu-id="09da2-106">\<host></span><span class="sxs-lookup"><span data-stu-id="09da2-106">\<host></span></span>  
<span data-ttu-id="09da2-107">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="09da2-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09da2-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="09da2-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09da2-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="09da2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="09da2-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="09da2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09da2-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="09da2-111">Attributes</span></span>  
  
|<span data-ttu-id="09da2-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="09da2-112">Attribute</span></span>|<span data-ttu-id="09da2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="09da2-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="09da2-114">A <xref:System.TimeSpan> wartość, która określa przedział czasu dozwolony na zamknięcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="09da2-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="09da2-115">A <xref:System.TimeSpan> wartość, która określa okres czasu dozwolony dla otwarcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="09da2-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09da2-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="09da2-116">Child Elements</span></span>  
 <span data-ttu-id="09da2-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="09da2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09da2-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="09da2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="09da2-119">Element</span><span class="sxs-lookup"><span data-stu-id="09da2-119">Element</span></span>|<span data-ttu-id="09da2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="09da2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09da2-121">\<host></span><span class="sxs-lookup"><span data-stu-id="09da2-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="09da2-122">Element konfiguracji, który określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="09da2-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09da2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09da2-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="09da2-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="09da2-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
