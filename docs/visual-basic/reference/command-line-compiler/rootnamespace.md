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
ms.openlocfilehash: b6a2f3ba0772d8f8c8c6a762a1be01703d21b778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403138"
---
# <a name="-rootnamespace"></a><span data-ttu-id="1a2ed-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="1a2ed-102">-rootnamespace</span></span>
<span data-ttu-id="1a2ed-103">Określa przestrzeń nazw dla wszystkich deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="1a2ed-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a2ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a2ed-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="1a2ed-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1a2ed-105">Arguments</span></span>  
  
|<span data-ttu-id="1a2ed-106">Termin</span><span class="sxs-lookup"><span data-stu-id="1a2ed-106">Term</span></span>|<span data-ttu-id="1a2ed-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="1a2ed-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="1a2ed-108">Nazwa przestrzeni nazw, w której należy ująć wszystkie deklaracje typu dla bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="1a2ed-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a2ed-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a2ed-109">Remarks</span></span>  
 <span data-ttu-id="1a2ed-110">Jeśli używasz pliku wykonywalnego programu Visual Studio (devenv. exe) do kompilowania projektu utworzonego w zintegrowanym środowisku programistycznym programu Visual Studio, użyj, `-rootnamespace` Aby określić wartość <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a2ed-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="1a2ed-111">Zobacz [przełączniki wiersza polecenia devenv](/visualstudio/ide/reference/devenv-command-line-switches) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1a2ed-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="1a2ed-112">Użyj Dezasembler MSIL () środowiska uruchomieniowego języka wspólnego, `Ildasm.exe` Aby wyświetlić nazwy przestrzeni nazw w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="1a2ed-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="1a2ed-113">Aby ustawić-RootNamespace w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1a2ed-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1a2ed-114">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="1a2ed-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1a2ed-115">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1a2ed-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1a2ed-116">2. Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="1a2ed-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="1a2ed-117">3. Zmodyfikuj wartość w polu **główna przestrzeń nazw** .</span><span class="sxs-lookup"><span data-stu-id="1a2ed-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1a2ed-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a2ed-118">Example</span></span>  
 <span data-ttu-id="1a2ed-119">Poniższy kod kompiluje `In.vb` i ujmuje wszystkie deklaracje typów w przestrzeni nazw `mynamespace` .</span><span class="sxs-lookup"><span data-stu-id="1a2ed-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a2ed-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a2ed-120">See also</span></span>

- [<span data-ttu-id="1a2ed-121">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a2ed-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="1a2ed-122">Ildasm. exe (IL dezasembler)</span><span class="sxs-lookup"><span data-stu-id="1a2ed-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="1a2ed-123">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="1a2ed-123">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
