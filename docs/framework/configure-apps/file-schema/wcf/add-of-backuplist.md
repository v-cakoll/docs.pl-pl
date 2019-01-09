---
title: '&lt;add&gt; w &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 4a8eb3df9be6b6b5bfe43aee330f3174ddca66ab
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151478"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="3a4d2-102">&lt;add&gt; w &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="3a4d2-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="3a4d2-103">Reprezentuje element konfiguracji, który definiuje element kopii zapasowej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3a4d2-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="3a4d2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3a4d2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3a4d2-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="3a4d2-105">\<routing></span></span>  
<span data-ttu-id="3a4d2-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="3a4d2-106">\<backupLists></span></span>  
<span data-ttu-id="3a4d2-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="3a4d2-107">\<backupList></span></span>  
<span data-ttu-id="3a4d2-108">\<add></span><span class="sxs-lookup"><span data-stu-id="3a4d2-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a4d2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a4d2-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a4d2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3a4d2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3a4d2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3a4d2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a4d2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3a4d2-112">Attributes</span></span>  
  
|<span data-ttu-id="3a4d2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3a4d2-113">Attribute</span></span>|<span data-ttu-id="3a4d2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3a4d2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a4d2-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="3a4d2-115">name</span></span>|<span data-ttu-id="3a4d2-116">Ciąg, który określa nazwę punktu końcowego, tworzenia kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="3a4d2-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a4d2-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3a4d2-117">Child Elements</span></span>  
 <span data-ttu-id="3a4d2-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="3a4d2-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a4d2-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3a4d2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3a4d2-120">Element</span><span class="sxs-lookup"><span data-stu-id="3a4d2-120">Element</span></span>|<span data-ttu-id="3a4d2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3a4d2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a4d2-122">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="3a4d2-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="3a4d2-123">Zawiera listę punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3a4d2-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a4d2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a4d2-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
