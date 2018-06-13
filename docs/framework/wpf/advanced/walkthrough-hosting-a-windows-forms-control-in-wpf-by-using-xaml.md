---
title: 'Wskazówki: Hosting formantu Windows Form w WPF z wykorzystaniem XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: b55a51a7ca16416b6963c57395da2f2a88a55648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548587"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="a3d4b-102">Wskazówki: Hosting formantu Windows Form w WPF z wykorzystaniem XAML</span><span class="sxs-lookup"><span data-stu-id="a3d4b-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="a3d4b-103"> udostępnia wiele formantów z zestawem funkcji zaawansowanych.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="a3d4b-104">Jednak czasami warto użyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="a3d4b-105">Na przykład może mieć znaczne inwestycji w istniejących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, lub może być [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który udostępnia funkcje unikatowy.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="a3d4b-106">W tym przewodniku przedstawiono sposób hosta formularzy systemu Windows <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> kontrolować na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3d4b-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="a3d4b-107">Kompletny kod lista zadań wyświetlane w tym przewodniku, zobacz [hostowanie kontrolki formularza systemu Windows na platformie WPF przez przy użyciu przykładowych XAML](http://go.microsoft.com/fwlink/?LinkID=160000).</span><span class="sxs-lookup"><span data-stu-id="a3d4b-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](http://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a3d4b-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a3d4b-108">Prerequisites</span></span>  
 <span data-ttu-id="a3d4b-109">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="a3d4b-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="a3d4b-110">.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="a3d4b-111">Hostowanie kontrolki formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a3d4b-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="a3d4b-112">Na hoście maskedtextbox — formant</span><span class="sxs-lookup"><span data-stu-id="a3d4b-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="a3d4b-113">Utwórz projekt aplikacji WPF o nazwie `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-113">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="a3d4b-114">Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="a3d4b-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="a3d4b-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="a3d4b-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="a3d4b-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="a3d4b-117">Otwórz MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3d4b-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="a3d4b-118">W <xref:System.Windows.Window> elementu, Dodaj następujące mapowanie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-118">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="a3d4b-119">`wf` Mapowania przestrzeni nazw ustanawia odwołanie do zestawu, który zawiera kontrolki formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-119">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="a3d4b-120">W <xref:System.Windows.Controls.Grid> element Dodaj następujący kod XAML.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-120">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="a3d4b-121"><xref:System.Windows.Forms.MaskedTextBox> Formantu zostanie utworzona jako element podrzędny <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-121">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="a3d4b-122">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="a3d4b-122">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d4b-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3d4b-123">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="a3d4b-124">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="a3d4b-124">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="a3d4b-125">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="a3d4b-125">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="a3d4b-126">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="a3d4b-126">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="a3d4b-127">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a3d4b-127">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="a3d4b-128">Kontrolki formularzy Windows Forms i równoważne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="a3d4b-128">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="a3d4b-129">Hostowanie kontrolki formularza systemu Windows na platformie WPF przy użyciu przykładowych XAML</span><span class="sxs-lookup"><span data-stu-id="a3d4b-129">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160000)
