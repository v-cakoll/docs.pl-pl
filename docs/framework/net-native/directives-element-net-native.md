---
title: Element &lt;Directives&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd571255f924c9f3878c00a2bc01397d63e6d777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394449"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="8e58d-102">Element &lt;Directives&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="8e58d-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="8e58d-103">W każdym pliku dyrektyw środowiska uruchomieniowego dla elementu głównego [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e58d-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="8e58d-104">**\<Dyrektywy xmlns = "http://schemas.microsoft.com/netfx/2013/01/metadata" >**</span><span class="sxs-lookup"><span data-stu-id="8e58d-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e58d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e58d-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="8e58d-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8e58d-106">Attributes</span></span>  
  
|<span data-ttu-id="8e58d-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8e58d-107">Attribute</span></span>|<span data-ttu-id="8e58d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="8e58d-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="8e58d-109">Przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="8e58d-109">The XML namespace.</span></span> <span data-ttu-id="8e58d-110">Wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="8e58d-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="8e58d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8e58d-111">Child elements</span></span>  
  
|<span data-ttu-id="8e58d-112">Element</span><span class="sxs-lookup"><span data-stu-id="8e58d-112">Element</span></span>|<span data-ttu-id="8e58d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8e58d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e58d-114">\<Aplikacji ></span><span class="sxs-lookup"><span data-stu-id="8e58d-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="8e58d-115">Służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia.</span><span class="sxs-lookup"><span data-stu-id="8e58d-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="8e58d-116">\<Biblioteka ></span><span class="sxs-lookup"><span data-stu-id="8e58d-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="8e58d-117">Definiuje zestaw, których typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8e58d-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e58d-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e58d-118">Remarks</span></span>  
 <span data-ttu-id="8e58d-119">Każdy plik dyrektyw środowiska uruchomieniowego może zawierać tylko jeden `<Directives>` elementu.</span><span class="sxs-lookup"><span data-stu-id="8e58d-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="8e58d-120">`<Directives>` Element może zawierać zero lub jeden [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu, a wartość zero, co najmniej jeden [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="8e58d-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e58d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e58d-121">See Also</span></span>  
 [<span data-ttu-id="8e58d-122">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8e58d-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="8e58d-123">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8e58d-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
