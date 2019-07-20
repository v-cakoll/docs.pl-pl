---
title: 'Instrukcje: zawijanie kontrolki formularzy systemu Windows za pomocą elementu ToolStripControlHost'
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
ms.openlocfilehash: 6335d09a89225ae1e202a781a73bfd149608f5fc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364190"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="61a1f-102">Instrukcje: zawijanie kontrolki formularzy systemu Windows za pomocą elementu ToolStripControlHost</span><span class="sxs-lookup"><span data-stu-id="61a1f-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="61a1f-103"><xref:System.Windows.Forms.ToolStripControlHost>zaprojektowano w celu umożliwienia hostowania arbitralnych formantów Windows Forms <xref:System.Windows.Forms.ToolStripControlHost> przy użyciu konstruktora lub <xref:System.Windows.Forms.ToolStripControlHost> rozszerzając siebie.</span><span class="sxs-lookup"><span data-stu-id="61a1f-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="61a1f-104">Łatwiej jest otoczyć formant, rozszerzając <xref:System.Windows.Forms.ToolStripControlHost> i implementując właściwości i metody, które uwidaczniają często używane właściwości i metody formantu.</span><span class="sxs-lookup"><span data-stu-id="61a1f-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="61a1f-105">Możesz również uwidocznić zdarzenia dla formantu na <xref:System.Windows.Forms.ToolStripControlHost> poziomie.</span><span class="sxs-lookup"><span data-stu-id="61a1f-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="61a1f-106">Aby hostować formant w elementu ToolStripControlHost przez wyprowadzenie</span><span class="sxs-lookup"><span data-stu-id="61a1f-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="61a1f-107">Rozszerzona <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="61a1f-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="61a1f-108">Zaimplementuj Konstruktor bez parametrów, który wywołuje konstruktora klasy bazowej przekazującej w żądanym formancie.</span><span class="sxs-lookup"><span data-stu-id="61a1f-108">Implement a parameterless constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="61a1f-109">Zadeklaruj Właściwość tego samego typu co zawinięty formant i Return `Control` jako poprawny typ formantu w metodzie dostępu właściwości.</span><span class="sxs-lookup"><span data-stu-id="61a1f-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="61a1f-110">Uwidocznij inne często używane właściwości i metody wbudowanej kontrolki z właściwościami i metodami w klasie rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="61a1f-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="61a1f-111">Opcjonalnie Zastąp <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A> <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> metody i i Dodaj zdarzenia kontroli, które chcesz uwidocznić.</span><span class="sxs-lookup"><span data-stu-id="61a1f-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="61a1f-112">Podaj niezbędne Zawijanie dla zdarzeń, które chcesz uwidocznić.</span><span class="sxs-lookup"><span data-stu-id="61a1f-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="61a1f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="61a1f-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61a1f-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="61a1f-114">Compiling the Code</span></span>  
  
<span data-ttu-id="61a1f-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="61a1f-115">This example requires:</span></span>
  
- <span data-ttu-id="61a1f-116">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="61a1f-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a1f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61a1f-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="61a1f-118">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="61a1f-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="61a1f-119">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="61a1f-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="61a1f-120">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="61a1f-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
