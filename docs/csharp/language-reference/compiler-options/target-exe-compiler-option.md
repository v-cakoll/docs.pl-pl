---
title: -target:exe (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606454"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="4ccc5-102">-target:exe (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="4ccc5-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="4ccc5-103">Opcja **-target:exe** powoduje, że kompilator tworzy plik wykonywalny (EXE), aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ccc5-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ccc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ccc5-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="4ccc5-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ccc5-105">Remarks</span></span>  
 <span data-ttu-id="4ccc5-106">Opcja **-target:exe** obowiązuje domyślnie.</span><span class="sxs-lookup"><span data-stu-id="4ccc5-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="4ccc5-107">Plik wykonywalny zostanie utworzony z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="4ccc5-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="4ccc5-108">Użyj [-target:winexe,](./target-winexe-compiler-option.md) aby utworzyć plik wykonywalny programu Windows.</span><span class="sxs-lookup"><span data-stu-id="4ccc5-108">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="4ccc5-109">O ile nie określono inaczej z opcją [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [metodę Main.](../../programming-guide/main-and-command-args/index.md)</span><span class="sxs-lookup"><span data-stu-id="4ccc5-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="4ccc5-110">Po określeniu w wierszu polecenia wszystkie pliki do następnej opcji **-out** lub **-target:module** są używane do tworzenia pliku exe</span><span class="sxs-lookup"><span data-stu-id="4ccc5-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="4ccc5-111">Jedna i tylko jedna **metoda główna** jest wymagana w plikach kodu źródłowego, które są kompilowane do pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="4ccc5-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="4ccc5-112">[Opcja -main](./main-compiler-option.md) kompilator pozwala określić, która klasa zawiera **Main** metody, w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="4ccc5-112">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4ccc5-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ccc5-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="4ccc5-114">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="4ccc5-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="4ccc5-115">Kliknij stronę **właściwości Application.**</span><span class="sxs-lookup"><span data-stu-id="4ccc5-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="4ccc5-116">Zmodyfikuj właściwość **Output type.**</span><span class="sxs-lookup"><span data-stu-id="4ccc5-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="4ccc5-117">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="4ccc5-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ccc5-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ccc5-118">Example</span></span>  
 <span data-ttu-id="4ccc5-119">Każdy z następujących wierszy `in.cs`polecenia `in.exe`skompiluje , tworząc:</span><span class="sxs-lookup"><span data-stu-id="4ccc5-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ccc5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ccc5-120">See also</span></span>

- [<span data-ttu-id="4ccc5-121">-target (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="4ccc5-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="4ccc5-122">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="4ccc5-122">C# Compiler Options</span></span>](./index.md)
