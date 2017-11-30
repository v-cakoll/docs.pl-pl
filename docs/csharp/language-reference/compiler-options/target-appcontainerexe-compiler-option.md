---
title: '-docelowych: appcontainerexe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ab407f14483bbb5abaf3dc23b0cf204091b74ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="317da-102">/target:appcontainerexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="317da-102">/target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="317da-103">Jeśli używasz **/target: appcontainerexe** — opcja kompilatora, kompilator tworzy plik wykonywalny (.exe) systemu Windows, które muszą być uruchamiane w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="317da-103">If you use the **/target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="317da-104">Ta opcja jest równoważna [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale jest przeznaczona dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="317da-104">This option is equivalent to [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="317da-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="317da-105">Syntax</span></span>  
  
```console  
/target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="317da-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="317da-106">Remarks</span></span>  
 <span data-ttu-id="317da-107">Aby wymagać aplikacji do uruchamiania w kontenerze aplikacji, ta opcja umożliwia ustawienie nieco [przenośny plik wykonywalny](http://go.microsoft.com/fwlink/p/?LinkId=236960) pliku (PE).</span><span class="sxs-lookup"><span data-stu-id="317da-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) (PE) file.</span></span> <span data-ttu-id="317da-108">Podczas tego bit jest ustawiony, jeśli metody CreateProcess podejmie próbę uruchomienia pliku wykonywalnego poza kontenerem aplikacji wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="317da-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="317da-109">Jeśli nie używasz [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) — metoda.</span><span class="sxs-lookup"><span data-stu-id="317da-109">Unless you use the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="317da-110">Po określeniu tej opcji w wierszu polecenia, wszystkie pliki, aż do następnego **/out** lub **/target** opcji są używane do tworzenia pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="317da-110">When you specify this option at a command prompt, all files until the next **/out** or **/target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="317da-111">Aby ustawić tę opcję kompilatora w IDE</span><span class="sxs-lookup"><span data-stu-id="317da-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="317da-112">W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="317da-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="317da-113">Na **aplikacji** karcie **Output typu** wybierz **aplikacji ze Sklepu Windows**.</span><span class="sxs-lookup"><span data-stu-id="317da-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="317da-114">Ta opcja jest dostępna tylko w przypadku [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="317da-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="317da-115">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="317da-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="317da-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="317da-116">Example</span></span>  
 <span data-ttu-id="317da-117">Następujące polecenie kompiluje `filename.cs` do pliku wykonywalnego systemu Windows, która może działać tylko w kontenerze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="317da-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc /target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="317da-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="317da-118">See Also</span></span>  
 [<span data-ttu-id="317da-119">/ TARGET (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="317da-119">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="317da-120">/ target: winexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="317da-120">/target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [<span data-ttu-id="317da-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="317da-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
