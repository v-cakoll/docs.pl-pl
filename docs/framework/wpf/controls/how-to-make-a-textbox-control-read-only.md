---
title: 'Instrukcje: Tworzenie kontrolki TextBox tylko do odczytu'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 7f24458eb98bd669d59f15c49d1d9e3beb6833b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229839"
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Instrukcje: Tworzenie kontrolki TextBox tylko do odczytu
W tym przykładzie pokazano, jak skonfigurować <xref:System.Windows.Controls.TextBox> formantu nie zezwalać na dane wejściowe użytkownika lub modyfikacji.  
  
## <a name="example"></a>Przykład  
 Aby uniemożliwić użytkownikom modyfikowanie zawartości <xref:System.Windows.Controls.TextBox> , ustaw <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atrybutu **true**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Atrybutu, dotyczy tylko dane wejściowe użytkownika; nie ma wpływu na tekstu, ustawianego [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] opis <xref:System.Windows.Controls.TextBox> formantu lub tekstu, ustawianego programowo za pomocą <xref:System.Windows.Controls.TextBox.Text%2A> właściwości.  
  
 Wartość domyślna <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> jest **false**.  
  
## <a name="see-also"></a>Zobacz także

- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
