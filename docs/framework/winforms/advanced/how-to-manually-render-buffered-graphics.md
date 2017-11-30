---
title: "Porady: ręczne renderowanie buforowanej grafiki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fd742e7fa2b7870b8988e889a0df2b18a240bd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="08187-102">Porady: ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="08187-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="08187-103">Jeśli zarządzasz buforowanej grafiki, należy mieć możliwość tworzenia i renderowania grafiki buforów.</span><span class="sxs-lookup"><span data-stu-id="08187-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="08187-104">Można utworzyć wystąpienia <xref:System.Drawing.BufferedGraphics> klasy, która jest skojarzona z rysunku powierzchni na ekranie, wywołując <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="08187-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="08187-105">Ta metoda tworzy <xref:System.Drawing.BufferedGraphics> wystąpienia, który jest skojarzony z powierzchnią określonego renderowania, takich jak formularz lub formant.</span><span class="sxs-lookup"><span data-stu-id="08187-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="08187-106">Po utworzeniu <xref:System.Drawing.BufferedGraphics> wystąpienia, można narysować grafiki w buforze reprezentuje za pośrednictwem <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="08187-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="08187-107">Po wykonaniu wszystkich operacji graficznych, wywołując można skopiować zawartość buforu ekranu <xref:System.Drawing.BufferedGraphics.Render%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="08187-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08187-108">Wykonywać własne renderowania, spowoduje zwiększenie zużycie pamięci, chociaż wzrost mogą być tylko niewielka.</span><span class="sxs-lookup"><span data-stu-id="08187-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="08187-109">Aby ręcznie wyświetlić buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="08187-109">To manually display buffered graphics</span></span>  
  
1.  <span data-ttu-id="08187-110">Uzyskać odwołania do wystąpienia <xref:System.Drawing.BufferedGraphicsContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="08187-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="08187-111">Aby uzyskać więcej informacji, zobacz [porady: ręczne zarządzanie buforowana grafika](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="08187-111">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2.  <span data-ttu-id="08187-112">Utwórz wystąpienie <xref:System.Drawing.BufferedGraphics> klasy przez wywołanie metody <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metody, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="08187-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="08187-113">Rysuj grafiki buforu grafiki przez ustawienie <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="08187-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="08187-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="08187-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  <span data-ttu-id="08187-115">Po ukończeniu wszystkich operacji rysowania do buforu grafiki, wywołaj <xref:System.Drawing.BufferedGraphics.Render%2A> metody do renderowania buforu, albo powierzchni rysowania skojarzonego z tym buforu, lub do określonej powierzchni rysowania, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="08187-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  <span data-ttu-id="08187-116">Po Zakończono renderowania grafiki wywołać `Dispose` metoda <xref:System.Drawing.BufferedGraphics> wystąpienia można zwolnić zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="08187-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="08187-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08187-117">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [<span data-ttu-id="08187-118">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="08187-118">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="08187-119">Porady: ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="08187-119">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
