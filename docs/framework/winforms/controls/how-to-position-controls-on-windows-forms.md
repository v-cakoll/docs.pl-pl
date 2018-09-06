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
ms.openlocfilehash: 6843c22fec964de92c41760f1108d1c83e1f5bf8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773063"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Porady: formanty pozycji na formularzach systemu Windows
Położenie formantów, za pomocą projektanta Windows Forms lub określ <xref:System.Windows.Forms.Control.Location%2A> właściwości.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Aby ustalić położenie formantu na powierzchni projektowej projektanta Windows Forms  
  
-   Przeciągnij formant do odpowiedniej lokalizacji za pomocą myszy.  
  
    > [!NOTE]
    >  Wybierz kontrolkę i przenieś ją za pomocą strzałki kluczy, aby umieść ją na bardziej precyzyjne. Ponadto *linii przyciągania* ułatwienie umieszczenie kontrolki dokładnie w formularzu. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
### <a name="to-position-a-control-using-the-properties-window"></a>Aby ustalić położenie formantu w oknie właściwości  
  
1.  Kliknij formant, który ma zostać ustawiony.  
  
2.  W **właściwości** okna, typ wartości <xref:System.Windows.Forms.Control.Location%2A> właściwości, oddzielając wartości przecinkami, aby ustalić położenie kontrolki wewnątrz jej kontenera.  
  
     Pierwsza liczba (X) jest odległość między lewą krawędzią kontenera; Druga liczba (Y) jest odległość od górnej krawędzi obszaru kontenera (w pikselach).  
  
    > [!NOTE]
    >  Można rozwinąć <xref:System.Windows.Forms.Control.Location%2A> właściwość do typu **X** i **Y** wartości indywidualnie.  
  
### <a name="to-position-a-control-programmatically"></a>Aby programowo położenie formantu  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwości formantu, aby <xref:System.Drawing.Point>.  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  Zmień współrzędną X lokalizacji kontrolki przy użyciu <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości.  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a>Aby programowo dodać kolejne położenie formantu  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Left%2A> właściwości podrzędnej, aby zwiększyć współrzędną X formantu.  
  
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
    >  Użyj <xref:System.Windows.Forms.Control.Location%2A> właściwość umożliwiająca ustawienie kontrolki X i Y umieszcza jednocześnie. Aby ustawić położenie indywidualnie, należy użyć formantu <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podwłaściwości. Nie należy próbować niejawnie Ustaw współrzędne X i Y <xref:System.Drawing.Point> strukturę, która reprezentuje przycisk lokalizacji, ponieważ ta struktura zawiera kopię współrzędnych przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Porady: Ustawianie lokalizacji ekranu formularzy Windows Forms](https://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
