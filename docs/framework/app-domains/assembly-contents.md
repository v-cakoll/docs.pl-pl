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
ms.openlocfilehash: d1334f8c8e1b5898e93697461f609429d4aae764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921703"
---
# <a name="assembly-contents"></a><span data-ttu-id="23a4b-102">Zawartość zestawu</span><span class="sxs-lookup"><span data-stu-id="23a4b-102">Assembly Contents</span></span>
<span data-ttu-id="23a4b-103">Ogólnie rzecz biorąc statyczny zestaw może składać się z czterech elementów:</span><span class="sxs-lookup"><span data-stu-id="23a4b-103">In general, a static assembly can consist of four elements:</span></span>  
  
- <span data-ttu-id="23a4b-104">[Manifest zestawu](../../../docs/framework/app-domains/assembly-manifest.md), który zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="23a4b-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
- <span data-ttu-id="23a4b-105">Metadane typu.</span><span class="sxs-lookup"><span data-stu-id="23a4b-105">Type metadata.</span></span>  
  
- <span data-ttu-id="23a4b-106">Kod języka Microsoft Intermediate Language (MSIL) firmy Microsoft, który implementuje typy.</span><span class="sxs-lookup"><span data-stu-id="23a4b-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
- <span data-ttu-id="23a4b-107">Zestaw zasobów.</span><span class="sxs-lookup"><span data-stu-id="23a4b-107">A set of resources.</span></span>  
  
 <span data-ttu-id="23a4b-108">Wymagany jest jedynie manifestu zestawu, ale aby zestaw posiadał znaczące funkcje potrzebne będą typy lub zasoby.</span><span class="sxs-lookup"><span data-stu-id="23a4b-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="23a4b-109">Istnieje kilka sposobów na grupowanie tych elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="23a4b-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="23a4b-110">Można grupować wszystkie elementy w jednym fizycznym pliku, który jest pokazany na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="23a4b-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 ![Diagram, który pokazuje jednoplikowy zestaw o nazwie Moja Assembly. dll.](./media/assembly-contents/single-file-assembly.gif)  
  
 <span data-ttu-id="23a4b-112">Alternatywnie elementy zestawu mogą być zawarte w kilku plikach.</span><span class="sxs-lookup"><span data-stu-id="23a4b-112">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="23a4b-113">Pliki te mogą być modułami skompilowanego kodu (.netmodule), zasobami (takimi jak pliki .bmp lub .jpg), lub innymi plikami wymaganymi przez tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="23a4b-113">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="23a4b-114">Należy utworzyć zestaw wieloplikowy gdy zajdzie potrzeba połączenia modułów napisanych w różnych językach oraz optymalizacji pobierania aplikacji poprzez umieszczenie rzadko używanych typów w module, który jest pobierany tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="23a4b-114">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="23a4b-115">Na poniższej ilustracji Deweloper hipotetycznej aplikacji zdecydował się oddzielić część kodu narzędziowego do innego modułu i zachować duży plik zasobów (w tym przypadku obraz .bmp) w jego oryginalnym pliku.</span><span class="sxs-lookup"><span data-stu-id="23a4b-115">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="23a4b-116">.NET Framework pobiera plik tylko wtedy, gdy istnieje do niego odwołanie; przechowywanie rzadko używanego kodu w osobnym pliku niż aplikacja optymalizuje pobieranie kodu.</span><span class="sxs-lookup"><span data-stu-id="23a4b-116">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 ![Diagram przedstawiający zestaw wieloplikowy.](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
> <span data-ttu-id="23a4b-118">Pliki z których składają się wieloplikowe zestawy nie są fizycznie połączone przez system plików.</span><span class="sxs-lookup"><span data-stu-id="23a4b-118">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="23a4b-119">Przeciwnie, są one połączone za pośrednictwem manifestu zestawu i aparatu plików wykonywalnych języka wspólnego zarządza nimi osobno.</span><span class="sxs-lookup"><span data-stu-id="23a4b-119">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="23a4b-120">Na tej ilustracji wszystkie trzy pliki należą do zestawu, zgodnie z opisem w manifeście zestawu zawartym w MyAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="23a4b-120">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="23a4b-121">Dla systemu plików są to trzy oddzielne pliki.</span><span class="sxs-lookup"><span data-stu-id="23a4b-121">To the file system, they are three separate files.</span></span> <span data-ttu-id="23a4b-122">Należy zauważyć, że plik Util.netmodule został skompilowany jako moduł, ponieważ nie zawiera żadnych informacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="23a4b-122">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="23a4b-123">Podczas tworzenia zestawu, manifest zestawu został dodany do MyAssembly.dll, wskazując na jego relację z Util.netmodule i Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="23a4b-123">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="23a4b-124">Obecnie podczas projektowania kodu źródłowego, należy podejmować jawne decyzje dotyczące partycji funkcje aplikacji w jeden lub więcej plików.</span><span class="sxs-lookup"><span data-stu-id="23a4b-124">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="23a4b-125">Podczas projektowania kodu .NET Framework, podejmiesz podobne decyzje, o tym jak podzielić funkcjonalności, tworząc jeden lub więcej zestawów.</span><span class="sxs-lookup"><span data-stu-id="23a4b-125">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a4b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23a4b-126">See also</span></span>

- [<span data-ttu-id="23a4b-127">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="23a4b-127">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="23a4b-128">Manifest zestawu</span><span class="sxs-lookup"><span data-stu-id="23a4b-128">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)
- [<span data-ttu-id="23a4b-129">Zagadnienia dotyczące zabezpieczeń zestawów</span><span class="sxs-lookup"><span data-stu-id="23a4b-129">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
