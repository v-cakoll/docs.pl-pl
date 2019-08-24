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
# <a name="how-to-position-controls-on-windows-forms"></a>Instrukcje: Kontrolki położenia na Windows Forms

Aby określić położenie formantów, użyj Projektant formularzy systemu Windows w programie Visual Studio lub Określ <xref:System.Windows.Forms.Control.Location%2A> właściwość.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Umieść kontrolkę na powierzchni projektowej Projektant formularzy systemu Windows

W programie Visual Studio przeciągnij formant do odpowiedniej lokalizacji za pomocą myszy.

> [!NOTE]
> Zaznacz kontrolkę i przenieś ją przy użyciu klawiszy strzałek, aby dokładniej umieścić ją na pozycji. Ponadto *linii wyrównania* ułatwiają precyzyjne umieszczanie kontrolek w formularzu. Aby uzyskać więcej informacji, [zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)przy użyciu linii wyrównania.

## <a name="position-a-control-using-the-properties-window"></a>Ustawianie kontrolki przy użyciu okno Właściwości

1. W programie Visual Studio Wybierz kontrolkę, którą chcesz umieścić.

2. W oknie **Właściwości** wprowadź wartości dla <xref:System.Windows.Forms.Control.Location%2A> właściwości, oddzielone przecinkami, aby umieścić formant w kontenerze.

   Pierwsza liczba (X) to odległość od lewej krawędzi kontenera; Druga liczba (Y) to odległość od górnego obramowania obszaru kontenera (w pikselach).

   > [!NOTE]
   > Można rozwinąć <xref:System.Windows.Forms.Control.Location%2A> właściwość, aby wpisać wartości **X** i **Y** osobno.

## <a name="position-a-control-programmatically"></a>Programowo ustawić kontrolkę

1. Ustaw właściwość formantu na <xref:System.Drawing.Point>. <xref:System.Windows.Forms.Control.Location%2A>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Zmień współrzędną X lokalizacji kontrolki za pomocą <xref:System.Windows.Forms.Control.Left%2A> właściwości Subproperty.

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>Programowo Zwiększ lokalizację kontrolki

<xref:System.Windows.Forms.Control.Left%2A> Ustaw właściwość Subproperty, aby zwiększyć współrzędną X formantu.

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
> Użyj właściwości <xref:System.Windows.Forms.Control.Location%2A> , aby jednocześnie ustawić współrzędne X i Y kontrolki. Aby ustawić położenie indywidualnie, użyj podwłaściwości kontrolki <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**). Nie należy próbować niejawnie ustawić współrzędnych <xref:System.Drawing.Point> X i Y struktury reprezentującej lokalizację przycisku, ponieważ ta struktura zawiera kopię współrzędnych przycisku.

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
- [Instrukcje: Ustaw lokalizację ekranu Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
