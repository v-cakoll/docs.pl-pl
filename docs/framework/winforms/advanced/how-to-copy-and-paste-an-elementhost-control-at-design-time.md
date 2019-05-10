---
title: 'Instrukcje: Kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 0f3367deaaec04744a3f812d7f2d08047d7eb588
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211391"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="bbf61-102">Instrukcje: Kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="bbf61-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>

<span data-ttu-id="bbf61-103">Ta procedura pokazuje, jak kopiowanie kontrolki Windows Presentation Foundation (WPF) w formularzu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bbf61-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

## <a name="copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="bbf61-104">Kopiowanie i wklejanie formantu ElementHost w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="bbf61-104">Copy and paste an ElementHost control at design time</span></span>

1. <span data-ttu-id="bbf61-105">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bbf61-105">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="bbf61-106">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="bbf61-106">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="bbf61-107">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="bbf61-107">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="bbf61-108">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `UserControl1` do `200`.</span><span class="sxs-lookup"><span data-stu-id="bbf61-108">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>

3. <span data-ttu-id="bbf61-109">Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwość `Blue`.</span><span class="sxs-lookup"><span data-stu-id="bbf61-109">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

4. <span data-ttu-id="bbf61-110">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="bbf61-110">Build the project.</span></span>

5. <span data-ttu-id="bbf61-111">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="bbf61-111">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="bbf61-112">Z **przybornika**, przeciągnij wystąpienie `UserControl1` na formularz.</span><span class="sxs-lookup"><span data-stu-id="bbf61-112">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="bbf61-113">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="bbf61-113">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="bbf61-114">Za pomocą `elementHost1` zaznaczone, naciśnij klawisze CTRL + C, aby skopiować go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="bbf61-114">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>

8. <span data-ttu-id="bbf61-115">Naciśnij klawisze CTRL + V, aby wkleić skopiowanych formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="bbf61-115">Press CTRL+V to paste the copied control onto the form.</span></span>

   <span data-ttu-id="bbf61-116">Nowy <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost2` jest tworzony w formularzu.</span><span class="sxs-lookup"><span data-stu-id="bbf61-116">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbf61-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbf61-117">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="bbf61-118">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="bbf61-118">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="bbf61-119">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="bbf61-119">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="bbf61-120">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bbf61-120">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
