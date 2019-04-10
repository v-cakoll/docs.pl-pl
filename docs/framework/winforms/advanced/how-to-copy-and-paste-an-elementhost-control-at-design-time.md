---
title: 'Instrukcje: Kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: e8bc4aa4ecd2bff2981b7d4faf1e270337f346e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59346213"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="910e6-102">Instrukcje: Kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="910e6-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="910e6-103">Ta procedura pokazuje, jak kopiowanie kontrolki Windows Presentation Foundation (WPF) w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="910e6-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="910e6-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="910e6-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="910e6-105">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="910e6-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="910e6-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="910e6-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="910e6-107">Kopiowanie i wklejanie formantu ElementHost w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="910e6-107">To copy and paste an ElementHost control at design time</span></span>  
  
1. <span data-ttu-id="910e6-108">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="910e6-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="910e6-109">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="910e6-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="910e6-110">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="910e6-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2. <span data-ttu-id="910e6-111">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `UserControl1` do `200`.</span><span class="sxs-lookup"><span data-stu-id="910e6-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3. <span data-ttu-id="910e6-112">Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwość `Blue`.</span><span class="sxs-lookup"><span data-stu-id="910e6-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4. <span data-ttu-id="910e6-113">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="910e6-113">Build the project.</span></span>  
  
5. <span data-ttu-id="910e6-114">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="910e6-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6. <span data-ttu-id="910e6-115">Z **przybornika**, przeciągnij wystąpienie `UserControl1` na formularz.</span><span class="sxs-lookup"><span data-stu-id="910e6-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="910e6-116">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="910e6-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7. <span data-ttu-id="910e6-117">Za pomocą `elementHost1` zaznaczone, naciśnij klawisze CTRL + C, aby skopiować go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="910e6-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8. <span data-ttu-id="910e6-118">Naciśnij klawisze CTRL + V, aby wkleić skopiowanych formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="910e6-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="910e6-119">Nowy <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost2` jest tworzony w formularzu.</span><span class="sxs-lookup"><span data-stu-id="910e6-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="910e6-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="910e6-120">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="910e6-121">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="910e6-121">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="910e6-122">Korzystanie z formantów WPF</span><span class="sxs-lookup"><span data-stu-id="910e6-122">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="910e6-123">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="910e6-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
