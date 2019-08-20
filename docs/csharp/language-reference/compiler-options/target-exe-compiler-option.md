---
title: '-target: exe (C# opcje kompilatora)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606454"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="bb392-102">-target: exe (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="bb392-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="bb392-103">Opcja **-target: exe** powoduje, że kompilator tworzy plik wykonywalny (exe), aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="bb392-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb392-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb392-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="bb392-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb392-105">Remarks</span></span>  
 <span data-ttu-id="bb392-106">Opcja **-target: exe** domyślnie działa.</span><span class="sxs-lookup"><span data-stu-id="bb392-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="bb392-107">Plik wykonywalny zostanie utworzony z rozszerzeniem. exe.</span><span class="sxs-lookup"><span data-stu-id="bb392-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="bb392-108">USE [-target: winexe](./target-winexe-compiler-option.md) do utworzenia pliku wykonywalnego programu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb392-108">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="bb392-109">O ile nie określono inaczej z opcją [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera metodę [Main](../../programming-guide/main-and-command-args/index.md) .</span><span class="sxs-lookup"><span data-stu-id="bb392-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="bb392-110">W przypadku określenia w wierszu polecenia wszystkie pliki do następnej lub docelowej opcji **modułu** są używane do tworzenia pliku. exe</span><span class="sxs-lookup"><span data-stu-id="bb392-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="bb392-111">Jedna i tylko jedna metoda **Main** jest wymagana w plikach kodu źródłowego, które są kompilowane w pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="bb392-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="bb392-112">[-Main —](./main-compiler-option.md) opcja kompilatora pozwala określić, która Klasa zawiera metodę **Main** , w przypadkach, gdy kod zawiera więcej niż jedną klasę za pomocą metody **Main** .</span><span class="sxs-lookup"><span data-stu-id="bb392-112">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="bb392-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb392-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="bb392-114">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="bb392-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="bb392-115">Kliknij stronę właściwości **aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="bb392-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="bb392-116">Zmodyfikuj właściwość **typu danych wyjściowych** .</span><span class="sxs-lookup"><span data-stu-id="bb392-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="bb392-117">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="bb392-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb392-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb392-118">Example</span></span>  
 <span data-ttu-id="bb392-119">Każdy z następujących wierszy poleceń zostanie skompilowany `in.cs`, tworzenie: `in.exe`</span><span class="sxs-lookup"><span data-stu-id="bb392-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb392-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb392-120">See also</span></span>

- [<span data-ttu-id="bb392-121">-Target (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="bb392-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="bb392-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="bb392-122">C# Compiler Options</span></span>](./index.md)
