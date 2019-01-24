---
title: 'Instrukcje: Tworzenie figur z linii, krzywych i kształtów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: cb0b13b8c7b27d6c85cc969f10c126df26a14acf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707833"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a>Instrukcje: Tworzenie figur z linii, krzywych i kształtów
Do utworzenia rysunku, należy utworzyć <xref:System.Drawing.Drawing2D.GraphicsPath>, a następnie wywołać metod, takich jak <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, aby dodać w nim elementów podstawowych do ścieżki.  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady kodu Utwórz ścieżek, które mają dane:  
  
-   Pierwszy przykład tworzy ścieżką, która ma jedną wartość. Rysunek składa się z pojedynczego łuku. Łuk ma kąt odchylenia –180 stopni, czyli do ruchu wskazówek zegara w układzie współrzędnych domyślne.  
  
-   Drugi przykład tworzy ścieżki, która ma dwie cyfry. Pierwszy rysunek jest łuk znak wiersza. Drugi rysunek jest linię następuje krzywej znak wiersza. Pierwszy rysunek pozostanie otwarty, a drugi rysunek jest zamknięty.  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzednie przykłady są skonstruowane do użycia za pomocą interfejsu Windows Forms i wymagają one <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [Konstruowanie i rysowanie ścieżek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
- [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
