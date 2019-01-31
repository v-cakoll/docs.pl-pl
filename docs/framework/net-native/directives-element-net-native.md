---
title: <Directives> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14eac92a2f3e5ed5d93f4e608f7d42b13849036e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254174"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="28b6c-102">\<Dyrektywy > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="28b6c-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="28b6c-103">Element główny w każdym pliku dyrektyw środowiska uruchomieniowego dla platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28b6c-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="28b6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28b6c-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="28b6c-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28b6c-105">Attributes</span></span>  
  
|<span data-ttu-id="28b6c-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28b6c-106">Attribute</span></span>|<span data-ttu-id="28b6c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="28b6c-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="28b6c-108">Przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="28b6c-108">The XML namespace.</span></span> <span data-ttu-id="28b6c-109">Jego wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="28b6c-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="28b6c-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28b6c-110">Child elements</span></span>  
  
|<span data-ttu-id="28b6c-111">Element</span><span class="sxs-lookup"><span data-stu-id="28b6c-111">Element</span></span>|<span data-ttu-id="28b6c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="28b6c-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28b6c-113">\<Aplikacji ></span><span class="sxs-lookup"><span data-stu-id="28b6c-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="28b6c-114">Służy jako kontener dla całej aplikacji, typy i składowe typu, w których metadane są dostępne w celu odbicia.</span><span class="sxs-lookup"><span data-stu-id="28b6c-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="28b6c-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="28b6c-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="28b6c-116">Definiuje zestaw, w których typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="28b6c-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28b6c-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28b6c-117">Remarks</span></span>  
 <span data-ttu-id="28b6c-118">Każdy plik dyrektywy środowiska uruchomieniowego może zawierać tylko jeden `<Directives>` elementu.</span><span class="sxs-lookup"><span data-stu-id="28b6c-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="28b6c-119">`<Directives>` Element może zawierać zero lub jeden [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu, a wartość zero, co najmniej jeden [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="28b6c-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b6c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28b6c-120">See also</span></span>
- [<span data-ttu-id="28b6c-121">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="28b6c-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="28b6c-122">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="28b6c-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
