---
title: <add> dla <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850396"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="9b6a8-102">\<add> dla \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="9b6a8-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="9b6a8-103">Reprezentuje element konfiguracji, który zawiera przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="9b6a8-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="9b6a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b6a8-104">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b6a8-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9b6a8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9b6a8-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9b6a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b6a8-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9b6a8-107">Attributes</span></span>  
  
|<span data-ttu-id="9b6a8-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9b6a8-108">Attribute</span></span>|<span data-ttu-id="9b6a8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9b6a8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9b6a8-110">namespace</span><span class="sxs-lookup"><span data-stu-id="9b6a8-110">namespace</span></span>|<span data-ttu-id="9b6a8-111">Ciąg zawierający przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="9b6a8-111">A string containing the namespace.</span></span>|  
|<span data-ttu-id="9b6a8-112">prefiks</span><span class="sxs-lookup"><span data-stu-id="9b6a8-112">prefix</span></span>|<span data-ttu-id="9b6a8-113">Ciąg zawierający prefiks dla tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9b6a8-113">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b6a8-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9b6a8-114">Child Elements</span></span>  
 <span data-ttu-id="9b6a8-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="9b6a8-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b6a8-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9b6a8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9b6a8-117">Element</span><span class="sxs-lookup"><span data-stu-id="9b6a8-117">Element</span></span>|<span data-ttu-id="9b6a8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9b6a8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="9b6a8-119">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="9b6a8-119">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b6a8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b6a8-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
