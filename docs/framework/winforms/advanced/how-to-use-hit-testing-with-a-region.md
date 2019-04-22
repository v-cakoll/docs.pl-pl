---
title: 'Instrukcje: Stosowanie testowania trafień za pomocą obszaru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 136f15f1364fb2aed791b4a61d0f11411b055967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150504"
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="c4b19-102">Instrukcje: Stosowanie testowania trafień za pomocą obszaru</span><span class="sxs-lookup"><span data-stu-id="c4b19-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="c4b19-103">Testowanie trafień ma na celu określenia, czy kursor znajduje się za pośrednictwem danego obiektu, takie jak ikony lub przycisku.</span><span class="sxs-lookup"><span data-stu-id="c4b19-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b19-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4b19-104">Example</span></span>  
 <span data-ttu-id="c4b19-105">Poniższy przykład tworzy obszar ukształtowane plus tworzymy sumę dwóch regionach prostokątny.</span><span class="sxs-lookup"><span data-stu-id="c4b19-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="c4b19-106">Przyjęto założenie, że zmienna `point` jest przechowywana lokalizacja kliknij najbardziej aktualne.</span><span class="sxs-lookup"><span data-stu-id="c4b19-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="c4b19-107">Kod sprawdza, czy `point` znajduje się w regionie kształcie na znak plus.</span><span class="sxs-lookup"><span data-stu-id="c4b19-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="c4b19-108">Jeśli punkt znajduje się w regionie (naciśnij klawisz), region jest wypełniony nieprzezroczyste pędzla czerwony.</span><span class="sxs-lookup"><span data-stu-id="c4b19-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="c4b19-109">W przeciwnym razie region jest wypełniony półprzezroczystych pędzli czerwony.</span><span class="sxs-lookup"><span data-stu-id="c4b19-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4b19-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c4b19-110">Compiling the Code</span></span>  
 <span data-ttu-id="c4b19-111">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c4b19-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b19-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4b19-112">See also</span></span>

- <xref:System.Drawing.Region>
- [<span data-ttu-id="c4b19-113">Regiony w GDI+</span><span class="sxs-lookup"><span data-stu-id="c4b19-113">Regions in GDI+</span></span>](regions-in-gdi.md)
- [<span data-ttu-id="c4b19-114">Instrukcje: Stosowanie przycinania za pomocą obszaru</span><span class="sxs-lookup"><span data-stu-id="c4b19-114">How to: Use Clipping with a Region</span></span>](how-to-use-clipping-with-a-region.md)
