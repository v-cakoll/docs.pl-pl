---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: db6b047f521d8ef44d2bd1b70b654a4233ebb1a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347913"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="213ff-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="213ff-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="213ff-103">Powoduje, że kompilator nie będzie automatycznie odwoływać się do bibliotek standardowych.</span><span class="sxs-lookup"><span data-stu-id="213ff-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="213ff-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="213ff-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="213ff-105">Remarks</span></span>  
 <span data-ttu-id="213ff-106">`-nostdlib` Opcja usuwa automatyczne odwołanie do zestawu System. dll i uniemożliwia kompilatorowi odczytywanie pliku VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="213ff-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="213ff-107">Plik VBC. rsp, który znajduje się w tym samym katalogu, co plik VBC. exe, odwołuje się do najczęściej używanych zestawów .NET Framework i `System` importuje `Microsoft.VisualBasic` przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="213ff-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="213ff-108">Zestawy mscorlib. dll i Microsoft. VisualBasic. dll są zawsze wywoływane.</span><span class="sxs-lookup"><span data-stu-id="213ff-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="213ff-109">`-nostdlib` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="213ff-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="213ff-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="213ff-110">Example</span></span>  
 <span data-ttu-id="213ff-111">Poniższy kod kompiluje się `T2.vb` bez odwoływania się do bibliotek standardowych.</span><span class="sxs-lookup"><span data-stu-id="213ff-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="213ff-112">Aby usunąć `My` obiekt, `_MYTYPE` należy ustawić stałą dla kompilacji warunkowej na ciąg "Empty".</span><span class="sxs-lookup"><span data-stu-id="213ff-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="213ff-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="213ff-113">See also</span></span>

- [<span data-ttu-id="213ff-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="213ff-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="213ff-115">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="213ff-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="213ff-116">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="213ff-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="213ff-117">Dostosowywanie, które obiekty są dostępne w My</span><span class="sxs-lookup"><span data-stu-id="213ff-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
