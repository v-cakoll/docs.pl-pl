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
ms.openlocfilehash: f77137e3cc2f734435d3b1d391a303fcd3e16332
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520279"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="3493e-102">-target: winexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="3493e-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="3493e-103">**-Target: winexe** opcja powoduje, że kompilator, aby utworzyć plik wykonywalny (EXE), Windows program.</span><span class="sxs-lookup"><span data-stu-id="3493e-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3493e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3493e-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="3493e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3493e-105">Remarks</span></span>  
 <span data-ttu-id="3493e-106">Zostanie utworzony plik wykonywalny z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="3493e-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="3493e-107">Windows program to taki, który zapewnia interfejs użytkownika z biblioteki .NET Framework lub za pomocą interfejsów API systemu Win32.</span><span class="sxs-lookup"><span data-stu-id="3493e-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="3493e-108">Użyj [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) do tworzenia aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="3493e-108">Use [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="3493e-109">Chyba że określono inaczej, za pomocą [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3493e-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="3493e-110">Po określeniu w wierszu polecenia, wszystkie pliki, aż do następnej **-się** lub [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcji są używane do tworzenia programu Windows.</span><span class="sxs-lookup"><span data-stu-id="3493e-110">When specified at the command line, all files until the next **-out** or [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="3493e-111">Jeden i tylko jeden **Main** metoda jest wymagany w plikach źródłowych kodu, które są kompilowane do pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="3493e-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="3493e-112">[-Głównego](../../../csharp/language-reference/compiler-options/main-compiler-option.md) pozwala określić, która klasa zawiera **Main** metodę, w przypadkach, gdy kod ma więcej niż jednej klasy za pomocą **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="3493e-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3493e-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3493e-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3493e-114">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="3493e-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="3493e-115">Kliknij przycisk **aplikacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="3493e-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="3493e-116">Modyfikowanie **typ danych wyjściowych** właściwości.</span><span class="sxs-lookup"><span data-stu-id="3493e-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="3493e-117">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="3493e-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3493e-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3493e-118">Example</span></span>  
 <span data-ttu-id="3493e-119">Skompilować `in.cs` do programu Windows:</span><span class="sxs-lookup"><span data-stu-id="3493e-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3493e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3493e-120">See Also</span></span>  

- [<span data-ttu-id="3493e-121">-target (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="3493e-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="3493e-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="3493e-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
