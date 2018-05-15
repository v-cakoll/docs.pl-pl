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
ms.openlocfilehash: 7db975909f498a0b84e7405a12a8f8ec1e2dd34b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="986fa-102">-lib (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="986fa-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="986fa-103">**-Lib** opcji określa lokalizację zestawy, do których odwołuje się za pomocą klasy [— odwołanie (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) opcji.</span><span class="sxs-lookup"><span data-stu-id="986fa-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="986fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="986fa-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="986fa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="986fa-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="986fa-106">Katalog dla kompilatora do przeszukania Jeśli przywoływany zestaw nie znajduje się w bieżący katalog roboczy (katalogu, z którego są wywoływanie kompilatora) lub w katalogu systemowym środowisko uruchomieniowe języka wspólnego firmy.</span><span class="sxs-lookup"><span data-stu-id="986fa-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="986fa-107">Jeden lub więcej dodatkowych katalogów do przeszukania pod kątem odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="986fa-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="986fa-108">Nazwy katalogów dodatkowe przecinkami i bez biały znak między nimi.</span><span class="sxs-lookup"><span data-stu-id="986fa-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="986fa-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="986fa-109">Remarks</span></span>  
 <span data-ttu-id="986fa-110">Kompilator szuka odwołań do zestawu, które nie są w pełni kwalifikowana w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="986fa-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="986fa-111">Bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="986fa-111">Current working directory.</span></span> <span data-ttu-id="986fa-112">To jest katalog, z którego jest wywoływany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="986fa-112">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="986fa-113">Katalogu środowiska CLR systemu.</span><span class="sxs-lookup"><span data-stu-id="986fa-113">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="986fa-114">Katalogi określone przez **-lib**.</span><span class="sxs-lookup"><span data-stu-id="986fa-114">Directories specified by **-lib**.</span></span>  
  
4.  <span data-ttu-id="986fa-115">Katalogi określonej przez zmienną środowiskową LIB.</span><span class="sxs-lookup"><span data-stu-id="986fa-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="986fa-116">Użyj **— odwołanie** do określenia odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="986fa-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="986fa-117">**-lib** dodatku; Określanie on więcej niż raz dołącza wszystkie wcześniejsze wartości.</span><span class="sxs-lookup"><span data-stu-id="986fa-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="986fa-118">Zamiast **-lib** ma na celu kopiowanie do katalogu roboczego wszystkie wymagane zestawy; ta umożliwia po prostu przekaż nazwę zestawu **— odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="986fa-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="986fa-119">Następnie można usunąć zestawów z katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="986fa-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="986fa-120">Ponieważ ścieżka do zestawu zależnego nie jest określona w manifeście zestawu, aplikacja może zostać uruchomiona na komputerze docelowym i Znajdź i użyć zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="986fa-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="986fa-121">Ponieważ kompilator może odwoływać się do zestawu nie oznacza, że środowisko uruchomieniowe języka wspólnego będzie mógł odnaleźć i załadować zestawu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="986fa-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="986fa-122">Zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../framework/deployment/how-the-runtime-locates-assemblies.md) szczegółowe informacje na temat jak wyszukuje środowiska uruchomieniowego dla zestawów występujących w odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="986fa-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="986fa-123">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="986fa-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="986fa-124">Otwórz projekt **strony właściwości** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="986fa-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2.  <span data-ttu-id="986fa-125">Kliknij przycisk **ścieżkę odwołania** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="986fa-125">Click the **References Path** property page.</span></span>  
  
3.  <span data-ttu-id="986fa-126">Zmodyfikuj zawartość pola listy.</span><span class="sxs-lookup"><span data-stu-id="986fa-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="986fa-127">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="986fa-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="986fa-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="986fa-128">Example</span></span>  
 <span data-ttu-id="986fa-129">Kompiluj t2.cs do utworzenia pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="986fa-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="986fa-130">Kompilator będzie szukać w katalogu roboczego i w katalogu głównym dysku c. odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="986fa-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="986fa-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="986fa-131">See Also</span></span>  
 [<span data-ttu-id="986fa-132">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="986fa-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="986fa-133">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="986fa-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
