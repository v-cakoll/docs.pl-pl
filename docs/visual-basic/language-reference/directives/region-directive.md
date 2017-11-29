---
title: '#<a name="region-directive"></a>Dyrektywy regionu'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb308da6ad0ca6243f14e0d825ed7eb005d622bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="region-directive"></a><span data-ttu-id="890a7-102">#Region — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="890a7-102">#Region Directive</span></span>
<span data-ttu-id="890a7-103">Zwija i ukrywa sekcje kodu w plikach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="890a7-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="890a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="890a7-104">Syntax</span></span>  
  
```  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="890a7-105">Części</span><span class="sxs-lookup"><span data-stu-id="890a7-105">Parts</span></span>  
  
|<span data-ttu-id="890a7-106">Termin</span><span class="sxs-lookup"><span data-stu-id="890a7-106">Term</span></span>|<span data-ttu-id="890a7-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="890a7-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="890a7-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="890a7-108">Required.</span></span> <span data-ttu-id="890a7-109">Ciąg, który działa jako tytuł regionu, gdy jest zwinięte.</span><span class="sxs-lookup"><span data-stu-id="890a7-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="890a7-110">Regiony są zwijane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="890a7-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="890a7-111">Kończy `#Region` bloku.</span><span class="sxs-lookup"><span data-stu-id="890a7-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="890a7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="890a7-112">Remarks</span></span>  
 <span data-ttu-id="890a7-113">Użyj `#Region` dyrektywy bloku kodu, aby rozwinąć lub zwinąć podczas korzystania z funkcji zwijania edytora kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="890a7-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="890a7-114">Można umieścić lub *zagnieździć*, regionów, w ramach innych regionów, do grupowania podobnych regionów.</span><span class="sxs-lookup"><span data-stu-id="890a7-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="890a7-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="890a7-115">Example</span></span>  
 <span data-ttu-id="890a7-116">W tym przykładzie użyto `#Region` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="890a7-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="890a7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="890a7-117">See Also</span></span>  
 [<span data-ttu-id="890a7-118">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="890a7-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="890a7-119">Tworzenie konspektu</span><span class="sxs-lookup"><span data-stu-id="890a7-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="890a7-120">Porady: zwijanie i ukrywanie fragmentów kodu</span><span class="sxs-lookup"><span data-stu-id="890a7-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
