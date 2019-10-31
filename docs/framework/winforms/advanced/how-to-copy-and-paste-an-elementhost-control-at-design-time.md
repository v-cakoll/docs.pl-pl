---
title: 'Porady: kopiowanie i wklejanie formantu ElementHost w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197480"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="c94d2-102">Instrukcje: kopiowanie i wklejanie kontrolki ElementHost</span><span class="sxs-lookup"><span data-stu-id="c94d2-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="c94d2-103">Ta procedura pokazuje, jak skopiować formant Windows Presentation Foundation (WPF) w formularzu systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c94d2-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="c94d2-104">W programie Visual Studio Dodaj nowy <xref:System.Windows.Controls.UserControl> WPF do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c94d2-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="c94d2-105">Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c94d2-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c94d2-106">Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c94d2-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="c94d2-107">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> `UserControl1` na **200**.</span><span class="sxs-lookup"><span data-stu-id="c94d2-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="c94d2-108">Ustaw wartość właściwości <xref:System.Windows.Controls.Control.Background%2A> na **niebieską**.</span><span class="sxs-lookup"><span data-stu-id="c94d2-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="c94d2-109">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="c94d2-109">Build the project.</span></span>

5. <span data-ttu-id="c94d2-110">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c94d2-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="c94d2-111">Z **przybornika**przeciągnij wystąpienie `UserControl1` na formularz.</span><span class="sxs-lookup"><span data-stu-id="c94d2-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="c94d2-112">Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c94d2-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="c94d2-113">Po wybraniu `elementHost1` naciśnij **kombinację klawiszy Ctrl**+**C** , aby skopiować ją do Schowka.</span><span class="sxs-lookup"><span data-stu-id="c94d2-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="c94d2-114">Naciśnij klawisz **Ctrl**+**V** , aby wkleić skopiowany formant do formularza.</span><span class="sxs-lookup"><span data-stu-id="c94d2-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="c94d2-115">W formularzu zostanie utworzona nowa kontrolka <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="c94d2-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="c94d2-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c94d2-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c94d2-117">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c94d2-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="c94d2-118">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="c94d2-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="c94d2-119">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c94d2-119">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
