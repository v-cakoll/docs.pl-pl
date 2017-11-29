---
title: '-docelowych: library (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66e2edd86dc4a1302b23dab07226a5d56cb79b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetlibrary-c-compiler-options"></a><span data-ttu-id="f4c5b-102">/target:library (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="f4c5b-102">/target:library (C# Compiler Options)</span></span>
<span data-ttu-id="f4c5b-103">**/Target: Library** opcja powoduje, że kompilator, aby utworzyć biblioteki dołączanej (dynamicznie DLL) zamiast pliku wykonywalnego (EXE).</span><span class="sxs-lookup"><span data-stu-id="f4c5b-103">The **/target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4c5b-104">Syntax</span></span>  
  
```console  
/target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="f4c5b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4c5b-105">Remarks</span></span>  
 <span data-ttu-id="f4c5b-106">Plik DLL, który zostanie utworzony z rozszerzeniem dll.</span><span class="sxs-lookup"><span data-stu-id="f4c5b-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="f4c5b-107">Jeżeli nie określono inaczej z [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.</span><span class="sxs-lookup"><span data-stu-id="f4c5b-107">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="f4c5b-108">Jeśli określona w wierszu polecenia, wszystkie pliki do następnej **/out** lub **/target: module** opcji są używane do tworzenia pliku dll.</span><span class="sxs-lookup"><span data-stu-id="f4c5b-108">When specified at the command line, all files up to the next **/out** or **/target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="f4c5b-109">Podczas tworzenia pliku .dll [Main](../../../csharp/programming-guide/main-and-command-args/index.md) — metoda nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="f4c5b-109">When building a .dll file, a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f4c5b-110">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f4c5b-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="f4c5b-111">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="f4c5b-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="f4c5b-112">Kliknij przycisk **aplikacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4c5b-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="f4c5b-113">Modyfikowanie **Output typu** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4c5b-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="f4c5b-114">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4c5b-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4c5b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4c5b-115">Example</span></span>  
 <span data-ttu-id="f4c5b-116">Kompiluj `in.cs`, tworzenie `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="f4c5b-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc /target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4c5b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4c5b-117">See Also</span></span>  
 [<span data-ttu-id="f4c5b-118">/ TARGET (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="f4c5b-118">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="f4c5b-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="f4c5b-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
