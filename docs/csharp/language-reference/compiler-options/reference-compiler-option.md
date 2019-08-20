---
title: -Reference (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: 247fb222eaacdb5ee60df2dded3a857f0395eb34
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606571"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="b7ccb-102">-Reference (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="b7ccb-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="b7ccb-103">Opcja **-Reference** powoduje, że kompilator importuje informacje o typie [publicznym](../keywords/public.md) w określonym pliku do bieżącego projektu, co pozwala na odwoływanie się do metadanych z określonych plików zestawów.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-103">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ccb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7ccb-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="b7ccb-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b7ccb-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="b7ccb-106">Nazwa pliku, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="b7ccb-107">Aby zaimportować więcej niż jeden plik, należy dołączyć osobną opcję **odwołania** dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="b7ccb-108">Prawidłowy C# identyfikator, który będzie reprezentować główną przestrzeń nazw, która będzie zawierać wszystkie przestrzenie nazw w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7ccb-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7ccb-109">Remarks</span></span>  
 <span data-ttu-id="b7ccb-110">Aby zaimportować z więcej niż jednego pliku, należy dołączyć opcję **-odwołanie** dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="b7ccb-111">Importowane pliki muszą zawierać manifest; plik wyjściowy musi być skompilowany za pomocą jednej z opcji [-Target](./target-compiler-option.md) [: module](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b7ccb-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="b7ccb-112">**-r** jest krótką formą **odwołania**.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="b7ccb-113">Użyj polecenia [-addmodule](./addmodule-compiler-option.md) , aby zaimportować metadane z pliku wyjściowego, który nie zawiera manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-113">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="b7ccb-114">Jeśli odwołujesz się do zestawu (zestawu A), który odwołuje się do innego zestawu (zestawu B), należy odwołać się do zestawu B, jeśli:</span><span class="sxs-lookup"><span data-stu-id="b7ccb-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="b7ccb-115">Typ używany z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="b7ccb-116">Wywołujesz pole, właściwość, zdarzenie lub metodę, która ma typ zwracany lub typ parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="b7ccb-117">Użyj [-lib](./lib-compiler-option.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-117">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="b7ccb-118">W temacie **-lib** omówiono również katalogi, w których Kompilator wyszukuje zestawy.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="b7ccb-119">Aby kompilator rozpoznawał typ w zestawie, a nie w module, należy go wymusić, aby rozpoznać typ, który można wykonać przez zdefiniowanie wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="b7ccb-120">Istnieją inne sposoby rozwiązywania nazw typów w zestawie dla kompilatora: na przykład, jeśli dziedziczysz z typu w zestawie, nazwa typu zostanie rozpoznana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="b7ccb-121">Czasami konieczne jest odwołanie się do dwóch różnych wersji tego samego składnika z jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="b7ccb-122">Aby to zrobić, użyj opcji alias w przełączniku **odwołania** dla każdego pliku, aby rozróżnić oba pliki.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="b7ccb-123">Ten alias będzie używany jako kwalifikator dla nazwy składnika i zostanie rozpoznany jako składnik w jednym z tych plików.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="b7ccb-124">Domyślnie używany jest plik odpowiedzi CSC (. RSP), który odwołuje się do najczęściej używanych zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="b7ccb-125">Użyj [-noconfig](./noconfig-compiler-option.md) , jeśli nie chcesz, aby kompilator korzystał z CSC. rsp.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-125">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7ccb-126">W programie Visual Studio Użyj okna dialogowego **Dodaj odwołanie** .</span><span class="sxs-lookup"><span data-stu-id="b7ccb-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="b7ccb-127">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań za pomocą Menedżera](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)odwołań.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="b7ccb-128">Aby zapewnić równoważne zachowanie między dodawaniem odwołań przy `-reference` użyciu i dodawaniu odwołań przy użyciu okna dialogowego **Dodaj odwołanie** , ustaw właściwość **Osadź typy** współdziałania na **wartość false** dla zestawu, który jest dodawany.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="b7ccb-129">Wartość **true** jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7ccb-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7ccb-130">Example</span></span>  
 <span data-ttu-id="b7ccb-131">Ten przykład pokazuje, jak używać funkcji [alias zewnętrzny](../keywords/extern-alias.md) .</span><span class="sxs-lookup"><span data-stu-id="b7ccb-131">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="b7ccb-132">Kompilowanie pliku źródłowego i Importowanie metadanych z `grid.dll` i `grid20.dll`, które zostały wcześniej skompilowane.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="b7ccb-133">Dwie biblioteki DLL zawierają oddzielne wersje tego samego składnika, a do kompilowania pliku źródłowego służą dwa **odwołania** z opcjami aliasów.</span><span class="sxs-lookup"><span data-stu-id="b7ccb-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="b7ccb-134">Opcje wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="b7ccb-134">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="b7ccb-135">Powoduje to skonfigurowanie aliasów `GridV1` zewnętrznych i `GridV2`, które są używane w `extern` programie, za pomocą instrukcji:</span><span class="sxs-lookup"><span data-stu-id="b7ccb-135">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="b7ccb-136">Po wykonaniu tej czynności można odwołać się do formantu siatki z `grid.dll` , tworząc prefiks `GridV1`nazwy kontrolki, tak jak to:</span><span class="sxs-lookup"><span data-stu-id="b7ccb-136">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="b7ccb-137">Ponadto można odwołać się do formantu siatki z `grid20.dll` , tworząc prefiks nazwy kontrolki w `GridV2` następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b7ccb-137">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="b7ccb-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7ccb-138">See also</span></span>

- [<span data-ttu-id="b7ccb-139">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="b7ccb-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b7ccb-140">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="b7ccb-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
