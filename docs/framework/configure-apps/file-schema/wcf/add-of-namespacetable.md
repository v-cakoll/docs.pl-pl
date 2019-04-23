---
title: <add> dla <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e65b66170465a8b3bb60754feebb7730b959d9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089721"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="b9d5d-102">\<Dodaj > z \<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="b9d5d-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="b9d5d-103">Reprezentuje element konfiguracji, który zawiera przestrzeń nazw jako przedrostkowe mapowanie, które następnie mogą być używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="b9d5d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b9d5d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b9d5d-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="b9d5d-105">\<routing></span></span>  
<span data-ttu-id="b9d5d-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="b9d5d-106">\<namespaceTable></span></span>  
<span data-ttu-id="b9d5d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="b9d5d-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d5d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9d5d-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9d5d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b9d5d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b9d5d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9d5d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b9d5d-111">Attributes</span></span>  
  
|<span data-ttu-id="b9d5d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b9d5d-112">Attribute</span></span>|<span data-ttu-id="b9d5d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b9d5d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9d5d-114">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b9d5d-114">namespace</span></span>|<span data-ttu-id="b9d5d-115">Ciąg zawierający przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="b9d5d-116">Prefiks</span><span class="sxs-lookup"><span data-stu-id="b9d5d-116">prefix</span></span>|<span data-ttu-id="b9d5d-117">Ciąg zawierający prefiks dla tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9d5d-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b9d5d-118">Child Elements</span></span>  
 <span data-ttu-id="b9d5d-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9d5d-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b9d5d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b9d5d-121">Element</span><span class="sxs-lookup"><span data-stu-id="b9d5d-121">Element</span></span>|<span data-ttu-id="b9d5d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b9d5d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9d5d-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="b9d5d-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="b9d5d-124">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które następnie mogą być używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9d5d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9d5d-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
