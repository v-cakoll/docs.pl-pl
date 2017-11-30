---
title: "Porady: włączanie przełączania między kształtami (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a39957ffaa67d6abeb6d394ae9826d42ad2230de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>Porady: włączanie przełączania między kształtami (Visual Studio)
Formanty linii i kształtu nie mają `TabStop` lub `TabIndex` właściwości, ale można nadal Włączanie przełączania między nimi. W poniższym przykładzie naciskając jednocześnie klawisze CTRL i kartę będzie karcie między kształtami; Naciśnięcie klawisza TAB będzie karcie między przyciskami.  
  
> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
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
 [Porady: Rysowanie kształtów za pomocą formantów OvalShape i Rectangleshape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Porady: Rysowanie linii za pomocą formantu LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Wprowadzenie do formanty linii i kształtu](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
