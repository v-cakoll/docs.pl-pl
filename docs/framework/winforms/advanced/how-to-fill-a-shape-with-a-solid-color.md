---
title: 'Instrukcje: Wypełnianie kształtów jednolitym kolorem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: 576042d9d8e7a7f77d5375b7dfafafdc63b3e824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601964"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Instrukcje: Wypełnianie kształtów jednolitym kolorem
Wypełnianie kształtów jednolitym kolorem, należy utworzyć <xref:System.Drawing.SolidBrush> obiektu, a następnie przekaż go <xref:System.Drawing.SolidBrush> obiektu jako argumentu do jednej z metod wypełnienia <xref:System.Drawing.Graphics> klasy. Poniższy przykład pokazuje, jak można wypełnić elipsę kolorem czerwonym.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor przyjmuje <xref:System.Drawing.Color> obiekt jako argument tylko. Wartości używane przez <xref:System.Drawing.Color.FromArgb%2A> metoda reprezentują alfa, czerwony, zielony i niebieski składników koloru. Każdy z tych wartości musi być z zakresu od 0 do 255. Pierwszy 255 wskazuje, że kolor odpowiada pełnemu kryciu i drugi 255 wskazuje na to, że składnik czerwony jest w pełnej intensywności. Dwa zera wskazują, że składniki zielony i niebieski mają intensywność 0.  
  
 Cztery cyfry (0, 0, 100, 60) przekazany do <xref:System.Drawing.Graphics.FillEllipse%2A> metoda Określ lokalizację i rozmiar prostokąt otaczający elipsy. Prostokąt ma lewego górnego rogu (0, 0), 100 szerokość i wysokość 60.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie pędzla do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
