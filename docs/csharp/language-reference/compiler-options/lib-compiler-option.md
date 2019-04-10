---
title: -lib (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 49920a46f1d970c3f00025c3dc3eb384c937aa99
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319407"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="7af7e-102">-lib (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="7af7e-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="7af7e-103">**-Lib** opcja określa lokalizację zestawów, do których odwołuje się poprzez [— odwołanie (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) opcji.</span><span class="sxs-lookup"><span data-stu-id="7af7e-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7af7e-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7af7e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7af7e-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="7af7e-106">Katalog dla kompilatora do przeszukania Jeśli przywoływany zestaw nie znajduje się w bieżącym katalogu roboczym (katalog, z którego są wywołując kompilator) lub w katalogu systemu wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="7af7e-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="7af7e-107">Jeden lub więcej dodatkowych katalogów do przeszukania pod kątem odwołań do zestawów.</span><span class="sxs-lookup"><span data-stu-id="7af7e-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="7af7e-108">Rozdziel nazwy dodatkowym katalogiem, za pomocą przecinka i bez biały znak między nimi.</span><span class="sxs-lookup"><span data-stu-id="7af7e-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7af7e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7af7e-109">Remarks</span></span>  
 <span data-ttu-id="7af7e-110">Kompilator wyszukuje odwołania do zestawów, które nie są w pełni kwalifikowane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="7af7e-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="7af7e-111">Bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="7af7e-111">Current working directory.</span></span> <span data-ttu-id="7af7e-112">Jest to katalog, w którym kompilator jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="7af7e-112">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="7af7e-113">Katalogu środowiska CLR systemu.</span><span class="sxs-lookup"><span data-stu-id="7af7e-113">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="7af7e-114">Katalogi określone przez **-lib**.</span><span class="sxs-lookup"><span data-stu-id="7af7e-114">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="7af7e-115">Katalogi określone przez zmienną środowiskową LIB.</span><span class="sxs-lookup"><span data-stu-id="7af7e-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="7af7e-116">Użyj **— dokumentacja** do określenia odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="7af7e-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="7af7e-117">**-lib** dodatku; Określanie on więcej niż jeden raz dołącza do dowolnych wartości wcześniejsze.</span><span class="sxs-lookup"><span data-stu-id="7af7e-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="7af7e-118">Alternatywa dla użycia **-lib** jest skopiowanie do katalogu roboczego wszystkie wymagane zestawy; temu będzie można po prostu przekazać nazwę zestawu, aby **— dokumentacja**.</span><span class="sxs-lookup"><span data-stu-id="7af7e-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="7af7e-119">Następnie można usunąć zestawów z katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="7af7e-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="7af7e-120">Ponieważ nie określono ścieżki do zależnego zestawu w manifeście zestawu, aplikacja może zostać uruchomiona na komputerze docelowym i znajdzie i używać zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7af7e-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="7af7e-121">Ponieważ kompilator może odwoływać się do zestawu nie oznacza, że środowisko uruchomieniowe języka wspólnego będzie można znaleźć i załadować zestawu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7af7e-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="7af7e-122">Zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../framework/deployment/how-the-runtime-locates-assemblies.md) szczegółowe informacje na temat jak środowisko uruchomieniowe wyszukuje przywoływanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="7af7e-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7af7e-123">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7af7e-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7af7e-124">Otwórz projekt **stron właściwości** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7af7e-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="7af7e-125">Kliknij przycisk **ścieżka odwołań** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="7af7e-125">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="7af7e-126">Zmodyfikuj zawartość pola listy.</span><span class="sxs-lookup"><span data-stu-id="7af7e-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="7af7e-127">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="7af7e-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7af7e-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7af7e-128">Example</span></span>  
 <span data-ttu-id="7af7e-129">Skompiluj t2.cs do tworzenia pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="7af7e-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="7af7e-130">Kompilator wyszuka w katalogu roboczym i w katalogu głównym dysku c. odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="7af7e-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7af7e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7af7e-131">See also</span></span>

- [<span data-ttu-id="7af7e-132">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="7af7e-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="7af7e-133">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="7af7e-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
