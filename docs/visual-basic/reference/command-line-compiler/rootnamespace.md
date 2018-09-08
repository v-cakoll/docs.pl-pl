---
title: -rootnamespace —
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
ms.openlocfilehash: 13bce09ca9fd1ae9ebb919a9245d8ccf87fbde1d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44174162"
---
# <a name="-rootnamespace"></a><span data-ttu-id="d4d81-102">-rootnamespace —</span><span class="sxs-lookup"><span data-stu-id="d4d81-102">-rootnamespace</span></span>
<span data-ttu-id="d4d81-103">Określa obszar nazw dla wszystkich deklaracji typów.</span><span class="sxs-lookup"><span data-stu-id="d4d81-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4d81-104">Syntax</span></span>  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="d4d81-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d4d81-105">Arguments</span></span>  
  
|<span data-ttu-id="d4d81-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d4d81-106">Term</span></span>|<span data-ttu-id="d4d81-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d4d81-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="d4d81-108">Nazwa przestrzeni nazw, w której chcesz umieścić wszystkie deklaracje typu dla bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="d4d81-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4d81-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4d81-109">Remarks</span></span>  
 <span data-ttu-id="d4d81-110">Jeśli używasz pliku wykonywalnego w programie Visual Studio (Devenv.exe) aby skompilować projekt utworzony w programie Visual Studio zintegrowanego środowiska programistycznego, użyj `-rootnamespace` można określić wartość <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d4d81-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="d4d81-111">Zobacz [przełączników wiersza polecenia Devenv](/visualstudio/ide/reference/devenv-command-line-switches) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d4d81-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="d4d81-112">Użyj środowiska uruchomieniowego języka wspólnego MSIL Disassembler (`Ildasm.exe`) aby wyświetlić nazwy przestrzeni nazw w pliku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d4d81-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="d4d81-113">Aby ustawić - rootnamespace — w programie Visual Studio zintegrowane środowisko projektowe</span><span class="sxs-lookup"><span data-stu-id="d4d81-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d4d81-114">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d4d81-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d4d81-115">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d4d81-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d4d81-116">2.  Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="d4d81-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="d4d81-117">3.  Zmodyfikuj wartość w **Namespace głównego** pole.</span><span class="sxs-lookup"><span data-stu-id="d4d81-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4d81-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4d81-118">Example</span></span>  
 <span data-ttu-id="d4d81-119">Poniższy kod kompiluje `In.vb` i umieszcza wszystkie deklaracje typów w przestrzeni nazw `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="d4d81-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4d81-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4d81-120">See also</span></span>

- [<span data-ttu-id="d4d81-121">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4d81-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
- [<span data-ttu-id="d4d81-122">Ildasm.exe (dezasembler IL)</span><span class="sxs-lookup"><span data-stu-id="d4d81-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)  
- [<span data-ttu-id="d4d81-123">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d4d81-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
