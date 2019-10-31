---
title: Element <Directives> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: abe2e7221e0afb984a6178b12fabc36ea24deb35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128475"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="fef19-102">Dyrektywy \<> element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="fef19-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="fef19-103">Element główny w każdym pliku dyrektywy środowiska uruchomieniowego dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fef19-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="fef19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fef19-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="fef19-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fef19-105">Attributes</span></span>  
  
|<span data-ttu-id="fef19-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fef19-106">Attribute</span></span>|<span data-ttu-id="fef19-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fef19-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="fef19-108">Przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="fef19-108">The XML namespace.</span></span> <span data-ttu-id="fef19-109">Jego wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"** .</span><span class="sxs-lookup"><span data-stu-id="fef19-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="fef19-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fef19-110">Child elements</span></span>  
  
|<span data-ttu-id="fef19-111">Element</span><span class="sxs-lookup"><span data-stu-id="fef19-111">Element</span></span>|<span data-ttu-id="fef19-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fef19-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fef19-113">\<> aplikacji</span><span class="sxs-lookup"><span data-stu-id="fef19-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="fef19-114">Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia.</span><span class="sxs-lookup"><span data-stu-id="fef19-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="fef19-115">Biblioteka \<</span><span class="sxs-lookup"><span data-stu-id="fef19-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="fef19-116">Definiuje zestaw, którego typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fef19-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fef19-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fef19-117">Remarks</span></span>  
 <span data-ttu-id="fef19-118">Każdy plik dyrektywy środowiska uruchomieniowego może zawierać tylko jeden `<Directives>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fef19-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="fef19-119">Element `<Directives>` może zawierać zero lub jeden [\<aplikacji >](application-element-net-native.md) i zero, jeden lub więcej elementów [\<Library >](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="fef19-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef19-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fef19-120">See also</span></span>

- [<span data-ttu-id="fef19-121">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="fef19-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="fef19-122">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fef19-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
