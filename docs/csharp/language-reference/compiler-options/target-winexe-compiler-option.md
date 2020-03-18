---
title: -target:winexe (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606378"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="2f882-102">-target:winexe (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2f882-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="2f882-103">Opcja **-target:winexe** powoduje, że kompilator tworzy plik wykonywalny (EXE), program Windows.</span><span class="sxs-lookup"><span data-stu-id="2f882-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f882-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f882-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="2f882-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f882-105">Remarks</span></span>  
 <span data-ttu-id="2f882-106">Plik wykonywalny zostanie utworzony z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="2f882-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="2f882-107">Program systemu Windows to taki, który zapewnia interfejs użytkownika z biblioteki .NET Framework lub interfejsów API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2f882-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="2f882-108">Użyj [-target:exe,](./target-exe-compiler-option.md) aby utworzyć aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="2f882-108">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="2f882-109">O ile nie określono inaczej z opcją [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [metodę Main.](../../programming-guide/main-and-command-args/index.md)</span><span class="sxs-lookup"><span data-stu-id="2f882-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="2f882-110">Po określeniu w wierszu polecenia wszystkie pliki do następnej opcji **-out** lub [-target](./target-compiler-option.md) są używane do tworzenia programu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2f882-110">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="2f882-111">Jedna i tylko jedna **metoda główna** jest wymagana w plikach kodu źródłowego, które są kompilowane do pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="2f882-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="2f882-112">Opcja [-main](./main-compiler-option.md) umożliwia określenie, która klasa zawiera **Main,** w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="2f882-112">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2f882-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2f882-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="2f882-114">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="2f882-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="2f882-115">Kliknij stronę **właściwości Application.**</span><span class="sxs-lookup"><span data-stu-id="2f882-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="2f882-116">Zmodyfikuj właściwość **Output type.**</span><span class="sxs-lookup"><span data-stu-id="2f882-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="2f882-117">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="2f882-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f882-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f882-118">Example</span></span>  
 <span data-ttu-id="2f882-119">Skompiluj `in.cs` w programie windowsowym:</span><span class="sxs-lookup"><span data-stu-id="2f882-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f882-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f882-120">See also</span></span>

- [<span data-ttu-id="2f882-121">-target (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2f882-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="2f882-122">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="2f882-122">C# Compiler Options</span></span>](./index.md)
