---
title: 'Porady: stosowanie przycinania za pomocą obszaru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: bfc40d985ec12a30b73935ace7ef034aadbd5385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522099"
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="c70b8-102">Porady: stosowanie przycinania za pomocą obszaru</span><span class="sxs-lookup"><span data-stu-id="c70b8-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="c70b8-103">Jedna z właściwości obiektu <xref:System.Drawing.Graphics> klasy jest obszar przycinania.</span><span class="sxs-lookup"><span data-stu-id="c70b8-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="c70b8-104">Rysowanie wszystkie wykonywane przez dany <xref:System.Drawing.Graphics> obiektu jest ograniczony do obszar przycinania na tym <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c70b8-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c70b8-105">Można ustawić obszar przycinania przez wywołanie metody <xref:System.Drawing.Graphics.SetClip%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c70b8-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c70b8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c70b8-106">Example</span></span>  
 <span data-ttu-id="c70b8-107">Poniższy przykład tworzy ścieżki, która składa się z jednego wielokąta.</span><span class="sxs-lookup"><span data-stu-id="c70b8-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="c70b8-108">Następnie kod tworzy regionu, w oparciu o tej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="c70b8-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="c70b8-109">Region jest przekazywana do <xref:System.Drawing.Graphics.SetClip%2A> metody <xref:System.Drawing.Graphics> obiektu, a następnie dwa ciągi są rysowane.</span><span class="sxs-lookup"><span data-stu-id="c70b8-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="c70b8-110">Na poniższej ilustracji przedstawiono przyciętą ciągów.</span><span class="sxs-lookup"><span data-stu-id="c70b8-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="c70b8-111">![Klip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="c70b8-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c70b8-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c70b8-112">Compiling the Code</span></span>  
 <span data-ttu-id="c70b8-113">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c70b8-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70b8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c70b8-114">See Also</span></span>  
 [<span data-ttu-id="c70b8-115">Regiony w GDI+</span><span class="sxs-lookup"><span data-stu-id="c70b8-115">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="c70b8-116">Używanie regionów</span><span class="sxs-lookup"><span data-stu-id="c70b8-116">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
