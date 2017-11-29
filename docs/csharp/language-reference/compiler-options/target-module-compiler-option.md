---
title: '-docelowych: module (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2b54ea9085ecc23d4a535d440d0634c997f22615
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetmodule-c-compiler-options"></a><span data-ttu-id="caa29-102">/target:module (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="caa29-102">/target:module (C# Compiler Options)</span></span>
<span data-ttu-id="caa29-103">Ta opcja powoduje, że kompilator nie Generuj manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="caa29-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="caa29-104">Syntax</span></span>  
  
```console  
/target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="caa29-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="caa29-105">Remarks</span></span>  
 <span data-ttu-id="caa29-106">Domyślnie plik danych wyjściowych, utworzone przez kompilowania przy użyciu tej opcji będzie miał rozszerzenie modułu .netmodule.</span><span class="sxs-lookup"><span data-stu-id="caa29-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="caa29-107">Nie można załadować pliku, który nie ma manifestu zestawu przez .NET Framework środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="caa29-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="caa29-108">Jednak taki plik można uwzględnić w manifeście zestawu zestawu za pomocą klasy [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="caa29-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="caa29-109">Jeśli więcej niż jeden moduł jest tworzony w jednej kompilacji, [wewnętrzny](../../../csharp/language-reference/keywords/internal.md) typów w jeden moduł będzie dostępna dla innych modułów w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="caa29-109">If more than one module is created in a single compilation, [internal](../../../csharp/language-reference/keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="caa29-110">Gdy kod w odwołaniach do modułów `internal` typów w innym module, a następnie obu modułów musi być włączona do manifestu zestawu za pomocą klasy **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="caa29-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **/addmodule**.</span></span>  
  
 <span data-ttu-id="caa29-111">Tworzenie modułu nie jest obsługiwane w środowisku projektowym Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="caa29-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="caa29-112">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="caa29-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caa29-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="caa29-113">Example</span></span>  
 <span data-ttu-id="caa29-114">Kompiluj `in.cs`, tworzenie `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="caa29-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc /target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="caa29-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="caa29-115">See Also</span></span>  
 [<span data-ttu-id="caa29-116">/ TARGET (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="caa29-116">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="caa29-117">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="caa29-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
