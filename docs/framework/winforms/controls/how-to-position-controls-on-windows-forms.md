---
title: Pozycjonowanie kontrolek
description: Dowiedz się, w jaki sposób używać Projektant formularzy systemu Windows w programie Visual Studio lub we właściwości Location w celu umieszczenia kontrolek.
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
ms.openlocfilehash: 0aa3faade71e0f7e0a9d5e676327a80747524b8c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904302"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="b78f3-103">Instrukcje: kontrolki położenia na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b78f3-103">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="b78f3-104">Aby określić położenie formantów, użyj Projektant formularzy systemu Windows w programie Visual Studio lub Określ <xref:System.Windows.Forms.Control.Location%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="b78f3-104">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="b78f3-105">Umieść kontrolkę na powierzchni projektowej Projektant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b78f3-105">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="b78f3-106">W programie Visual Studio przeciągnij formant do odpowiedniej lokalizacji za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="b78f3-106">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="b78f3-107">Zaznacz kontrolkę i przenieś ją przy użyciu klawiszy strzałek, aby dokładniej umieścić ją na pozycji.</span><span class="sxs-lookup"><span data-stu-id="b78f3-107">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="b78f3-108">Ponadto *linii wyrównania* ułatwiają precyzyjne umieszczanie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b78f3-108">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="b78f3-109">Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="b78f3-109">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="b78f3-110">Ustawianie kontrolki przy użyciu okno Właściwości</span><span class="sxs-lookup"><span data-stu-id="b78f3-110">Position a control using the Properties window</span></span>

1. <span data-ttu-id="b78f3-111">W programie Visual Studio Wybierz kontrolkę, którą chcesz umieścić.</span><span class="sxs-lookup"><span data-stu-id="b78f3-111">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="b78f3-112">W oknie **Właściwości** wprowadź wartości dla <xref:System.Windows.Forms.Control.Location%2A> właściwości, oddzielone przecinkami, aby umieścić formant w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="b78f3-112">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="b78f3-113">Pierwsza liczba (X) to odległość od lewej krawędzi kontenera; Druga liczba (Y) to odległość od górnego obramowania obszaru kontenera (w pikselach).</span><span class="sxs-lookup"><span data-stu-id="b78f3-113">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b78f3-114">Można rozwinąć właściwość, <xref:System.Windows.Forms.Control.Location%2A> Aby wpisać wartości **X** i **Y** osobno.</span><span class="sxs-lookup"><span data-stu-id="b78f3-114">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="b78f3-115">Programowo ustawić kontrolkę</span><span class="sxs-lookup"><span data-stu-id="b78f3-115">Position a control programmatically</span></span>

1. <span data-ttu-id="b78f3-116">Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwość formantu na <xref:System.Drawing.Point> .</span><span class="sxs-lookup"><span data-stu-id="b78f3-116">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="b78f3-117">Zmień współrzędną X lokalizacji kontrolki za pomocą <xref:System.Windows.Forms.Control.Left%2A> Właściwości Subproperty.</span><span class="sxs-lookup"><span data-stu-id="b78f3-117">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="b78f3-118">Programowo Zwiększ lokalizację kontrolki</span><span class="sxs-lookup"><span data-stu-id="b78f3-118">Increment a control's location programmatically</span></span>

<span data-ttu-id="b78f3-119">Ustaw <xref:System.Windows.Forms.Control.Left%2A> Właściwość Subproperty, aby zwiększyć współrzędną X formantu.</span><span class="sxs-lookup"><span data-stu-id="b78f3-119">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="b78f3-120">Użyj <xref:System.Windows.Forms.Control.Location%2A> właściwości, aby jednocześnie ustawić współrzędne X i Y kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b78f3-120">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="b78f3-121">Aby ustawić położenie indywidualnie, użyj podwłaściwości kontrolki <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**).</span><span class="sxs-lookup"><span data-stu-id="b78f3-121">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="b78f3-122">Nie należy próbować niejawnie ustawić współrzędnych X i Y <xref:System.Drawing.Point> struktury reprezentującej lokalizację przycisku, ponieważ ta struktura zawiera kopię współrzędnych przycisku.</span><span class="sxs-lookup"><span data-stu-id="b78f3-122">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="b78f3-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b78f3-123">See also</span></span>

- [<span data-ttu-id="b78f3-124">Kontrolki Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b78f3-124">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="b78f3-125">Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="b78f3-125">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="b78f3-126">Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b78f3-126">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="b78f3-127">Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b78f3-127">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="b78f3-128">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="b78f3-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="b78f3-129">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b78f3-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="b78f3-130">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="b78f3-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="b78f3-131">[Instrukcje: Ustawianie lokalizacji ekranu Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b78f3-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
