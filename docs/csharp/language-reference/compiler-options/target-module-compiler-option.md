---
title: '-target: module (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 7cc0e48a7a4a3ec3f28c89e80fadf6aa7e1130f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393129"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="63cb3-102">-target: module (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="63cb3-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="63cb3-103">Ta opcja powoduje, że kompilator generuje manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="63cb3-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63cb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63cb3-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="63cb3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63cb3-105">Remarks</span></span>  
 <span data-ttu-id="63cb3-106">Domyślnie plik wyjściowy, utworzone przez kompilowanie przy użyciu tej opcji będzie mieć rozszerzenie .netmodule.</span><span class="sxs-lookup"><span data-stu-id="63cb3-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="63cb3-107">Nie można załadować pliku, który nie ma w manifeście zestawu przez .NET Framework środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="63cb3-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="63cb3-108">Jednak taki plik, należy włączyć do manifestu zestawu zestawu poprzez [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="63cb3-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="63cb3-109">Jeśli więcej niż jeden moduł jest tworzona w jednej kompilacji, [wewnętrzny](../../../csharp/language-reference/keywords/internal.md) typów w jednym module będzie dostępny dla innych modułów w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="63cb3-109">If more than one module is created in a single compilation, [internal](../../../csharp/language-reference/keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="63cb3-110">Gdy kod w odwołaniach do modułów jeden `internal` typów w innym module, a następnie obu modułów musi być włączona do manifestu zestawu przez **- addmodule —**.</span><span class="sxs-lookup"><span data-stu-id="63cb3-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="63cb3-111">Tworzenie modułu nie jest obsługiwane w środowisku programowania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63cb3-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="63cb3-112">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="63cb3-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63cb3-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="63cb3-113">Example</span></span>  
 <span data-ttu-id="63cb3-114">Skompilować `in.cs`, tworzenie `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="63cb3-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="63cb3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63cb3-115">See Also</span></span>  

- [<span data-ttu-id="63cb3-116">-target (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="63cb3-116">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="63cb3-117">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="63cb3-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
