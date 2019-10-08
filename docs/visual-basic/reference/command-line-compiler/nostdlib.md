---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 819505df2e7d5f93302f9ed601de856e36ed7124
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005414"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="fb808-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb808-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="fb808-103">Powoduje, że kompilator nie będzie automatycznie odwoływać się do bibliotek standardowych.</span><span class="sxs-lookup"><span data-stu-id="fb808-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb808-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb808-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="fb808-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb808-105">Remarks</span></span>  
 <span data-ttu-id="fb808-106">Opcja `-nostdlib` usuwa automatyczne odwołanie do zestawu System. dll i uniemożliwia kompilatorowi odczytywanie pliku VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="fb808-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="fb808-107">Plik VBC. rsp, który znajduje się w tym samym katalogu co plik VBC. exe, odwołuje się do najczęściej używanych zestawów .NET Framework i importuje przestrzenie nazw `System` i `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="fb808-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb808-108">Zestawy mscorlib. dll i Microsoft. VisualBasic. dll są zawsze wywoływane.</span><span class="sxs-lookup"><span data-stu-id="fb808-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb808-109">Opcja `-nostdlib` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb808-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb808-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb808-110">Example</span></span>  
 <span data-ttu-id="fb808-111">Poniższy kod kompiluje `T2.vb` bez odwoływania się do bibliotek standardowych.</span><span class="sxs-lookup"><span data-stu-id="fb808-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="fb808-112">Aby usunąć obiekt `My`, należy ustawić stałą "`_MYTYPE`".</span><span class="sxs-lookup"><span data-stu-id="fb808-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb808-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb808-113">See also</span></span>

- [<span data-ttu-id="fb808-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="fb808-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="fb808-115">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb808-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fb808-116">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="fb808-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="fb808-117">Dostosowywanie, które obiekty są dostępne w My</span><span class="sxs-lookup"><span data-stu-id="fb808-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
