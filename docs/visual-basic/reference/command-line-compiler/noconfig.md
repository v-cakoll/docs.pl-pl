---
title: /noconfig
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94d13ccf0168027f4560b980c41e2a001ff503fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig"></a><span data-ttu-id="46b99-102">/noconfig</span><span class="sxs-lookup"><span data-stu-id="46b99-102">/noconfig</span></span>
<span data-ttu-id="46b99-103">Określa, że kompilator powinien automatycznie odwołuje się często używane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawy lub importu `System` i `Microsoft.VisualBasic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46b99-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46b99-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46b99-104">Syntax</span></span>  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="46b99-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46b99-105">Remarks</span></span>  
 <span data-ttu-id="46b99-106">`/noconfig` Opcja informuje kompilator, aby nie kompilacji z pliku Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="46b99-106">The `/noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="46b99-107">Pliku Vbc.rsp odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów i Importy `System` i `Microsoft.VisualBasic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46b99-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="46b99-108">Kompilator niejawnie odwołuje się do zestawu System.dll chyba że `/nostdlib` określono opcję.</span><span class="sxs-lookup"><span data-stu-id="46b99-108">The compiler implicitly references the System.dll assembly unless the `/nostdlib` option is specified.</span></span> <span data-ttu-id="46b99-109">`/nostdlib` Opcja nakazuje kompilatorowi nie kompilacji z Vbc.rsp lub automatycznie odwołuje się do zestawu System.dll.</span><span class="sxs-lookup"><span data-stu-id="46b99-109">The `/nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46b99-110">Zawsze odwołuje się do pliku Mscorlib.dll i pliku Microsoft.VisualBasic.dll zestawów.</span><span class="sxs-lookup"><span data-stu-id="46b99-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="46b99-111">Można zmodyfikować pliku Vbc.rsp umożliwia określenie opcji kompilatora dodatkowe, które powinny być uwzględnione w każdej kompilacji Vbc.exe (z wyjątkiem podczas określania `/noconfig` opcja).</span><span class="sxs-lookup"><span data-stu-id="46b99-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `/noconfig` option).</span></span> <span data-ttu-id="46b99-112">Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="46b99-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="46b99-113">Kompilator przetwarza opcje przekazane do `vbc` ostatniego polecenia.</span><span class="sxs-lookup"><span data-stu-id="46b99-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="46b99-114">W związku z tym każda opcja, w wierszu polecenia zastępuje ustawienie opcji tego samego pliku Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="46b99-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46b99-115">`/noconfig` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="46b99-115">The `/noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b99-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46b99-116">See Also</span></span>  
 [<span data-ttu-id="46b99-117">/ nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46b99-117">/nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [<span data-ttu-id="46b99-118">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46b99-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="46b99-119">@ (Określ plik odpowiedzi)</span><span class="sxs-lookup"><span data-stu-id="46b99-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [<span data-ttu-id="46b99-120">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46b99-120">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
