---
title: <Directives>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ec9a09e2fc03adbfcff0d7e69489e37da6e4a5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049883"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="acc41-102">\<Dyrektywy > element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="acc41-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="acc41-103">Element główny w każdym pliku dyrektywy środowiska uruchomieniowego dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="acc41-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="acc41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="acc41-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="acc41-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="acc41-105">Attributes</span></span>  
  
|<span data-ttu-id="acc41-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="acc41-106">Attribute</span></span>|<span data-ttu-id="acc41-107">Opis</span><span class="sxs-lookup"><span data-stu-id="acc41-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="acc41-108">Przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="acc41-108">The XML namespace.</span></span> <span data-ttu-id="acc41-109">Jego wartość to zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"** .</span><span class="sxs-lookup"><span data-stu-id="acc41-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="acc41-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="acc41-110">Child elements</span></span>  
  
|<span data-ttu-id="acc41-111">Element</span><span class="sxs-lookup"><span data-stu-id="acc41-111">Element</span></span>|<span data-ttu-id="acc41-112">Opis</span><span class="sxs-lookup"><span data-stu-id="acc41-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acc41-113">\<> Aplikacji</span><span class="sxs-lookup"><span data-stu-id="acc41-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="acc41-114">Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia.</span><span class="sxs-lookup"><span data-stu-id="acc41-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="acc41-115">\<> Biblioteki</span><span class="sxs-lookup"><span data-stu-id="acc41-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="acc41-116">Definiuje zestaw, którego typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="acc41-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acc41-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acc41-117">Remarks</span></span>  
 <span data-ttu-id="acc41-118">Każdy plik dyrektywy środowiska uruchomieniowego może zawierać `<Directives>` tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="acc41-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="acc41-119">Element może zawierać zero lub jeden [ \<element > aplikacji](application-element-net-native.md) oraz zero, jeden lub więcej [ \<elementów > biblioteki.](library-element-net-native.md) `<Directives>`</span><span class="sxs-lookup"><span data-stu-id="acc41-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc41-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acc41-120">See also</span></span>

- [<span data-ttu-id="acc41-121">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="acc41-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="acc41-122">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="acc41-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
