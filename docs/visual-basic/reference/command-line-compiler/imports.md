---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 380e71e462f736d4564a37b83567007fa9461b05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332966"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="ab982-102">-imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab982-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="ab982-103">Imports namespaces from a specified assembly.</span><span class="sxs-lookup"><span data-stu-id="ab982-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab982-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab982-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ab982-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ab982-105">Arguments</span></span>  
  
|<span data-ttu-id="ab982-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ab982-106">Term</span></span>|<span data-ttu-id="ab982-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ab982-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="ab982-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ab982-108">Required.</span></span> <span data-ttu-id="ab982-109">Comma-delimited list of namespaces to be imported.</span><span class="sxs-lookup"><span data-stu-id="ab982-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab982-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab982-110">Remarks</span></span>  
 <span data-ttu-id="ab982-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span><span class="sxs-lookup"><span data-stu-id="ab982-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="ab982-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span><span class="sxs-lookup"><span data-stu-id="ab982-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="ab982-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span><span class="sxs-lookup"><span data-stu-id="ab982-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="ab982-114">To set /imports in the Visual Studio integrated development environment</span><span class="sxs-lookup"><span data-stu-id="ab982-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ab982-115">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="ab982-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ab982-116">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="ab982-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ab982-117">2.  Click the **References** tab.</span><span class="sxs-lookup"><span data-stu-id="ab982-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="ab982-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span><span class="sxs-lookup"><span data-stu-id="ab982-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="ab982-119">4.  Click the **Add User Import** button.</span><span class="sxs-lookup"><span data-stu-id="ab982-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ab982-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab982-120">Example</span></span>  
 <span data-ttu-id="ab982-121">The following code compiles when `/imports:system.globalization` is specified.</span><span class="sxs-lookup"><span data-stu-id="ab982-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="ab982-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="ab982-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="ab982-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab982-123">See also</span></span>

- [<span data-ttu-id="ab982-124">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="ab982-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ab982-125">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="ab982-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="ab982-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ab982-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
