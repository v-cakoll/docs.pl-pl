---
title: 'Porady: włączanie przełączania między kształtami (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
ms.openlocfilehash: 437027e53cb651dd5fabe40b9d8952250f108dad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589550"
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>Porady: włączanie przełączania między kształtami (Visual Studio)
Formanty linii i kształtu nie mają `TabStop` lub `TabIndex` właściwości, ale można nadal Włączanie przełączania między nimi. W poniższym przykładzie naciskając jednocześnie klawisze CTRL i kartę będzie karcie między kształtami; Naciśnięcie klawisza TAB będzie karcie między przyciskami.  
  
> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="to-enable-tabbing-among-shapes"></a>Aby włączyć przełączania między kształtami  
  
1.  Przeciągnij trzy <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kontrolek i dwa <xref:System.Windows.Forms.Button> formantów **przybornika** do formularza.  
  
2.  W **edytora kodu**, Dodaj `Imports` lub `using` instrukcji w górnej części modułu:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  Dodaj następujący kod w procedurze zdarzenia:  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  Dodaj następujący kod w `Button1_PreviewKeyDown` procedury zdarzenia:  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: rysowanie kształtów za pomocą kontrolek OvalShape i RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Instrukcje: rysowanie linii za pomocą kontrolki LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Linie i kształty — Wprowadzenie do kontrolek](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
