---
title: 'Instrukcje: Rysowanie linii za pomocą pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 8b4eb7684e15ffd5b0b528771490ba66f3b7bb45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954443"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>Instrukcje: Rysowanie linii za pomocą pióra
Rysowanie linii, potrzebujesz <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawLine%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje funkcji, takich jak kolor i szerokość linii.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera wiersz z (20, 10) do (300, 100). Pierwsza instrukcja używa <xref:System.Drawing.Pen.%23ctor%2A> konstruktora klasy, aby utworzyć czarne pióro. Jeden argument przekazany do <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiekt utworzony za pomocą <xref:System.Drawing.Color.FromArgb%2A> metody. Wartości użyte do utworzenia <xref:System.Drawing.Color> obiektu — (255, 0, 0, 0) — odpowiadają alfa, czerwony, zielony i niebieski składników koloru. Wartości te definiują nieprzezroczysty czarny pióra.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Pen>
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
- [Pióra, linie i prostokąty w GDI+](pens-lines-and-rectangles-in-gdi.md)
