---
title: "Porady: ładowanie i wyświetlanie metaplików"
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
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 722b6d36801c69e500535a32e952ef8f45634d03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-load-and-display-metafiles"></a>Porady: ładowanie i wyświetlanie metaplików
<xref:System.Drawing.Imaging.Metafile> Klasy, która dziedziczy <xref:System.Drawing.Image> klasy, metody do rejestrowania, wyświetlanie i badanie wektor obrazów.  
  
## <a name="example"></a>Przykład  
 Aby wyświetlić obraz wektora (metaplik) na ekranie, należy <xref:System.Drawing.Imaging.Metafile> obiektu i <xref:System.Drawing.Graphics> obiektu. Przekaż nazwę pliku (lub strumień) do <xref:System.Drawing.Imaging.Metafile> konstruktora. Po utworzeniu <xref:System.Drawing.Imaging.Metafile> obiektu, który przekazać <xref:System.Drawing.Imaging.Metafile> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
 W przykładzie jest tworzony <xref:System.Drawing.Imaging.Metafile> obiektów z pliku EMF (rozszerzony metaplik), a następnie Rysuje obraz z jego lewego górnego rogu na (60, 10).  
  
 Na poniższej ilustracji przedstawiono metaplik rysowana w określonej lokalizacji.  
  
 ![Pozycja obrazu](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z obrazami, mapami bitowymi, ikony i metapliki](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
