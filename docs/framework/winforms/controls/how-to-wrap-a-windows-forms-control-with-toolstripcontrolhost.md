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
ms.openlocfilehash: b90e47f9cd20d4f963f6223877cefc901f1c0667
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591565"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="6b37f-102">Instrukcje: zawijanie kontrolki formularzy systemu Windows za pomocą elementu ToolStripControlHost</span><span class="sxs-lookup"><span data-stu-id="6b37f-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="6b37f-103"><xref:System.Windows.Forms.ToolStripControlHost> zaprojektowana w celu umożliwienia obsługi dowolnego kontrolek Windows Forms przy użyciu <xref:System.Windows.Forms.ToolStripControlHost> konstruktora lub rozszerzając <xref:System.Windows.Forms.ToolStripControlHost> sam.</span><span class="sxs-lookup"><span data-stu-id="6b37f-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="6b37f-104">Ułatwia to zawijanie formantu, rozszerzając <xref:System.Windows.Forms.ToolStripControlHost> i implementowanie właściwości i metod, które uwidaczniają często używane, właściwości i metod formantu.</span><span class="sxs-lookup"><span data-stu-id="6b37f-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="6b37f-105">Można również udostępnić zdarzeń dla formantu w <xref:System.Windows.Forms.ToolStripControlHost> poziom.</span><span class="sxs-lookup"><span data-stu-id="6b37f-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="6b37f-106">Do hostowania kontrolki w pomocą elementu ToolStripControlHost przez tworzenie wartości pochodnych</span><span class="sxs-lookup"><span data-stu-id="6b37f-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="6b37f-107">Rozszerzanie <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="6b37f-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="6b37f-108">Implementuje domyślnego konstruktora wywołuje przekazywanie konstruktora klasy bazowej odpowiednią kontrolę.</span><span class="sxs-lookup"><span data-stu-id="6b37f-108">Implement a default constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="6b37f-109">Deklarowanie właściwości z tego samego typu co opakowana kontroli i zwracają `Control` jako poprawny typ kontrolki w właściwości metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="6b37f-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="6b37f-110">Uwidacznianie innych często używanych właściwości i metod kontroli opakowanej za pomocą właściwości i metody w klasie rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="6b37f-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="6b37f-111">Opcjonalnie można zastąpić <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, i <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> metod i dodawaj zdarzenia kontroli, chcesz udostępnić.</span><span class="sxs-lookup"><span data-stu-id="6b37f-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="6b37f-112">Podaj niezbędne zawijania dla zdarzeń, które chcesz udostępnić.</span><span class="sxs-lookup"><span data-stu-id="6b37f-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="6b37f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b37f-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b37f-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6b37f-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="6b37f-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6b37f-115">This example requires:</span></span>  
  
- <span data-ttu-id="6b37f-116">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6b37f-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6b37f-117">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6b37f-117">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6b37f-118">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b37f-118">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b37f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b37f-119">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="6b37f-120">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6b37f-120">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="6b37f-121">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="6b37f-121">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="6b37f-122">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="6b37f-122">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
