---
title: '&lt;add&gt; w &lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 1d3b61fa6653b3910e65b95fa96fd0657e72bf7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632913"
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="0635a-102">&lt;add&gt; w &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="0635a-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="0635a-103">Reprezentuje element konfiguracji, który zawiera przestrzeń nazw jako przedrostkowe mapowanie, które następnie mogą być używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="0635a-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="0635a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0635a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0635a-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="0635a-105">\<routing></span></span>  
<span data-ttu-id="0635a-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="0635a-106">\<namespaceTable></span></span>  
<span data-ttu-id="0635a-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0635a-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0635a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="0635a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0635a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0635a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0635a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0635a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0635a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0635a-111">Attributes</span></span>  
  
|<span data-ttu-id="0635a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0635a-112">Attribute</span></span>|<span data-ttu-id="0635a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0635a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0635a-114">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="0635a-114">namespace</span></span>|<span data-ttu-id="0635a-115">Ciąg zawierający przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="0635a-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="0635a-116">Prefiks</span><span class="sxs-lookup"><span data-stu-id="0635a-116">prefix</span></span>|<span data-ttu-id="0635a-117">Ciąg zawierający prefiks dla tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0635a-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0635a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0635a-118">Child Elements</span></span>  
 <span data-ttu-id="0635a-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="0635a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0635a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0635a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0635a-121">Element</span><span class="sxs-lookup"><span data-stu-id="0635a-121">Element</span></span>|<span data-ttu-id="0635a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0635a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0635a-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="0635a-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="0635a-124">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które następnie mogą być używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="0635a-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0635a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0635a-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
