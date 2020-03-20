---
title: <Directives>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181044"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="9347e-102">\<Dyrektywy> element (.NET native)</span><span class="sxs-lookup"><span data-stu-id="9347e-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="9347e-103">Element główny w każdym pliku dyrektyw środowiska wykonawczego dla platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9347e-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="9347e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9347e-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="9347e-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9347e-105">Attributes</span></span>  
  
|<span data-ttu-id="9347e-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9347e-106">Attribute</span></span>|<span data-ttu-id="9347e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9347e-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="9347e-108">Obszar nazw XML.</span><span class="sxs-lookup"><span data-stu-id="9347e-108">The XML namespace.</span></span> <span data-ttu-id="9347e-109">Jego wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="9347e-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="9347e-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9347e-110">Child elements</span></span>  
  
|<span data-ttu-id="9347e-111">Element</span><span class="sxs-lookup"><span data-stu-id="9347e-111">Element</span></span>|<span data-ttu-id="9347e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9347e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9347e-113">\<>aplikacji</span><span class="sxs-lookup"><span data-stu-id="9347e-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="9347e-114">Służy jako kontener dla typów całej aplikacji i członków typu, których metadane są dostępne do odbicia.</span><span class="sxs-lookup"><span data-stu-id="9347e-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="9347e-115">\<>biblioteczna</span><span class="sxs-lookup"><span data-stu-id="9347e-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="9347e-116">Definiuje zestaw, którego typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9347e-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9347e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9347e-117">Remarks</span></span>  
 <span data-ttu-id="9347e-118">Każdy plik dyrektyw środowiska wykonawczego `<Directives>` może zawierać tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="9347e-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="9347e-119">Element `<Directives>` może zawierać zero [ \<](application-element-net-native.md) lub jeden element>aplikacji i zero, jeden lub więcej [ \<elementów>biblioteki.](library-element-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="9347e-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9347e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9347e-120">See also</span></span>

- [<span data-ttu-id="9347e-121">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9347e-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9347e-122">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9347e-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
