---
title: 'Porady: rysowanie linii za pomocą formantów LineShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 5e1a837578aab4b4609a58ffee46406b022b8f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Porady: rysowanie linii za pomocą formantów LineShape (Visual Studio)
Można użyć <xref:Microsoft.VisualBasic.PowerPacks.LineShape> formantu do rysowania poziomych, pionowy lub ukośnych linii w formularzu lub kontenera, zarówno w czasie projektowania, jak i w czasie wykonywania.  
  
 **Uwaga** komputera mogą być wyświetlane inne nazwy i lokalizacje niektórych użytkownika programu Visual Studio interfejsu elementów w poniższych instrukcjach. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Rysowanie linii w czasie projektowania  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.LineShape> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** przeciągnij formularza lub kontenera formantu.  
  
2.  Przeciągnij zmiany rozmiaru i Przenieś dojścia do rozmiaru i pozycji wiersza.  
  
     Możesz również rozmiar i położenie wiersza, zmieniając `X1`, `X2`, `Y1`, i `Y2` właściwości w **właściwości** okna.  
  
3.  W **właściwości** okna, takich jak opcjonalnie skonfigurować dodatkowe właściwości `BorderStyle` lub `BorderColor` Aby zmienić wygląd linii.  
  
### <a name="to-draw-a-line-at-run-time"></a>Rysowanie linii w czasie wykonywania  
  
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
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [Linie i kształty — Wprowadzenie do kontrolek](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Instrukcje: rysowanie kształtów za pomocą kontrolek OvalShape i RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
