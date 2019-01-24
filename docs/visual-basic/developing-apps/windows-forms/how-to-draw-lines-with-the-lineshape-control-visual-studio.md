---
title: 'Instrukcje: Rysowanie linii za pomocą formantów LineShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 46360c01dfaf2c6fe199725a9ecfba2248c72d6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596231"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Instrukcje: Rysowanie linii za pomocą formantów LineShape (Visual Studio)
Możesz użyć <xref:Microsoft.VisualBasic.PowerPacks.LineShape> formantu do rysowania linii poziomej, pionowej lub na skos na formularzu lub kontenera, zarówno w czasie projektowania, jak i w czasie wykonywania.  
  
 **Uwaga** komputer może wyświetlać różne nazwy lub lokalizacje dla niektórych użytkowników programu Visual Studio elementy interfejsu w poniższych instrukcjach. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Aby narysować linię w czasie projektowania  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.LineShape> z kontrolować **Visual Basic PowerPacks** karcie **przybornika** przeciągnij do kontrolki formularza lub kontenera.  
  
2.  Przeciągnij zmiany rozmiaru i przenoszenie dojścia do rozmiaru i pozycji wiersza.  
  
     Można także rozmiar i położenie wiersza, zmieniając `X1`, `X2`, `Y1`, i `Y2` właściwości w **właściwości** okna.  
  
3.  W **właściwości** okna, takie jak opcjonalnie ustawić dodatkowe właściwości `BorderStyle` lub `BorderColor` można zmienić wygląd linii.  
  
### <a name="to-draw-a-line-at-run-time"></a>Aby narysować linię w czasie wykonywania  
  
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
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.LineShape>
- [Linie i kształty — Wprowadzenie do kontrolek](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [Instrukcje: Rysowanie kształtów za pomocą formantów OvalShape i Rectangleshape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
