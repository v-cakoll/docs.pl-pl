---
title: 'Instrukcje: Rysowanie kształtów za pomocą formantów OvalShape i Rectangleshape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: fe937236332591f6065e618c49ca5cf2c54b987c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701225"
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Instrukcje: Rysowanie kształtów za pomocą formantów OvalShape i Rectangleshape (Visual Studio)
Możesz użyć <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> kontroli Rysowanie okręgów lub elipsy w formularzu lub kontenera, zarówno w czasie projektowania, jak i w czasie wykonywania. Możesz użyć <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> formantu, aby narysować kwadratów, prostokąty lub prostokąty z zaokrąglonymi narożnikami na formularzu lub kontenera. Można również użyć tej kontrolki do rysowania kształtów, zarówno w czasie projektowania, jak i w czasie wykonywania.  
  
 Można dostosować wygląd kształtu, zmieniając szerokości, kolor i styl obramowania. Tło kształt jest niewidoczna domyślnie; można dostosować tło, aby wyświetlić pełny kolor, wzorzec, wypełniacza gradientu (przejście z jednego koloru do drugiego) lub obrazu.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Aby narysować kształt proste w czasie projektowania  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> lub <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> z kontrolować **Visual Basic PowerPacks** kartę (Aby zainstalować, zobacz [formantów Powerpack Visual Basic](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) w **przybornika** formularz lub kontener formantu.  
  
2.  Przeciągnij zmiany rozmiaru i przenoszenie obsługuje rozmiar i położenie kształtu.  
  
     Można także rozmiar i położenie kształtu, zmieniając `Size` i `Position` właściwości w **właściwości** okna.  
  
     Aby utworzyć prostokąta z zaokrąglonymi narożnikami, wybierz `CornerRadius` właściwość **właściwości** okna i ustaw ją na wartość, która jest większa niż 0.  
  
3.  W **właściwości** okna, opcjonalnie ustaw dodatkowe właściwości, aby zmienić wygląd kształtu.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Aby narysować kształt proste w czasie wykonywania  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Microsoft.VisualBasic.PowerPacks.VS**, a następnie kliknij przycisk **OK**.  
  
3.  W **Edytor kodu**, Dodaj `Imports` lub `using` instrukcji w górnej części modułu:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Dodaj następujący kod w `Event` procedury:  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>Dostosowywanie kształtów  
 Korzystając z ustawień domyślnych <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> formanty są wyświetlane przy użyciu stałych czarne obramowanie o szerokości jednego piksela i przezroczyste tło. Możesz zmienić szerokości, stylu i koloru obramowania przez ustawienie właściwości. Dodatkowe właściwości umożliwiają zmianę tła kształtu do pełnego koloru, wzorzec, wypełnieniem gradientowym lub obrazu.  
  
 Przed zmianą tła kształtu należy wiedzieć, jak kilka właściwości wchodzić w interakcje.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Ustawienie właściwości jest ignorowany, chyba że <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Jeśli <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> zastępuje <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Jeśli <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> właściwości ustawiono wartość wzorca takiego jak <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> lub <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, wzorzec, które będą wyświetlane w <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>. Tło będą wyświetlane w <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>pod warunkiem, że <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Aby wyświetlić wypełniacza gradientu <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> właściwość musi być równa <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> i <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> właściwość musi być równa wartości innych niż <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.  
  
-   Ustawienie <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> właściwość obrazu zastępuje wszystkie inne ustawienia w tle.  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Aby narysować circle, który ma obramowanie niestandardowe  
  
1.  Przeciągnij `OvalShape` z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.  
  
2.  W **właściwości** okna w `Size` , właściwością `Height` i `Width` równe wartości.  
  
3.  Ustaw `BorderColor` właściwość kolor, który chcesz.  
  
4.  Ustaw `BorderStyle` właściwości do dowolnej wartości innych niż `Solid`.  
  
5.  Ustaw `BorderWidth` do rozmiaru który chcesz, w pikselach.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Aby narysować circle, który ma wypełnienia kryjącego  
  
1.  Przeciągnij `OvalShape` z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.  
  
2.  W **właściwości** okna w `Size` , właściwością `Height` i `Width` równe wartości.  
  
3.  Ustaw `BackColor` właściwość kolor, który chcesz.  
  
4.  Ustaw `BackStyle` właściwość `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Aby narysować circle, który ma wypełnienia deseniem  
  
1.  Przeciągnij `OvalShape` z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.  
  
2.  W **właściwości** okna w `Size` , właściwością `Height` i `Width` równe wartości.  
  
3.  Ustaw `BackColor` właściwość kolor tła.  
  
4.  Ustaw `BackStyle` właściwość `Opaque`.  
  
5.  Ustaw `FillColor` właściwości na kolor, który ma zostać wzorzec.  
  
6.  Ustaw `FillStyle` właściwości do dowolnej wartości innych niż `Transparent` lub `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Aby narysować okrąg, która ma wypełnieniem gradientowym  
  
1.  Przeciągnij `OvalShape` z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.  
  
2.  W **właściwości** okna w `Size` , właściwością `Height` i `Width` równe wartości.  
  
3.  Ustaw `FillColor` właściwości na kolor, który ma zostać kolor początkowy.  
  
4.  Ustaw `FillGradientColor` właściwości na kolor, który ma zostać kolor końcowy.  
  
5.  Ustaw `FillGradientStyle` właściwości na wartość inną niż `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Aby narysować okrąg wypełnionej obrazu  
  
1.  Przeciągnij `OvalShape` z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.  
  
2.  W **właściwości** okna w `Size` , właściwością `Height` i `Width` równe wartości.  
  
3.  Wybierz `BackgroundImage` właściwości i kliknij przycisk **wielokropka** przycisku (...).  
  
4.  W **wybierz zasób** okno dialogowe, wybierz obraz do wyświetlania. Jeśli nie są wyświetlane nie zasoby obrazów, kliknij przycisk **importu** aby przejść do lokalizacji obrazu.  
  
5.  Kliknij przycisk **OK** można wstawić obrazu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>
- <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>
- [Linie i kształty — Wprowadzenie do kontrolek](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [Instrukcje: Rysowanie linii za pomocą formantu LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
