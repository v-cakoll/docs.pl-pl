---
title: 'Wskazówki: Hosting formantu Windows Form w WPF z wykorzystaniem XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 2f13689a15e91ee0f80c0d7b6bc71c5f973b8333
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873153"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="ada11-102">Wskazówki: Hosting formantu Windows Form w WPF z wykorzystaniem XAML</span><span class="sxs-lookup"><span data-stu-id="ada11-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="ada11-103"> udostępnia wiele kontrolek z rozbudowanym zestawie funkcji.</span><span class="sxs-lookup"><span data-stu-id="ada11-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="ada11-104">Jednak czasami warto użyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów na Twoje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron.</span><span class="sxs-lookup"><span data-stu-id="ada11-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="ada11-105">Na przykład może mieć znaczne inwestycje w istniejących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, lub może być [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który oferuje unikatową funkcję.</span><span class="sxs-lookup"><span data-stu-id="ada11-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="ada11-106">W tym instruktażu dowiesz się, jak hostować formularzy Windows <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> kontrolować na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ada11-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="ada11-107">Aby uzyskać kompletny kod listę zadań przedstawione w niniejszym instruktażu, zobacz [Hosting kontrolki Windows Forms w WPF próbki przy użyciu XAML](https://go.microsoft.com/fwlink/?LinkID=160000).</span><span class="sxs-lookup"><span data-stu-id="ada11-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ada11-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ada11-108">Prerequisites</span></span>  
 <span data-ttu-id="ada11-109">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="ada11-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="ada11-110">.</span><span class="sxs-lookup"><span data-stu-id="ada11-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="ada11-111">Hostowanie kontrolki formularza Windows</span><span class="sxs-lookup"><span data-stu-id="ada11-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="ada11-112">Do hostowania maskedtextbox — formant</span><span class="sxs-lookup"><span data-stu-id="ada11-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="ada11-113">Utwórz projekt aplikacji WPF, o nazwie `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="ada11-113">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="ada11-114">Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="ada11-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="ada11-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="ada11-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="ada11-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="ada11-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="ada11-117">Otwieranie pliku MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ada11-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="ada11-118">W <xref:System.Windows.Window> elementu, Dodaj następujące mapowanie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ada11-118">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="ada11-119">`wf` Mapowanie przestrzeni nazw ustanawia odwołanie do zestawu, który zawiera kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ada11-119">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="ada11-120">W <xref:System.Windows.Controls.Grid> elementu Dodawanie następujące XAML.</span><span class="sxs-lookup"><span data-stu-id="ada11-120">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="ada11-121"><xref:System.Windows.Forms.MaskedTextBox> Formant zostanie utworzony jako element podrzędny elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ada11-121">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="ada11-122">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="ada11-122">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada11-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ada11-123">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="ada11-124">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ada11-124">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="ada11-125">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="ada11-125">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="ada11-126">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="ada11-126">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="ada11-127">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ada11-127">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="ada11-128">Kontrolki formularzy Windows Forms i równoważne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="ada11-128">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="ada11-129">Hosting kontrolki Windows Forms w WPF za pomocą przykładowych XAML</span><span class="sxs-lookup"><span data-stu-id="ada11-129">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
