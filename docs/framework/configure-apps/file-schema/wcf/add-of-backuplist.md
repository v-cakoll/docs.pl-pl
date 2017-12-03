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
ms.openlocfilehash: b93b442d21d34eea5031cea565bdcf62139abc81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="c610c-102">&lt;add&gt; w &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="c610c-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="c610c-103">Reprezentuje element konfiguracji, który definiuje element zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c610c-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="c610c-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c610c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c610c-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="c610c-105">\<routing></span></span>  
<span data-ttu-id="c610c-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="c610c-106">\<backupLists></span></span>  
<span data-ttu-id="c610c-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="c610c-107">\<backupList></span></span>  
<span data-ttu-id="c610c-108">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="c610c-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c610c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c610c-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c610c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c610c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c610c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c610c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c610c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c610c-112">Attributes</span></span>  
  
|<span data-ttu-id="c610c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c610c-113">Attribute</span></span>|<span data-ttu-id="c610c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c610c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c610c-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="c610c-115">name</span></span>|<span data-ttu-id="c610c-116">Ciąg określający nazwę zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c610c-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c610c-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c610c-117">Child Elements</span></span>  
 <span data-ttu-id="c610c-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="c610c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c610c-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c610c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c610c-120">Element</span><span class="sxs-lookup"><span data-stu-id="c610c-120">Element</span></span>|<span data-ttu-id="c610c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c610c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c610c-122">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="c610c-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="c610c-123">Zawiera listę punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny.</span><span class="sxs-lookup"><span data-stu-id="c610c-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c610c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c610c-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
