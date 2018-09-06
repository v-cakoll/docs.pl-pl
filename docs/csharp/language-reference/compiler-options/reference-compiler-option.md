---
title: — Odwołanie (opcje kompilatora C#)
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
ms.openlocfilehash: 76a53d6adcf4c55faa57c25f851e46dd4c2c6c22
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788139"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="1d6a3-102">— Odwołanie (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1d6a3-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="1d6a3-103">**— Dokumentacja** opcja powoduje, że kompilator, aby zaimportować [publicznych](../../../csharp/language-reference/keywords/public.md) wpisz informacje w określonym pliku do bieżącego projektu, dzięki czemu można odwoływać się do metadanych z określonych plików zestawów.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-103">The **-reference** option causes the compiler to import [public](../../../csharp/language-reference/keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d6a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d6a3-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d6a3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1d6a3-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="1d6a3-106">Nazwa pliku, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="1d6a3-107">Aby zaimportować więcej niż jeden plik, należy dołączyć oddzielnego **— dokumentacja** opcji dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="1d6a3-108">Prawidłowe identyfikatorem języka C#, która będzie reprezentować głównej przestrzeni nazw, który będzie zawierać wszystkie przestrzenie nazw w zestawie.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d6a3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d6a3-109">Remarks</span></span>  
 <span data-ttu-id="1d6a3-110">Aby zaimportować z więcej niż jeden plik, należy dołączyć **— dokumentacja** opcji dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="1d6a3-111">Pliki, które należy zaimportować musi zawierać manifest; Plik wyjściowy muszą być skompilowane przy użyciu jednego z [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcji innych niż [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1d6a3-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="1d6a3-112">**-r** jest krótka forma **— dokumentacja**.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="1d6a3-113">Użyj [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) Importowanie metadanych z pliku wyjściowego, który nie zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-113">Use [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="1d6a3-114">Jeśli odwołujesz się zestaw (Assembly A), który odwołuje się do innego zestawu (Assembly B), konieczne będzie odwołanie do zestawu B jeśli:</span><span class="sxs-lookup"><span data-stu-id="1d6a3-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="1d6a3-115">Typ używanej z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="1d6a3-116">Wywołuje się, pola, właściwości, zdarzenia lub metody, która ma typ zwracany lub typu parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="1d6a3-117">Użyj [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) określić katalog, w którym znajduje się co najmniej jeden z odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-117">Use [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="1d6a3-118">**-Lib** temacie omówiono również katalogi, w których kompilator wyszukuje zestawy.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="1d6a3-119">Kompilator rozpoznaje typu w zestawie, a nie w module, potrzebny zmuszeni do rozpoznania typu, co można zrobić, określając wystąpienie tego typu.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="1d6a3-120">Istnieją inne sposoby, aby rozwiązać nazwy typów w zestawie dla kompilatora: na przykład, jeśli możesz dziedziczyć z typu w zestawie, nazwa typu zostanie następnie być rozpoznawane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="1d6a3-121">Czasami zachodzi konieczność odwoływać się do dwóch różnych wersji jednego składnika, z poziomu jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="1d6a3-122">Aby to zrobić, należy użyć alias suboption na **— dokumentacja** przełącznika dla każdego pliku w celu rozróżnienia między dwoma plikami.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="1d6a3-123">Ten alias będzie służyć jako kwalifikator nazwy składnika i zostanie rozwiązany do składnika w jeden z plików.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="1d6a3-124">Csc pliku odpowiedzi (rsp), która odwołuje się do powszechnie stosowane zestawów .NET Framework, jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="1d6a3-125">Użyj [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) , jeśli nie chcesz, aby kompilator korzystać csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-125">Use [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d6a3-126">W programie Visual Studio, należy użyć **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="1d6a3-127">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="1d6a3-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="1d6a3-128">Aby zapewnić zachowanie równoważne między dodawaniem odwołań za pomocą `-reference` i dodawaniem odwołań za pomocą **Dodaj odwołanie** okno dialogowe, zestaw **Osadź typy współdziałania** właściwość **False** dla zestawu, który dodajesz.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="1d6a3-129">**Wartość true,** jest wartością domyślną dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d6a3-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d6a3-130">Example</span></span>  
 <span data-ttu-id="1d6a3-131">W tym przykładzie pokazano, jak używać [alias zewnętrzny](../../../csharp/language-reference/keywords/extern-alias.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-131">This example shows how to use the [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="1d6a3-132">Kompilowanie pliku źródłowego i zaimportować metadane z `grid.dll` i `grid20.dll`, które zostały skompilowane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`,which have been compiled previously.</span></span> <span data-ttu-id="1d6a3-133">Dwa pliki dll zawiera różne wersje tego samego składnika, a następnie użyj dwóch **— dokumentacja** przy użyciu opcji alias do kompilowania pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1d6a3-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="1d6a3-134">Opcje wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="1d6a3-134">The options look like this:</span></span>  
  
 <span data-ttu-id="1d6a3-135">-reference:GridV1=grid.dll i - reference:GridV2=grid20.dll</span><span class="sxs-lookup"><span data-stu-id="1d6a3-135">-reference:GridV1=grid.dll and -reference:GridV2=grid20.dll</span></span>  
  
 <span data-ttu-id="1d6a3-136">Powoduje to skonfigurowanie aliasów zewnętrznych "GridV1" i "GridV2" używane w programach za pomocą instrukcji zewnętrzny:</span><span class="sxs-lookup"><span data-stu-id="1d6a3-136">This sets up the external aliases "GridV1" and "GridV2," which you use in your program by means of an extern statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="1d6a3-137">Po zakończeniu tej operacji może dotyczyć formant siatki z grid.dll przez dodanie przedrostka nazwę formantu GridV1, następująco:</span><span class="sxs-lookup"><span data-stu-id="1d6a3-137">Once this is done, you can refer to the grid control from grid.dll by prefixing the control name with GridV1, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="1d6a3-138">Ponadto można skorzystać na formancie siatki z grid20.dll przez dodanie przedrostka nazwę formantu GridV2 następująco:</span><span class="sxs-lookup"><span data-stu-id="1d6a3-138">In addition, you can refer to the grid control from grid20.dll by prefixing the control name with GridV2 like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="1d6a3-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d6a3-139">See Also</span></span>  

- [<span data-ttu-id="1d6a3-140">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="1d6a3-140">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="1d6a3-141">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="1d6a3-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
