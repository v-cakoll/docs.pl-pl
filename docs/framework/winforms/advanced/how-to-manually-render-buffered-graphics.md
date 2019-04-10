---
title: 'Instrukcje: Ręczne renderowanie buforowanej grafiki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: 48dd1d76a42661df6ba642c032c991be4d6a2900
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339934"
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="51c92-102">Instrukcje: Ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="51c92-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="51c92-103">Jeśli zarządzasz buforowanej grafiki, należy mieć możliwość tworzenia i bufory grafiki typu renderowania.</span><span class="sxs-lookup"><span data-stu-id="51c92-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="51c92-104">Można utworzyć wystąpienia elementu <xref:System.Drawing.BufferedGraphics> klasę, która jest skojarzona z rysunku powierzchnie na ekranie, wywołując <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="51c92-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="51c92-105">Ta metoda tworzy <xref:System.Drawing.BufferedGraphics> wystąpienia, który jest skojarzony z powierzchnię renderowania określonego, takie jak formularz lub formant.</span><span class="sxs-lookup"><span data-stu-id="51c92-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="51c92-106">Po utworzeniu <xref:System.Drawing.BufferedGraphics> wypadku grafiki można narysować w buforze, czyli przedstawia liczbę za pomocą <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="51c92-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="51c92-107">Po wykonaniu wszystkich operacji graficznych, wywołując można skopiować zawartość buforu ekranu <xref:System.Drawing.BufferedGraphics.Render%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="51c92-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51c92-108">Możesz wykonać własne renderowania, spowoduje zwiększenie zużycie pamięci, chociaż wzrost mogą być tylko niewielka.</span><span class="sxs-lookup"><span data-stu-id="51c92-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="51c92-109">Aby ręcznie wyświetlić buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="51c92-109">To manually display buffered graphics</span></span>  
  
1. <span data-ttu-id="51c92-110">Uzyskaj odwołanie do wystąpienia <xref:System.Drawing.BufferedGraphicsContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="51c92-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="51c92-111">Aby uzyskać więcej informacji, zobacz [jak: Ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="51c92-111">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2. <span data-ttu-id="51c92-112">Utwórz wystąpienie obiektu <xref:System.Drawing.BufferedGraphics> klasy przez wywołanie metody <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metodzie, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="51c92-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="51c92-113">Rysowanie grafiki do buforu grafiki, ustawiając <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="51c92-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="51c92-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="51c92-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. <span data-ttu-id="51c92-115">Po ukończeniu wszystkich operacji rysowania do buforu grafiki, wywołaj <xref:System.Drawing.BufferedGraphics.Render%2A> metody do renderowania buforu, albo na powierzchni do rysowania skojarzone z tego buforu lub określony powierzchnię rysunku, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="51c92-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. <span data-ttu-id="51c92-116">Wywołania, gdy jesteś gotowy Renderowanie grafiki, `Dispose` metody <xref:System.Drawing.BufferedGraphics> wystąpienia można zwolnić zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="51c92-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="51c92-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51c92-117">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="51c92-118">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="51c92-118">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="51c92-119">Instrukcje: Ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="51c92-119">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)
