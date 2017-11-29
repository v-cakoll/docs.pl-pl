---
title: '-docelowych: exe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b66ab51b30e17ab2f34f88158c3f6095e185468d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetexe-c-compiler-options"></a><span data-ttu-id="2e0e1-102">/target:exe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2e0e1-102">/target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="2e0e1-103">**/Target: exe** opcja powoduje, że kompilator, aby utworzyć pliku wykonywalnego (EXE), aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-103">The **/target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e0e1-104">Syntax</span></span>  
  
```console  
/target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="2e0e1-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e0e1-105">Remarks</span></span>  
 <span data-ttu-id="2e0e1-106">**/Target: exe** opcja jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-106">The **/target:exe** option is in effect by default.</span></span> <span data-ttu-id="2e0e1-107">Będzie można utworzyć pliku wykonywalnego z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="2e0e1-108">Użyj [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) do utworzenia pliku wykonywalnego programu dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-108">Use [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="2e0e1-109">Chyba że określono inaczej [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-109">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="2e0e1-110">Jeśli określona w wierszu polecenia, wszystkie pliki do następnej **/out** lub **/target: module** opcji są używane do tworzenia pliku .exe</span><span class="sxs-lookup"><span data-stu-id="2e0e1-110">When specified at the command line, all files up to the next **/out** or **/target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="2e0e1-111">Jeden i tylko jeden **Main** metody jest wymagane pliki kodu źródłowego, które są łączone w pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="2e0e1-112">[/Main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) — opcja kompilatora pozwala określić, która klasa zawiera **Main** metody w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-112">The [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2e0e1-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2e0e1-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="2e0e1-114">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="2e0e1-115">Kliknij przycisk **aplikacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="2e0e1-116">Modyfikowanie **Output typu** właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="2e0e1-117">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e0e1-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e0e1-118">Example</span></span>  
 <span data-ttu-id="2e0e1-119">Każdy z następujących wierszy polecenia zostanie skompilowany `in.cs`, tworzenie `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="2e0e1-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc /target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e0e1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e0e1-120">See Also</span></span>  
 [<span data-ttu-id="2e0e1-121">/ TARGET (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2e0e1-121">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="2e0e1-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="2e0e1-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
