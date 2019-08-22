---
title: 'Instrukcje: Kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania'
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
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666178"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="0ca08-102">Instrukcje: Kopiowanie i wklejanie kontrolki ElementHost</span><span class="sxs-lookup"><span data-stu-id="0ca08-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="0ca08-103">Ta procedura pokazuje, jak skopiować formant Windows Presentation Foundation (WPF) w formularzu systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ca08-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="0ca08-104">W programie Visual Studio Dodaj nową WPF <xref:System.Windows.Controls.UserControl> do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0ca08-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="0ca08-105">Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="0ca08-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="0ca08-106">Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)projektowania.</span><span class="sxs-lookup"><span data-stu-id="0ca08-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="0ca08-107">W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości `UserControl1` i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="0ca08-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="0ca08-108">Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości na niebieską.</span><span class="sxs-lookup"><span data-stu-id="0ca08-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="0ca08-109">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="0ca08-109">Build the project.</span></span>

5. <span data-ttu-id="0ca08-110">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0ca08-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="0ca08-111">Z **przybornika**przeciągnij wystąpienie `UserControl1` na formularz.</span><span class="sxs-lookup"><span data-stu-id="0ca08-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="0ca08-112">Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="0ca08-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="0ca08-113">Po wybraniu naciśnij klawisz **Ctrl**+C, aby skopiować go do Schowka. `elementHost1`</span><span class="sxs-lookup"><span data-stu-id="0ca08-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="0ca08-114">Naciśnij klawisz **Ctrl**+, aby wkleić skopiowany formant do formularza.</span><span class="sxs-lookup"><span data-stu-id="0ca08-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="0ca08-115">W formularzu <xref:System.Windows.Forms.Integration.ElementHost> zostanie utworzona `elementHost2` Nowa kontrolka o nazwie.</span><span class="sxs-lookup"><span data-stu-id="0ca08-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ca08-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ca08-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="0ca08-117">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="0ca08-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="0ca08-118">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="0ca08-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="0ca08-119">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ca08-119">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
