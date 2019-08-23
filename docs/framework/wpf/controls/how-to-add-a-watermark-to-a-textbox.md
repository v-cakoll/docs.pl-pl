---
title: 'Instrukcje: Dodawanie znaku wodnego do kontrolki TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923576"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Instrukcje: Dodawanie znaku wodnego do kontrolki TextBox
Poniższy przykład przedstawia sposób ułatwienia użyteczności <xref:System.Windows.Controls.TextBox> przez wyświetlanie obrazu tła wyjaśniającego wewnątrz <xref:System.Windows.Controls.TextBox> elementu do momentu, w którym użytkownik wprowadza tekst. Ponadto obraz tła jest przywracany ponownie, jeśli użytkownik usunie swoje dane wejściowe. Zobacz ilustrację poniżej.  
  
 ![Pole tekstowe z obrazem tła](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
> Przyczyną tego przykładu jest użycie obrazu tła w tym przykładzie <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox>, a dopiero po prostu manipulowanie właściwością, polega na tym, że obraz tła nie zakłóca powiązania danych.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
