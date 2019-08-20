---
title: '-target: winexe (C# opcje kompilatora)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606378"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="2ee9f-102">-target: winexe (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="2ee9f-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="2ee9f-103">Opcja **-target: winexe** powoduje, że kompilator tworzy plik wykonywalny (exe), program systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2ee9f-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ee9f-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="2ee9f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ee9f-105">Remarks</span></span>  
 <span data-ttu-id="2ee9f-106">Plik wykonywalny zostanie utworzony z rozszerzeniem. exe.</span><span class="sxs-lookup"><span data-stu-id="2ee9f-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="2ee9f-107">Program systemu Windows to taki, który udostępnia interfejs użytkownika z biblioteki .NET Framework lub interfejsów API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2ee9f-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="2ee9f-108">Użyj [-target: exe](./target-exe-compiler-option.md) , aby utworzyć aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="2ee9f-108">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="2ee9f-109">O ile nie określono inaczej z opcją [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera metodę [Main](../../programming-guide/main-and-command-args/index.md) .</span><span class="sxs-lookup"><span data-stu-id="2ee9f-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="2ee9f-110">Gdy jest określony w wierszu polecenia, wszystkie pliki do momentu użycia opcji Dalej lub [-Target](./target-compiler-option.md) są używane do tworzenia programu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2ee9f-110">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="2ee9f-111">Jedna i tylko jedna metoda **Main** jest wymagana w plikach kodu źródłowego, które są kompilowane w pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="2ee9f-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="2ee9f-112">Opcja [-Main](./main-compiler-option.md) pozwala określić, która Klasa zawiera metodę **Main** , w przypadkach, gdy kod zawiera więcej niż jedną klasę przy użyciu metody **Main** .</span><span class="sxs-lookup"><span data-stu-id="2ee9f-112">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2ee9f-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ee9f-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="2ee9f-114">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="2ee9f-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="2ee9f-115">Kliknij stronę właściwości **aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="2ee9f-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="2ee9f-116">Zmodyfikuj właściwość **typu danych wyjściowych** .</span><span class="sxs-lookup"><span data-stu-id="2ee9f-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="2ee9f-117">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="2ee9f-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ee9f-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ee9f-118">Example</span></span>  
 <span data-ttu-id="2ee9f-119">Kompiluj `in.cs` do programu Windows:</span><span class="sxs-lookup"><span data-stu-id="2ee9f-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ee9f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ee9f-120">See also</span></span>

- [<span data-ttu-id="2ee9f-121">-Target (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="2ee9f-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="2ee9f-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="2ee9f-122">C# Compiler Options</span></span>](./index.md)
