---
title: 'Instrukcje: Utwórz formant TextBox tylko do odczytu'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 3784471020210f995c8bb0a377d56a2466d97da1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364545"
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Instrukcje: Utwórz formant TextBox tylko do odczytu
W tym przykładzie pokazano, jak skonfigurować <xref:System.Windows.Controls.TextBox> formantu nie zezwalać na dane wejściowe użytkownika lub modyfikacji.  
  
## <a name="example"></a>Przykład  
 Aby uniemożliwić użytkownikom modyfikowanie zawartości <xref:System.Windows.Controls.TextBox> , ustaw <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atrybutu **true**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Atrybutu, dotyczy tylko dane wejściowe użytkownika; nie ma wpływu na tekstu, ustawianego [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] opis <xref:System.Windows.Controls.TextBox> formantu lub tekstu, ustawianego programowo za pomocą <xref:System.Windows.Controls.TextBox.Text%2A> właściwości.  
  
 Wartość domyślna <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> jest **false**.  
  
## <a name="see-also"></a>Zobacz także
- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
