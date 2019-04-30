---
title: <add> dla <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e65b66170465a8b3bb60754feebb7730b959d9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673670"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="fc08a-102">\<Dodaj > z \<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="fc08a-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="fc08a-103">Reprezentuje element konfiguracji, który zawiera przestrzeń nazw jako przedrostkowe mapowanie, które następnie mogą być używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="fc08a-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="fc08a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fc08a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fc08a-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="fc08a-105">\<routing></span></span>  
<span data-ttu-id="fc08a-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="fc08a-106">\<namespaceTable></span></span>  
<span data-ttu-id="fc08a-107">\<add></span><span class="sxs-lookup"><span data-stu-id="fc08a-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc08a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc08a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc08a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fc08a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fc08a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fc08a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc08a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fc08a-111">Attributes</span></span>  
  
|<span data-ttu-id="fc08a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fc08a-112">Attribute</span></span>|<span data-ttu-id="fc08a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fc08a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc08a-114">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fc08a-114">namespace</span></span>|<span data-ttu-id="fc08a-115">Ciąg zawierający przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="fc08a-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="fc08a-116">Prefiks</span><span class="sxs-lookup"><span data-stu-id="fc08a-116">prefix</span></span>|<span data-ttu-id="fc08a-117">Ciąg zawierający prefiks dla tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fc08a-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc08a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fc08a-118">Child Elements</span></span>  
 <span data-ttu-id="fc08a-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="fc08a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc08a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fc08a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fc08a-121">Element</span><span class="sxs-lookup"><span data-stu-id="fc08a-121">Element</span></span>|<span data-ttu-id="fc08a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fc08a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc08a-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="fc08a-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="fc08a-124">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które następnie mogą być używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="fc08a-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc08a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc08a-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
