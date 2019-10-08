---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005434"
---
# <a name="-noconfig"></a><span data-ttu-id="6777d-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="6777d-102">-noconfig</span></span>
<span data-ttu-id="6777d-103">Określa, że kompilator nie powinien automatycznie odwoływać się do najczęściej używanych zestawów .NET Framework lub zaimportować przestrzenie nazw `System` i `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="6777d-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6777d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6777d-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="6777d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6777d-105">Remarks</span></span>  
 <span data-ttu-id="6777d-106">Opcja `-noconfig` instruuje kompilator, aby nie kompilować przy użyciu pliku VBC. rsp, który znajduje się w tym samym katalogu, co plik VBC. exe.</span><span class="sxs-lookup"><span data-stu-id="6777d-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="6777d-107">Plik VBC. rsp odwołuje się do najczęściej używanych zestawów .NET Framework i importuje przestrzenie nazw `System` i `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="6777d-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="6777d-108">Kompilator niejawnie odwołuje się do zestawu System. dll, chyba że jest określona opcja `-nostdlib`.</span><span class="sxs-lookup"><span data-stu-id="6777d-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="6777d-109">Opcja `-nostdlib` instruuje kompilator, aby nie kompilować z VBC. rsp lub automatycznie odwoływać się do zestawu System. dll.</span><span class="sxs-lookup"><span data-stu-id="6777d-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6777d-110">Zestawy mscorlib. dll i Microsoft. VisualBasic. dll są zawsze wywoływane.</span><span class="sxs-lookup"><span data-stu-id="6777d-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="6777d-111">Plik VBC. rsp można zmodyfikować, aby określić dodatkowe opcje kompilatora, które powinny być zawarte w każdej kompilacji VBC. exe (z wyjątkiem sytuacji, gdy określono opcję `-noconfig`).</span><span class="sxs-lookup"><span data-stu-id="6777d-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="6777d-112">Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="6777d-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="6777d-113">Kompilator przetwarza opcje przesłane do `vbc` polecenie Last.</span><span class="sxs-lookup"><span data-stu-id="6777d-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="6777d-114">W związku z tym każda opcja w wierszu polecenia zastępuje ustawienie tej samej opcji w pliku VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="6777d-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6777d-115">Opcja `-noconfig` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6777d-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6777d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6777d-116">See also</span></span>

- [<span data-ttu-id="6777d-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6777d-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="6777d-118">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6777d-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6777d-119">@ (określenie pliku odpowiedzi)</span><span class="sxs-lookup"><span data-stu-id="6777d-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="6777d-120">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6777d-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
