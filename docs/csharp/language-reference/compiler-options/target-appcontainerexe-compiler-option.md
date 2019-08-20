---
title: '-target: appcontainerexe (C# opcje kompilatora)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 09ae01d95138b72a0012f294189d288fc71c74b2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606519"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="b60ee-102">-target: appcontainerexe (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="b60ee-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="b60ee-103">W przypadku użycia opcji kompilatora **-target: appcontainerexe** kompilator tworzy plik wykonywalny systemu Windows (exe), który musi być uruchamiany w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b60ee-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="b60ee-104">Ta opcja jest równoznaczna z parametrem [-target: winexe](./target-winexe-compiler-option.md) , [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] ale jest zaprojektowana dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b60ee-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b60ee-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b60ee-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="b60ee-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b60ee-106">Remarks</span></span>  
 <span data-ttu-id="b60ee-107">Aby wymagać uruchamiania aplikacji w kontenerze aplikacji, ta opcja ustawia bit w przenośnym pliku [wykonywalnym](/windows/desktop/Debug/pe-format) (PE).</span><span class="sxs-lookup"><span data-stu-id="b60ee-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="b60ee-108">Gdy ten bit jest ustawiony, występuje błąd, jeśli metoda CreateProcess podejmie próbę uruchomienia pliku wykonywalnego poza kontenerem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b60ee-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="b60ee-109">O ile nie zostanie użyta opcja [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera metodę [Main](../../programming-guide/main-and-command-args/index.md) .</span><span class="sxs-lookup"><span data-stu-id="b60ee-109">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="b60ee-110">Po określeniu tej opcji w wierszu polecenia wszystkie pliki do momentu użycia opcji dalej lub **-Target** są używane do tworzenia pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="b60ee-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="b60ee-111">Aby ustawić tę opcję kompilatora w IDE</span><span class="sxs-lookup"><span data-stu-id="b60ee-111">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="b60ee-112">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b60ee-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="b60ee-113">Na karcie **aplikacja** na liście **Typ danych wyjściowych** wybierz pozycję **aplikacja ze sklepu Windows**.</span><span class="sxs-lookup"><span data-stu-id="b60ee-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="b60ee-114">Ta opcja jest dostępna tylko dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b60ee-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="b60ee-115">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="b60ee-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b60ee-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b60ee-116">Example</span></span>  
 <span data-ttu-id="b60ee-117">Następujące polecenie kompiluje `filename.cs` do pliku wykonywalnego systemu Windows, który można uruchomić tylko w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b60ee-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b60ee-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b60ee-118">See also</span></span>

- [<span data-ttu-id="b60ee-119">-Target (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="b60ee-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="b60ee-120">-target: winexe (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="b60ee-120">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="b60ee-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="b60ee-121">C# Compiler Options</span></span>](./index.md)
