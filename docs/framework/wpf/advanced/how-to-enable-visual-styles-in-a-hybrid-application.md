---
title: Jak włączyć style Visual w aplikacji hybrydowej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 251c53a8665d2eae7c3b5bb23b0a388009362dcc
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960115"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="d8a27-102">Jak włączyć style Visual w aplikacji hybrydowej</span><span class="sxs-lookup"><span data-stu-id="d8a27-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="d8a27-103">W tym temacie przedstawiono sposób włączania stylów wizualnych w formancie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hostowanym w aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8a27-103">This topic shows how to enable visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="d8a27-104">Jeśli aplikacja wywołuje metodę <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, większość kontrolek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] będzie automatycznie używać stylów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="d8a27-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles.</span></span> <span data-ttu-id="d8a27-105">Aby uzyskać więcej informacji, zobacz [renderowanie formantów przy użyciu stylów wizualnych](../../winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="d8a27-105">For more information, see [Rendering Controls with Visual Styles](../../winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="d8a27-106">Aby uzyskać pełną listę kodów zadań przedstawionych w tym temacie, zobacz [Włączanie stylów wizualnych w przykładowej aplikacji hybrydowej](https://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="d8a27-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="d8a27-107">Włączanie Windows Forms stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="d8a27-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="d8a27-108">Aby włączyć Windows Forms style wizualizacji</span><span class="sxs-lookup"><span data-stu-id="d8a27-108">To enable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="d8a27-109">Utwórz projekt aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o nazwie `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="d8a27-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2. <span data-ttu-id="d8a27-110">W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="d8a27-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="d8a27-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="d8a27-111">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="d8a27-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="d8a27-112">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="d8a27-113">W przyborniku kliknij dwukrotnie ikonę <xref:System.Windows.Controls.Grid>, aby umieścić element <xref:System.Windows.Controls.Grid> na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="d8a27-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4. <span data-ttu-id="d8a27-114">W okno Właściwości ustaw wartości właściwości <xref:System.Windows.FrameworkElement.Height%2A> i **<xref:System.Windows.FrameworkElement.Width%2A> na wartość**Auto.</span><span class="sxs-lookup"><span data-stu-id="d8a27-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5. <span data-ttu-id="d8a27-115">W widoku widok Projekt lub XAML wybierz <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="d8a27-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6. <span data-ttu-id="d8a27-116">W okno Właściwości kliknij kartę **zdarzenia** .</span><span class="sxs-lookup"><span data-stu-id="d8a27-116">In the Properties window, click the **Events** tab.</span></span>  
  
7. <span data-ttu-id="d8a27-117">Kliknij dwukrotnie zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="d8a27-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8. <span data-ttu-id="d8a27-118">W MainWindow. XAML. vb lub MainWindow.xaml.cs Wstaw następujący kod, aby obsłużyć zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="d8a27-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="d8a27-119">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d8a27-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="d8a27-120">Formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest malowany przy użyciu stylów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="d8a27-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="d8a27-121">Wyłączanie Windows Forms stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="d8a27-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="d8a27-122">Aby wyłączyć style wizualne, po prostu usuń wywołanie metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8a27-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="d8a27-123">Aby wyłączyć Windows Forms style wizualizacji</span><span class="sxs-lookup"><span data-stu-id="d8a27-123">To disable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="d8a27-124">Otwórz MainWindow. XAML. vb lub MainWindow.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d8a27-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2. <span data-ttu-id="d8a27-125">Dodaj komentarz do wywołania metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8a27-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3. <span data-ttu-id="d8a27-126">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d8a27-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="d8a27-127">Formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest malowany przy użyciu domyślnego stylu systemowego.</span><span class="sxs-lookup"><span data-stu-id="d8a27-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a27-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8a27-128">See also</span></span>

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="d8a27-129">Renderowanie kontrolek przy użyciu stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="d8a27-129">Rendering Controls with Visual Styles</span></span>](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [<span data-ttu-id="d8a27-130">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="d8a27-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
