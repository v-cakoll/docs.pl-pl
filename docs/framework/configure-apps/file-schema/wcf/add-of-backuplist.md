---
title: '&lt;add&gt; w &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 7e7361b24c0444b5f3d51a6f5bf079d5eb2dee18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="d7b28-102">&lt;add&gt; w &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="d7b28-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="d7b28-103">Reprezentuje element konfiguracji, który definiuje element zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d7b28-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="d7b28-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d7b28-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d7b28-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="d7b28-105">\<routing></span></span>  
<span data-ttu-id="d7b28-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="d7b28-106">\<backupLists></span></span>  
<span data-ttu-id="d7b28-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="d7b28-107">\<backupList></span></span>  
<span data-ttu-id="d7b28-108">\<add></span><span class="sxs-lookup"><span data-stu-id="d7b28-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b28-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7b28-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7b28-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d7b28-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d7b28-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d7b28-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7b28-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d7b28-112">Attributes</span></span>  
  
|<span data-ttu-id="d7b28-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d7b28-113">Attribute</span></span>|<span data-ttu-id="d7b28-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d7b28-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7b28-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="d7b28-115">name</span></span>|<span data-ttu-id="d7b28-116">Ciąg określający nazwę zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d7b28-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7b28-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d7b28-117">Child Elements</span></span>  
 <span data-ttu-id="d7b28-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="d7b28-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7b28-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d7b28-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d7b28-120">Element</span><span class="sxs-lookup"><span data-stu-id="d7b28-120">Element</span></span>|<span data-ttu-id="d7b28-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d7b28-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7b28-122">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="d7b28-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d7b28-123">Zawiera listę punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny.</span><span class="sxs-lookup"><span data-stu-id="d7b28-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7b28-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7b28-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
