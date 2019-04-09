---
title: 'Instrukcje: Stosowanie przycinania za pomocą obszaru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: cf60b32df805a49f8da2760332dc32e34209f6dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163738"
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="f4d25-102">Instrukcje: Stosowanie przycinania za pomocą obszaru</span><span class="sxs-lookup"><span data-stu-id="f4d25-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="f4d25-103">Jedna z właściwości obiektu <xref:System.Drawing.Graphics> klasa jest obszar przycinania.</span><span class="sxs-lookup"><span data-stu-id="f4d25-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="f4d25-104">Wszystkie rysunku, wykonywane przez dany <xref:System.Drawing.Graphics> obiektu jest ograniczona do regionu klipu tego <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4d25-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="f4d25-105">Można ustawić obszar przycinania, wywołując <xref:System.Drawing.Graphics.SetClip%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f4d25-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4d25-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4d25-106">Example</span></span>  
 <span data-ttu-id="f4d25-107">Poniższy przykład tworzy ścieżkę, która składa się z pojedynczego wielokąta.</span><span class="sxs-lookup"><span data-stu-id="f4d25-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="f4d25-108">Następnie kod tworzy regionu, w oparciu o tej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="f4d25-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="f4d25-109">Region jest przekazywany do <xref:System.Drawing.Graphics.SetClip%2A> metody <xref:System.Drawing.Graphics> obiektu, a następnie dwa ciągi są rysowane.</span><span class="sxs-lookup"><span data-stu-id="f4d25-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="f4d25-110">Poniższa ilustracja przedstawia obciętych ciągów.</span><span class="sxs-lookup"><span data-stu-id="f4d25-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="f4d25-111">![Clip](./media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="f4d25-111">![Clip](./media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4d25-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f4d25-112">Compiling the Code</span></span>  
 <span data-ttu-id="f4d25-113">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f4d25-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d25-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4d25-114">See also</span></span>

- [<span data-ttu-id="f4d25-115">Regiony w GDI+</span><span class="sxs-lookup"><span data-stu-id="f4d25-115">Regions in GDI+</span></span>](regions-in-gdi.md)
- [<span data-ttu-id="f4d25-116">Używanie regionów</span><span class="sxs-lookup"><span data-stu-id="f4d25-116">Using Regions</span></span>](using-regions.md)
