---
title: Linie i kształty — Wprowadzenie do formantów (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3623c2363f39150fd4bb202ba61ebd51df383ca8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699925"
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Linie i kształty — Wprowadzenie do formantów (Visual Studio)
Formanty Visual Basic Power Packs linii i kształtu to zestaw trzech graficzny formantów, które pozwalają na rysowanie linii i kształtów w formularzach i kontenerów. <xref:Microsoft.VisualBasic.PowerPacks.LineShape> Formant jest używany do rysowania linii poziomej, pionowej i ukośne. <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Formant jest używany do rysowania okręgi i elipsy i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> formant jest używany do rysowania prostokątów i kwadratów.  
  
## <a name="line-and-shape-controls"></a>Formanty linii i kształtu  
 Formanty linii i kształtu hermetyzacji wiele metod graficznych, które są zawarte w <xref:System.Drawing> przestrzeni nazw. Dzięki temu można narysować linie i kształty w jednym kroku, bez konieczności tworzenia obiektów graficznych, pióra i pędzle. Złożone grafiki technik, takich jak gradientem, można osiągnąć przez ustawienie tylko niektóre właściwości.  
  
 Mimo że istnieje również możliwość Rysowanie linii i kształtów za pomocą metod grafiki, istnieje kilka zalet za pomocą kontrolki linii i kształtu:  
  
-   Grafika metody można wywołać tylko w czasie wykonywania. Formanty linii i kształtów można dodać do formularza w czasie projektowania. Dzięki temu można zobaczyć, jak wyglądają i umieść je dokładnie; mogą być również dodawane w czasie wykonywania.  
  
-   Formanty linii i kształtu są można wybierać w czasie wykonywania, dostarczający zdarzenia, takie jak <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> i <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>. Dane wyjściowe grafiki metod nie są można wybierać i nie są oferowane zdarzenia.  
  
-   Formanty linii i kształtu udostępniają <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> i <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> metody, które umożliwiają kontrolowanie porządku ich w czasie projektowania i w czasie wykonywania. Porządek grafiki metod można kontrolować, zmieniając ich kolejność wykonywania w czasie wykonywania.  
  
-   Formanty linii i kształtu są kontrolek bez okien; nie dojścia okna mają i w związku z tym zużywać mniej zasobów systemowych.  
  
### <a name="object-model"></a>Model obiektów  
 Formanty linii i kształtu pochodzić od podstawowej <xref:Microsoft.VisualBasic.PowerPacks.Shape> klasę, która definiuje ich udostępnione właściwości, metody i zdarzenia.  
  
 Poniższa ilustracja przedstawia hierarchii obiektów linii i kształtu.  
  
 ![Diagram hierarchii obiektów linii i kształtu](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Hierarchia obiektów linii i kształtu  
  
 Pochodnej <xref:Microsoft.VisualBasic.PowerPacks.LineShape> klasa zawiera właściwości, metody i zdarzenia, które są unikatowe dla wierszy. Pochodnej <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> klasa jest klasą bazową dla <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; zawiera właściwości, metody i zdarzenia wspólne dla wszystkich kształtów. Można również dziedziczyć <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> utworzyć własny `Shape` kontrolki.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> klasy mogą być używane do rysowania okręgów, elipsy, prostokąty lub prostokąty z zaokrąglonymi rogami.  
  
 Po dodaniu kontrolki linii i kształtu do formularza lub kontener, niewidoczne <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> obiekt zostanie utworzony. <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> Działa jako kanwy dla kształtów w każdej kontrolce kontenera; każdy <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> ma odpowiadające mu <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> to pozwala wykonać iterację formanty linii i kształtu. Kształty można przenosić z jednego kontenera do innego za pomocą wycinanie i wklejanie lub metodą przeciągania i upuszczania. Po usunięciu ostatniego kształtu z kontenera, <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> zostanie również usunięte.  
  
> [!NOTE]
>  Nie wszystkie formanty innych kontenerów obsługuje formanty linii i kształtu. Nie można hostować kontrolkę wiersza lub kształtu na <xref:System.Windows.Forms.TableLayoutPanel> lub <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks>
- [Instrukcje: Rysowanie linii za pomocą formantu LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [Instrukcje: Rysowanie kształtów za pomocą formantów OvalShape i Rectangleshape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [Instrukcje: Włączanie przełączania między kształtami](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
