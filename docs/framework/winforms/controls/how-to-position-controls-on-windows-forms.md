---
title: 'Instrukcje: kontrolki pozycji na formularzach systemu Windows'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1cc2cb4c749b7290a6edf914a8e6a697006ef43c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987076"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="7f470-102">Instrukcje: Kontrolki położenia na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f470-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="7f470-103">Aby określić położenie formantów, użyj Projektant formularzy systemu Windows w programie Visual Studio lub Określ <xref:System.Windows.Forms.Control.Location%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="7f470-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="7f470-104">Umieść kontrolkę na powierzchni projektowej Projektant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7f470-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="7f470-105">W programie Visual Studio przeciągnij formant do odpowiedniej lokalizacji za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="7f470-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="7f470-106">Zaznacz kontrolkę i przenieś ją przy użyciu klawiszy strzałek, aby dokładniej umieścić ją na pozycji.</span><span class="sxs-lookup"><span data-stu-id="7f470-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="7f470-107">Ponadto *linii wyrównania* ułatwiają precyzyjne umieszczanie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7f470-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="7f470-108">Aby uzyskać więcej informacji, [zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)przy użyciu linii wyrównania.</span><span class="sxs-lookup"><span data-stu-id="7f470-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="7f470-109">Ustawianie kontrolki przy użyciu okno Właściwości</span><span class="sxs-lookup"><span data-stu-id="7f470-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="7f470-110">W programie Visual Studio Wybierz kontrolkę, którą chcesz umieścić.</span><span class="sxs-lookup"><span data-stu-id="7f470-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="7f470-111">W oknie **Właściwości** wprowadź wartości dla <xref:System.Windows.Forms.Control.Location%2A> właściwości, oddzielone przecinkami, aby umieścić formant w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="7f470-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="7f470-112">Pierwsza liczba (X) to odległość od lewej krawędzi kontenera; Druga liczba (Y) to odległość od górnego obramowania obszaru kontenera (w pikselach).</span><span class="sxs-lookup"><span data-stu-id="7f470-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7f470-113">Można rozwinąć <xref:System.Windows.Forms.Control.Location%2A> właściwość, aby wpisać wartości **X** i **Y** osobno.</span><span class="sxs-lookup"><span data-stu-id="7f470-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="7f470-114">Programowo ustawić kontrolkę</span><span class="sxs-lookup"><span data-stu-id="7f470-114">Position a control programmatically</span></span>

1. <span data-ttu-id="7f470-115">Ustaw właściwość formantu na <xref:System.Drawing.Point>. <xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="7f470-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="7f470-116">Zmień współrzędną X lokalizacji kontrolki za pomocą <xref:System.Windows.Forms.Control.Left%2A> właściwości Subproperty.</span><span class="sxs-lookup"><span data-stu-id="7f470-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="7f470-117">Programowo Zwiększ lokalizację kontrolki</span><span class="sxs-lookup"><span data-stu-id="7f470-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="7f470-118"><xref:System.Windows.Forms.Control.Left%2A> Ustaw właściwość Subproperty, aby zwiększyć współrzędną X formantu.</span><span class="sxs-lookup"><span data-stu-id="7f470-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="7f470-119">Użyj właściwości <xref:System.Windows.Forms.Control.Location%2A> , aby jednocześnie ustawić współrzędne X i Y kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7f470-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="7f470-120">Aby ustawić położenie indywidualnie, użyj podwłaściwości kontrolki <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**).</span><span class="sxs-lookup"><span data-stu-id="7f470-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="7f470-121">Nie należy próbować niejawnie ustawić współrzędnych <xref:System.Drawing.Point> X i Y struktury reprezentującej lokalizację przycisku, ponieważ ta struktura zawiera kopię współrzędnych przycisku.</span><span class="sxs-lookup"><span data-stu-id="7f470-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f470-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f470-122">See also</span></span>

- [<span data-ttu-id="7f470-123">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f470-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="7f470-124">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania</span><span class="sxs-lookup"><span data-stu-id="7f470-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="7f470-125">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7f470-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="7f470-126">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7f470-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="7f470-127">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="7f470-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="7f470-128">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f470-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="7f470-129">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="7f470-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="7f470-130">[Instrukcje: Ustaw lokalizację ekranu Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7f470-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
