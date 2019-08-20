---
title: '-target: module (C# opcje kompilatora)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602444"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="c6138-102">-target: module (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="c6138-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="c6138-103">Ta opcja powoduje, że kompilator nie generuje manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6138-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6138-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6138-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="c6138-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6138-105">Remarks</span></span>  
 <span data-ttu-id="c6138-106">Domyślnie plik wyjściowy utworzony przez kompilację z tą opcją będzie miał rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="c6138-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="c6138-107">Nie można załadować pliku, który nie zawiera manifestu zestawu, za pomocą środowiska uruchomieniowego języka wspólnego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6138-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="c6138-108">Jednak taki plik można włączyć do manifestu zestawu zestawu za pomocą [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c6138-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="c6138-109">W przypadku utworzenia więcej niż jednego modułu w pojedynczej kompilacji typy [wewnętrzne](../keywords/internal.md) w jednym module będą dostępne dla innych modułów w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c6138-109">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="c6138-110">Gdy kod w jednym module odwołuje `internal` się do typów w innym module, oba moduły muszą być dołączone do manifestu zestawu, za pomocą **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="c6138-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="c6138-111">Tworzenie modułu nie jest obsługiwane w środowisku deweloperskim programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6138-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="c6138-112">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="c6138-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6138-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6138-113">Example</span></span>  
 <span data-ttu-id="c6138-114">Kompiluj `in.cs`, Utwórz `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="c6138-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6138-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6138-115">See also</span></span>

- [<span data-ttu-id="c6138-116">-Target (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="c6138-116">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="c6138-117">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c6138-117">C# Compiler Options</span></span>](./index.md)
