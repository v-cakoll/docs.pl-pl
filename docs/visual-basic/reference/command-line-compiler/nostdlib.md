---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764409f13a00f6d8a050bfbdd0f59e537a5ded3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456295"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="cf6ce-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf6ce-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="cf6ce-103">Powoduje, że kompilator nie automatycznie odwołuje się do standardowych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="cf6ce-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf6ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf6ce-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf6ce-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf6ce-105">Remarks</span></span>  
 <span data-ttu-id="cf6ce-106">`-nostdlib` Opcja usuwa automatyczne odwołanie do zestawu System.dll i uniemożliwia odczytywanie soubor Vbc.rsp przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="cf6ce-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="cf6ce-107">Soubor Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe, odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów i Importy `System` i `Microsoft.VisualBasic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cf6ce-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf6ce-108">Zestawy Mscorlib.dll i Microsoft.VisualBasic.dll zawsze są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="cf6ce-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf6ce-109">`-nostdlib` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf6ce-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf6ce-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf6ce-110">Example</span></span>  
 <span data-ttu-id="cf6ce-111">Poniższy kod kompiluje `T2.vb` bez odwołania do bibliotek standardowych.</span><span class="sxs-lookup"><span data-stu-id="cf6ce-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="cf6ce-112">Należy ustawić `_MYTYPE` Stała kompilacji warunkowej do ciągu "Puste", aby usunąć `My` obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf6ce-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf6ce-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf6ce-113">See Also</span></span>  
 [<span data-ttu-id="cf6ce-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="cf6ce-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="cf6ce-115">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf6ce-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="cf6ce-116">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="cf6ce-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="cf6ce-117">Dostosowywanie, które obiekty są dostępne w My</span><span class="sxs-lookup"><span data-stu-id="cf6ce-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
