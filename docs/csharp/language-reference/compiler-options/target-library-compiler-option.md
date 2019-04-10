---
title: '-target: library (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 2e0935965e9225ab524290429803fe4c9ccc80c6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313648"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="433f6-102">-target: library (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="433f6-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="433f6-103">**-Target: library** opcji powoduje, że kompilator do tworzenia biblioteki dołączanej (dynamicznie DLL), a nie plik wykonywalny (EXE).</span><span class="sxs-lookup"><span data-stu-id="433f6-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="433f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="433f6-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="433f6-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="433f6-105">Remarks</span></span>  
 <span data-ttu-id="433f6-106">Biblioteki DLL, zostanie utworzona z rozszerzeniem dll.</span><span class="sxs-lookup"><span data-stu-id="433f6-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="433f6-107">Chyba że określono inaczej, za pomocą [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.</span><span class="sxs-lookup"><span data-stu-id="433f6-107">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="433f6-108">Po określeniu w wierszu polecenia, wszystkie pliki, aż do następnego **-out** lub **-target: module** opcji są używane do tworzenia pliku dll.</span><span class="sxs-lookup"><span data-stu-id="433f6-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="433f6-109">Podczas tworzenia pliku .dll [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metoda nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="433f6-109">When building a .dll file, a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="433f6-110">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="433f6-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="433f6-111">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="433f6-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="433f6-112">Kliknij przycisk **aplikacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="433f6-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="433f6-113">Modyfikowanie **typ danych wyjściowych** właściwości.</span><span class="sxs-lookup"><span data-stu-id="433f6-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="433f6-114">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="433f6-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="433f6-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="433f6-115">Example</span></span>  
 <span data-ttu-id="433f6-116">Skompilować `in.cs`, tworzenie `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="433f6-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="433f6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="433f6-117">See also</span></span>

- [<span data-ttu-id="433f6-118">-target (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="433f6-118">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="433f6-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="433f6-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
