---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 8a8a352380fe6eedb41ead089405e7b79fad29fe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272786"
---
# <a name="timeouts"></a><span data-ttu-id="e6a33-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="e6a33-101">\<timeOuts></span></span>
<span data-ttu-id="e6a33-102">Reprezentuje element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.</span><span class="sxs-lookup"><span data-stu-id="e6a33-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="e6a33-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6a33-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6a33-104">\<client></span><span class="sxs-lookup"><span data-stu-id="e6a33-104">\<client></span></span>  
<span data-ttu-id="e6a33-105">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="e6a33-105">\<endpoint></span></span>  
<span data-ttu-id="e6a33-106">\<host></span><span class="sxs-lookup"><span data-stu-id="e6a33-106">\<host></span></span>  
<span data-ttu-id="e6a33-107">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="e6a33-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a33-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6a33-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6a33-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6a33-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e6a33-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e6a33-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6a33-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6a33-111">Attributes</span></span>  
  
|<span data-ttu-id="e6a33-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e6a33-112">Attribute</span></span>|<span data-ttu-id="e6a33-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e6a33-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e6a33-114">A <xref:System.TimeSpan> wartość, która określa przedział czasu dozwolony na zamknięcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="e6a33-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="e6a33-115">A <xref:System.TimeSpan> wartość, która określa okres czasu dozwolony dla otwarcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="e6a33-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6a33-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6a33-116">Child Elements</span></span>  
 <span data-ttu-id="e6a33-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="e6a33-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6a33-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6a33-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e6a33-119">Element</span><span class="sxs-lookup"><span data-stu-id="e6a33-119">Element</span></span>|<span data-ttu-id="e6a33-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e6a33-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6a33-121">\<host></span><span class="sxs-lookup"><span data-stu-id="e6a33-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e6a33-122">Element konfiguracji, który określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="e6a33-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6a33-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6a33-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="e6a33-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="e6a33-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
