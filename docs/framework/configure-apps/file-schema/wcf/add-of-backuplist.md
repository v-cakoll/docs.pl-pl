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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1475983f7dc54a597198d48a2a404e431ce9c0a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="39100-102">&lt;add&gt; w &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="39100-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="39100-103">Reprezentuje element konfiguracji, który definiuje element zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="39100-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="39100-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="39100-104">\<system.serviceModel></span></span>  
<span data-ttu-id="39100-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="39100-105">\<routing></span></span>  
<span data-ttu-id="39100-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="39100-106">\<backupLists></span></span>  
<span data-ttu-id="39100-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="39100-107">\<backupList></span></span>  
<span data-ttu-id="39100-108">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="39100-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39100-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="39100-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39100-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39100-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39100-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39100-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39100-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39100-112">Attributes</span></span>  
  
|<span data-ttu-id="39100-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39100-113">Attribute</span></span>|<span data-ttu-id="39100-114">Opis</span><span class="sxs-lookup"><span data-stu-id="39100-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39100-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="39100-115">name</span></span>|<span data-ttu-id="39100-116">Ciąg określający nazwę zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="39100-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39100-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39100-117">Child Elements</span></span>  
 <span data-ttu-id="39100-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="39100-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39100-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39100-119">Parent Elements</span></span>  
  
|<span data-ttu-id="39100-120">Element</span><span class="sxs-lookup"><span data-stu-id="39100-120">Element</span></span>|<span data-ttu-id="39100-121">Opis</span><span class="sxs-lookup"><span data-stu-id="39100-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39100-122">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="39100-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="39100-123">Zawiera listę punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny.</span><span class="sxs-lookup"><span data-stu-id="39100-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39100-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39100-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
