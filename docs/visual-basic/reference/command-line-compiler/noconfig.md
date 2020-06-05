---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ee7cd1b8039a8d9312a8b058cc85c41ca536ed2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401943"
---
# <a name="-noconfig"></a><span data-ttu-id="6e37a-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="6e37a-102">-noconfig</span></span>
<span data-ttu-id="6e37a-103">Określa, że kompilator nie powinien automatycznie odwoływać się do najczęściej używanych zestawów .NET Framework lub `System` zaimportować `Microsoft.VisualBasic` przestrzenie nazw i.</span><span class="sxs-lookup"><span data-stu-id="6e37a-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e37a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e37a-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="6e37a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e37a-105">Remarks</span></span>  
 <span data-ttu-id="6e37a-106">`-noconfig`Opcja instruuje kompilator, aby nie kompilować przy użyciu pliku VBC. rsp, który znajduje się w tym samym katalogu, co plik VBC. exe.</span><span class="sxs-lookup"><span data-stu-id="6e37a-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="6e37a-107">Plik VBC. rsp odwołuje się do najczęściej używanych zestawów .NET Framework i importuje `System` `Microsoft.VisualBasic` przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="6e37a-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="6e37a-108">Kompilator niejawnie odwołuje się do zestawu System. dll, chyba że `-nostdlib` określono opcję.</span><span class="sxs-lookup"><span data-stu-id="6e37a-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="6e37a-109">`-nostdlib`Opcja informuje kompilator, że nie kompiluje z VBC. rsp lub automatycznie odwołuje się do zestawu System. dll.</span><span class="sxs-lookup"><span data-stu-id="6e37a-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e37a-110">Zestawy mscorlib. dll i Microsoft. VisualBasic. dll są zawsze wywoływane.</span><span class="sxs-lookup"><span data-stu-id="6e37a-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="6e37a-111">Plik VBC. rsp można zmodyfikować, aby określić dodatkowe opcje kompilatora, które powinny być zawarte w każdej kompilacji VBC. exe (z wyjątkiem sytuacji, gdy jest określana `-noconfig` opcja).</span><span class="sxs-lookup"><span data-stu-id="6e37a-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="6e37a-112">Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="6e37a-112">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="6e37a-113">Kompilator przetwarza opcje przesłane do `vbc` ostatniego polecenia.</span><span class="sxs-lookup"><span data-stu-id="6e37a-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="6e37a-114">W związku z tym każda opcja w wierszu polecenia zastępuje ustawienie tej samej opcji w pliku VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="6e37a-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e37a-115">`-noconfig`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6e37a-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e37a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e37a-116">See also</span></span>

- [<span data-ttu-id="6e37a-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e37a-117">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="6e37a-118">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e37a-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6e37a-119">@ (określenie pliku odpowiedzi)</span><span class="sxs-lookup"><span data-stu-id="6e37a-119">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="6e37a-120">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e37a-120">-reference (Visual Basic)</span></span>](reference.md)
