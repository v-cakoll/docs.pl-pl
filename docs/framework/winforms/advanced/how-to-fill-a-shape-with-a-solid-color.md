---
title: 'Porady: wypełnianie kształtów jednolitym kolorem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: 7f719417a6a1226d7dc4d600518711ba31920a6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Porady: wypełnianie kształtów jednolitym kolorem
Wypełnianie kształtów jednolitym kolorem, należy utworzyć <xref:System.Drawing.SolidBrush> obiekt, a następnie przekazać który <xref:System.Drawing.SolidBrush> obiektu jako argument metody fill <xref:System.Drawing.Graphics> klasy. Poniższy przykład pokazuje, jak do wypełnienia elipsy kolorem czerwonym.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor pobiera <xref:System.Drawing.Color> obiektu jako jej argument tylko. Wartości używane przez <xref:System.Drawing.Color.FromArgb%2A> metody reprezentują składniki alfa, czerwony, zielony i niebieski koloru. Każdy z tych wartości musi być z zakresu od 0 do 255. Pierwszy 255 wskazuje, że kolor jest całkowicie nieprzezroczyste i drugi 255 oznacza, że składnik red jest na pełną intensywność. Dwa zera oznacza, że składniki zielonemu i niebieskiemu mieć intensywność 0.  
  
 Cztery cyfry (0, 0, 100, 60) przekazany do <xref:System.Drawing.Graphics.FillEllipse%2A> metody Określ lokalizację i rozmiar prostokątem elipsy. Prostokąt ma lewym górnym rogu (0, 0), 100 szerokość i wysokość 60.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie pędzla do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
