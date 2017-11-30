---
title: "RichTextBox — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4278f569a789ca6e8466e0b8e71557446b63955e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant jest używany do wyświetlania, wprowadzania i manipulowanie formatowanie tekstu. <xref:System.Windows.Forms.RichTextBox> Formant wykonuje wszystko <xref:System.Windows.Forms.TextBox> formant wykonuje, ale można również wyświetlić czcionek, kolorów i łączy; załadować z pliku; tekst i obrazy osadzone i znaleźć określonych znaków. <xref:System.Windows.Forms.RichTextBox> Kontroli jest zwykle służą do udostępniania manipulowania tekstu i wyświetlić funkcje podobne do edytora aplikacji, takich jak Microsoft Word. Podobnie jak <xref:System.Windows.Forms.TextBox> kontroli, <xref:System.Windows.Forms.RichTextBox> formant może wyświetlać paski przewijania; ale w przeciwieństwie do <xref:System.Windows.Forms.TextBox> kontroli, jego domyślne ustawienie to można wyświetlić zarówno poziome i pionowe paski przewijania, zgodnie z potrzebami i zawiera ustawienia dodatkowe paska przewijania.  
  
## <a name="working-with-the-richtextbox-control"></a>Praca z formantu RichTextBox  
 Jak <xref:System.Windows.Forms.TextBox> kontroli, tekst wyświetlany jest ustawiana przez <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwości. <xref:System.Windows.Forms.RichTextBox> Formant ma wiele właściwości formatowania tekstu. Aby uzyskać więcej informacji na temat tych właściwości, zobacz [porady: Ustawianie atrybutów czcionki dla formantu RichTextBox formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) i [porady: Ustawianie wcięć, wiszące wcięcia i akapitów punktowanych za pomocą formantu RichTextBox formularzy systemu Windows ](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Do modyfikowania plików, <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> i <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metod można wyświetlać i zapisać w wielu formatach plików, w tym w postaci zwykłego tekstu, Unicode zwykły tekst i Format tekstu sformatowanego (RTF). Formaty plików możliwe są wymienione w <xref:System.Windows.Forms.RichTextBoxStreamType>. Można użyć <xref:System.Windows.Forms.RichTextBox.Find%2A> metody do znalezienia ciągów tekstu lub określonych znaków.  
  
 Można również użyć <xref:System.Windows.Forms.RichTextBox> kontroli łączy stylu sieci Web przez ustawienie <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> właściwości `true` i pisanie kodu do obsługi <xref:System.Windows.Forms.RichTextBox.LinkClicked> zdarzeń. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Możesz uniemożliwić użytkownikowi manipulowanie niektórych lub wszystkich tekst w formancie przez ustawienie <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> właściwości `true`.  
  
 Można cofnąć i wykonaj ponownie większości operacji edycji w <xref:System.Windows.Forms.RichTextBox> kontroli przez wywołanie metody <xref:System.Windows.Forms.TextBoxBase.Undo%2A> i <xref:System.Windows.Forms.RichTextBox.Redo%2A> metody. <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> Metody umożliwia określenie, czy formant zostanie zastosowana Ostatnia operacja wycofywania użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox — formant](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Informacje o formancie TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
