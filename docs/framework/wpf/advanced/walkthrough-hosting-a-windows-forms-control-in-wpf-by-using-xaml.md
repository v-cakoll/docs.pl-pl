---
title: Hostowanie kontrolki Windows Forms w WPF przy użyciu języka XAML
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: a0a88c39a25e5292365a6447cefdd8f31db5e5c3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744917"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="b401d-102">Wskazówki: Hosting formantu Windows Form w WPF z wykorzystaniem XAML</span><span class="sxs-lookup"><span data-stu-id="b401d-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="b401d-103">udostępnia wiele kontrolek z bogatym zestawem funkcji.</span><span class="sxs-lookup"><span data-stu-id="b401d-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="b401d-104">Czasami jednak może być konieczne użycie formantów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na stronach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b401d-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="b401d-105">Na przykład możesz mieć znaczną inwestycję w istniejące kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub mieć kontrolkę [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], która zapewnia unikalne funkcje.</span><span class="sxs-lookup"><span data-stu-id="b401d-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="b401d-106">W tym instruktażu pokazano, jak hostować Windows Forms kontrolę <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> na stronie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b401d-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="b401d-107">Aby zapoznać się z pełną listą zadań przedstawionych w tym instruktażu, zobacz [hostowanie kontrolki Windows Forms w WPF przy użyciu języka XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="b401d-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="b401d-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b401d-108">Prerequisites</span></span>  

<span data-ttu-id="b401d-109">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b401d-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="b401d-110">Hostowanie kontrolki Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b401d-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="b401d-111">Aby hostować formant formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="b401d-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="b401d-112">Utwórz projekt aplikacji WPF o nazwie `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="b401d-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="b401d-113">Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="b401d-113">Add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="b401d-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="b401d-114">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="b401d-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="b401d-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="b401d-116">Otwórz MainWindow. XAML w projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="b401d-116">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
4. <span data-ttu-id="b401d-117">W <xref:System.Windows.Window> elementu Dodaj następujące mapowanie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b401d-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="b401d-118">Mapowanie przestrzeni nazw `wf` ustanawia odwołanie do zestawu, który zawiera kontrolkę Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b401d-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="b401d-119">W <xref:System.Windows.Controls.Grid> element Dodaj następujący kod XAML.</span><span class="sxs-lookup"><span data-stu-id="b401d-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="b401d-120">Formant <xref:System.Windows.Forms.MaskedTextBox> jest tworzony jako element podrzędny kontrolki <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="b401d-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="b401d-121">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b401d-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b401d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b401d-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="b401d-123">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b401d-123">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="b401d-124">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="b401d-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="b401d-125">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="b401d-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="b401d-126">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b401d-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="b401d-127">Kontrolki formularzy Windows Forms i równoważne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="b401d-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="b401d-128">Hostowanie formantu Windows Forms w WPF przy użyciu przykładu XAML</span><span class="sxs-lookup"><span data-stu-id="b401d-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
