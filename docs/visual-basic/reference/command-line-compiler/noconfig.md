---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: b707899c845b6b08e008fe229497f682c930044a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588846"
---
# <a name="-noconfig"></a><span data-ttu-id="0253a-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="0253a-102">-noconfig</span></span>
<span data-ttu-id="0253a-103">Określa, że kompilator powinien automatycznie odwołuje się do często używanych zestawów .NET Framework lub zaimportować `System` i `Microsoft.VisualBasic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0253a-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0253a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0253a-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="0253a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0253a-105">Remarks</span></span>  
 <span data-ttu-id="0253a-106">`-noconfig` Opcja informuje kompilator, aby nie kompilacji z soubor Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="0253a-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="0253a-107">Soubor Vbc.rsp odwołuje się do często używanych zestawów .NET Framework i importuje `System` i `Microsoft.VisualBasic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0253a-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="0253a-108">Kompilator niejawnie odwołuje się do zestawu System.dll chyba że `-nostdlib` określono opcję.</span><span class="sxs-lookup"><span data-stu-id="0253a-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="0253a-109">`-nostdlib` Opcja informuje kompilator, aby nie kompilować z Vbc.rsp lub automatycznie odwołuje się do zestawu System.dll.</span><span class="sxs-lookup"><span data-stu-id="0253a-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0253a-110">Zestawy Mscorlib.dll i Microsoft.VisualBasic.dll zawsze są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="0253a-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="0253a-111">Można zmodyfikować soubor Vbc.rsp, aby określić opcje dodatkowe kompilatora, które powinny być uwzględnione w każdej kompilacji Vbc.exe (z wyjątkiem sytuacji, określając `-noconfig` opcji).</span><span class="sxs-lookup"><span data-stu-id="0253a-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="0253a-112">Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="0253a-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="0253a-113">Kompilator przetwarza opcje przekazywane do `vbc` ostatnie polecenie.</span><span class="sxs-lookup"><span data-stu-id="0253a-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="0253a-114">W związku z tym dowolnej opcji w wierszu polecenia zastępuje ustawienie tych samych opcji w soubor Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="0253a-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0253a-115">`-noconfig` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="0253a-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0253a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0253a-116">See also</span></span>

- [<span data-ttu-id="0253a-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0253a-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="0253a-118">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0253a-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0253a-119">@ (określenie pliku odpowiedzi)</span><span class="sxs-lookup"><span data-stu-id="0253a-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="0253a-120">— Odwołanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0253a-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
