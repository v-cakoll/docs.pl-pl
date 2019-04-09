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
ms.openlocfilehash: ef2536f03ba6ed08e27d2fcf30cd1f72df2cf460
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142418"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Instrukcje: Dodawanie znaku wodnego do kontrolki TextBox
Poniższy przykład pokazuje, jak użyteczność pomocy dotyczącej <xref:System.Windows.Controls.TextBox> , wyświetlając objaśnienia obraz tła wewnątrz <xref:System.Windows.Controls.TextBox> dopóki tekst danych wejściowych użytkownika, w tym momencie obraz jest usuwany. Ponadto obraz tła jest przywracany ponownie, jeśli użytkownik usunie swoje dane wejściowe. Zobacz na poniższej ilustracji.  
  
 ![Pole tekstowe z obrazem tła](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  Przyczyna obrazu tła jest używany w tym przykładzie zamiast, po prostu manipulowanie <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox>, to, że obraz tła nie zakłóca powiązanie danych.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [TextBox — Przegląd](textbox-overview.md)
- [RichTextBox — Przegląd](richtextbox-overview.md)
