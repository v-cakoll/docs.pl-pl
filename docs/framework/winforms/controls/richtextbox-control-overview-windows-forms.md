---
title: RichTextBox — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0d40967d97622b23e9dcb07e861f190327e6baba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742398"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms służy do wyświetlania, wprowadzania i manipulowania tekstem z formatowaniem. Formant <xref:System.Windows.Forms.RichTextBox> wykonuje wszystko kontrolkę <xref:System.Windows.Forms.TextBox>, ale może również wyświetlać czcionki, kolory i linki; Ładowanie tekstu i osadzonych obrazów z pliku; i Znajdź określone znaki. Formant <xref:System.Windows.Forms.RichTextBox> jest zazwyczaj używany do udostępniania tekstu i funkcji wyświetlania, podobnie jak w przypadku aplikacji do przetwarzania tekstów, takich jak Microsoft Word. Podobnie jak w przypadku kontrolki <xref:System.Windows.Forms.TextBox> kontrolka <xref:System.Windows.Forms.RichTextBox> może wyświetlać paski przewijania. ale w przeciwieństwie do kontrolki <xref:System.Windows.Forms.TextBox>, jej domyślnym ustawieniem jest wyświetlanie pasków przewijania poziomych i pionowych w miarę potrzeby i ma dodatkowe ustawienia paska przewijania.  
  
## <a name="working-with-the-richtextbox-control"></a>Praca z kontrolką RichTextBox  
 Podobnie jak w przypadku kontrolki <xref:System.Windows.Forms.TextBox>, wyświetlany tekst jest ustawiany przez właściwość <xref:System.Windows.Forms.RichTextBox.Text%2A>. Formant <xref:System.Windows.Forms.RichTextBox> ma wiele właściwości do formatowania tekstu. Aby uzyskać szczegółowe informacje o tych właściwościach, zobacz [How to: Set Fonts for the Windows Forms RichTextBox Control](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) i [How to: Set wcięcia, wysunięcie i akapity punktowane przy użyciu formantu Windows Forms RichTextBox](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Aby manipulować plikami, metody <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> i <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> mogą wyświetlać i zapisywać wiele formatów plików, w tym zwykły tekst, zwykły tekst Unicode i format tekstu sformatowanego (RTF). Możliwe formaty plików są wymienione w <xref:System.Windows.Forms.RichTextBoxStreamType>. Możesz użyć metody <xref:System.Windows.Forms.RichTextBox.Find%2A>, aby znaleźć ciągi tekstu lub określonych znaków.  
  
 Możesz również użyć kontrolki <xref:System.Windows.Forms.RichTextBox> dla łączy w stylu sieci Web, ustawiając właściwość <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> na `true` i pisząc kod do obsługi zdarzenia <xref:System.Windows.Forms.RichTextBox.LinkClicked>. Aby uzyskać więcej informacji, zobacz [How to: Display Web-style Links with the Windows Forms RichTextBox Control](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Można uniemożliwić użytkownikowi manipulowanie części lub całością tekstu w kontrolce, ustawiając właściwość <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> na `true`.  
  
 Większość operacji edycji można cofnąć i wykonać ponownie w kontrolce <xref:System.Windows.Forms.RichTextBox>, wywołując metody <xref:System.Windows.Forms.TextBoxBase.Undo%2A> i <xref:System.Windows.Forms.RichTextBox.Redo%2A>. Metoda <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> pozwala określić, czy Ostatnia operacja, którą użytkownik cofnięto, może zostać ponownie zastosowana do kontrolki.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
