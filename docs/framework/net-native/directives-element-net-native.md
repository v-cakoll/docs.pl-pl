---
title: <Directives> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cfc9dc5c8122f9b1b1696cedcd5d9a8ceead403
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868591"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="dfe12-102">\<Dyrektywy > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="dfe12-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="dfe12-103">Element główny w każdym pliku dyrektyw środowiska uruchomieniowego dla platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dfe12-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="dfe12-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfe12-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="dfe12-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dfe12-105">Attributes</span></span>  
  
|<span data-ttu-id="dfe12-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dfe12-106">Attribute</span></span>|<span data-ttu-id="dfe12-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dfe12-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="dfe12-108">Przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="dfe12-108">The XML namespace.</span></span> <span data-ttu-id="dfe12-109">Jego wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="dfe12-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="dfe12-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dfe12-110">Child elements</span></span>  
  
|<span data-ttu-id="dfe12-111">Element</span><span class="sxs-lookup"><span data-stu-id="dfe12-111">Element</span></span>|<span data-ttu-id="dfe12-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dfe12-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfe12-113">\<Aplikacji ></span><span class="sxs-lookup"><span data-stu-id="dfe12-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="dfe12-114">Służy jako kontener dla całej aplikacji, typy i składowe typu, w których metadane są dostępne w celu odbicia.</span><span class="sxs-lookup"><span data-stu-id="dfe12-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="dfe12-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="dfe12-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="dfe12-116">Definiuje zestaw, w których typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dfe12-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfe12-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfe12-117">Remarks</span></span>  
 <span data-ttu-id="dfe12-118">Każdy plik dyrektywy środowiska uruchomieniowego może zawierać tylko jeden `<Directives>` elementu.</span><span class="sxs-lookup"><span data-stu-id="dfe12-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="dfe12-119">`<Directives>` Element może zawierać zero lub jeden [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu, a wartość zero, co najmniej jeden [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="dfe12-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe12-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfe12-120">See also</span></span>

- [<span data-ttu-id="dfe12-121">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="dfe12-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="dfe12-122">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="dfe12-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
