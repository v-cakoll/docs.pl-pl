---
title: '-docelowych: exe (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 194e4f7efaebd9523791090bcab09c019f8554a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218832"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="5feca-102">-docelowych: exe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="5feca-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="5feca-103">**-Docelowych: exe** opcja powoduje, że kompilator, aby utworzyć pliku wykonywalnego (EXE), aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="5feca-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5feca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5feca-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="5feca-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5feca-105">Remarks</span></span>  
 <span data-ttu-id="5feca-106">**-Docelowych: exe** opcja jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5feca-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="5feca-107">Będzie można utworzyć pliku wykonywalnego z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="5feca-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="5feca-108">Użyj [-docelowych: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) do utworzenia pliku wykonywalnego programu dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5feca-108">Use [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="5feca-109">Chyba że określono inaczej [— limit](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5feca-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="5feca-110">Kiedy określona w wierszu polecenia, wszystkie pliki do następnej **-out** lub **-docelowych: moduł** opcji są używane do tworzenia pliku .exe</span><span class="sxs-lookup"><span data-stu-id="5feca-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="5feca-111">Jeden i tylko jeden **Main** metody jest wymagane pliki kodu źródłowego, które są łączone w pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="5feca-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="5feca-112">[— Głównego](../../../csharp/language-reference/compiler-options/main-compiler-option.md) — opcja kompilatora pozwala określić, która klasa zawiera **Main** metody w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="5feca-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5feca-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5feca-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="5feca-114">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="5feca-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="5feca-115">Kliknij przycisk **aplikacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="5feca-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="5feca-116">Modyfikowanie **Output typu** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5feca-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="5feca-117">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="5feca-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5feca-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5feca-118">Example</span></span>  
 <span data-ttu-id="5feca-119">Każdy z następujących wierszy polecenia zostanie skompilowany `in.cs`, tworzenie `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="5feca-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5feca-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5feca-120">See Also</span></span>  
 [<span data-ttu-id="5feca-121">-docelowego (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="5feca-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="5feca-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="5feca-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
