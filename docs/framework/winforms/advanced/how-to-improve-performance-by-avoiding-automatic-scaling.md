---
title: "Porady: poprawianie wydajności dzięki unikaniu automatycznego skalowania"
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
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0130e0745dfca20da5dc723bb7cc84748bb0b148
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>Porady: poprawianie wydajności dzięki unikaniu automatycznego skalowania
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]może automatycznie skalować obrazu podczas rysowania, które mogłoby obniżyć wydajność. Alternatywnie można kontrolować skalowanie obrazu przekazując wymiary prostokąt docelowy <xref:System.Drawing.Graphics.DrawImage%2A> metody.  
  
 Na przykład następujące wywołanie do <xref:System.Drawing.Graphics.DrawImage%2A> metody określa lewym górnym rogu (50, 30), ale nie określa prostokątne docelowego.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 Chociaż jest to wersja najprostszym <xref:System.Drawing.Graphics.DrawImage%2A> metody pod względem liczby wymaganych argumentów nie jest zawsze najbardziej efektywny. Jeśli rozwiązanie używany przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (zazwyczaj 96 punktów na cal) różni się od rozdzielczości, przechowywane w <xref:System.Drawing.Image> obiektu, a następnie <xref:System.Drawing.Graphics.DrawImage%2A> metody mogą być skalowane obrazu. Załóżmy na przykład, <xref:System.Drawing.Image> obiekt ma szerokość 216 pikseli i wartości przechowywanej rozdzielczość pozioma 72 dpi. Ponieważ 216/72 to 3, <xref:System.Drawing.Graphics.DrawImage%2A> skaluje obraz, aby miała ona szerokość 3 cale przy rozdzielczości 96 dpi. Oznacza to, że <xref:System.Drawing.Graphics.DrawImage%2A> wyświetli obraz, który ma szerokość 96 x 3 = 288 pikseli.  
  
 Nawet jeśli rozdzielczość ekranu jest inny niż 96 punktów na cal, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] będzie prawdopodobnie skali obrazu tak, jakby 96 punktów na cal był rozdzielczość ekranu. Jest to spowodowane tym [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> obiekt jest skojarzony z kontekstu urządzenia i kiedy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zapytania kontekst urządzenia dla rozdzielczość ekranu, wynik jest zwykle 96, niezależnie od rzeczywistej rozdzielczości. Można uniknąć, automatyczne skalowanie, określając docelowy prostokąt w <xref:System.Drawing.Graphics.DrawImage%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rysuje dwa razy ten sam obraz. W pierwszym przypadku szerokość i wysokość prostokąta docelowego nie są określone, a obraz jest automatycznie skalowany. W drugim przypadku szerokość i wysokość (podawana w pikselach) prostokąta docelowej są określone na taki sam jak szerokość i wysokość oryginalnego obrazu. Na poniższej ilustracji przedstawiono obrazu renderowania dwa razy.  
  
 ![Skalować tekstury](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Zamień na Texture.jpg obrazu nazwę i ścieżkę, które są prawidłowe w tym systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Praca z obrazami, mapami bitowymi, ikony i metapliki](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
