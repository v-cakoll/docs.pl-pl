---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cdb7cff2221930113d6b49a640da0844f175f1b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="8414c-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8414c-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="8414c-103">Importuje przestrzeni nazw z określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8414c-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8414c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8414c-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="8414c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8414c-105">Arguments</span></span>  
  
|<span data-ttu-id="8414c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="8414c-106">Term</span></span>|<span data-ttu-id="8414c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="8414c-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="8414c-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8414c-108">Required.</span></span> <span data-ttu-id="8414c-109">Rozdzielana przecinkami lista obszarów nazw do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="8414c-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8414c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8414c-110">Remarks</span></span>  
 <span data-ttu-id="8414c-111">`/imports` Opcja importuje przestrzeni nazw zdefiniowane w obrębie bieżącego zestawu plików źródłowych lub z dowolnej przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8414c-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="8414c-112">Elementy członkowskie w przestrzeni nazw określony za pomocą `/imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8414c-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="8414c-113">Użyj [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do użycia w pliku kodu źródłowego w jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8414c-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="8414c-114">Aby ustawić/Import w Visual Studio zintegrowane środowisko programistyczne</span><span class="sxs-lookup"><span data-stu-id="8414c-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8414c-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="8414c-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8414c-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="8414c-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8414c-117">2.  Kliknij przycisk **odwołania** kartę.</span><span class="sxs-lookup"><span data-stu-id="8414c-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="8414c-118">3.  Wprowadź nazwę przestrzeni nazw w polu obok **dodać importu użytkownika** przycisku.</span><span class="sxs-lookup"><span data-stu-id="8414c-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="8414c-119">4.  Kliknij przycisk **dodać importu użytkownika** przycisku.</span><span class="sxs-lookup"><span data-stu-id="8414c-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8414c-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="8414c-120">Example</span></span>  
 <span data-ttu-id="8414c-121">Poniższy kod kompiluje kiedy `/imports:system` jest określona.</span><span class="sxs-lookup"><span data-stu-id="8414c-121">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8414c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8414c-122">See Also</span></span>  
 [<span data-ttu-id="8414c-123">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8414c-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8414c-124">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="8414c-124">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="8414c-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="8414c-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
