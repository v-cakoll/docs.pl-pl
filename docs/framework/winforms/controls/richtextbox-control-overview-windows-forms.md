---
title: RichTextBox — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0827c1919597e9eb85bfa41721676008b76564d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201601"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.RichTextBox> formant jest używany do wyświetlania, wprowadzania i manipulowanie formatowanie tekstu. <xref:System.Windows.Forms.RichTextBox> Kontroli działanie jest <xref:System.Windows.Forms.TextBox> kontroli jest, ale można również wyświetlać czcionki, kolory i łącza; ładowanie z pliku; tekstu i obrazów osadzonych i znaleźć określonych znaków. <xref:System.Windows.Forms.RichTextBox> Kontroli zazwyczaj służy do zapewnienia manipulacja tekstem i wyświetlić funkcje podobne do aplikacji edytora tekstów, takiego jak Microsoft Word. Podobnie jak <xref:System.Windows.Forms.TextBox> kontroli <xref:System.Windows.Forms.RichTextBox> formant może wyświetlić paski przewijania; ale w przeciwieństwie do <xref:System.Windows.Forms.TextBox> formant, ustawienie domyślne jest do wyświetlenia zarówno poziome i pionowe paski przewijania, zgodnie z potrzebami i ma ustawienia dodatkowe paska przewijania.  
  
## <a name="working-with-the-richtextbox-control"></a>Praca z kontrolki RichTextBox  
 Podobnie jak w przypadku <xref:System.Windows.Forms.TextBox> tekst wyświetlany formantu, jest ustawiana przez <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwości. <xref:System.Windows.Forms.RichTextBox> Formant ma wiele właściwości do formatowania tekstu. Aby uzyskać więcej informacji na temat tych właściwości, zobacz [jak: Ustawianie atrybutów czcionki dla kontrolki RichTextBox formularzy Windows Forms](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) i [jak: Ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą formantu RichTextBox formularzy Windows](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Do manipulowania plikami, <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> i <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metod można wyświetlać i zapisać wiele formatów plików, w tym zwykłego tekstu, Unicode zwykły tekst i Format tekstu sformatowanego (RTF). Formaty plików możliwe są wymienione w <xref:System.Windows.Forms.RichTextBoxStreamType>. Możesz użyć <xref:System.Windows.Forms.RichTextBox.Find%2A> metody do znalezienia ciągów tekstu lub określonych znaków.  
  
 Można również użyć <xref:System.Windows.Forms.RichTextBox> Kontrola łączy stylu sieci Web, ustawiając <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> właściwości `true` i pisanie kodu do obsługi <xref:System.Windows.Forms.RichTextBox.LinkClicked> zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie łączy stylu sieci Web za pomocą Windows formantu RichTextBox formularzy](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Uniemożliwia użytkownikowi manipulowanie niektóre lub wszystkie z tekstem w kontrolce, ustawiając <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> właściwość `true`.  
  
 Można cofnąć i wykonaj ponownie większość operacji edycji w <xref:System.Windows.Forms.RichTextBox> kontroli przez wywołanie metody <xref:System.Windows.Forms.TextBoxBase.Undo%2A> i <xref:System.Windows.Forms.RichTextBox.Redo%2A> metody. <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> Metody umożliwia określenie, czy kontrolka zostanie zastosowana Ostatnia operacja wycofywania użytkownika.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
