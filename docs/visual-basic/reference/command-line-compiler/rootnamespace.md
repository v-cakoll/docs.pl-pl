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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60cd661fe321c7bc3346f4d20e373240d6c35b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653163"
---
# <a name="-rootnamespace"></a><span data-ttu-id="a86e8-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="a86e8-102">-rootnamespace</span></span>
<span data-ttu-id="a86e8-103">Określa przestrzeń nazw dla wszystkich deklaracji typów.</span><span class="sxs-lookup"><span data-stu-id="a86e8-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a86e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a86e8-104">Syntax</span></span>  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="a86e8-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a86e8-105">Arguments</span></span>  
  
|<span data-ttu-id="a86e8-106">Termin</span><span class="sxs-lookup"><span data-stu-id="a86e8-106">Term</span></span>|<span data-ttu-id="a86e8-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="a86e8-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="a86e8-108">Nazwa przestrzeni nazw, w którym należy ująć wszystkich deklaracji typów dla bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="a86e8-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a86e8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a86e8-109">Remarks</span></span>  
 <span data-ttu-id="a86e8-110">Jeśli używasz pliku wykonywalnego programu Visual Studio (Devenv.exe) aby skompilować projekt utworzony w programie Visual Studio zintegrowane środowisko programistyczne, użyj `-rootnamespace` do określenia wartości <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a86e8-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="a86e8-111">Zobacz [przełączniki wiersza polecenia Devenv](/visualstudio/ide/reference/devenv-command-line-switches) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="a86e8-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="a86e8-112">Użyj środowiska CLR dezasembler MSIL (`Ildasm.exe`) do wyświetlenia nazwy przestrzeni nazw w pliku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a86e8-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="a86e8-113">Aby ustawić - rootnamespace w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="a86e8-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="a86e8-114">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="a86e8-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a86e8-115">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a86e8-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="a86e8-116">2.  Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="a86e8-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="a86e8-117">3.  Zmodyfikuj wartość w **Namespace głównego** pole.</span><span class="sxs-lookup"><span data-stu-id="a86e8-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a86e8-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a86e8-118">Example</span></span>  
 <span data-ttu-id="a86e8-119">Poniższy kod kompiluje `In.vb` i umieszcza wszystkie deklaracje typu w przestrzeni nazw `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="a86e8-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a86e8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a86e8-120">See Also</span></span>  
 [<span data-ttu-id="a86e8-121">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a86e8-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a86e8-122">Ildasm.exe (dezasembler IL)</span><span class="sxs-lookup"><span data-stu-id="a86e8-122">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="a86e8-123">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="a86e8-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
