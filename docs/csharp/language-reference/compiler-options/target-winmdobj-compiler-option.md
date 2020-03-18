---
title: -target:winmdobj (Opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204493"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="6820f-102">-target:winmdobj (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="6820f-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="6820f-103">Jeśli używasz opcji **kompilatora -target:winmdobj,** kompilator tworzy pośredni plik .winmdobj, który można przekonwertować na plik binarny środowiska uruchomieniowego systemu Windows (winmd).</span><span class="sxs-lookup"><span data-stu-id="6820f-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="6820f-104">Plik .winmd może być następnie używany przez programy JavaScript i C++, oprócz zarządzanych programów językowych.</span><span class="sxs-lookup"><span data-stu-id="6820f-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6820f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6820f-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="6820f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6820f-106">Remarks</span></span>  
 <span data-ttu-id="6820f-107">Ustawienie **winmdobj** sygnalizuje kompilator, że wymagany jest moduł pośredni.</span><span class="sxs-lookup"><span data-stu-id="6820f-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="6820f-108">W odpowiedzi Visual Studio kompiluje biblioteki klas C# jako plik .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="6820f-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="6820f-109">Plik .winmdobj może być następnie <xref:Microsoft.Build.Tasks.WinMDExp> podawany za pomocą narzędzia eksportu w celu wygenerowania pliku metadanych systemu Windows (winmd).</span><span class="sxs-lookup"><span data-stu-id="6820f-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="6820f-110">Plik .winmd zawiera zarówno kod z oryginalnej biblioteki, jak i metadane WinMD używane przez JavaScript lub C++ oraz przez środowisko uruchomieniowe systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6820f-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="6820f-111">Dane wyjściowe pliku, który jest kompilowany przy użyciu opcji kompilatora **-target:winmdobj** jest przeznaczony do użycia tylko jako dane wejściowe dla narzędzia eksportu WimMDExp; plik .winmdobj sam nie odwołuje się bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="6820f-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="6820f-112">Jeśli nie użyjesz opcji [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.</span><span class="sxs-lookup"><span data-stu-id="6820f-112">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="6820f-113">[Metoda główna](../../programming-guide/main-and-command-args/index.md) nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="6820f-113">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="6820f-114">Jeśli określisz opcję -target:winmdobj w wierszu polecenia, wszystkie pliki do następnego **-out** lub [-target:module](./target-module-compiler-option.md) opcja są używane do tworzenia programu Windows.</span><span class="sxs-lookup"><span data-stu-id="6820f-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="6820f-115">Aby ustawić tę opcję kompilatora w programie Visual Studio IDE dla aplikacji magazynu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6820f-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="6820f-116">W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6820f-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="6820f-117">Wybierz **kartę Aplikacja.**</span><span class="sxs-lookup"><span data-stu-id="6820f-117">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="6820f-118">Na liście **Typ wyjściowy** wybierz pozycję **Plik WinMD**.</span><span class="sxs-lookup"><span data-stu-id="6820f-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="6820f-119">Opcja **Plik WinMD** jest dostępna tylko dla szablonów aplikacji ze Sklepu Windows 8.x.</span><span class="sxs-lookup"><span data-stu-id="6820f-119">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="6820f-120">Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.ProjectProperties3.OutputType%2A>opcji kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="6820f-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6820f-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="6820f-121">Example</span></span>  
 <span data-ttu-id="6820f-122">Następujące polecenie kompiluje `filename.cs` się do pośredniego pliku .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="6820f-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6820f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6820f-123">See also</span></span>

- [<span data-ttu-id="6820f-124">-target (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="6820f-124">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="6820f-125">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="6820f-125">C# Compiler Options</span></span>](./index.md)
