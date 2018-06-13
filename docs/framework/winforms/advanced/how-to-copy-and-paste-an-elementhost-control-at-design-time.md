---
title: 'Porady: kopiowanie i wklejanie formantu ElementHost w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 1a9938500287b3b44f13f0aa664da85b7fdb4675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524859"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="49488-102">Porady: kopiowanie i wklejanie formantu ElementHost w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="49488-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="49488-103">Ta procedura przedstawia sposób kopiowania formantu Windows Presentation Foundation (WPF) na formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="49488-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49488-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="49488-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="49488-105">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="49488-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="49488-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="49488-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="49488-107">Kopiowanie i wklejanie formantu ElementHost w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="49488-107">To copy and paste an ElementHost control at design time</span></span>  
  
1.  <span data-ttu-id="49488-108">Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> do projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="49488-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="49488-109">Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="49488-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="49488-110">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="49488-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="49488-111">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `UserControl1` do `200`.</span><span class="sxs-lookup"><span data-stu-id="49488-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3.  <span data-ttu-id="49488-112">Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości `Blue`.</span><span class="sxs-lookup"><span data-stu-id="49488-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4.  <span data-ttu-id="49488-113">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="49488-113">Build the project.</span></span>  
  
5.  <span data-ttu-id="49488-114">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="49488-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6.  <span data-ttu-id="49488-115">Z **przybornika**, przeciągnij wystąpienia `UserControl1` na formularzu.</span><span class="sxs-lookup"><span data-stu-id="49488-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="49488-116">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="49488-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7.  <span data-ttu-id="49488-117">Z `elementHost1` zaznaczone, naciśnij klawisze CTRL + C, aby skopiować go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="49488-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8.  <span data-ttu-id="49488-118">Naciśnij klawisze CTRL + V Aby wkleić skopiowanych kontrolki na formularzu.</span><span class="sxs-lookup"><span data-stu-id="49488-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="49488-119">Nowy <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost2` jest tworzony w formularzu.</span><span class="sxs-lookup"><span data-stu-id="49488-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49488-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49488-120">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="49488-121">Przewodnik: kopiowanie i wklejanie kontrolki ElementHost w oddzielnych formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49488-121">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [<span data-ttu-id="49488-122">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="49488-122">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="49488-123">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="49488-123">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="49488-124">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="49488-124">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
