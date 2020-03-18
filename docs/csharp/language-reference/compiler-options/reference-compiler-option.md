---
title: -reference (Opcje kompilatora C#)
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
ms.openlocfilehash: 3e6a999d528be111ba2b92886f4e6e3ebf185d5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173669"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="1817c-102">-reference (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1817c-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="1817c-103">Opcja **-reference** powoduje, że kompilator importuje informacje o typie [publicznym](../keywords/public.md) w określonym pliku do bieżącego projektu, umożliwiając w ten sposób odwoływanie się do metadanych z określonych plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="1817c-103">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1817c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1817c-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1817c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1817c-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="1817c-106">Nazwa pliku, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="1817c-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="1817c-107">Aby zaimportować więcej niż jeden plik, dołącz oddzielną opcję **-reference** dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="1817c-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="1817c-108">Prawidłowy identyfikator Języka C#, który będzie reprezentował główny obszar nazw, który będzie zawierał wszystkie obszary nazw w zestawie.</span><span class="sxs-lookup"><span data-stu-id="1817c-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1817c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1817c-109">Remarks</span></span>  
 <span data-ttu-id="1817c-110">Aby zaimportować z więcej niż jednego pliku, dołącz opcję **-reference** dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="1817c-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="1817c-111">Importowane pliki muszą zawierać manifest; plik wyjściowy musi zostać skompilowany z jedną z opcji [-target](./target-compiler-option.md) innych niż [-target:module](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1817c-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="1817c-112">**-r** jest krótką formą **-reference**.</span><span class="sxs-lookup"><span data-stu-id="1817c-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="1817c-113">Użyj [-addmodule](./addmodule-compiler-option.md) do importowania metadanych z pliku wyjściowego, który nie zawiera manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="1817c-113">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="1817c-114">W przypadku odwoływania się do złożenia (zestawu A), który odwołuje się do innego złożenia (złożenia B), należy odwołać się do zestawu B, jeśli:</span><span class="sxs-lookup"><span data-stu-id="1817c-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="1817c-115">Typ używany z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="1817c-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="1817c-116">Wywołanie pola, właściwości, zdarzenia lub metody, która ma typ zwracany lub typ parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="1817c-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="1817c-117">Użyj [-lib,](./lib-compiler-option.md) aby określić katalog, w którym znajduje się co najmniej jedno z odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="1817c-117">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="1817c-118">Temat **-lib** omawia również katalogi, w których kompilator wyszukuje zestawy.</span><span class="sxs-lookup"><span data-stu-id="1817c-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="1817c-119">Aby kompilator rozpoznał typ w zestawie, a nie w module, musi być zmuszony do rozwiązania typu, co można zrobić, definiując wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="1817c-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="1817c-120">Istnieją inne sposoby rozpoznawania nazw typów w zestawie dla kompilatora: na przykład, jeśli dziedziczysz po typie w zestawie, nazwa typu zostanie rozpoznana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="1817c-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="1817c-121">Czasami konieczne jest odwołanie się do dwóch różnych wersji tego samego komponentu z poziomu jednego złożenia.</span><span class="sxs-lookup"><span data-stu-id="1817c-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="1817c-122">Aby to zrobić, należy użyć podopcji aliasu na przełączniku **-reference** dla każdego pliku, aby odróżnić dwa pliki.</span><span class="sxs-lookup"><span data-stu-id="1817c-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="1817c-123">Ten alias będzie używany jako kwalifikator nazwy składnika i zostanie rozwiązany ze składnikiem w jednym z plików.</span><span class="sxs-lookup"><span data-stu-id="1817c-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="1817c-124">Plik odpowiedzi csc (.rsp), który odwołuje się do często używanych zestawów .NET Framework, jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="1817c-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="1817c-125">Użyj [-noconfig,](./noconfig-compiler-option.md) jeśli nie chcesz, aby kompilator używał csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="1817c-125">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1817c-126">W programie Visual Studio użyj okna dialogowego **Dodawanie odwołania.**</span><span class="sxs-lookup"><span data-stu-id="1817c-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="1817c-127">Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="1817c-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="1817c-128">Aby zapewnić równoważne zachowanie `-reference` między dodawaniem odwołań przy użyciu i dodawaniem odwołań przy użyciu okna dialogowego **Dodawanie odwołania,** ustaw właściwość **Embed Interop Types** na **False** dla zestawu, który dodajesz.</span><span class="sxs-lookup"><span data-stu-id="1817c-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="1817c-129">**Wartość True** jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="1817c-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1817c-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="1817c-130">Example</span></span>  
 <span data-ttu-id="1817c-131">W tym przykładzie pokazano, jak korzystać z funkcji [aliasu extern.](../keywords/extern-alias.md)</span><span class="sxs-lookup"><span data-stu-id="1817c-131">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="1817c-132">Skompilować plik źródłowy i `grid.dll` `grid20.dll`zaimportować metadane z i , które zostały skompilowane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="1817c-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="1817c-133">Dwa biblioteki DLL zawierają oddzielne wersje tego samego składnika i do skompilowania pliku źródłowego są używane **dwie** odwołania z opcjami aliasu.</span><span class="sxs-lookup"><span data-stu-id="1817c-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="1817c-134">Opcje wyglądają tak:</span><span class="sxs-lookup"><span data-stu-id="1817c-134">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="1817c-135">Spowoduje to skonfigurowanie aliasów `GridV1` zewnętrznych i `GridV2`, których używasz `extern` w programie za pomocą instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1817c-135">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="1817c-136">Gdy to zrobisz, można odwołać `grid.dll` się do kontroli siatki z preplikując nazwę formantu z `GridV1`, w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="1817c-136">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="1817c-137">Ponadto można odwoływać się do `grid20.dll` formantu siatki, `GridV2` poprzedzając nazwę formantu w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="1817c-137">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a><span data-ttu-id="1817c-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1817c-138">See also</span></span>

- [<span data-ttu-id="1817c-139">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="1817c-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1817c-140">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="1817c-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
