---
title: 'Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: ef05b72b33d3f28d1811389dfae65554a1567d43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096956"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="6c4ce-102">Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek</span><span class="sxs-lookup"><span data-stu-id="6c4ce-102">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="6c4ce-103">Podwójnego buforowania używa bufora pamięci, aby rozwiązywać problemy migotania skojarzonych wiele operacji malowania.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-103">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="6c4ce-104">Po włączeniu podwójnego buforowania wszystkich operacji malowania najpierw są renderowane w buforze pamięci zamiast powierzchni do rysowania na ekranie.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-104">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="6c4ce-105">Po ukończeniu wszystkich operacji malowania bufora pamięci jest kopiowana bezpośrednio na powierzchni do rysowania skojarzone z nią.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-105">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="6c4ce-106">Ponieważ grafiki tylko jedna operacja jest wykonywana na ekranie, obraz migotanie skojarzone z operacjami złożonego rysowania zostanie wyeliminowany. W przypadku większości aplikacji domyślnej podwójnego buforowania podał [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] udostępni najlepsze rezultaty.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-106">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] will provide the best results.</span></span> <span data-ttu-id="6c4ce-107">Standardowych kontrolek Windows Forms są double buforowana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-107">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="6c4ce-108">Można włączyć domyślny podwójnego buforowania w formularzach i autorstwa formantów na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-108">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="6c4ce-109">Możesz albo zestaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true`, można też wywołać <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flaga `true`.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-109">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="6c4ce-110">Obie metody zostanie włączony, domyślne podwójnego buforowania danych formularza lub formantu i podaj renderowania pozbawionej migotania grafiki.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-110">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="6c4ce-111">Wywoływanie <xref:System.Windows.Forms.Control.SetStyle%2A> metoda jest zalecana tylko w przypadku kontrolek niestandardowych, dla których ma napisany cały kod renderowania.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-111">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="6c4ce-112">Dla bardziej zaawansowanych podwójnego buforowania scenariuszach, na przykład animacji lub zarządzanie zaawansowanej pamięci można zaimplementować własną podwójnego buforowania logikę.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-112">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="6c4ce-113">Aby uzyskać więcej informacji, zobacz [jak: Ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="6c4ce-113">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="6c4ce-114">Aby Zmniejszanie migotania</span><span class="sxs-lookup"><span data-stu-id="6c4ce-114">To reduce flicker</span></span>  
  
-   <span data-ttu-id="6c4ce-115">Ustaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-115">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="6c4ce-116">\- lub —</span><span class="sxs-lookup"><span data-stu-id="6c4ce-116">\- or -</span></span>  
  
-   <span data-ttu-id="6c4ce-117">Wywołaj <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flaga `true`.</span><span class="sxs-lookup"><span data-stu-id="6c4ce-117">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="6c4ce-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c4ce-118">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="6c4ce-119">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="6c4ce-119">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="6c4ce-120">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6c4ce-120">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
