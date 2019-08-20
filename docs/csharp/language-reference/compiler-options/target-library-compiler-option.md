---
title: '-target: Library (C# opcje kompilatora)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606394"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="3b65b-102">-target: Library (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="3b65b-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="3b65b-103">Opcja **-target: Library** powoduje, że kompilator tworzy bibliotekę dołączaną dynamicznie (dll), a nie plik wykonywalny (exe).</span><span class="sxs-lookup"><span data-stu-id="3b65b-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b65b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b65b-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b65b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b65b-105">Remarks</span></span>  
 <span data-ttu-id="3b65b-106">Biblioteka DLL zostanie utworzona z rozszerzeniem dll.</span><span class="sxs-lookup"><span data-stu-id="3b65b-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="3b65b-107">O ile nie określono inaczej z opcją [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.</span><span class="sxs-lookup"><span data-stu-id="3b65b-107">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="3b65b-108">W przypadku określenia w wierszu polecenia wszystkie pliki do następnej lub docelowej opcji **modułu** są używane do tworzenia pliku dll.</span><span class="sxs-lookup"><span data-stu-id="3b65b-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="3b65b-109">Podczas kompilowania pliku DLL Metoda [Main](../../programming-guide/main-and-command-args/index.md) nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="3b65b-109">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3b65b-110">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b65b-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3b65b-111">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="3b65b-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="3b65b-112">Kliknij stronę właściwości **aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="3b65b-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="3b65b-113">Zmodyfikuj właściwość **typu danych wyjściowych** .</span><span class="sxs-lookup"><span data-stu-id="3b65b-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="3b65b-114">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="3b65b-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b65b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b65b-115">Example</span></span>  
 <span data-ttu-id="3b65b-116">Kompiluj `in.cs`, Utwórz `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="3b65b-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b65b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b65b-117">See also</span></span>

- [<span data-ttu-id="3b65b-118">-Target (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="3b65b-118">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="3b65b-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="3b65b-119">C# Compiler Options</span></span>](./index.md)
