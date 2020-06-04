---
title: '##Region, dyrektywa'
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
ms.openlocfilehash: cd53a6079c1564a8c73a0a1a6273fc166d18d3e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409946"
---
# <a name="region-directive"></a><span data-ttu-id="fe2fe-102">#Region — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="fe2fe-102">#Region Directive</span></span>

<span data-ttu-id="fe2fe-103">Zwija i ukrywa sekcje kodu w plikach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fe2fe-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe2fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe2fe-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="fe2fe-105">Części</span><span class="sxs-lookup"><span data-stu-id="fe2fe-105">Parts</span></span>  
  
|<span data-ttu-id="fe2fe-106">Termin</span><span class="sxs-lookup"><span data-stu-id="fe2fe-106">Term</span></span>|<span data-ttu-id="fe2fe-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="fe2fe-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="fe2fe-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fe2fe-108">Required.</span></span> <span data-ttu-id="fe2fe-109">Ciąg, który działa jako tytuł regionu, gdy jest zwinięty.</span><span class="sxs-lookup"><span data-stu-id="fe2fe-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="fe2fe-110">Regiony są domyślnie zwinięte.</span><span class="sxs-lookup"><span data-stu-id="fe2fe-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="fe2fe-111">Kończy `#Region` blok.</span><span class="sxs-lookup"><span data-stu-id="fe2fe-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe2fe-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe2fe-112">Remarks</span></span>  

 <span data-ttu-id="fe2fe-113">Użyj `#Region` dyrektywy, aby określić blok kodu do rozwinięcia lub zwinięcia przy użyciu funkcji tworzenia konspektu edytora Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="fe2fe-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="fe2fe-114">Możesz umieszczać lub *zagnieżdżać*regiony w innych regionach, aby grupować podobne regiony jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="fe2fe-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe2fe-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe2fe-115">Example</span></span>  

 <span data-ttu-id="fe2fe-116">Ten przykład używa `#Region` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="fe2fe-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="fe2fe-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe2fe-117">See also</span></span>

- [<span data-ttu-id="fe2fe-118">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="fe2fe-118">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="fe2fe-119">Tworzenie konspektu</span><span class="sxs-lookup"><span data-stu-id="fe2fe-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="fe2fe-120">Instrukcje: Zwijanie i ukrywanie fragmentów kodu</span><span class="sxs-lookup"><span data-stu-id="fe2fe-120">How to: Collapse and Hide Sections of Code</span></span>](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
