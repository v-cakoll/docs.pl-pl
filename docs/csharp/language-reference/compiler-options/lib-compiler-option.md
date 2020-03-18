---
title: -lib (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606821"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="7daa3-102">-lib (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="7daa3-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="7daa3-103">Opcja **-lib** określa lokalizację zestawów, do których odwołuje się opcja [-reference (C# Compiler Options).](./reference-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="7daa3-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](./reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7daa3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7daa3-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7daa3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7daa3-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="7daa3-106">Katalog kompilatora, aby sprawdzić, czy nie można znaleźć zestawu, do którego istnieje odwołanie, w bieżącym katalogu roboczym (katalogu, z którego wywołujesz kompilator) lub w katalogu systemowym programu w czasie wykonywania języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="7daa3-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="7daa3-107">Co najmniej jeden dodatkowe katalogi do wyszukiwania w poszukiwaniu odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="7daa3-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="7daa3-108">Oddziel dodatkowe nazwy katalogów przecinkiem i bez odstępu między nimi.</span><span class="sxs-lookup"><span data-stu-id="7daa3-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7daa3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7daa3-109">Remarks</span></span>  
 <span data-ttu-id="7daa3-110">Kompilator wyszukuje odwołania do zestawu, które nie są w pełni kwalifikowane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="7daa3-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="7daa3-111">Bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="7daa3-111">Current working directory.</span></span> <span data-ttu-id="7daa3-112">Jest to katalog, z którego jest wywoływany kompilator.</span><span class="sxs-lookup"><span data-stu-id="7daa3-112">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="7daa3-113">Katalog systemu wykonywania języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="7daa3-113">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="7daa3-114">Katalogi określone przez **-lib**.</span><span class="sxs-lookup"><span data-stu-id="7daa3-114">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="7daa3-115">Katalogi określone przez zmienną środowiskową LIB.</span><span class="sxs-lookup"><span data-stu-id="7daa3-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="7daa3-116">Użyj **-reference,** aby określić odwołanie do złożenia.</span><span class="sxs-lookup"><span data-stu-id="7daa3-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="7daa3-117">**-lib** jest addytywny; określając go więcej niż jeden raz dołącza do wszelkich wcześniejszych wartości.</span><span class="sxs-lookup"><span data-stu-id="7daa3-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="7daa3-118">Alternatywą dla używania **-lib** jest skopiowanie do katalogu roboczego wymaganych zestawów; pozwoli to po prostu przekazać nazwę zestawu do **-reference**.</span><span class="sxs-lookup"><span data-stu-id="7daa3-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="7daa3-119">Następnie można usunąć zestawy z katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="7daa3-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="7daa3-120">Ponieważ ścieżka do zestawu zależnego nie jest określona w manifeście zestawu, aplikację można uruchomić na komputerze docelowym i znajdzie i użyje zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="7daa3-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="7daa3-121">Ponieważ kompilator może odwoływać się do zestawu nie oznacza, że czas wykonywania języka wspólnego będzie mógł znaleźć i załadować zestaw w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7daa3-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="7daa3-122">Zobacz [Jak runtime lokalizuje zestawy,](../../../framework/deployment/how-the-runtime-locates-assemblies.md) aby uzyskać szczegółowe informacje na temat wyszukiwania w czasie wykonywania dla zestawów, do których istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7daa3-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7daa3-123">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7daa3-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7daa3-124">Otwieranie okna dialogowego **Strony właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="7daa3-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="7daa3-125">Kliknij stronę właściwości **Ścieżka odwołania.**</span><span class="sxs-lookup"><span data-stu-id="7daa3-125">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="7daa3-126">Zmodyfikuj zawartość pola listy.</span><span class="sxs-lookup"><span data-stu-id="7daa3-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="7daa3-127">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="7daa3-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7daa3-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7daa3-128">Example</span></span>  
 <span data-ttu-id="7daa3-129">Skompiluj t2.cs, aby utworzyć plik exe.</span><span class="sxs-lookup"><span data-stu-id="7daa3-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="7daa3-130">Kompilator będzie wyglądał w katalogu roboczym i w katalogu głównym dysku C dla odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="7daa3-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7daa3-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7daa3-131">See also</span></span>

- [<span data-ttu-id="7daa3-132">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="7daa3-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7daa3-133">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="7daa3-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
