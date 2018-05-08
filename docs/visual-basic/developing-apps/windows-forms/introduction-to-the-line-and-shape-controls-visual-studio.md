---
title: Linie i kształty — Wprowadzenie do formantów (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3ad740f7dd15194830959a5493970b4ba54ce142
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Linie i kształty — Wprowadzenie do formantów (Visual Studio)
Formanty Visual Basic Powerpack linii i kształtu są zestawem trzy graficznego formantów, które pozwalają na rysowanie linii i kształtów w formularzach i kontenerów. <xref:Microsoft.VisualBasic.PowerPacks.LineShape> Formant jest używany do rysowania linii poziomych, pionowych i ukośnych. <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Formant jest używany do rysowania okręgi i elipsy i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> formant jest używany do rysowania prostokątów i kwadratów.  
  
## <a name="line-and-shape-controls"></a>Formanty linii i kształtu  
 Formanty linii i kształtu Hermetyzowanie wiele metod graficznych, które są zawarte w <xref:System.Drawing> przestrzeni nazw. Pozwala na rysowanie linii i kształtów w jednym kroku, bez konieczności tworzenia obiektów graficznych, pióra i pędzle. Grafika złożonych technik, takich jak gradientem można osiągnąć, ustawiając tylko niektóre właściwości.  
  
 Chociaż jest również możliwe do rysowania linii i kształtów za pomocą metod grafiki, ma kilka zalet za pomocą formantów linii i kształtu:  
  
-   Grafika metody może zostać wywołany tylko w czasie wykonywania. Formanty linii i kształtu można dodać do formularza w czasie projektowania. Dzięki temu można je wyświetlić i umieść je dokładnie; mogą one również dodać w czasie wykonywania.  
  
-   Formanty linii i kształtu są wybieranych w czasie wykonywania, takich jak dostarczający zdarzenia <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> i <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>. Dane wyjściowe metody grafiki nie są można wybierać i nie zapewnia zdarzeń.  
  
-   Formanty linii i kształtu udostępniają <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> i <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> metody, które umożliwiają kontrolowanie kolejności ich w czasie projektowania i w czasie wykonywania. Porządek osi z metody grafiki można kontrolować, zmieniając ich kolejność wykonywania w czasie wykonywania.  
  
-   Formanty linii i kształtu są formanty bez okien; nie dojścia do okna mają i w związku z tym zużywać mniej zasobów systemowych.  
  
### <a name="object-model"></a>Model obiektu  
 Formanty linii i kształtu pochodzi z podstawowej <xref:Microsoft.VisualBasic.PowerPacks.Shape> klasy definiującej ich właściwości udostępnionych, metod i zdarzeń.  
  
 Na poniższej ilustracji przedstawiono hierarchii obiektów linii i kształtu.  
  
 ![Diagram hierarchii obiektów linii i kształtu](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Hierarchia obiektów linii i kształtu  
  
 Pochodne <xref:Microsoft.VisualBasic.PowerPacks.LineShape> klasy zawiera właściwości, metod i zdarzeń, które są unikatowe dla wierszy. Pochodne <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> klasa jest klasą bazową dla <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; zawiera właściwości, metod i zdarzeń wspólne dla wszystkich kształtów. Może również pochodzić z <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> do tworzenia własnych `Shape` kontrolki.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> klasy mogą być używane do rysowania okręgi, elipsy, prostokąty lub prostokąty z zaokrąglonymi narożnikami.  
  
 Po dodaniu wiersza lub kształt formantu do formularza lub kontenera, niewidoczne <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> tworzony jest obiekt. <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> Działa jako kanwy kształtów w ramach każdego formantu kontenera; każda <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> ma odpowiadające mu <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> , umożliwia iterację formanty linii i kształtu. Kształty z jednego kontenera można przenosić na inny przy użyciu wycinanie i wklejanie lub metodą przeciągania i upuszczania. Po usunięciu ostatniego kształtu z kontenera, <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> zostaną również usunięte.  
  
> [!NOTE]
>  Nie wszystkie formanty kontener obsługuje formanty linii i kształtu. Wiersz lub kształt formantu nie może obsługiwać na <xref:System.Windows.Forms.TableLayoutPanel> lub <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks>  
 [Instrukcje: rysowanie linii za pomocą kontrolki LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Instrukcje: rysowanie kształtów za pomocą kontrolek OvalShape i RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Instrukcje: włączanie przełączania między kształtami](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
