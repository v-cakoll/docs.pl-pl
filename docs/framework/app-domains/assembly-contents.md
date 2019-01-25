---
title: Zawartość zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27bbc1b382d962379a50fba4557e3f2a408d9bc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649170"
---
# <a name="assembly-contents"></a><span data-ttu-id="123ca-102">Zawartość zestawu</span><span class="sxs-lookup"><span data-stu-id="123ca-102">Assembly Contents</span></span>
<span data-ttu-id="123ca-103">Ogólnie rzecz biorąc statyczny zestaw może składać się z czterech elementów:</span><span class="sxs-lookup"><span data-stu-id="123ca-103">In general, a static assembly can consist of four elements:</span></span>  
  
-   <span data-ttu-id="123ca-104">[Manifestu zestawu](../../../docs/framework/app-domains/assembly-manifest.md), który zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="123ca-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
-   <span data-ttu-id="123ca-105">Metadane typu.</span><span class="sxs-lookup"><span data-stu-id="123ca-105">Type metadata.</span></span>  
  
-   <span data-ttu-id="123ca-106">Kod języka Microsoft Intermediate Language (MSIL) firmy Microsoft, który implementuje typy.</span><span class="sxs-lookup"><span data-stu-id="123ca-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
-   <span data-ttu-id="123ca-107">Zestaw zasobów.</span><span class="sxs-lookup"><span data-stu-id="123ca-107">A set of resources.</span></span>  
  
 <span data-ttu-id="123ca-108">Wymagany jest jedynie manifestu zestawu, ale aby zestaw posiadał znaczące funkcje potrzebne będą typy lub zasoby.</span><span class="sxs-lookup"><span data-stu-id="123ca-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="123ca-109">Istnieje kilka sposobów na grupowanie tych elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="123ca-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="123ca-110">Można grupować wszystkie elementy w jednym fizycznym pliku, który jest pokazany na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="123ca-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 <span data-ttu-id="123ca-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span><span class="sxs-lookup"><span data-stu-id="123ca-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span></span>  
<span data-ttu-id="123ca-112">Zestaw jednoplikowy</span><span class="sxs-lookup"><span data-stu-id="123ca-112">Single-file assembly</span></span>  
  
 <span data-ttu-id="123ca-113">Alternatywnie elementy zestawu mogą być zawarte w kilku plikach.</span><span class="sxs-lookup"><span data-stu-id="123ca-113">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="123ca-114">Pliki te mogą być modułami skompilowanego kodu (.netmodule), zasobami (takimi jak pliki .bmp lub .jpg), lub innymi plikami wymaganymi przez tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="123ca-114">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="123ca-115">Należy utworzyć zestaw wieloplikowy gdy zajdzie potrzeba połączenia modułów napisanych w różnych językach oraz optymalizacji pobierania aplikacji poprzez umieszczenie rzadko używanych typów w module, który jest pobierany tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="123ca-115">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="123ca-116">Na poniższej ilustracji Deweloper hipotetycznej aplikacji zdecydował się oddzielić część kodu narzędziowego do innego modułu i zachować duży plik zasobów (w tym przypadku obraz .bmp) w jego oryginalnym pliku.</span><span class="sxs-lookup"><span data-stu-id="123ca-116">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="123ca-117">.NET Framework pobiera plik tylko wtedy, gdy istnieje do niego odwołanie; przechowywanie rzadko używanego kodu w osobnym pliku niż aplikacja optymalizuje pobieranie kodu.</span><span class="sxs-lookup"><span data-stu-id="123ca-117">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 <span data-ttu-id="123ca-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span><span class="sxs-lookup"><span data-stu-id="123ca-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span></span>  
<span data-ttu-id="123ca-119">Zestaw wieloplikowy</span><span class="sxs-lookup"><span data-stu-id="123ca-119">Multifile assembly</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="123ca-120">Pliki z których składają się wieloplikowe zestawy nie są fizycznie połączone przez system plików.</span><span class="sxs-lookup"><span data-stu-id="123ca-120">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="123ca-121">Przeciwnie, są one połączone za pośrednictwem manifestu zestawu i aparatu plików wykonywalnych języka wspólnego zarządza nimi osobno.</span><span class="sxs-lookup"><span data-stu-id="123ca-121">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="123ca-122">Na tej ilustracji wszystkie trzy pliki należą do zestawu, zgodnie z opisem w manifeście zestawu zawartym w MyAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="123ca-122">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="123ca-123">Dla systemu plików są to trzy oddzielne pliki.</span><span class="sxs-lookup"><span data-stu-id="123ca-123">To the file system, they are three separate files.</span></span> <span data-ttu-id="123ca-124">Należy zauważyć, że plik Util.netmodule został skompilowany jako moduł, ponieważ nie zawiera żadnych informacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="123ca-124">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="123ca-125">Podczas tworzenia zestawu, manifest zestawu został dodany do MyAssembly.dll, wskazując na jego relację z Util.netmodule i Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="123ca-125">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="123ca-126">Obecnie podczas projektowania kodu źródłowego, należy podejmować jawne decyzje dotyczące partycji funkcje aplikacji w jeden lub więcej plików.</span><span class="sxs-lookup"><span data-stu-id="123ca-126">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="123ca-127">Podczas projektowania kodu .NET Framework, podejmiesz podobne decyzje, o tym jak podzielić funkcjonalności, tworząc jeden lub więcej zestawów.</span><span class="sxs-lookup"><span data-stu-id="123ca-127">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="123ca-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="123ca-128">See also</span></span>
- [<span data-ttu-id="123ca-129">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="123ca-129">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="123ca-130">Manifest zestawu</span><span class="sxs-lookup"><span data-stu-id="123ca-130">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)
- [<span data-ttu-id="123ca-131">Zagadnienia dotyczące zabezpieczeń zestawów</span><span class="sxs-lookup"><span data-stu-id="123ca-131">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
