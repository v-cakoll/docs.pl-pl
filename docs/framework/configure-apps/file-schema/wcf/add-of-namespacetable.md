---
title: <add> dla <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e2a2e26099f2d31116e4a89297fc1ac984c480d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920080"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="31da1-102">\<Dodaj > \<przestrzeni nazw ></span><span class="sxs-lookup"><span data-stu-id="31da1-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="31da1-103">Reprezentuje element konfiguracji, który zawiera przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="31da1-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="31da1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="31da1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="31da1-105">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="31da1-105">\<routing></span></span>  
<span data-ttu-id="31da1-106">\<Przestrzeń nazw ></span><span class="sxs-lookup"><span data-stu-id="31da1-106">\<namespaceTable></span></span>  
<span data-ttu-id="31da1-107">\<add></span><span class="sxs-lookup"><span data-stu-id="31da1-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31da1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="31da1-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31da1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="31da1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="31da1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="31da1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31da1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="31da1-111">Attributes</span></span>  
  
|<span data-ttu-id="31da1-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="31da1-112">Attribute</span></span>|<span data-ttu-id="31da1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="31da1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31da1-114">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="31da1-114">namespace</span></span>|<span data-ttu-id="31da1-115">Ciąg zawierający przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="31da1-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="31da1-116">prefix</span><span class="sxs-lookup"><span data-stu-id="31da1-116">prefix</span></span>|<span data-ttu-id="31da1-117">Ciąg zawierający prefiks dla tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="31da1-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31da1-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="31da1-118">Child Elements</span></span>  
 <span data-ttu-id="31da1-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="31da1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31da1-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="31da1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="31da1-121">Element</span><span class="sxs-lookup"><span data-stu-id="31da1-121">Element</span></span>|<span data-ttu-id="31da1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="31da1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31da1-123">\<Przestrzeń nazw ></span><span class="sxs-lookup"><span data-stu-id="31da1-123">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="31da1-124">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="31da1-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31da1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31da1-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
