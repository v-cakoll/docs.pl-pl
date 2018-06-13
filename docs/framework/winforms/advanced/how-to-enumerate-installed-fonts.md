---
title: 'Porady: wyliczanie zainstalowanych czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: 9f31880cbfb42c03122fc7d2730b9ca89db49226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524442"
---
# <a name="how-to-enumerate-installed-fonts"></a>Porady: wyliczanie zainstalowanych czcionek
<xref:System.Drawing.Text.InstalledFontCollection> Klasa dziedziczy <xref:System.Drawing.Text.FontCollection> abstrakcyjnej klasy podstawowej. Można użyć <xref:System.Drawing.Text.InstalledFontCollection> obiektu wyliczyć czcionek zainstalowanych na komputerze. <xref:System.Drawing.Text.FontCollection.Families%2A> Właściwość <xref:System.Drawing.Text.InstalledFontCollection> obiektu to tablica <xref:System.Drawing.FontFamily> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera listę nazw rodzin czcionek zainstalowanych na komputerze. Pobiera kod <xref:System.Drawing.FontFamily.Name%2A> właściwości każdego <xref:System.Drawing.FontFamily> obiektu w tablicy zwracanej przez <xref:System.Drawing.Text.FontCollection.Families%2A> właściwości. Jako nazwy rodziny są pobierane, są one połączone do postaci rozdzielanej przecinkami listy. Następnie przy użyciu <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy rysuje listy rozdzielanej przecinkami w prostokącie.  
  
 Po uruchomieniu przykładowy kod dane wyjściowe będą podobne jak pokazano na poniższej ilustracji.  
  
 ![Zainstalowane czcionki](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>. Ponadto należy zaimportować <xref:System.Drawing.Text> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
