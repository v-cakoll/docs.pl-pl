---
title: '-target: winexe (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 3c16bf8aed0d281b2b5a3f9c6ae06f343b1eff7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662351"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="c3545-102">-target: winexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c3545-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="c3545-103">**-Target: winexe** opcja powoduje, że kompilator, aby utworzyć plik wykonywalny (EXE), Windows program.</span><span class="sxs-lookup"><span data-stu-id="c3545-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3545-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3545-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="c3545-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3545-105">Remarks</span></span>  
 <span data-ttu-id="c3545-106">Zostanie utworzony plik wykonywalny z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="c3545-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="c3545-107">Windows program to taki, który zapewnia interfejs użytkownika z biblioteki .NET Framework lub za pomocą interfejsów API Windows.</span><span class="sxs-lookup"><span data-stu-id="c3545-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="c3545-108">Użyj [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) do tworzenia aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="c3545-108">Use [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="c3545-109">Chyba że określono inaczej, za pomocą [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c3545-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="c3545-110">Po określeniu w wierszu polecenia, wszystkie pliki, aż do następnej **-się** lub [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcji są używane do tworzenia programu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3545-110">When specified at the command line, all files until the next **-out** or [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="c3545-111">Jeden i tylko jeden **Main** metoda jest wymagany w plikach źródłowych kodu, które są kompilowane do pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="c3545-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="c3545-112">[-Głównego](../../../csharp/language-reference/compiler-options/main-compiler-option.md) pozwala określić, która klasa zawiera **Main** metodę, w przypadkach, gdy kod ma więcej niż jednej klasy za pomocą **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="c3545-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c3545-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3545-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c3545-114">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="c3545-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="c3545-115">Kliknij przycisk **aplikacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="c3545-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="c3545-116">Modyfikowanie **typ danych wyjściowych** właściwości.</span><span class="sxs-lookup"><span data-stu-id="c3545-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="c3545-117">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3545-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3545-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3545-118">Example</span></span>  
 <span data-ttu-id="c3545-119">Skompilować `in.cs` do programu Windows:</span><span class="sxs-lookup"><span data-stu-id="c3545-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3545-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3545-120">See also</span></span>

- [<span data-ttu-id="c3545-121">-target (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c3545-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="c3545-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c3545-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
