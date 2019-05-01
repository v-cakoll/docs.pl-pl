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
ms.openlocfilehash: d6fe7a252029ff80f21d99f7342fabb1d29fbe24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781293"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Instrukcje: Wypełnianie kształtów jednolitym kolorem
Wypełnianie kształtów jednolitym kolorem, należy utworzyć <xref:System.Drawing.SolidBrush> obiektu, a następnie przekaż go <xref:System.Drawing.SolidBrush> obiektu jako argumentu do jednej z metod wypełnienia <xref:System.Drawing.Graphics> klasy. Poniższy przykład pokazuje, jak można wypełnić elipsę kolorem czerwonym.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor przyjmuje <xref:System.Drawing.Color> obiekt jako argument tylko. Wartości używane przez <xref:System.Drawing.Color.FromArgb%2A> metoda reprezentują alfa, czerwony, zielony i niebieski składników koloru. Każdy z tych wartości musi być z zakresu od 0 do 255. Pierwszy 255 wskazuje, że kolor odpowiada pełnemu kryciu i drugi 255 wskazuje na to, że składnik czerwony jest w pełnej intensywności. Dwa zera wskazują, że składniki zielony i niebieski mają intensywność 0.  
  
 Cztery cyfry (0, 0, 100, 60) przekazany do <xref:System.Drawing.Graphics.FillEllipse%2A> metoda Określ lokalizację i rozmiar prostokąt otaczający elipsy. Prostokąt ma lewego górnego rogu (0, 0), 100 szerokość i wysokość 60.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie pędzla do wypełniania kształtów](using-a-brush-to-fill-shapes.md)
