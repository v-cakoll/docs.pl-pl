---
title: 'Instrukcje: Użyj testowania trafień za pomocą obszaru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 1866810b875063271e206da1fe5d6fc06f7b5de0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564308"
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="0a8d2-102">Instrukcje: Użyj testowania trafień za pomocą obszaru</span><span class="sxs-lookup"><span data-stu-id="0a8d2-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="0a8d2-103">Testowanie trafień ma na celu określenia, czy kursor znajduje się za pośrednictwem danego obiektu, takie jak ikony lub przycisku.</span><span class="sxs-lookup"><span data-stu-id="0a8d2-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a8d2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a8d2-104">Example</span></span>  
 <span data-ttu-id="0a8d2-105">Poniższy przykład tworzy obszar ukształtowane plus tworzymy sumę dwóch regionach prostokątny.</span><span class="sxs-lookup"><span data-stu-id="0a8d2-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="0a8d2-106">Przyjęto założenie, że zmienna `point` jest przechowywana lokalizacja kliknij najbardziej aktualne.</span><span class="sxs-lookup"><span data-stu-id="0a8d2-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="0a8d2-107">Kod sprawdza, czy `point` znajduje się w regionie kształcie na znak plus.</span><span class="sxs-lookup"><span data-stu-id="0a8d2-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="0a8d2-108">Jeśli punkt znajduje się w regionie (naciśnij klawisz), region jest wypełniony nieprzezroczyste pędzla czerwony.</span><span class="sxs-lookup"><span data-stu-id="0a8d2-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="0a8d2-109">W przeciwnym razie region jest wypełniony półprzezroczystych pędzli czerwony.</span><span class="sxs-lookup"><span data-stu-id="0a8d2-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0a8d2-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0a8d2-110">Compiling the Code</span></span>  
 <span data-ttu-id="0a8d2-111">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0a8d2-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8d2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a8d2-112">See also</span></span>
- <xref:System.Drawing.Region>
- [<span data-ttu-id="0a8d2-113">Regiony w GDI+</span><span class="sxs-lookup"><span data-stu-id="0a8d2-113">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)
- [<span data-ttu-id="0a8d2-114">Instrukcje: Stosowanie przycinania za pomocą obszaru</span><span class="sxs-lookup"><span data-stu-id="0a8d2-114">How to: Use Clipping with a Region</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
