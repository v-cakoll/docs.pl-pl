---
title: -addmodule (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970187"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="a86bb-102">-addmodule (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="a86bb-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="a86bb-103">Ta opcja dodaje moduł, który został utworzony za pomocą elementu docelowego: przełączenie modułu do bieżącej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a86bb-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a86bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a86bb-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a86bb-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a86bb-105">Arguments</span></span>  
 <span data-ttu-id="a86bb-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="a86bb-106">`file`, `file2`</span></span>  
 <span data-ttu-id="a86bb-107">Plik wyjściowy zawierający metadane.</span><span class="sxs-lookup"><span data-stu-id="a86bb-107">An output file that contains metadata.</span></span> <span data-ttu-id="a86bb-108">Plik nie może zawierać manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="a86bb-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="a86bb-109">Aby zaimportować więcej niż jeden plik, oddziel nazwy plików przecinkami lub średnikami.</span><span class="sxs-lookup"><span data-stu-id="a86bb-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a86bb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a86bb-110">Remarks</span></span>  
 <span data-ttu-id="a86bb-111">Wszystkie moduły dodane za pomocą polecenia **-addmodule** muszą znajdować się w tym samym katalogu co plik wyjściowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a86bb-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="a86bb-112">Oznacza to, że można określić moduł w dowolnym katalogu w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a86bb-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="a86bb-113">Jeśli moduł nie znajduje się w katalogu aplikacji w czasie wykonywania, <xref:System.TypeLoadException>otrzymasz.</span><span class="sxs-lookup"><span data-stu-id="a86bb-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="a86bb-114">`file`nie może zawierać zestawu.</span><span class="sxs-lookup"><span data-stu-id="a86bb-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="a86bb-115">Na przykład jeśli plik wyjściowy został utworzony za pomocą [elementu-target: module](./target-module-compiler-option.md), jego metadane można zaimportować za pomocą polecenia **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="a86bb-115">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="a86bb-116">Jeśli plik wyjściowy został utworzony z opcją **-Target** inną niż **-target: module**, nie można zaimportować jej metadanych przy użyciu parametru **-addmodule** , ale można go zaimportować z [-Reference](./reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a86bb-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a86bb-117">Ta opcja kompilatora jest niedostępna w programie Visual Studio; projekt nie może odwoływać się do modułu.</span><span class="sxs-lookup"><span data-stu-id="a86bb-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="a86bb-118">Ponadto nie można programowo zmienić tej opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a86bb-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a86bb-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a86bb-119">Example</span></span>  
 <span data-ttu-id="a86bb-120">Kompiluj plik `input.cs` źródłowy i Dodaj metadane z `metad1.netmodule` i `metad2.netmodule` do produkcji `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="a86bb-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a86bb-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a86bb-121">See also</span></span>

- [<span data-ttu-id="a86bb-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a86bb-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a86bb-123">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a86bb-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="a86bb-124">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="a86bb-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="a86bb-125">Instrukcje: Kompilowanie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="a86bb-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
