---
title: '-target: winmdobj (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 4000394a35c8990d3c5793c1313fc768a61c3271
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608969"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="c730f-102">-target: winmdobj (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c730f-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="c730f-103">Jeśli używasz **-target: winmdobj** — opcja kompilatora, kompilator tworzy plik pośredni .winmdobj, który można przekonwertować na plik binarny (.winmd) środowiska wykonawczego Windows.</span><span class="sxs-lookup"><span data-stu-id="c730f-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="c730f-104">Plik .winmd może następnie być używany przez programy JavaScript i C++, oprócz programów zarządzanych języka.</span><span class="sxs-lookup"><span data-stu-id="c730f-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c730f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c730f-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="c730f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c730f-106">Remarks</span></span>  
 <span data-ttu-id="c730f-107">**Winmdobj** ustawienie sygnalizuje kompilatorowi, że wymagany jest pośredni moduł.</span><span class="sxs-lookup"><span data-stu-id="c730f-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="c730f-108">W odpowiedzi skrypt Visual Studio kompiluje bibliotekę klas języka C# jako plik .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="c730f-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="c730f-109">Plik .winmdobj następnie może być zasilany przez <xref:Microsoft.Build.Tasks.WinMDExp> wyeksportować narzędzie w celu utworzenia pliku metadanych (.winmd) Windows.</span><span class="sxs-lookup"><span data-stu-id="c730f-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="c730f-110">Plik .winmd zawiera kod z oryginalnej biblioteki i metadane WinMD, które jest używane przez programy JavaScript lub C++ i przez środowisko wykonawcze Windows.</span><span class="sxs-lookup"><span data-stu-id="c730f-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="c730f-111">Dane wyjściowe pliku, który jest kompilowany przy użyciu **-target: winmdobj** — opcja kompilatora jest przeznaczona do użycia tylko jako dane wejściowe dla narzędzia do eksportu WimMDExp; do pliku .winmdobj nie jest przywoływany bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="c730f-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="c730f-112">Jeśli nie używasz [-się](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.</span><span class="sxs-lookup"><span data-stu-id="c730f-112">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="c730f-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metoda nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="c730f-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="c730f-114">W przypadku określenia opcji target: winmdobj w wierszu polecenia wszystkie pliki, aż do następnej **-się** lub [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) opcji są używane do tworzenia programów Windows.</span><span class="sxs-lookup"><span data-stu-id="c730f-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="c730f-115">Aby ustawić tę opcję kompilatora w programie Visual Studio IDE dla aplikacji magazynu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c730f-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1.  <span data-ttu-id="c730f-116">W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c730f-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="c730f-117">Wybierz **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="c730f-117">Choose the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="c730f-118">W **typ danych wyjściowych** wybierz **plik WinMD**.</span><span class="sxs-lookup"><span data-stu-id="c730f-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="c730f-119">**Plik WinMD** opcja jest dostępna tylko w przypadku [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c730f-119">The **WinMD File** option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="c730f-120">Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c730f-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c730f-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="c730f-121">Example</span></span>  
 <span data-ttu-id="c730f-122">Następujące polecenie kompiluje `filename.cs` do pliku .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="c730f-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c730f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c730f-123">See also</span></span>

- [<span data-ttu-id="c730f-124">-target (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c730f-124">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="c730f-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c730f-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
