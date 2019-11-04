---
title: 'Porady: formanty pozycji na formularzach systemu Windows'
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
ms.openlocfilehash: bb57d14397a4626e01c41dd687dfed7331282a10
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458327"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Instrukcje: kontrolki położenia na Windows Forms

Aby określić położenie formantów, użyj Projektant formularzy systemu Windows w programie Visual Studio lub Określ właściwość <xref:System.Windows.Forms.Control.Location%2A>.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Umieść kontrolkę na powierzchni projektowej Projektant formularzy systemu Windows

W programie Visual Studio przeciągnij formant do odpowiedniej lokalizacji za pomocą myszy.

> [!NOTE]
> Zaznacz kontrolkę i przenieś ją przy użyciu klawiszy strzałek, aby dokładniej umieścić ją na pozycji. Ponadto *linii wyrównania* ułatwiają precyzyjne umieszczanie kontrolek w formularzu. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Ustawianie kontrolki przy użyciu okno Właściwości

1. W programie Visual Studio Wybierz kontrolkę, którą chcesz umieścić.

2. W oknie **Właściwości** wpisz wartości właściwości <xref:System.Windows.Forms.Control.Location%2A>, oddzielając je przecinkami, aby umieścić formant w kontenerze.

   Pierwsza liczba (X) to odległość od lewej krawędzi kontenera; Druga liczba (Y) to odległość od górnego obramowania obszaru kontenera (w pikselach).

   > [!NOTE]
   > Można rozwinąć Właściwość <xref:System.Windows.Forms.Control.Location%2A>, aby jednocześnie wpisywać wartości **X** i **Y** .

## <a name="position-a-control-programmatically"></a>Programowo ustawić kontrolkę

1. Ustaw właściwość <xref:System.Windows.Forms.Control.Location%2A> formantu na <xref:System.Drawing.Point>.

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Zmień współrzędną X lokalizacji kontrolki za pomocą <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości.

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

Ustaw właściwość <xref:System.Windows.Forms.Control.Left%2A>, aby zwiększyć współrzędną X formantu.

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
> Użyj właściwości <xref:System.Windows.Forms.Control.Location%2A>, aby jednocześnie ustawić współrzędne X i Y kontrolki. Aby ustawić pozycję indywidualnie, użyj właściwości pod<xref:System.Windows.Forms.Control.Left%2A> kontrolki (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**). Nie należy próbować niejawnie ustawić współrzędnych X i Y struktury <xref:System.Drawing.Point>, która reprezentuje lokalizację przycisku, ponieważ ta struktura zawiera kopię współrzędnych przycisku.

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
- [Instrukcje: Ustawianie lokalizacji ekranu Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
