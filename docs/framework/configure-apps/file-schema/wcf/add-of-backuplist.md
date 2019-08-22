---
title: <add> dla <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 53af01a519c244376b262db1f6515a438dcc554f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663372"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="05c1c-102">\<Dodawanie > \<backupList ></span><span class="sxs-lookup"><span data-stu-id="05c1c-102">\<add> of \<backupList></span></span>
<span data-ttu-id="05c1c-103">Reprezentuje element konfiguracji, który definiuje kopię zapasową elementu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="05c1c-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="05c1c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="05c1c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="05c1c-105">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="05c1c-105">\<routing></span></span>  
<span data-ttu-id="05c1c-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="05c1c-106">\<backupLists></span></span>  
<span data-ttu-id="05c1c-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="05c1c-107">\<backupList></span></span>  
<span data-ttu-id="05c1c-108">\<add></span><span class="sxs-lookup"><span data-stu-id="05c1c-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c1c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="05c1c-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05c1c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05c1c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="05c1c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05c1c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05c1c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05c1c-112">Attributes</span></span>  
  
|<span data-ttu-id="05c1c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05c1c-113">Attribute</span></span>|<span data-ttu-id="05c1c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="05c1c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05c1c-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="05c1c-115">name</span></span>|<span data-ttu-id="05c1c-116">Ciąg określający nazwę punktu końcowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="05c1c-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05c1c-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05c1c-117">Child Elements</span></span>  
 <span data-ttu-id="05c1c-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="05c1c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05c1c-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05c1c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="05c1c-120">Element</span><span class="sxs-lookup"><span data-stu-id="05c1c-120">Element</span></span>|<span data-ttu-id="05c1c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="05c1c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05c1c-122">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="05c1c-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="05c1c-123">Zawiera listę punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="05c1c-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05c1c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05c1c-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
