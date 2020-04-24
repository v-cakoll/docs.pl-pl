---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 9a5822a097828f818da020735c3822e86eb3236b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716638"
---
# <a name="-libpath"></a><span data-ttu-id="de394-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="de394-102">-libpath</span></span>
<span data-ttu-id="de394-103">Określa lokalizację przywoływanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="de394-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de394-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de394-104">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="de394-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="de394-105">Arguments</span></span>  
  
|<span data-ttu-id="de394-106">Termin</span><span class="sxs-lookup"><span data-stu-id="de394-106">Term</span></span>|<span data-ttu-id="de394-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="de394-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="de394-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="de394-108">Required.</span></span> <span data-ttu-id="de394-109">Rozdzielana średnikami lista katalogów, które mają być używane przez kompilator, jeśli zestaw, do którego się odwoływano, nie został znaleziony w bieżącym katalogu roboczym (katalog, z którego prowadzisz kompilator) lub katalog systemowy środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="de394-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="de394-110">Jeśli nazwa katalogu zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="de394-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de394-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de394-111">Remarks</span></span>  
 <span data-ttu-id="de394-112">`-libpath` Opcja określa lokalizację zestawów, do których odwołuje się opcja [-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) .</span><span class="sxs-lookup"><span data-stu-id="de394-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="de394-113">Kompilator wyszukuje odwołania do zestawów, które nie są w pełni kwalifikowane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="de394-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="de394-114">Bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="de394-114">Current working directory.</span></span> <span data-ttu-id="de394-115">Jest to katalog, z którego wywołano kompilator.</span><span class="sxs-lookup"><span data-stu-id="de394-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="de394-116">Katalog systemowy środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="de394-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="de394-117">Katalogi określone przez `-libpath`.</span><span class="sxs-lookup"><span data-stu-id="de394-117">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="de394-118">Katalogi określone przez zmienną środowiskową LIB.</span><span class="sxs-lookup"><span data-stu-id="de394-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="de394-119">`-libpath` Opcja jest dodatkiem; określenie go więcej niż raz dołącza do dowolnych wcześniejszych wartości.</span><span class="sxs-lookup"><span data-stu-id="de394-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="de394-120">Użyj `-reference` , aby określić odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="de394-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="de394-121">Aby ustawić-LIBPATH w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="de394-121">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="de394-122">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="de394-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="de394-123">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="de394-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="de394-124">2. Kliknij kartę **odwołania** .</span><span class="sxs-lookup"><span data-stu-id="de394-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="de394-125">3. kliknij przycisk **ścieżki odwołania...** .</span><span class="sxs-lookup"><span data-stu-id="de394-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="de394-126">4. w oknie dialogowym **ścieżki odwołań** wprowadź nazwę katalogu w polu **folder:** .</span><span class="sxs-lookup"><span data-stu-id="de394-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="de394-127">5. kliknij pozycję **Dodaj folder**.</span><span class="sxs-lookup"><span data-stu-id="de394-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de394-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="de394-128">Example</span></span>  
 <span data-ttu-id="de394-129">Poniższy kod kompiluje `T2.vb` się w celu utworzenia pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="de394-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="de394-130">Kompilator przeszukuje katalog roboczy, w katalogu głównym dysku C: i w nowym katalogu zestawów dysku C: na potrzeby odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="de394-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="de394-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de394-131">See also</span></span>

- [<span data-ttu-id="de394-132">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="de394-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="de394-133">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de394-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="de394-134">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="de394-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
