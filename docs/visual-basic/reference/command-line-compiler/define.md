---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a><span data-ttu-id="323bf-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="323bf-102">/define (Visual Basic)</span></span>
<span data-ttu-id="323bf-103">Definiuje warunkowe stałe kompilatora.</span><span class="sxs-lookup"><span data-stu-id="323bf-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="323bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="323bf-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="323bf-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="323bf-105">Arguments</span></span>  
  
|<span data-ttu-id="323bf-106">Termin</span><span class="sxs-lookup"><span data-stu-id="323bf-106">Term</span></span>|<span data-ttu-id="323bf-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="323bf-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="323bf-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="323bf-108">Required.</span></span> <span data-ttu-id="323bf-109">Symbol do definiowania.</span><span class="sxs-lookup"><span data-stu-id="323bf-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="323bf-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="323bf-110">Optional.</span></span> <span data-ttu-id="323bf-111">Wartość do przypisania `symbol`.</span><span class="sxs-lookup"><span data-stu-id="323bf-111">The value to assign `symbol`.</span></span> <span data-ttu-id="323bf-112">Jeśli `value` jest ciągiem, muszą być ujęte przez sekwencje ukośnik odwrotny cudzysłowu (\\") zamiast znaków cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="323bf-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="323bf-113">Jeśli nie określono wartości, a następnie jest traktowana jako True.</span><span class="sxs-lookup"><span data-stu-id="323bf-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="323bf-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="323bf-114">Remarks</span></span>  
 <span data-ttu-id="323bf-115">`/define` Opcji jest efekt jest podobny do sposobu używania `#Const` dyrektywy preprocesora w pliku źródłowym, z wyjątkiem tego stałe zdefiniowane z `/define` są publiczne i dotyczą wszystkich plików w projekcie.</span><span class="sxs-lookup"><span data-stu-id="323bf-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="323bf-116">Można użyć symboli utworzone przez tę opcję z `#If`... `Then`... `#Else` dyrektywy warunkowo skompilować plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="323bf-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="323bf-117">`/d`jest krótka forma `/define`.</span><span class="sxs-lookup"><span data-stu-id="323bf-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="323bf-118">Można zdefiniować wiele symboli z `/define` za pomocą przecinka do oddzielania definicji symbolu.</span><span class="sxs-lookup"><span data-stu-id="323bf-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="323bf-119">Aby ustawić / define w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="323bf-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="323bf-120">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="323bf-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="323bf-121">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="323bf-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="323bf-122">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="323bf-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="323bf-123">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="323bf-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="323bf-124">3.  Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="323bf-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="323bf-125">4.  Zmodyfikuj wartość w **stałe niestandardowe** pole.</span><span class="sxs-lookup"><span data-stu-id="323bf-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="323bf-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="323bf-126">Example</span></span>  
 <span data-ttu-id="323bf-127">Poniższy kod definiuje, a następnie używa dwóch warunkowe stałe kompilatora.</span><span class="sxs-lookup"><span data-stu-id="323bf-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="323bf-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="323bf-128">See Also</span></span>  
 [<span data-ttu-id="323bf-129">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="323bf-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="323bf-130">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="323bf-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="323bf-131">#Const-dyrektywa</span><span class="sxs-lookup"><span data-stu-id="323bf-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="323bf-132">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="323bf-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
