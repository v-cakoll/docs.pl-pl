---
title: Kontrolki Windows Forms i ekwiwalentne kontrolki WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: 0daa399e2d000a228773ee20f157af7439f7acbb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396670"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="15f22-102">Kontrolki Windows Forms i ekwiwalentne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="15f22-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="15f22-103">Wiele [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki ma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolek, ale niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki ma odpowiedników w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15f22-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="15f22-104">W tym temacie przedstawiono porównanie typów formantów, udostępniane przez te dwie technologie.</span><span class="sxs-lookup"><span data-stu-id="15f22-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="15f22-105">Współdziałanie z hostem zawsze można użyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, które nie mają odpowiedniki w swojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— aplikacje oparte na.</span><span class="sxs-lookup"><span data-stu-id="15f22-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="15f22-106">W poniższej tabeli przedstawiono, które [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek i składników ma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroluje funkcji.</span><span class="sxs-lookup"><span data-stu-id="15f22-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="15f22-107">Formant Formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="15f22-107">Windows Forms control</span></span>|<span data-ttu-id="15f22-108">Równoważne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="15f22-108">WPF equivalent control</span></span>|<span data-ttu-id="15f22-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15f22-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="15f22-110">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<span data-ttu-id="15f22-111"><xref:System.Windows.Controls.ListBox> za pomocą kompozycji.</span><span class="sxs-lookup"><span data-stu-id="15f22-111"><xref:System.Windows.Controls.ListBox> with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="15f22-112">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<span data-ttu-id="15f22-113"><xref:System.Windows.Controls.ComboBox> nie obsługuje automatycznego uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="15f22-113"><xref:System.Windows.Controls.ComboBox> does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<span data-ttu-id="15f22-114"><xref:System.Windows.Controls.TextBox> oraz dwóch <xref:System.Windows.Controls.Primitives.RepeatButton> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="15f22-114"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="15f22-115">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<span data-ttu-id="15f22-116"><xref:System.Windows.Controls.WrapPanel> lub <xref:System.Windows.Controls.StackPanel></span><span class="sxs-lookup"><span data-stu-id="15f22-116"><xref:System.Windows.Controls.WrapPanel> or <xref:System.Windows.Controls.StackPanel></span></span>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="15f22-117">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="15f22-118">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<span data-ttu-id="15f22-119"><xref:System.Windows.Window> nie obsługuje okien podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="15f22-119"><xref:System.Windows.Window> does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="15f22-120">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-120">No equivalent control.</span></span>|<span data-ttu-id="15f22-121">Brak pomocy F1.</span><span class="sxs-lookup"><span data-stu-id="15f22-121">No F1 Help.</span></span> <span data-ttu-id="15f22-122">"Co to jest" pomocy został zastąpiony etykietek narzędzi.</span><span class="sxs-lookup"><span data-stu-id="15f22-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="15f22-123">Przewijanie jest wbudowana w kontenerze kontrolek.</span><span class="sxs-lookup"><span data-stu-id="15f22-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="15f22-124">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="15f22-125">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-125">No equivalent control.</span></span>|<span data-ttu-id="15f22-126">Możesz użyć <xref:System.Windows.Documents.Hyperlink> klasy hosta hiperlinki w dowolnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="15f22-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="15f22-127"><xref:System.Windows.Controls.ListView> Kontroli udostępnia widok szczegółów tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="15f22-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="15f22-128">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<span data-ttu-id="15f22-129"><xref:System.Windows.Controls.Menu> Nadawanie stylów kontrolek przybliżyć zachowania i wyglądu <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="15f22-129"><xref:System.Windows.Controls.Menu> control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="15f22-130">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<span data-ttu-id="15f22-131"><xref:System.Windows.Controls.TextBox> oraz dwóch <xref:System.Windows.Controls.Primitives.RepeatButton> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="15f22-131"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="15f22-132"><xref:Microsoft.Win32.OpenFileDialog> Klasa jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otokę [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="15f22-133">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="15f22-134">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="15f22-135">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="15f22-136">Brak równoważne kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="15f22-137"><xref:Microsoft.Win32.SaveFileDialog> Klasa jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otokę [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="15f22-138"><xref:System.Windows.Controls.ToolBar> za pomocą kompozycji.</span><span class="sxs-lookup"><span data-stu-id="15f22-138"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="15f22-139"><xref:System.Windows.Controls.ToolBar> za pomocą kompozycji.</span><span class="sxs-lookup"><span data-stu-id="15f22-139"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<span data-ttu-id="15f22-140"><xref:System.Windows.Controls.ToolBar> za pomocą kompozycji.</span><span class="sxs-lookup"><span data-stu-id="15f22-140"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<span data-ttu-id="15f22-141"><xref:System.Windows.Controls.ToolBar> za pomocą kompozycji.</span><span class="sxs-lookup"><span data-stu-id="15f22-141"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="15f22-142">Przewijanie jest wbudowana w kontenerze kontrolek.</span><span class="sxs-lookup"><span data-stu-id="15f22-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<span data-ttu-id="15f22-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="15f22-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span></span>|<span data-ttu-id="15f22-144"><xref:System.Windows.Controls.Frame> Kontroli może obsługiwać stron HTML.</span><span class="sxs-lookup"><span data-stu-id="15f22-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="15f22-145">Począwszy od [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> kontroli może obsługiwać strony HTML, a także tworzy kopię <xref:System.Windows.Controls.Frame> kontroli.</span><span class="sxs-lookup"><span data-stu-id="15f22-145">Starting in the [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15f22-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15f22-146">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="15f22-147">WPF Designer for Windows Forms deweloperów</span><span class="sxs-lookup"><span data-stu-id="15f22-147">WPF Designer for Windows Forms Developers</span></span>](https://msdn.microsoft.com/library/47ad0909-e89b-4996-b4ac-874d929f94ca)  
 [<span data-ttu-id="15f22-148">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="15f22-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="15f22-149">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15f22-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="15f22-150">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="15f22-150">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
