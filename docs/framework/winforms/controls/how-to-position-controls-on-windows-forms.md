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
# <a name="how-to-position-controls-on-windows-forms"></a>Instrukcje: kontrolki położenia na Windows Forms

Aby określić położenie formantów, użyj Projektant formularzy systemu Windows w programie Visual Studio lub Określ <xref:System.Windows.Forms.Control.Location%2A> Właściwość.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Umieść kontrolkę na powierzchni projektowej Projektant formularzy systemu Windows

W programie Visual Studio przeciągnij formant do odpowiedniej lokalizacji za pomocą myszy.

> [!NOTE]
> Zaznacz kontrolkę i przenieś ją przy użyciu klawiszy strzałek, aby dokładniej umieścić ją na pozycji. Ponadto *linii wyrównania* ułatwiają precyzyjne umieszczanie kontrolek w formularzu. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Ustawianie kontrolki przy użyciu okno Właściwości

1. W programie Visual Studio Wybierz kontrolkę, którą chcesz umieścić.

2. W oknie **Właściwości** wprowadź wartości dla <xref:System.Windows.Forms.Control.Location%2A> właściwości, oddzielone przecinkami, aby umieścić formant w kontenerze.

   Pierwsza liczba (X) to odległość od lewej krawędzi kontenera; Druga liczba (Y) to odległość od górnego obramowania obszaru kontenera (w pikselach).

   > [!NOTE]
   > Można rozwinąć właściwość, <xref:System.Windows.Forms.Control.Location%2A> Aby wpisać wartości **X** i **Y** osobno.

## <a name="position-a-control-programmatically"></a>Programowo ustawić kontrolkę

1. Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwość formantu na <xref:System.Drawing.Point> .

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Zmień współrzędną X lokalizacji kontrolki za pomocą <xref:System.Windows.Forms.Control.Left%2A> Właściwości Subproperty.

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

Ustaw <xref:System.Windows.Forms.Control.Left%2A> Właściwość Subproperty, aby zwiększyć współrzędną X formantu.

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
> Użyj <xref:System.Windows.Forms.Control.Location%2A> właściwości, aby jednocześnie ustawić współrzędne X i Y kontrolki. Aby ustawić położenie indywidualnie, użyj podwłaściwości kontrolki <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**). Nie należy próbować niejawnie ustawić współrzędnych X i Y <xref:System.Drawing.Point> struktury reprezentującej lokalizację przycisku, ponieważ ta struktura zawiera kopię współrzędnych przycisku.

## <a name="see-also"></a>Zobacz też

- [Kontrolki Windows Forms](index.md)
- [Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
- [Instrukcje: Ustawianie lokalizacji ekranu Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
