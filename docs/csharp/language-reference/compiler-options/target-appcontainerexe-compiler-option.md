---
title: -target:appcontainerexe (Opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204524"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="154f2-102">-target:appcontainerexe (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="154f2-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="154f2-103">Jeśli używasz opcji **kompilatora -target:appcontainerexe,** kompilator tworzy plik wykonywalny systemu Windows (exe), który musi być uruchamiany w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="154f2-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="154f2-104">Ta opcja jest odpowiednikiem [-target:winexe,](./target-winexe-compiler-option.md) ale jest przeznaczona dla aplikacji ze Sklepu Windows 8.x.</span><span class="sxs-lookup"><span data-stu-id="154f2-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="154f2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="154f2-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="154f2-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="154f2-106">Remarks</span></span>  
 <span data-ttu-id="154f2-107">Aby wymagać uruchamiania aplikacji w kontenerze aplikacji, ta opcja ustawia nieco w pliku [Przenośny plik wykonywalny](/windows/desktop/Debug/pe-format) (PE).</span><span class="sxs-lookup"><span data-stu-id="154f2-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="154f2-108">Gdy ten bit jest ustawiony, występuje błąd, jeśli CreateProcess metoda próbuje uruchomić plik wykonywalny poza kontenerem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="154f2-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="154f2-109">Jeśli nie użyjesz opcji [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../programming-guide/main-and-command-args/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="154f2-109">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="154f2-110">Po określeniu tej opcji w wierszu polecenia wszystkie pliki do następnego **-out** lub **-target** opcja są używane do tworzenia pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="154f2-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="154f2-111">Aby ustawić tę opcję kompilatora w IDE</span><span class="sxs-lookup"><span data-stu-id="154f2-111">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="154f2-112">W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="154f2-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="154f2-113">Na **karcie Aplikacja** na liście **Typ wyjściowy** wybierz pozycję Aplikacja **ze Sklepu Windows**.</span><span class="sxs-lookup"><span data-stu-id="154f2-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="154f2-114">Ta opcja jest dostępna tylko dla szablonów aplikacji ze Sklepu Windows 8.x.</span><span class="sxs-lookup"><span data-stu-id="154f2-114">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="154f2-115">Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.ProjectProperties3.OutputType%2A>opcji kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="154f2-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="154f2-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="154f2-116">Example</span></span>  
 <span data-ttu-id="154f2-117">Następujące polecenie kompiluje `filename.cs` się do pliku wykonywalnego systemu Windows, który można uruchomić tylko w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="154f2-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="154f2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="154f2-118">See also</span></span>

- [<span data-ttu-id="154f2-119">-target (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="154f2-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="154f2-120">-target:winexe (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="154f2-120">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="154f2-121">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="154f2-121">C# Compiler Options</span></span>](./index.md)
