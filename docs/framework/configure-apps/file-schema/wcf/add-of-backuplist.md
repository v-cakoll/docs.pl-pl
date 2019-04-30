---
title: <add> dla <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 03bf1bbb8156e4722d987e171d9034747ac6bb61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701206"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="113d5-102">\<Dodaj > z \<backupList ></span><span class="sxs-lookup"><span data-stu-id="113d5-102">\<add> of \<backupList></span></span>
<span data-ttu-id="113d5-103">Reprezentuje element konfiguracji, który definiuje element kopii zapasowej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="113d5-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="113d5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="113d5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="113d5-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="113d5-105">\<routing></span></span>  
<span data-ttu-id="113d5-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="113d5-106">\<backupLists></span></span>  
<span data-ttu-id="113d5-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="113d5-107">\<backupList></span></span>  
<span data-ttu-id="113d5-108">\<add></span><span class="sxs-lookup"><span data-stu-id="113d5-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="113d5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="113d5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="113d5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="113d5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="113d5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="113d5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="113d5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="113d5-112">Attributes</span></span>  
  
|<span data-ttu-id="113d5-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="113d5-113">Attribute</span></span>|<span data-ttu-id="113d5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="113d5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="113d5-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="113d5-115">name</span></span>|<span data-ttu-id="113d5-116">Ciąg, który określa nazwę punktu końcowego, tworzenia kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="113d5-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="113d5-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="113d5-117">Child Elements</span></span>  
 <span data-ttu-id="113d5-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="113d5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="113d5-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="113d5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="113d5-120">Element</span><span class="sxs-lookup"><span data-stu-id="113d5-120">Element</span></span>|<span data-ttu-id="113d5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="113d5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="113d5-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="113d5-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="113d5-123">Zawiera listę punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="113d5-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="113d5-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="113d5-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
