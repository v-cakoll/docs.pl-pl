---
title: "Porady: rysowanie kształtów za pomocą formantów OvalShape i RectangleShape (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53d91d10cc4735bbae521d17d05045cc7ea75fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Porady: rysowanie kształtów za pomocą formantów OvalShape i RectangleShape (Visual Studio)
Można użyć <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> formantu, aby narysować okręgi lub elipsy w formularzu lub kontenera, zarówno w czasie projektowania, jak i w czasie wykonywania. Można użyć <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> formantu do rysowania kwadratów, prostokąty lub prostokąty z zaokrąglonymi narożnikami w formularzu lub kontenera. Ten formant umożliwia również Rysowanie kształtów zarówno w czasie projektowania, jak i w czasie wykonywania.  
  
 Można dostosować wygląd kształtu, zmieniając szerokości, kolorów i styl obramowania. Tło kształt jest niewidoczny domyślnie; można dostosować do wyświetlenia pełnego koloru, wzorzec, wypełnienia gradientowego (Przechodzenie z jednego koloru do innego) lub obrazu tła.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Aby narysować kształt proste w czasie projektowania  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> lub <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kontrolować z **Visual Basic PowerPacks** kartę (Aby zainstalować, zobacz [formantów Powerpack Visual Basic](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) w **przybornika** formularz lub kontenera formantu.  
  
2.  Przeciągnij zmiany rozmiaru i Przenieś dojścia do rozmiaru i pozycji kształtu.  
  
     Możesz również rozmiar i położenie kształtu, zmieniając `Size` i `Position` właściwości w **właściwości** okna.  
  
     Aby utworzyć prostokąt z zaokrąglonymi narożnikami, wybierz `CornerRadius` właściwości w **właściwości** okna i ustaw ją na wartość, która jest większa niż 0.  
  
3.  W **właściwości** okna, opcjonalnie zestaw dodatkowe właściwości, aby zmienić wygląd kształtu.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Aby narysować kształt proste w czasie wykonywania  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Microsoft.VisualBasic.PowerPacks.VS**, a następnie kliknij przycisk **OK**.  
  
3.  W **edytora kodu**, Dodaj `Imports` lub `using` instrukcji w górnej części modułu:  
  
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
 Korzystając z ustawienia domyślne <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> formanty są wyświetlane z stałe czarnym obramowaniem jeden piksel szerokości i przezroczyste tło. Przez ustawienie właściwości można zmienić szerokości, stylu i koloru obramowania. Dodatkowe właściwości umożliwiają zmianę tła kształtów jednolitym kolorem, wzorzec, wypełnieniem gradientowym lub obrazu.  
  
 Przed wprowadzeniem zmian w tle kształtu, należy poznać kilka właściwości interakcje.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Ustawienie właściwości nie obowiązuje, chyba że <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Jeśli <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> zastępuje <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Jeśli <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> właściwość ma ustawioną wartość wzorca takich jak <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> lub <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, wzorzec zostanie wyświetlona w <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>. Tło będą wyświetlane w <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, pod warunkiem że <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Aby wyświetlić wypełnienia gradientowego <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> musi mieć ustawioną właściwość <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> i <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> właściwość musi mieć ustawioną wartość innych niż <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.  
  
-   Ustawienie <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> właściwość do obrazu zastępuje wszystkie inne ustawienia tła.  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Aby narysować okrąg, który ma obramowanie niestandardowe  
  
1.  Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.  
  
3.  Ustaw `BorderColor` kolor, który chcesz dla właściwości.  
  
4.  Ustaw `BorderStyle` właściwości wartości innych niż `Solid`.  
  
5.  Ustaw `BorderWidth` rozmiar w pikselach.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Aby narysować koło z wypełnieniem  
  
1.  Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.  
  
3.  Ustaw `BackColor` kolor, który chcesz dla właściwości.  
  
4.  Ustaw `BackStyle` właściwości `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Aby narysować okrąg deseniem wypełnieniem  
  
1.  Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.  
  
3.  Ustaw `BackColor` kolor tła dla właściwości.  
  
4.  Ustaw `BackStyle` właściwości `Opaque`.  
  
5.  Ustaw `FillColor` kolor, który ma wzorca dla właściwości.  
  
6.  Ustaw `FillStyle` właściwości wartości innych niż `Transparent` lub `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Aby narysować koło z wypełnieniem gradientowym  
  
1.  Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.  
  
3.  Ustaw `FillColor` kolor kolor początkowy dla właściwości.  
  
4.  Ustaw `FillGradientColor` kolor końcowy kolor dla właściwości.  
  
5.  Ustaw `FillGradientStyle` właściwości na wartość inną niż `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Rysowanie wypełnionej obrazu okręgu  
  
1.  Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.  
  
3.  Wybierz `BackgroundImage` właściwości i kliknij przycisk **wielokropka** przycisk (...).  
  
4.  W **zasobów wybierz** okno dialogowe, wybierz obraz do wyświetlenia. Jeśli nie są wyświetlane nie zasoby obrazów, kliknij przycisk **importu** aby przejść do lokalizacji obrazu.  
  
5.  Kliknij przycisk **OK** do wstawiania obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [Wprowadzenie do formanty linii i kształtu](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Porady: Rysowanie linii za pomocą formantu LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
