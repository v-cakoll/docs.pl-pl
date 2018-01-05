---
title: '&lt;add&gt; w &lt;backupList&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 786620b0daf1cd22a95f9d0c94b7fc3d17c1a2c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="87d62-102">&lt;add&gt; w &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="87d62-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="87d62-103">Reprezentuje element konfiguracji, który definiuje element zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="87d62-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="87d62-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="87d62-104">\<system.serviceModel></span></span>  
<span data-ttu-id="87d62-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="87d62-105">\<routing></span></span>  
<span data-ttu-id="87d62-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="87d62-106">\<backupLists></span></span>  
<span data-ttu-id="87d62-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="87d62-107">\<backupList></span></span>  
<span data-ttu-id="87d62-108">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="87d62-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d62-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="87d62-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87d62-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87d62-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87d62-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87d62-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87d62-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87d62-112">Attributes</span></span>  
  
|<span data-ttu-id="87d62-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="87d62-113">Attribute</span></span>|<span data-ttu-id="87d62-114">Opis</span><span class="sxs-lookup"><span data-stu-id="87d62-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87d62-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="87d62-115">name</span></span>|<span data-ttu-id="87d62-116">Ciąg określający nazwę zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="87d62-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87d62-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87d62-117">Child Elements</span></span>  
 <span data-ttu-id="87d62-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="87d62-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87d62-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87d62-119">Parent Elements</span></span>  
  
|<span data-ttu-id="87d62-120">Element</span><span class="sxs-lookup"><span data-stu-id="87d62-120">Element</span></span>|<span data-ttu-id="87d62-121">Opis</span><span class="sxs-lookup"><span data-stu-id="87d62-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87d62-122">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="87d62-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="87d62-123">Zawiera listę punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny.</span><span class="sxs-lookup"><span data-stu-id="87d62-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87d62-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87d62-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
