---
title: '-docelowych: module (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: d02a46390ca34b8063320df6ec237a00c0423c88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="5a5db-102">-docelowych: module (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="5a5db-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="5a5db-103">Ta opcja powoduje, że kompilator nie Generuj manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="5a5db-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a5db-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a5db-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a5db-105">Remarks</span></span>  
 <span data-ttu-id="5a5db-106">Domyślnie plik danych wyjściowych, utworzone przez kompilowania przy użyciu tej opcji będzie miał rozszerzenie modułu .netmodule.</span><span class="sxs-lookup"><span data-stu-id="5a5db-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="5a5db-107">Nie można załadować pliku, który nie ma manifestu zestawu przez .NET Framework środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="5a5db-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="5a5db-108">Jednak taki plik można uwzględnić w manifeście zestawu zestawu za pomocą klasy [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5a5db-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="5a5db-109">Jeśli więcej niż jeden moduł jest tworzony w jednej kompilacji, [wewnętrzny](../../../csharp/language-reference/keywords/internal.md) typów w jeden moduł będzie dostępna dla innych modułów w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5a5db-109">If more than one module is created in a single compilation, [internal](../../../csharp/language-reference/keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="5a5db-110">Gdy kod w odwołaniach do modułów `internal` typów w innym module, a następnie obu modułów musi być włączona do manifestu zestawu za pomocą klasy **- addmodule**.</span><span class="sxs-lookup"><span data-stu-id="5a5db-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="5a5db-111">Tworzenie modułu nie jest obsługiwane w środowisku projektowym Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a5db-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="5a5db-112">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a5db-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5db-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a5db-113">Example</span></span>  
 <span data-ttu-id="5a5db-114">Kompiluj `in.cs`, tworzenie `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="5a5db-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a5db-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a5db-115">See Also</span></span>  
 [<span data-ttu-id="5a5db-116">-docelowego (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="5a5db-116">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="5a5db-117">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="5a5db-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
