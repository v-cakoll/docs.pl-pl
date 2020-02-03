---
title: Zawijaj formant z elementu ToolStripControlHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: c7dbe042623006ed9501016669d6451ba0667cbc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728177"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="8100a-102">Porady: zawijanie formantu formularzy systemu Windows za pomocą elementu ToolStripControlHost</span><span class="sxs-lookup"><span data-stu-id="8100a-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="8100a-103"><xref:System.Windows.Forms.ToolStripControlHost> jest zaprojektowana w celu umożliwienia hostowania dowolnych kontrolek Windows Forms przy użyciu konstruktora <xref:System.Windows.Forms.ToolStripControlHost> lub poprzez rozszerzanie <xref:System.Windows.Forms.ToolStripControlHost> siebie.</span><span class="sxs-lookup"><span data-stu-id="8100a-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="8100a-104">Łatwiej jest otoczyć formant, rozszerzając <xref:System.Windows.Forms.ToolStripControlHost> i implementując właściwości i metody, które uwidaczniają często używane właściwości i metody formantu.</span><span class="sxs-lookup"><span data-stu-id="8100a-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="8100a-105">Możesz również uwidocznić zdarzenia dla formantu na poziomie <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="8100a-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="8100a-106">Aby hostować formant w elementu ToolStripControlHost przez wyprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8100a-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="8100a-107">Rozwiń <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="8100a-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="8100a-108">Zaimplementuj Konstruktor bez parametrów, który wywołuje konstruktora klasy bazowej przekazującej w żądanym formancie.</span><span class="sxs-lookup"><span data-stu-id="8100a-108">Implement a parameterless constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="8100a-109">Zadeklaruj Właściwość tego samego typu co zawinięty formant i zwróć `Control` jako poprawny typ kontrolki w metodzie dostępu właściwości.</span><span class="sxs-lookup"><span data-stu-id="8100a-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="8100a-110">Uwidocznij inne często używane właściwości i metody wbudowanej kontrolki z właściwościami i metodami w klasie rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="8100a-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="8100a-111">Opcjonalnie Zastąp <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>i <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> metody i Dodaj zdarzenia kontroli, które chcesz uwidocznić.</span><span class="sxs-lookup"><span data-stu-id="8100a-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="8100a-112">Podaj niezbędne Zawijanie dla zdarzeń, które chcesz uwidocznić.</span><span class="sxs-lookup"><span data-stu-id="8100a-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="8100a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8100a-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8100a-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8100a-114">Compiling the Code</span></span>  
  
<span data-ttu-id="8100a-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="8100a-115">This example requires:</span></span>
  
- <span data-ttu-id="8100a-116">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="8100a-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8100a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8100a-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="8100a-118">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="8100a-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="8100a-119">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="8100a-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="8100a-120">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="8100a-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
