---
title: 'Przewodnik: hostowanie kontrolki Windows Forms w WPF z wykorzystaniem języka XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 10554145de9725bb4cfc655ed88195dce28d739c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032113"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="baaa1-102">Przewodnik: hostowanie kontrolki Windows Forms w WPF z wykorzystaniem języka XAML</span><span class="sxs-lookup"><span data-stu-id="baaa1-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="baaa1-103">udostępnia wiele kontrolek z rozbudowanym zestawie funkcji.</span><span class="sxs-lookup"><span data-stu-id="baaa1-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="baaa1-104">Jednak czasami warto użyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów na Twoje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron.</span><span class="sxs-lookup"><span data-stu-id="baaa1-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="baaa1-105">Na przykład może mieć znaczne inwestycje w istniejących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, lub może być [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który oferuje unikatową funkcję.</span><span class="sxs-lookup"><span data-stu-id="baaa1-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="baaa1-106">W tym instruktażu dowiesz się, jak hostować formularzy Windows <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> kontrolować na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="baaa1-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="baaa1-107">Aby uzyskać kompletny kod listę zadań przedstawione w niniejszym instruktażu, zobacz [Hosting kontrolki Windows Forms w WPF próbki przy użyciu XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="baaa1-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="baaa1-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="baaa1-108">Prerequisites</span></span>  

<span data-ttu-id="baaa1-109">Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="baaa1-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="baaa1-110">Hostowanie kontrolki formularza Windows</span><span class="sxs-lookup"><span data-stu-id="baaa1-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="baaa1-111">Do hostowania maskedtextbox — formant</span><span class="sxs-lookup"><span data-stu-id="baaa1-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="baaa1-112">Utwórz projekt aplikacji WPF, o nazwie `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="baaa1-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="baaa1-113">Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="baaa1-113">Add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="baaa1-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="baaa1-114">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="baaa1-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="baaa1-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="baaa1-116">Otwieranie pliku MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="baaa1-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4. <span data-ttu-id="baaa1-117">W <xref:System.Windows.Window> elementu, Dodaj następujące mapowanie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="baaa1-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="baaa1-118">`wf` Mapowanie przestrzeni nazw ustanawia odwołanie do zestawu, który zawiera kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="baaa1-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="baaa1-119">W <xref:System.Windows.Controls.Grid> elementu Dodawanie następujące XAML.</span><span class="sxs-lookup"><span data-stu-id="baaa1-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="baaa1-120"><xref:System.Windows.Forms.MaskedTextBox> Formant zostanie utworzony jako element podrzędny elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="baaa1-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="baaa1-121">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="baaa1-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaa1-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baaa1-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="baaa1-123">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="baaa1-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="baaa1-124">Przewodnik: Hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="baaa1-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="baaa1-125">Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="baaa1-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="baaa1-126">Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="baaa1-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="baaa1-127">Kontrolki formularzy Windows Forms i równoważne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="baaa1-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="baaa1-128">Hosting kontrolki Windows Forms w WPF za pomocą przykładowych XAML</span><span class="sxs-lookup"><span data-stu-id="baaa1-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
