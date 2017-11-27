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
ms.openlocfilehash: e8e9cd761263b3b61a4e6d3e33c5f7f875be7a1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="9edeb-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9edeb-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="9edeb-103">Importuje przestrzeni nazw z określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9edeb-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9edeb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9edeb-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="9edeb-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9edeb-105">Arguments</span></span>  
  
|<span data-ttu-id="9edeb-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9edeb-106">Term</span></span>|<span data-ttu-id="9edeb-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9edeb-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="9edeb-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9edeb-108">Required.</span></span> <span data-ttu-id="9edeb-109">Rozdzielana przecinkami lista obszarów nazw do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="9edeb-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9edeb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9edeb-110">Remarks</span></span>  
 <span data-ttu-id="9edeb-111">`/imports` Opcja importuje przestrzeni nazw zdefiniowane w obrębie bieżącego zestawu plików źródłowych lub z dowolnej przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9edeb-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="9edeb-112">Elementy członkowskie w przestrzeni nazw określony za pomocą `/imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9edeb-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="9edeb-113">Użyj [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do użycia w pliku kodu źródłowego w jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9edeb-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="9edeb-114">Aby ustawić/Import w Visual Studio zintegrowane środowisko programistyczne</span><span class="sxs-lookup"><span data-stu-id="9edeb-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9edeb-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="9edeb-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9edeb-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9edeb-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="9edeb-117">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="9edeb-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="9edeb-118">2.  Kliknij przycisk **odwołania** kartę.</span><span class="sxs-lookup"><span data-stu-id="9edeb-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="9edeb-119">3.  Wprowadź nazwę przestrzeni nazw w polu obok **dodać importu użytkownika** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9edeb-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="9edeb-120">4.  Kliknij przycisk **dodać importu użytkownika** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9edeb-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9edeb-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="9edeb-121">Example</span></span>  
 <span data-ttu-id="9edeb-122">Poniższy kod kompiluje kiedy `/imports:system` jest określona.</span><span class="sxs-lookup"><span data-stu-id="9edeb-122">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9edeb-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9edeb-123">See Also</span></span>  
 [<span data-ttu-id="9edeb-124">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9edeb-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9edeb-125">Referencje i Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9edeb-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="9edeb-126">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="9edeb-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
