---
title: Pozycjonowanie kontrolek
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 144a0021c74f0fb5afec1d511315168fb28528e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735916"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="95f41-102">Instrukcje: kontrolki położenia na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f41-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="95f41-103">Aby określić położenie formantów, użyj Projektant formularzy systemu Windows w programie Visual Studio lub Określ właściwość <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="95f41-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="95f41-104">Umieść kontrolkę na powierzchni projektowej Projektant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="95f41-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="95f41-105">W programie Visual Studio przeciągnij formant do odpowiedniej lokalizacji za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="95f41-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="95f41-106">Zaznacz kontrolkę i przenieś ją przy użyciu klawiszy strzałek, aby dokładniej umieścić ją na pozycji.</span><span class="sxs-lookup"><span data-stu-id="95f41-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="95f41-107">Ponadto *linii wyrównania* ułatwiają precyzyjne umieszczanie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="95f41-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="95f41-108">Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="95f41-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="95f41-109">Ustawianie kontrolki przy użyciu okno Właściwości</span><span class="sxs-lookup"><span data-stu-id="95f41-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="95f41-110">W programie Visual Studio Wybierz kontrolkę, którą chcesz umieścić.</span><span class="sxs-lookup"><span data-stu-id="95f41-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="95f41-111">W oknie **Właściwości** wpisz wartości właściwości <xref:System.Windows.Forms.Control.Location%2A>, oddzielając je przecinkami, aby umieścić formant w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="95f41-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="95f41-112">Pierwsza liczba (X) to odległość od lewej krawędzi kontenera; Druga liczba (Y) to odległość od górnego obramowania obszaru kontenera (w pikselach).</span><span class="sxs-lookup"><span data-stu-id="95f41-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="95f41-113">Można rozwinąć Właściwość <xref:System.Windows.Forms.Control.Location%2A>, aby jednocześnie wpisywać wartości **X** i **Y** .</span><span class="sxs-lookup"><span data-stu-id="95f41-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="95f41-114">Programowo ustawić kontrolkę</span><span class="sxs-lookup"><span data-stu-id="95f41-114">Position a control programmatically</span></span>

1. <span data-ttu-id="95f41-115">Ustaw właściwość <xref:System.Windows.Forms.Control.Location%2A> formantu na <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="95f41-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="95f41-116">Zmień współrzędną X lokalizacji kontrolki za pomocą <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości.</span><span class="sxs-lookup"><span data-stu-id="95f41-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="95f41-117">Programowo Zwiększ lokalizację kontrolki</span><span class="sxs-lookup"><span data-stu-id="95f41-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="95f41-118">Ustaw właściwość <xref:System.Windows.Forms.Control.Left%2A>, aby zwiększyć współrzędną X formantu.</span><span class="sxs-lookup"><span data-stu-id="95f41-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="95f41-119">Użyj właściwości <xref:System.Windows.Forms.Control.Location%2A>, aby jednocześnie ustawić współrzędne X i Y kontrolki.</span><span class="sxs-lookup"><span data-stu-id="95f41-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="95f41-120">Aby ustawić pozycję indywidualnie, użyj właściwości pod<xref:System.Windows.Forms.Control.Left%2A> kontrolki (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**).</span><span class="sxs-lookup"><span data-stu-id="95f41-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="95f41-121">Nie należy próbować niejawnie ustawić współrzędnych X i Y struktury <xref:System.Drawing.Point>, która reprezentuje lokalizację przycisku, ponieważ ta struktura zawiera kopię współrzędnych przycisku.</span><span class="sxs-lookup"><span data-stu-id="95f41-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="95f41-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95f41-122">See also</span></span>

- [<span data-ttu-id="95f41-123">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f41-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="95f41-124">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="95f41-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="95f41-125">Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="95f41-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="95f41-126">Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="95f41-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="95f41-127">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="95f41-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="95f41-128">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f41-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="95f41-129">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="95f41-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="95f41-130">[Instrukcje: Ustawianie lokalizacji ekranu Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="95f41-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
