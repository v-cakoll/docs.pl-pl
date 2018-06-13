---
title: 'Porady: rysowanie linii za pomocą pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 6a728bcaf9946b2b92ce0ee97599f4c4fd0fea69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522988"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>Porady: rysowanie linii za pomocą pióra
Do rysowania linii, należy <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawLine%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje funkcje wiersza, np. kolor i szerokość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rysuje z (20, 10) do (300, 100). Pierwsza instrukcja używa <xref:System.Drawing.Pen.%23ctor%2A> konstruktora klasy w celu utworzenia czarny pióra. Jeden argument przekazany do <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> utworzone za pomocą obiektu <xref:System.Drawing.Color.FromArgb%2A> metody. Wartości użyte do utworzenia <xref:System.Drawing.Color> obiektu — (255, 0, 0, 0) — odpowiadają składniki alfa, czerwony, zielony i niebieski koloru. Te wartości definiują nieprzezroczyste czarne pióro.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Pen>  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Pióra, linie i prostokąty w GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
