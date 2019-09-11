---
title: <add> dla <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850396"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="c7e0c-102">\<Dodaj > \<przestrzeni nazw ></span><span class="sxs-lookup"><span data-stu-id="c7e0c-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="c7e0c-103">Reprezentuje element konfiguracji, który zawiera przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
<span data-ttu-id="c7e0c-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c7e0c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c7e0c-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c7e0c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c7e0c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="c7e0c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="c7e0c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Przestrzeń nazw >** ](namespacetable.md)</span><span class="sxs-lookup"><span data-stu-id="c7e0c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)</span></span>\
<span data-ttu-id="c7e0c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="c7e0c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e0c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7e0c-109">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7e0c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c7e0c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c7e0c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7e0c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c7e0c-112">Attributes</span></span>  
  
|<span data-ttu-id="c7e0c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c7e0c-113">Attribute</span></span>|<span data-ttu-id="c7e0c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c7e0c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c7e0c-115">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c7e0c-115">namespace</span></span>|<span data-ttu-id="c7e0c-116">Ciąg zawierający przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-116">A string containing the namespace.</span></span>|  
|<span data-ttu-id="c7e0c-117">prefix</span><span class="sxs-lookup"><span data-stu-id="c7e0c-117">prefix</span></span>|<span data-ttu-id="c7e0c-118">Ciąg zawierający prefiks dla tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-118">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7e0c-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c7e0c-119">Child Elements</span></span>  
 <span data-ttu-id="c7e0c-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7e0c-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c7e0c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c7e0c-122">Element</span><span class="sxs-lookup"><span data-stu-id="c7e0c-122">Element</span></span>|<span data-ttu-id="c7e0c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c7e0c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7e0c-124">\<Przestrzeń nazw ></span><span class="sxs-lookup"><span data-stu-id="c7e0c-124">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="c7e0c-125">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-125">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7e0c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7e0c-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
