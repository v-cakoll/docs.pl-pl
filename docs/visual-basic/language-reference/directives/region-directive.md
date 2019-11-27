---
title: '#Dyrektywa #Region'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343793"
---
# <a name="region-directive"></a><span data-ttu-id="4da87-102">#Region — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="4da87-102">#Region Directive</span></span>

<span data-ttu-id="4da87-103">Zwija i ukrywa sekcje kodu w plikach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4da87-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4da87-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="4da87-105">Części</span><span class="sxs-lookup"><span data-stu-id="4da87-105">Parts</span></span>  
  
|<span data-ttu-id="4da87-106">Termin</span><span class="sxs-lookup"><span data-stu-id="4da87-106">Term</span></span>|<span data-ttu-id="4da87-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="4da87-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="4da87-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4da87-108">Required.</span></span> <span data-ttu-id="4da87-109">Ciąg, który funkcjonuje jako tytuł regionu, gdy jest zwinięty.</span><span class="sxs-lookup"><span data-stu-id="4da87-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="4da87-110">Regiony są domyślnie zwinięte.</span><span class="sxs-lookup"><span data-stu-id="4da87-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="4da87-111">Kończy blok `#Region`.</span><span class="sxs-lookup"><span data-stu-id="4da87-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4da87-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4da87-112">Remarks</span></span>  

 <span data-ttu-id="4da87-113">Użyj dyrektywy `#Region`, aby określić blok kodu do rozwinięcia lub zwinięcia przy użyciu funkcji tworzenia konspektu edytora Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4da87-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="4da87-114">Możesz umieszczać lub *zagnieżdżać*regiony w innych regionach, aby grupować podobne regiony jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="4da87-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4da87-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4da87-115">Example</span></span>  

 <span data-ttu-id="4da87-116">Ten przykład używa dyrektywy `#Region`.</span><span class="sxs-lookup"><span data-stu-id="4da87-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4da87-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4da87-117">See also</span></span>

- [<span data-ttu-id="4da87-118">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="4da87-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="4da87-119">Obramowanie</span><span class="sxs-lookup"><span data-stu-id="4da87-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="4da87-120">Instrukcje: zwijanie i ukrywanie fragmentów kodu</span><span class="sxs-lookup"><span data-stu-id="4da87-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
