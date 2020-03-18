---
title: -target:module (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602444"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="10955-102">-target:module (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="10955-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="10955-103">Ta opcja powoduje, że kompilator nie generuje manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="10955-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10955-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10955-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="10955-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10955-105">Remarks</span></span>  
 <span data-ttu-id="10955-106">Domyślnie plik wyjściowy utworzony przez kompilację z tą opcją będzie miał rozszerzenie .netmodule.</span><span class="sxs-lookup"><span data-stu-id="10955-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="10955-107">Nie można załadować pliku, który nie ma manifestu zestawu, przez czas uruchomieniowy wspólnego języka .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10955-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="10955-108">Jednak taki plik może być włączony do manifestu zestawu za pomocą [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="10955-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="10955-109">Jeśli więcej niż jeden moduł jest tworzony w jednej kompilacji, typy [wewnętrzne](../keywords/internal.md) w jednym module będą dostępne dla innych modułów w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="10955-109">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="10955-110">Gdy kod w `internal` jednym module odwołuje się do typów w innym module, oba moduły muszą być włączone do manifestu zestawu za pomocą **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="10955-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="10955-111">Tworzenie modułu nie jest obsługiwane w środowisku programistycznym programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10955-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="10955-112">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="10955-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10955-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="10955-113">Example</span></span>  
 <span data-ttu-id="10955-114">`in.cs`Kompiluj `in.netmodule`, tworząc:</span><span class="sxs-lookup"><span data-stu-id="10955-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="10955-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10955-115">See also</span></span>

- [<span data-ttu-id="10955-116">-target (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="10955-116">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="10955-117">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="10955-117">C# Compiler Options</span></span>](./index.md)
