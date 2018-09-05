---
title: '-target: appcontainerexe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 8042e1888da63d26f3639ed372bfc7fadcd515f0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507877"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="c34c4-102">-target: appcontainerexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c34c4-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="c34c4-103">Jeśli używasz **-target: appcontainerexe** — opcja kompilatora, kompilator tworzy plik wykonywalny (.exe) Windows, który musi być uruchamiany w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c34c4-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="c34c4-104">Ta opcja jest równoznaczna z [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale jest przeznaczona dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c34c4-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c34c4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c34c4-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="c34c4-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c34c4-106">Remarks</span></span>  
 <span data-ttu-id="c34c4-107">Aby wymagać uruchamiania aplikacji w pojemniku aplikacji, ta opcja ustawia bit w [przenośny plik wykonywalny](/windows/desktop/Debug/pe-format) (PE) pliku.</span><span class="sxs-lookup"><span data-stu-id="c34c4-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="c34c4-108">Jeśli ten bit jest ustawiony, błąd występuje, gdy metoda funkcji CreateProcess próbuje uruchomić plik wykonywalny poza kontenerem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c34c4-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="c34c4-109">Chyba że używasz [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c34c4-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="c34c4-110">Po określeniu tej opcji w wierszu polecenia, wszystkie pliki, aż do następnej **-się** lub **-target** opcji są używane do tworzenia pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c34c4-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="c34c4-111">Aby ustawić tę opcję kompilatora w IDE</span><span class="sxs-lookup"><span data-stu-id="c34c4-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="c34c4-112">W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c34c4-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="c34c4-113">Na **aplikacji** na karcie **typ danych wyjściowych** wybierz **Windows Store App**.</span><span class="sxs-lookup"><span data-stu-id="c34c4-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="c34c4-114">Ta opcja jest dostępna tylko w przypadku [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c34c4-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="c34c4-115">Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c34c4-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c34c4-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="c34c4-116">Example</span></span>  
 <span data-ttu-id="c34c4-117">Następujące polecenie kompiluje `filename.cs` do Windows plik wykonywalny, który można uruchomić tylko w pojemniku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c34c4-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c34c4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c34c4-118">See Also</span></span>  

- [<span data-ttu-id="c34c4-119">-target (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c34c4-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="c34c4-120">-target: winexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c34c4-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
- [<span data-ttu-id="c34c4-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c34c4-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
