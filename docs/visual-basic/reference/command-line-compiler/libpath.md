---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4f8a87ea3f3e551dfc84212e92f1409ef61bcba2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="libpath"></a><span data-ttu-id="8ec5b-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="8ec5b-102">/libpath</span></span>
<span data-ttu-id="8ec5b-103">Określa lokalizację zestawów występujących w odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ec5b-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="8ec5b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8ec5b-105">Arguments</span></span>  
  
|<span data-ttu-id="8ec5b-106">Termin</span><span class="sxs-lookup"><span data-stu-id="8ec5b-106">Term</span></span>|<span data-ttu-id="8ec5b-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="8ec5b-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="8ec5b-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-108">Required.</span></span> <span data-ttu-id="8ec5b-109">Rozdzielana średnikami lista katalogów dla kompilatora do przeszukania Jeśli przywoływany zestaw nie znajduje się w jednym bieżący katalog roboczy (katalogu, z którego są wywoływanie kompilatora) lub środowisko uruchomieniowe języka wspólnego w katalogu systemowym.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="8ec5b-110">Jeśli nazwa katalogu zawiera spację, nazwę należy ująć w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="8ec5b-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ec5b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ec5b-111">Remarks</span></span>  
 <span data-ttu-id="8ec5b-112">`/libpath` Opcji określa lokalizację zestawów odwołuje się [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) opcji.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="8ec5b-113">Kompilator szuka odwołań do zestawu, które nie są w pełni kwalifikowana w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="8ec5b-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="8ec5b-114">Bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-114">Current working directory.</span></span> <span data-ttu-id="8ec5b-115">To jest katalog, z którego jest wywoływany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="8ec5b-116">Katalogu środowiska CLR systemu.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="8ec5b-117">Katalogi określone przez `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="8ec5b-118">Katalogi określonej przez zmienną środowiskową LIB.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="8ec5b-119">`/libpath` Jest opcja dodawania; Określanie on więcej niż raz dołącza wszystkie wcześniejsze wartości.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="8ec5b-120">Użyj `/reference` do określenia odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="8ec5b-121">Aby ustawić/libpath w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="8ec5b-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8ec5b-122">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8ec5b-123">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8ec5b-124">2.  Kliknij przycisk **odwołania** kartę.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="8ec5b-125">3.  Kliknij przycisk **ścieżek odwołania...**  przycisku.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="8ec5b-126">4.  W **ścieżek odwołania** okna dialogowego wprowadź nazwę katalogu w **Folder:** pole.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="8ec5b-127">5.  Kliknij przycisk **dodać Folder**.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8ec5b-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ec5b-128">Example</span></span>  
 <span data-ttu-id="8ec5b-129">Poniższy kod kompiluje `T2.vb` do utworzenia pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="8ec5b-130">Kompilator w katalogu roboczym, w katalogu głównym dysku C: i w katalogu zestawy nowego dysku C: szuka odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="8ec5b-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ec5b-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ec5b-131">See Also</span></span>  
 [<span data-ttu-id="8ec5b-132">Zestawy i globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="8ec5b-132">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="8ec5b-133">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ec5b-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8ec5b-134">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="8ec5b-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
