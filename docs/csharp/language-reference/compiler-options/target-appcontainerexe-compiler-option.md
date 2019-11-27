---
title: '-target: appcontainerexe (C# opcje kompilatora)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204524"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="03c54-102">-target: appcontainerexe (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="03c54-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="03c54-103">W przypadku użycia opcji kompilatora **-target: appcontainerexe** kompilator tworzy plik wykonywalny systemu Windows (exe), który musi być uruchamiany w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03c54-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="03c54-104">Ta opcja jest równoznaczna z parametrem [-target: winexe](./target-winexe-compiler-option.md) , ale jest przeznaczona dla aplikacji ze sklepu Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="03c54-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03c54-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="03c54-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="03c54-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03c54-106">Remarks</span></span>  
 <span data-ttu-id="03c54-107">Aby wymagać uruchamiania aplikacji w kontenerze aplikacji, ta opcja ustawia bit w [przenośnym pliku wykonywalnym](/windows/desktop/Debug/pe-format) (PE).</span><span class="sxs-lookup"><span data-stu-id="03c54-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="03c54-108">Gdy ten bit jest ustawiony, występuje błąd, jeśli metoda CreateProcess podejmie próbę uruchomienia pliku wykonywalnego poza kontenerem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03c54-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="03c54-109">O ile nie zostanie użyta opcja [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera metodę [Main](../../programming-guide/main-and-command-args/index.md) .</span><span class="sxs-lookup"><span data-stu-id="03c54-109">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="03c54-110">Po określeniu tej opcji w wierszu polecenia wszystkie pliki do momentu użycia opcji **Dalej lub** **-Target** są używane do tworzenia pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="03c54-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="03c54-111">Aby ustawić tę opcję kompilatora w IDE</span><span class="sxs-lookup"><span data-stu-id="03c54-111">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="03c54-112">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="03c54-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="03c54-113">Na karcie **aplikacja** na liście **Typ danych wyjściowych** wybierz pozycję **aplikacja ze sklepu Windows**.</span><span class="sxs-lookup"><span data-stu-id="03c54-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="03c54-114">Ta opcja jest dostępna tylko dla szablonów aplikacji ze sklepu Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="03c54-114">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="03c54-115">Aby uzyskać informacje o tym, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="03c54-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03c54-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="03c54-116">Example</span></span>  
 <span data-ttu-id="03c54-117">Poniższe polecenie kompiluje `filename.cs` do pliku wykonywalnego systemu Windows, który można uruchomić tylko w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03c54-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="03c54-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03c54-118">See also</span></span>

- [<span data-ttu-id="03c54-119">-Target (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="03c54-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="03c54-120">-target: winexe (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="03c54-120">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="03c54-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="03c54-121">C# Compiler Options</span></span>](./index.md)
