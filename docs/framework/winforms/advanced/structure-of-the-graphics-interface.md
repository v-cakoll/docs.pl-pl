---
title: Struktura interfejsu grafiki
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd1da930df151869ea3e891da7057f44ed0a4603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="structure-of-the-graphics-interface"></a>Struktura interfejsu grafiki
Interfejs zarządzanej klasy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zawiera około 60 klas, 50 wyliczenia i struktury 8. <xref:System.Drawing.Graphics> Klasy jest stanowiącej podstawę [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcji; jest klasa, która faktycznie rysuje linii, krzywych rysunki, obrazy i tekst.  
  
## <a name="important-classes"></a>Ważne klas  
 Wiele klas działają razem z <xref:System.Drawing.Graphics> klasy. Na przykład <xref:System.Drawing.Graphics.DrawLine%2A> metoda <xref:System.Drawing.Pen> obiektu, który przechowuje atrybuty (kolor, szerokość, Styl kreskowany i podobnych) wiersz, który ma być rysowany. <xref:System.Drawing.Graphics.FillRectangle%2A> Metody może otrzymywać wskaźnik do <xref:System.Drawing.Drawing2D.LinearGradientBrush> obiektu, który współpracuje z <xref:System.Drawing.Graphics> obiekt, aby wypełnić prostokąt stopniowo zmiana kolorów. <xref:System.Drawing.Font>i <xref:System.Drawing.StringFormat> obiektów określić sposób <xref:System.Drawing.Graphics> obiektu rysuje tekst. A <xref:System.Drawing.Drawing2D.Matrix> obiekt przechowuje i manipuluje transformacji świata <xref:System.Drawing.Graphics> obiektu, który służy do obracania, skalowanie i przerzucanie obrazów.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]udostępnia kilka struktur (na przykład <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, i <xref:System.Drawing.Size>) służący do organizowania danych grafiki. Ponadto niektórych klas służą głównie w strukturze typów danych. Na przykład <xref:System.Drawing.Imaging.BitmapData> klasy jest pomocnika dla <xref:System.Drawing.Bitmap> klasy i <xref:System.Drawing.Drawing2D.PathData> klasy jest pomocnika dla <xref:System.Drawing.Drawing2D.GraphicsPath> klasy.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]definiuje kilka wyliczenia, które są kolekcjami elementów pokrewnych stałe. Na przykład <xref:System.Drawing.Drawing2D.LineJoin> wyliczenie zawiera elementy <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, i <xref:System.Drawing.Drawing2D.LineJoin.Round>, które określą, style, które mogą służyć do przyłączenia dwa wiersze.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd grafiki](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [Kodzie zarządzanym GDI + — informacje](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Używanie zarządzanych klas grafiki](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
