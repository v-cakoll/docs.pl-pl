---
title: "Porady: rysowanie linii za pomocą formantów LineShape (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42e7f01a57a514ad1dc64e3d4451ce38ea199f93
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
