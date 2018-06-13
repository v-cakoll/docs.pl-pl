---
title: 'Porady: wypełnianie otwartych figur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: b7422ae2a4dc4d59fd337ab2294caa0d65057bae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521163"
---
# <a name="how-to-fill-open-figures"></a>Porady: wypełnianie otwartych figur
Możesz wpisać ścieżkę przez przekazanie <xref:System.Drawing.Drawing2D.GraphicsPath> do obiektu <xref:System.Drawing.Graphics.FillPath%2A> metody. <xref:System.Drawing.Graphics.FillPath%2A> Metody wypełnia ścieżki zgodnie z trybu wypełnienia (alternatywnego lub zawijania) aktualnie ustawione dla ścieżki. Jeśli ścieżka zawiera wszystkie otwartych figur, ścieżka zostanie wypełniony tak, jakby te dane zostały zamknięte. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Zamyka rysunku za pomocą rysowania linii prostej od punktu końcowego do punktu początkowego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy ścieżki, która ma jedną figurę otwartą (łuk) i jeden figurę zamkniętą (elipsy). <xref:System.Drawing.Graphics.FillPath%2A> Metody wypełnia ścieżki zgodnie z wypełnienia domyślny tryb, który jest <xref:System.Drawing.Drawing2D.FillMode.Alternate>.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe przykładowy kod. Należy pamiętać, że ścieżka jest wypełniony (zgodnie ze standardem <xref:System.Drawing.Drawing2D.FillMode.Alternate>) tak, jakby figurę otwartą zostały zamknięte przez prostej od punktu końcowego do punktu początkowego.  
  
 ![Ścieżka otwartego wypełnienia](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [Ścieżki grafiki w GDI+](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
