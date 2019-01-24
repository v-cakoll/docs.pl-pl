---
title: 'Instrukcje: Położenie formantów na formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 2baf311f04209e988f2f5dd562e247ee13ed59ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607163"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="f49a5-102">Instrukcje: Położenie formantów na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f49a5-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="f49a5-103">Położenie formantów, za pomocą projektanta Windows Forms lub określ <xref:System.Windows.Forms.Control.Location%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f49a5-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f49a5-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="f49a5-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f49a5-105">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="f49a5-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f49a5-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f49a5-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="f49a5-107">Aby ustalić położenie formantu na powierzchni projektowej projektanta Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f49a5-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="f49a5-108">Przeciągnij formant do odpowiedniej lokalizacji za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="f49a5-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f49a5-109">Wybierz kontrolkę i przenieś ją za pomocą strzałki kluczy, aby umieść ją na bardziej precyzyjne.</span><span class="sxs-lookup"><span data-stu-id="f49a5-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="f49a5-110">Ponadto *linii przyciągania* ułatwienie umieszczenie kontrolki dokładnie w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f49a5-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="f49a5-111">Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie formantów Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="f49a5-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="f49a5-112">Aby ustalić położenie formantu w oknie właściwości</span><span class="sxs-lookup"><span data-stu-id="f49a5-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="f49a5-113">Kliknij formant, który ma zostać ustawiony.</span><span class="sxs-lookup"><span data-stu-id="f49a5-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="f49a5-114">W **właściwości** okna, typ wartości <xref:System.Windows.Forms.Control.Location%2A> właściwości, oddzielając wartości przecinkami, aby ustalić położenie kontrolki wewnątrz jej kontenera.</span><span class="sxs-lookup"><span data-stu-id="f49a5-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="f49a5-115">Pierwsza liczba (X) jest odległość między lewą krawędzią kontenera; Druga liczba (Y) jest odległość od górnej krawędzi obszaru kontenera (w pikselach).</span><span class="sxs-lookup"><span data-stu-id="f49a5-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f49a5-116">Można rozwinąć <xref:System.Windows.Forms.Control.Location%2A> właściwość do typu **X** i **Y** wartości indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="f49a5-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="f49a5-117">Aby programowo położenie formantu</span><span class="sxs-lookup"><span data-stu-id="f49a5-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="f49a5-118">Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwości formantu, aby <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="f49a5-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="f49a5-119">Zmień współrzędną X lokalizacji kontrolki przy użyciu <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości.</span><span class="sxs-lookup"><span data-stu-id="f49a5-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="f49a5-120">Aby programowo dodać kolejne położenie formantu</span><span class="sxs-lookup"><span data-stu-id="f49a5-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="f49a5-121">Ustaw <xref:System.Windows.Forms.Control.Left%2A> właściwości podrzędnej, aby zwiększyć współrzędną X formantu.</span><span class="sxs-lookup"><span data-stu-id="f49a5-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f49a5-122">Użyj <xref:System.Windows.Forms.Control.Location%2A> właściwość umożliwiająca ustawienie kontrolki X i Y umieszcza jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="f49a5-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="f49a5-123">Aby ustawić położenie indywidualnie, należy użyć formantu <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podwłaściwości.</span><span class="sxs-lookup"><span data-stu-id="f49a5-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="f49a5-124">Nie należy próbować niejawnie Ustaw współrzędne X i Y <xref:System.Drawing.Point> strukturę, która reprezentuje przycisk lokalizacji, ponieważ ta struktura zawiera kopię współrzędnych przycisku.</span><span class="sxs-lookup"><span data-stu-id="f49a5-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49a5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f49a5-125">See also</span></span>
- [<span data-ttu-id="f49a5-126">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f49a5-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
- [<span data-ttu-id="f49a5-127">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="f49a5-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="f49a5-128">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f49a5-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="f49a5-129">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f49a5-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="f49a5-130">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f49a5-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="f49a5-131">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="f49a5-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="f49a5-132">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f49a5-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="f49a5-133">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="f49a5-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
- [<span data-ttu-id="f49a5-134">Instrukcje: Ustawianie lokalizacji ekranu formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f49a5-134">How to: Set the Screen Location of Windows Forms</span></span>](https://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
