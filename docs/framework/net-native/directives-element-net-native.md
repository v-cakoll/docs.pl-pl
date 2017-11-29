---
title: Element &lt;Directives&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a55048ea5b2889da82b10ac2a51865d945635143
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="5ef20-102">Element &lt;Directives&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="5ef20-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="5ef20-103">W każdym pliku dyrektyw środowiska uruchomieniowego dla elementu głównego [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ef20-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="5ef20-104">**\<Dyrektywy xmlns = "http://schemas.microsoft.com/netfx/2013/01/metadata" >**</span><span class="sxs-lookup"><span data-stu-id="5ef20-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef20-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ef20-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="5ef20-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ef20-106">Attributes</span></span>  
  
|<span data-ttu-id="5ef20-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ef20-107">Attribute</span></span>|<span data-ttu-id="5ef20-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5ef20-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="5ef20-109">Przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="5ef20-109">The XML namespace.</span></span> <span data-ttu-id="5ef20-110">Wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="5ef20-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="5ef20-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5ef20-111">Child elements</span></span>  
  
|<span data-ttu-id="5ef20-112">Element</span><span class="sxs-lookup"><span data-stu-id="5ef20-112">Element</span></span>|<span data-ttu-id="5ef20-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5ef20-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ef20-114">\<Aplikacji ></span><span class="sxs-lookup"><span data-stu-id="5ef20-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="5ef20-115">Służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia.</span><span class="sxs-lookup"><span data-stu-id="5ef20-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="5ef20-116">\<Biblioteka ></span><span class="sxs-lookup"><span data-stu-id="5ef20-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="5ef20-117">Definiuje zestaw, których typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5ef20-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ef20-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ef20-118">Remarks</span></span>  
 <span data-ttu-id="5ef20-119">Każdy plik dyrektyw środowiska uruchomieniowego może zawierać tylko jeden `<Directives>` elementu.</span><span class="sxs-lookup"><span data-stu-id="5ef20-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="5ef20-120">`<Directives>` Element może zawierać zero lub jeden [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu, a wartość zero, co najmniej jeden [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="5ef20-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef20-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ef20-121">See Also</span></span>  
 [<span data-ttu-id="5ef20-122">Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="5ef20-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="5ef20-123">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5ef20-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
