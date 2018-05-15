---
title: '-docelowych: appcontainerexe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: b8765f64aeb08d816ca17fce64c13e981d85145b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="2498c-102">-docelowych: appcontainerexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2498c-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="2498c-103">Jeśli używasz **-docelowych: appcontainerexe** — opcja kompilatora, kompilator tworzy plik wykonywalny (.exe) systemu Windows, które muszą być uruchamiane w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2498c-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="2498c-104">Ta opcja jest równoważna [-docelowych: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale jest przeznaczona dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2498c-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2498c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2498c-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="2498c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2498c-106">Remarks</span></span>  
 <span data-ttu-id="2498c-107">Aby wymagać aplikacji do uruchamiania w kontenerze aplikacji, ta opcja umożliwia ustawienie nieco [przenośny plik wykonywalny](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) pliku (PE).</span><span class="sxs-lookup"><span data-stu-id="2498c-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) (PE) file.</span></span> <span data-ttu-id="2498c-108">Podczas tego bit jest ustawiony, jeśli metody CreateProcess podejmie próbę uruchomienia pliku wykonywalnego poza kontenerem aplikacji wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="2498c-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="2498c-109">Tylko w przypadku [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) — metoda.</span><span class="sxs-lookup"><span data-stu-id="2498c-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="2498c-110">Po określeniu tej opcji w wierszu polecenia, wszystkie pliki, aż do następnego **-out** lub **-docelowego** opcji są używane do tworzenia pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="2498c-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="2498c-111">Aby ustawić tę opcję kompilatora w IDE</span><span class="sxs-lookup"><span data-stu-id="2498c-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="2498c-112">W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2498c-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="2498c-113">Na **aplikacji** karcie **Output typu** wybierz **aplikacji ze Sklepu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2498c-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="2498c-114">Ta opcja jest dostępna tylko w przypadku [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2498c-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="2498c-115">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="2498c-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2498c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="2498c-116">Example</span></span>  
 <span data-ttu-id="2498c-117">Następujące polecenie kompiluje `filename.cs` do pliku wykonywalnego systemu Windows, która może działać tylko w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2498c-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2498c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2498c-118">See Also</span></span>  
 [<span data-ttu-id="2498c-119">-docelowego (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2498c-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="2498c-120">-docelowych: winexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2498c-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [<span data-ttu-id="2498c-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="2498c-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
