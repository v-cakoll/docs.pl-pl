---
title: '#Dyrektywa #Region'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83ceac7d73eff23e16c5f6efb1c4eb8a2210ee2c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="region-directive"></a><span data-ttu-id="3f05f-102">#Region — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="3f05f-102">#Region Directive</span></span>
<span data-ttu-id="3f05f-103">Zwija i ukrywa sekcje kodu w plikach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3f05f-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f05f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f05f-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="3f05f-105">Części</span><span class="sxs-lookup"><span data-stu-id="3f05f-105">Parts</span></span>  
  
|<span data-ttu-id="3f05f-106">Termin</span><span class="sxs-lookup"><span data-stu-id="3f05f-106">Term</span></span>|<span data-ttu-id="3f05f-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="3f05f-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="3f05f-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="3f05f-108">Required.</span></span> <span data-ttu-id="3f05f-109">Ciąg, który funkcjonuje jako tytuł regionu, gdy jest zwinięty.</span><span class="sxs-lookup"><span data-stu-id="3f05f-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="3f05f-110">Regiony są domyślnie zwinięte.</span><span class="sxs-lookup"><span data-stu-id="3f05f-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="3f05f-111">Kończy blok `#Region`.</span><span class="sxs-lookup"><span data-stu-id="3f05f-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f05f-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f05f-112">Remarks</span></span>  
 <span data-ttu-id="3f05f-113">Dyrektywa `#Region` służy do określania bloku kodu, który będzie rozwijany lub zwijany podczas korzystania z funkcji zwijania w edytorze kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f05f-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="3f05f-114">Regiony można umieszczać lub *zagnieżdżać* w innych regionach w celu grupowania podobnych regionów.</span><span class="sxs-lookup"><span data-stu-id="3f05f-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f05f-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f05f-115">Example</span></span>  
 <span data-ttu-id="3f05f-116">Dyrektywa `#Region` została użyta w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3f05f-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3f05f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f05f-117">See Also</span></span>  
 [<span data-ttu-id="3f05f-118">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="3f05f-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="3f05f-119">Obramowanie</span><span class="sxs-lookup"><span data-stu-id="3f05f-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="3f05f-120">Instrukcje: zwijanie i ukrywanie fragmentów kodu</span><span class="sxs-lookup"><span data-stu-id="3f05f-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
