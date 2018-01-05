---
title: "Porady: ustawianie szerokości i wyrównania pióra"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e5858da25174c8bc1de18d534023b57b58253e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-pen-width-and-alignment"></a>Porady: ustawianie szerokości i wyrównania pióra
Po utworzeniu <xref:System.Drawing.Pen>, możesz podać szerokość pióra jako jeden z argumentów konstruktora. Możesz również zmienić szerokość z <xref:System.Drawing.Pen.Width%2A> właściwość <xref:System.Drawing.Pen> klasy.  
  
 Teoretyczna ma szerokość 0. Podczas rysowania linii, o szerokości 1 piksela pikseli jest wyśrodkowywana w wierszu teoretycznego. Jeśli rysowania więcej niż jeden piksel szerokości linii pikseli albo skupia się na teoretycznego wiersza lub są wyświetlane obok teoretycznego wiersza. Można ustawić właściwości wyrównania pióra <xref:System.Drawing.Pen> ustalenie położenie pikseli z tym pióra względem teoretycznego wierszy.  
  
 Wartości <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, i <xref:System.Drawing.Drawing2D.PenAlignment.Inset> znajdujących się na następujące przykłady kodu są elementami członkowskimi <xref:System.Drawing.Drawing2D.PenAlignment> wyliczenia.  
  
 Poniższy przykładowy kod rysuje dwa razy: raz piórem czarny o szerokości 1 i drugi raz z zielonym pióra szerokości 10.  
  
### <a name="to-vary-the-width-of-a-pen"></a>Aby zróżnicować szerokość pióra  
  
-   Ustaw wartość <xref:System.Drawing.Pen.Alignment%2A> właściwości <xref:System.Drawing.Drawing2D.PenAlignment.Center> (ustawienie domyślne) do określenia, że pikseli z zielonym pióro zostanie wyśrodkowany teoretycznego wiersza. Na poniższej ilustracji przedstawiono wynikowego wiersza.  
  
     ![Pióra](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")  
  
     Poniższy przykładowy kod rysuje prostokąt dwa razy: raz piórem czarny o szerokości 1 i drugi raz z zielonym pióra szerokości 10.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>Aby zmienić wyrównania pióra  
  
-   Ustaw wartość <xref:System.Drawing.Pen.Alignment%2A> właściwości <xref:System.Drawing.Drawing2D.PenAlignment.Center> do określenia, że pikseli z zielonym pióra zostaną wyśrodkowane na krawędzi prostokąta.  
  
     Na poniższej ilustracji przedstawiono wynikowy prostokąta.  
  
     ![Pióra](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>Aby utworzyć wstawki pióra  
  
-   Zmienić wyrównania pióra zielony, modyfikując trzeci instrukcji w poprzednim przykładzie kodu w następujący sposób:  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Teraz pikseli szerokości zielony wiersza pojawiają się wewnątrz prostokąta, jak pokazano na poniższej ilustracji.  
  
     ![Pióra](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")  
  
## <a name="see-also"></a>Zobacz też  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
