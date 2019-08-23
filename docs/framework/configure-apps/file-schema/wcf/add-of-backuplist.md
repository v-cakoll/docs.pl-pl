---
title: <add> dla <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: c590dbd671807b32e08ad5d871d376a0dc51e611
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926878"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="4e2f4-102">\<Dodawanie > \<backupList ></span><span class="sxs-lookup"><span data-stu-id="4e2f4-102">\<add> of \<backupList></span></span>
<span data-ttu-id="4e2f4-103">Reprezentuje element konfiguracji, który definiuje kopię zapasową elementu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4e2f4-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="4e2f4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4e2f4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4e2f4-105">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="4e2f4-105">\<routing></span></span>  
<span data-ttu-id="4e2f4-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="4e2f4-106">\<backupLists></span></span>  
<span data-ttu-id="4e2f4-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="4e2f4-107">\<backupList></span></span>  
<span data-ttu-id="4e2f4-108">\<add></span><span class="sxs-lookup"><span data-stu-id="4e2f4-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e2f4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e2f4-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e2f4-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e2f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4e2f4-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e2f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e2f4-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e2f4-112">Attributes</span></span>  
  
|<span data-ttu-id="4e2f4-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4e2f4-113">Attribute</span></span>|<span data-ttu-id="4e2f4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4e2f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e2f4-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="4e2f4-115">name</span></span>|<span data-ttu-id="4e2f4-116">Ciąg określający nazwę punktu końcowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="4e2f4-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e2f4-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e2f4-117">Child Elements</span></span>  
 <span data-ttu-id="4e2f4-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="4e2f4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e2f4-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e2f4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4e2f4-120">Element</span><span class="sxs-lookup"><span data-stu-id="4e2f4-120">Element</span></span>|<span data-ttu-id="4e2f4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4e2f4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e2f4-122">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="4e2f4-122">\<routing></span></span>](routing.md)|<span data-ttu-id="4e2f4-123">Zawiera listę punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="4e2f4-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e2f4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e2f4-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
