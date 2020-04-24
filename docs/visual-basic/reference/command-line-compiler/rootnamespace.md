---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005211"
---
# <a name="-rootnamespace"></a><span data-ttu-id="194f7-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="194f7-102">-rootnamespace</span></span>
<span data-ttu-id="194f7-103">Określa przestrzeń nazw dla wszystkich deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="194f7-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="194f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="194f7-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="194f7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="194f7-105">Arguments</span></span>  
  
|<span data-ttu-id="194f7-106">Termin</span><span class="sxs-lookup"><span data-stu-id="194f7-106">Term</span></span>|<span data-ttu-id="194f7-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="194f7-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="194f7-108">Nazwa przestrzeni nazw, w której należy ująć wszystkie deklaracje typu dla bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="194f7-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="194f7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="194f7-109">Remarks</span></span>  
 <span data-ttu-id="194f7-110">Jeśli używasz pliku wykonywalnego programu Visual Studio (devenv. exe) do kompilowania projektu utworzonego w zintegrowanym środowisku programistycznym programu Visual Studio `-rootnamespace` , użyj, aby określić wartość <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="194f7-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="194f7-111">Zobacz [przełączniki wiersza polecenia devenv](/visualstudio/ide/reference/devenv-command-line-switches) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="194f7-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="194f7-112">Użyj Dezasembler MSIL (`Ildasm.exe`) środowiska uruchomieniowego języka wspólnego, aby wyświetlić nazwy przestrzeni nazw w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="194f7-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="194f7-113">Aby ustawić-RootNamespace w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="194f7-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="194f7-114">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="194f7-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="194f7-115">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="194f7-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="194f7-116">2. Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="194f7-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="194f7-117">3. Zmodyfikuj wartość w polu **główna przestrzeń nazw** .</span><span class="sxs-lookup"><span data-stu-id="194f7-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="194f7-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="194f7-118">Example</span></span>  
 <span data-ttu-id="194f7-119">Poniższy kod kompiluje `In.vb` i ujmuje wszystkie deklaracje typów w przestrzeni nazw `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="194f7-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="194f7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="194f7-120">See also</span></span>

- [<span data-ttu-id="194f7-121">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="194f7-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="194f7-122">Ildasm. exe (IL dezasembler)</span><span class="sxs-lookup"><span data-stu-id="194f7-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="194f7-123">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="194f7-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
