---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 4f3dc61a6e78b0fb2135d4132c53e7efc22447a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814995"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="af80c-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af80c-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="af80c-103">Powoduje, że kompilator nie automatycznie odwołuje się do standardowych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="af80c-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af80c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af80c-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="af80c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af80c-105">Remarks</span></span>  
 <span data-ttu-id="af80c-106">`-nostdlib` Opcja usuwa automatyczne odwołanie do zestawu System.dll i uniemożliwia odczytywanie soubor Vbc.rsp przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="af80c-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="af80c-107">Soubor Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe, odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów i Importy `System` i `Microsoft.VisualBasic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="af80c-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af80c-108">Zestawy Mscorlib.dll i Microsoft.VisualBasic.dll zawsze są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="af80c-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af80c-109">`-nostdlib` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="af80c-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af80c-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="af80c-110">Example</span></span>  
 <span data-ttu-id="af80c-111">Poniższy kod kompiluje `T2.vb` bez odwołania do bibliotek standardowych.</span><span class="sxs-lookup"><span data-stu-id="af80c-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="af80c-112">Należy ustawić `_MYTYPE` Stała kompilacji warunkowej do ciągu "Puste", aby usunąć `My` obiektu.</span><span class="sxs-lookup"><span data-stu-id="af80c-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="af80c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af80c-113">See also</span></span>

- [<span data-ttu-id="af80c-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="af80c-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="af80c-115">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af80c-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="af80c-116">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="af80c-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="af80c-117">Dostosowywanie, które obiekty są dostępne w My</span><span class="sxs-lookup"><span data-stu-id="af80c-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
