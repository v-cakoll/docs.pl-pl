---
title: Element &lt;Directives&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8921d2841f9a7b4228ae3b8735d7047453f71bcb
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525649"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="c37f6-102">Element &lt;Directives&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="c37f6-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="c37f6-103">Element główny w każdym pliku dyrektyw środowiska uruchomieniowego dla platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c37f6-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="c37f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c37f6-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="c37f6-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c37f6-105">Attributes</span></span>  
  
|<span data-ttu-id="c37f6-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c37f6-106">Attribute</span></span>|<span data-ttu-id="c37f6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c37f6-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="c37f6-108">Przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="c37f6-108">The XML namespace.</span></span> <span data-ttu-id="c37f6-109">Jego wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="c37f6-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="c37f6-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c37f6-110">Child elements</span></span>  
  
|<span data-ttu-id="c37f6-111">Element</span><span class="sxs-lookup"><span data-stu-id="c37f6-111">Element</span></span>|<span data-ttu-id="c37f6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c37f6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c37f6-113">\<Aplikacji ></span><span class="sxs-lookup"><span data-stu-id="c37f6-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="c37f6-114">Służy jako kontener dla całej aplikacji, typy i składowe typu, w których metadane są dostępne w celu odbicia.</span><span class="sxs-lookup"><span data-stu-id="c37f6-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="c37f6-115">\<Biblioteki ></span><span class="sxs-lookup"><span data-stu-id="c37f6-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="c37f6-116">Definiuje zestaw, w których typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c37f6-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c37f6-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c37f6-117">Remarks</span></span>  
 <span data-ttu-id="c37f6-118">Każdy plik dyrektywy środowiska uruchomieniowego może zawierać tylko jeden `<Directives>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c37f6-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="c37f6-119">`<Directives>` Element może zawierać zero lub jeden [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu, a wartość zero, co najmniej jeden [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="c37f6-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37f6-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c37f6-120">See Also</span></span>  
 [<span data-ttu-id="c37f6-121">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="c37f6-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="c37f6-122">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c37f6-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
