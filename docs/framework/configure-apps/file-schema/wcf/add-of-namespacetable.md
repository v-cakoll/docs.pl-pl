---
title: '&lt;add&gt; w &lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394657abcebb42192fb7a8b57b0402bcacf37693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="39fa4-102">&lt;add&gt; w &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="39fa4-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="39fa4-103">Reprezentuje element konfiguracji, który zawiera przestrzeń nazw jako przedrostkowe mapowanie, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="39fa4-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="39fa4-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="39fa4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="39fa4-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="39fa4-105">\<routing></span></span>  
<span data-ttu-id="39fa4-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="39fa4-106">\<namespaceTable></span></span>  
<span data-ttu-id="39fa4-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="39fa4-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39fa4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="39fa4-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39fa4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39fa4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="39fa4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39fa4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39fa4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39fa4-111">Attributes</span></span>  
  
|<span data-ttu-id="39fa4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39fa4-112">Attribute</span></span>|<span data-ttu-id="39fa4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="39fa4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39fa4-114">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="39fa4-114">namespace</span></span>|<span data-ttu-id="39fa4-115">Ciąg zawierający przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="39fa4-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="39fa4-116">Prefiks</span><span class="sxs-lookup"><span data-stu-id="39fa4-116">prefix</span></span>|<span data-ttu-id="39fa4-117">Ciąg zawierający prefiks dla tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="39fa4-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39fa4-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39fa4-118">Child Elements</span></span>  
 <span data-ttu-id="39fa4-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="39fa4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39fa4-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39fa4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="39fa4-121">Element</span><span class="sxs-lookup"><span data-stu-id="39fa4-121">Element</span></span>|<span data-ttu-id="39fa4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="39fa4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39fa4-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="39fa4-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="39fa4-124">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="39fa4-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39fa4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39fa4-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
