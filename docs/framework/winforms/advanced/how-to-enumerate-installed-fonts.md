---
title: 'Instrukcje: Wyliczanie zainstalowanych czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: e56f06d6f7a762a1ef1ff85fa30751ea64f9f14b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653746"
---
# <a name="how-to-enumerate-installed-fonts"></a>Instrukcje: Wyliczanie zainstalowanych czcionek
<xref:System.Drawing.Text.InstalledFontCollection> Klasa dziedziczy <xref:System.Drawing.Text.FontCollection> abstrakcyjna klasa bazowa. Możesz użyć <xref:System.Drawing.Text.InstalledFontCollection> obiektów do wyliczenia czcionki zainstalowane na komputerze. <xref:System.Drawing.Text.FontCollection.Families%2A> Właściwość <xref:System.Drawing.Text.InstalledFontCollection> obiekt jest tablicą <xref:System.Drawing.FontFamily> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wyświetla listę nazw rodzin czcionek zainstalowany na komputerze. Pobiera kod <xref:System.Drawing.FontFamily.Name%2A> właściwości każdego <xref:System.Drawing.FontFamily> obiektów w tablicy zwracanej przez <xref:System.Drawing.Text.FontCollection.Families%2A> właściwości. Jako nazwy rodziny są pobierane, są łączone w do listy formularzy rozdzielonych przecinkami. A następnie <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy rysuje rozdzielana przecinkami lista w prostokącie.  
  
 Jeśli uruchamiasz przykładowy kod, dane wyjściowe będą podobne do przedstawionego na poniższej ilustracji:  
  
 ![Zrzut ekranu pokazujący rodzin czcionek zainstalowane.](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>. Ponadto należy zaimportować <xref:System.Drawing.Text> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
