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
ms.openlocfilehash: 241edbe60c327493c9123c6cf7bdc19b7ba2b724
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211652"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="7bf1d-102">Instrukcje: kontrolki pozycji na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7bf1d-102">How to: Position Controls on Windows Forms</span></span>

<span data-ttu-id="7bf1d-103">Położenie formantów, za pomocą projektanta formularzy Windows w programie Visual Studio lub określić <xref:System.Windows.Forms.Control.Location%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="7bf1d-104">Położenie formantu na powierzchni projektowej projektanta Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7bf1d-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="7bf1d-105">W programie Visual Studio przeciągnij go do odpowiedniej lokalizacji za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="7bf1d-106">Wybierz kontrolkę i przenieś ją za pomocą strzałki kluczy, aby umieść ją na bardziej precyzyjne.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="7bf1d-107">Ponadto *linii przyciągania* ułatwienie umieszczenie kontrolki dokładnie w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="7bf1d-108">Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie formantów Windows Forms za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="7bf1d-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="7bf1d-109">Położenie formantu w oknie właściwości</span><span class="sxs-lookup"><span data-stu-id="7bf1d-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="7bf1d-110">W programie Visual Studio kliknij formant, który ma zostać ustawiony.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-110">In Visual Studio, click the control you want to position.</span></span>

2. <span data-ttu-id="7bf1d-111">W **właściwości** okna, typ wartości <xref:System.Windows.Forms.Control.Location%2A> właściwości, oddzielając wartości przecinkami, aby ustalić położenie kontrolki wewnątrz jej kontenera.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-111">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

     <span data-ttu-id="7bf1d-112">Pierwsza liczba (X) jest odległość między lewą krawędzią kontenera; Druga liczba (Y) jest odległość od górnej krawędzi obszaru kontenera (w pikselach).</span><span class="sxs-lookup"><span data-stu-id="7bf1d-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7bf1d-113">Można rozwinąć <xref:System.Windows.Forms.Control.Location%2A> właściwość do typu **X** i **Y** wartości indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="7bf1d-114">Położenie formantu programowe</span><span class="sxs-lookup"><span data-stu-id="7bf1d-114">Position a control programmatically</span></span>

1. <span data-ttu-id="7bf1d-115">Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwości formantu, aby <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="7bf1d-116">Zmień współrzędną X lokalizacji kontrolki przy użyciu <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="7bf1d-117">Zwiększ położenie formantu programowe</span><span class="sxs-lookup"><span data-stu-id="7bf1d-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="7bf1d-118">Ustaw <xref:System.Windows.Forms.Control.Left%2A> właściwości podrzędnej, aby zwiększyć współrzędną X formantu.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="7bf1d-119">Użyj <xref:System.Windows.Forms.Control.Location%2A> właściwość umożliwiająca ustawienie kontrolki X i Y umieszcza jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="7bf1d-120">Aby ustawić położenie indywidualnie, należy użyć formantu <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podwłaściwości.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="7bf1d-121">Nie należy próbować niejawnie Ustaw współrzędne X i Y <xref:System.Drawing.Point> strukturę, która reprezentuje przycisk lokalizacji, ponieważ ta struktura zawiera kopię współrzędnych przycisku.</span><span class="sxs-lookup"><span data-stu-id="7bf1d-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bf1d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bf1d-122">See also</span></span>

- [<span data-ttu-id="7bf1d-123">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7bf1d-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="7bf1d-124">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="7bf1d-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="7bf1d-125">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7bf1d-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="7bf1d-126">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7bf1d-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="7bf1d-127">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7bf1d-127">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="7bf1d-128">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="7bf1d-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="7bf1d-129">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7bf1d-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="7bf1d-130">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="7bf1d-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="7bf1d-131">[Instrukcje: Ustawianie lokalizacji ekranu formularzy Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7bf1d-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
