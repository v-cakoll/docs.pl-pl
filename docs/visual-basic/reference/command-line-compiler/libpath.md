---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: b7bfcb0f2034145822922126fe61efea8d8ef269
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793929"
---
# <a name="-libpath"></a><span data-ttu-id="ff66b-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="ff66b-102">-libpath</span></span>
<span data-ttu-id="ff66b-103">Określa lokalizację przywoływanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="ff66b-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff66b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff66b-104">Syntax</span></span>  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff66b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ff66b-105">Arguments</span></span>  
  
|<span data-ttu-id="ff66b-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ff66b-106">Term</span></span>|<span data-ttu-id="ff66b-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ff66b-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="ff66b-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ff66b-108">Required.</span></span> <span data-ttu-id="ff66b-109">Rozdzielana średnikami lista katalogów dla kompilatora do przeszukania Jeśli przywoływany zestaw nie znajduje się w jednym bieżący katalog roboczy (katalog, z którego są wywołując kompilator) lub katalogu systemu wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ff66b-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="ff66b-110">Jeśli nazwa katalogu zawiera spację, nazwę należy ująć w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="ff66b-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff66b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff66b-111">Remarks</span></span>  
 <span data-ttu-id="ff66b-112">`-libpath` Opcja określa lokalizację zestawów odwołuje się [— dokumentacja](../../../visual-basic/reference/command-line-compiler/reference.md) opcji.</span><span class="sxs-lookup"><span data-stu-id="ff66b-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="ff66b-113">Kompilator wyszukuje odwołania do zestawów, które nie są w pełni kwalifikowane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="ff66b-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="ff66b-114">Bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="ff66b-114">Current working directory.</span></span> <span data-ttu-id="ff66b-115">Jest to katalog, w którym kompilator jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="ff66b-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="ff66b-116">Katalogu środowiska CLR systemu.</span><span class="sxs-lookup"><span data-stu-id="ff66b-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="ff66b-117">Katalogi określone przez `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="ff66b-117">Directories specified by `/libpath`.</span></span>  
  
4. <span data-ttu-id="ff66b-118">Katalogi określone przez zmienną środowiskową LIB.</span><span class="sxs-lookup"><span data-stu-id="ff66b-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="ff66b-119">`-libpath` Opcja jest dodatku; Określanie on więcej niż jeden raz dołącza do dowolnych wartości wcześniejsze.</span><span class="sxs-lookup"><span data-stu-id="ff66b-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="ff66b-120">Użyj `-reference` do określenia odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="ff66b-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="ff66b-121">Aby ustawić/libpath — w programie Visual Studio zintegrowane środowisko projektowe</span><span class="sxs-lookup"><span data-stu-id="ff66b-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ff66b-122">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ff66b-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ff66b-123">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ff66b-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ff66b-124">2.  Kliknij przycisk **odwołania** kartę.</span><span class="sxs-lookup"><span data-stu-id="ff66b-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="ff66b-125">3.  Kliknij przycisk **odwoływać się do ścieżki...**  przycisku.</span><span class="sxs-lookup"><span data-stu-id="ff66b-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="ff66b-126">4.  W **ścieżki odwołania** okna dialogowego wprowadź nazwę katalogu, w **Folder:** pole.</span><span class="sxs-lookup"><span data-stu-id="ff66b-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="ff66b-127">5.  Kliknij przycisk **Dodaj Folder**.</span><span class="sxs-lookup"><span data-stu-id="ff66b-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff66b-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff66b-128">Example</span></span>  
 <span data-ttu-id="ff66b-129">Poniższy kod kompiluje `T2.vb` do tworzenia pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="ff66b-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="ff66b-130">Kompilator w katalogu roboczym, w katalogu głównym dysku C: i w katalogu nowych zestawów na dysku C: szuka odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="ff66b-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff66b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff66b-131">See also</span></span>

- [<span data-ttu-id="ff66b-132">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="ff66b-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="ff66b-133">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff66b-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ff66b-134">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ff66b-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
