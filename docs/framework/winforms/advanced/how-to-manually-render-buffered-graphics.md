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
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931835"
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="5f297-102">Instrukcje: Ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="5f297-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="5f297-103">Jeśli zarządzasz własną buforowaną grafiki, musisz mieć możliwość tworzenia i renderowania buforów graficznych.</span><span class="sxs-lookup"><span data-stu-id="5f297-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="5f297-104">Można utworzyć wystąpienia <xref:System.Drawing.BufferedGraphics> klasy skojarzonej z powierzchniami rysowania na ekranie przez <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="5f297-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="5f297-105">Ta metoda tworzy <xref:System.Drawing.BufferedGraphics> wystąpienie skojarzone z określoną powierzchnią renderowania, taką jak formularz lub kontrolka.</span><span class="sxs-lookup"><span data-stu-id="5f297-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="5f297-106">Po utworzeniu <xref:System.Drawing.BufferedGraphics> wystąpienia możesz narysować grafikę do bufora, który reprezentuje <xref:System.Drawing.BufferedGraphics.Graphics%2A> przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="5f297-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="5f297-107">Po wykonaniu wszystkich operacji graficznych można skopiować zawartość bufora na ekran, wywołując <xref:System.Drawing.BufferedGraphics.Render%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="5f297-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f297-108">Jeśli wykonujesz własne renderowanie, zużycie pamięci zwiększy się, ale wzrost może być nieznaczny.</span><span class="sxs-lookup"><span data-stu-id="5f297-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="5f297-109">Aby ręcznie wyświetlić buforowaną grafikę</span><span class="sxs-lookup"><span data-stu-id="5f297-109">To manually display buffered graphics</span></span>  
  
1. <span data-ttu-id="5f297-110">Uzyskaj odwołanie do wystąpienia <xref:System.Drawing.BufferedGraphicsContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="5f297-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="5f297-111">Aby uzyskać więcej informacji, zobacz [jak: Ręcznie Zarządzaj buforowaną](how-to-manually-manage-buffered-graphics.md)grafiką.</span><span class="sxs-lookup"><span data-stu-id="5f297-111">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2. <span data-ttu-id="5f297-112">Utwórz wystąpienie <xref:System.Drawing.BufferedGraphics> klasy, <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> wywołując metodę, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5f297-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="5f297-113">Rysowanie grafiki do buforu grafiki przez ustawienie <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5f297-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="5f297-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5f297-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. <span data-ttu-id="5f297-115">Po zakończeniu wszystkich operacji rysowania w buforze grafiki Wywołaj <xref:System.Drawing.BufferedGraphics.Render%2A> metodę w celu renderowania buforu, na powierzchnię rysowania skojarzoną z tym buforem lub z określoną powierzchnią rysowania, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5f297-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. <span data-ttu-id="5f297-116">Po zakończeniu renderowania grafiki Wywołaj `Dispose` metodę <xref:System.Drawing.BufferedGraphics> w wystąpieniu, aby zwolnić zasoby systemowe.</span><span class="sxs-lookup"><span data-stu-id="5f297-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="5f297-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f297-117">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="5f297-118">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="5f297-118">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="5f297-119">Instrukcje: Ręcznie Zarządzaj buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="5f297-119">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)
