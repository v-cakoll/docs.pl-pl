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
ms.openlocfilehash: f4684e277335a119d41d5bd79d504ed37a76d6fc
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268474"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="fc4b4-102">Jak włączyć style Visual w aplikacji hybrydowej</span><span class="sxs-lookup"><span data-stu-id="fc4b4-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="fc4b4-103">W tym temacie przedstawiono sposób włączania [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual style na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowania hostowaną w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-103">This topic shows how to enable [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="fc4b4-104">Jeśli Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody, większość swojej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek będzie automatycznie używać stylów wizualnych, gdy aplikacja jest uruchamiana na [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc4b4-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles when your application is run on [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span> <span data-ttu-id="fc4b4-105">Aby uzyskać więcej informacji, zobacz [renderowanie kontrolek przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="fc4b4-105">For more information, see [Rendering Controls with Visual Styles](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="fc4b4-106">Aby uzyskać kompletny kod listę zadań przedstawionych w tym temacie, zobacz [Włączanie stylów wizualnych w przykładowej aplikacji hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="fc4b4-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="fc4b4-107">Włączanie Windows Forms stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="fc4b4-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="fc4b4-108">Aby włączyć stylów wizualnych Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc4b4-108">To enable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="fc4b4-109">Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikacji o nazwie `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2.  <span data-ttu-id="fc4b4-110">W Eksploratorze rozwiązań należy dodać odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="fc4b4-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="fc4b4-111">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="fc4b4-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="fc4b4-112">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="fc4b4-113">W przyborniku, kliknij dwukrotnie <xref:System.Windows.Controls.Grid> ikonę, aby umieścić <xref:System.Windows.Controls.Grid> element na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4.  <span data-ttu-id="fc4b4-114">W oknie właściwości ustaw wartości <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości **automatycznie**.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5.  <span data-ttu-id="fc4b4-115">W widoku projektu lub XAML, wybierz <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6.  <span data-ttu-id="fc4b4-116">W oknie dialogowym właściwości kliknij **zdarzenia** kartę.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-116">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="fc4b4-117">Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8.  <span data-ttu-id="fc4b4-118">W MainWindow.xaml.vb lub MainWindow.xaml.cs, Wstaw następujący kod do obsługi <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="fc4b4-119">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="fc4b4-120">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Kontroli jest malowane przy użyciu stylów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="fc4b4-121">Wyłączanie Windows Forms stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="fc4b4-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="fc4b4-122">Aby wyłączyć stylów wizualnych, po prostu usuń wywołanie funkcji <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="fc4b4-123">Aby wyłączyć stylów wizualnych Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc4b4-123">To disable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="fc4b4-124">Otwórz pliku MainWindow.xaml.vb lub MainWindow.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="fc4b4-125">Komentarz wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3.  <span data-ttu-id="fc4b4-126">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="fc4b4-127">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Kontroli jest malowany domyślnego stylu systemu.</span><span class="sxs-lookup"><span data-stu-id="fc4b4-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4b4-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc4b4-128">See Also</span></span>  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="fc4b4-129">Renderowanie kontrolek przy użyciu stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="fc4b4-129">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [<span data-ttu-id="fc4b4-130">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="fc4b4-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
