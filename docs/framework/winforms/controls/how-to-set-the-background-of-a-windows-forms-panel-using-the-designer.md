---
title: Ustawianie tła panelu przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731923"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="af873-102">Instrukcje: Ustawianie tła panelu Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="af873-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="af873-103">Kontrolka <xref:System.Windows.Forms.Panel> Windows Forms może wyświetlać zarówno kolor tła, jak i obraz tła.</span><span class="sxs-lookup"><span data-stu-id="af873-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="af873-104">Właściwość <xref:System.Windows.Forms.Control.BackColor%2A> ustawia kolor tła dla kontrolek, które są zawarte w panelu, takich jak etykiety i przyciski radiowe.</span><span class="sxs-lookup"><span data-stu-id="af873-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="af873-105">Jeśli właściwość <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie jest ustawiona, wybór <xref:System.Windows.Forms.Control.BackColor%2A> spowoduje wypełnienie wszystkich paneli.</span><span class="sxs-lookup"><span data-stu-id="af873-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="af873-106">Jeśli właściwość <xref:System.Windows.Forms.Control.BackgroundImage%2A> jest ustawiona, obraz będzie wyświetlany za kontrolkami, które są zawarte w panelu.</span><span class="sxs-lookup"><span data-stu-id="af873-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="af873-107">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="af873-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="af873-108">Aby uzyskać informacje na temat sposobu konfigurowania takiego projektu w programie Visual Studio, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="af873-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="af873-109">Ustaw tło w Projektant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="af873-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="af873-110">Otwórz projekt w programie Visual Studio i wybierz formant <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="af873-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="af873-111">W oknie **Właściwości** kliknij przycisk strzałki obok właściwości <xref:System.Windows.Forms.Control.BackColor%2A>, aby wyświetlić okno z trzema kartami.</span><span class="sxs-lookup"><span data-stu-id="af873-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="af873-112">Wybierz kartę **niestandardową** , aby wyświetlić paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="af873-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="af873-113">Wybierz kartę **Sieć Web** lub **system** , aby wyświetlić listę wstępnie zdefiniowanych nazw dla kolorów, a następnie wybierz kolor.</span><span class="sxs-lookup"><span data-stu-id="af873-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="af873-114">W oknie **Właściwości** kliknij przycisk strzałki obok właściwości <xref:System.Windows.Forms.Control.BackgroundImage%2A>.</span><span class="sxs-lookup"><span data-stu-id="af873-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="af873-115">W oknie dialogowym **Otwórz** wybierz plik, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="af873-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="af873-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af873-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="af873-117">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="af873-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="af873-118">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="af873-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="af873-119">Instrukcje: grupowanie kontrolek za pomocą kontrolki Panel formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="af873-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
