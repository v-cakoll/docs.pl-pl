---
title: '&lt;add&gt; w &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 2cc7cce62082317bb86218d68bd2881b74649771
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670189"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="c533c-102">&lt;add&gt; w &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="c533c-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="c533c-103">Reprezentuje element konfiguracji, który definiuje element kopii zapasowej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c533c-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="c533c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c533c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c533c-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="c533c-105">\<routing></span></span>  
<span data-ttu-id="c533c-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="c533c-106">\<backupLists></span></span>  
<span data-ttu-id="c533c-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="c533c-107">\<backupList></span></span>  
<span data-ttu-id="c533c-108">\<add></span><span class="sxs-lookup"><span data-stu-id="c533c-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c533c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c533c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c533c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c533c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c533c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c533c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c533c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c533c-112">Attributes</span></span>  
  
|<span data-ttu-id="c533c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c533c-113">Attribute</span></span>|<span data-ttu-id="c533c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c533c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c533c-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="c533c-115">name</span></span>|<span data-ttu-id="c533c-116">Ciąg, który określa nazwę punktu końcowego, tworzenia kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="c533c-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c533c-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c533c-117">Child Elements</span></span>  
 <span data-ttu-id="c533c-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="c533c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c533c-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c533c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c533c-120">Element</span><span class="sxs-lookup"><span data-stu-id="c533c-120">Element</span></span>|<span data-ttu-id="c533c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c533c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c533c-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="c533c-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="c533c-123">Zawiera listę punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c533c-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c533c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c533c-124">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
