---
title: 'Instrukcje: Pobieranie kolekcji wierszy z kontrolki TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052485"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Instrukcje: Pobieranie kolekcji wierszy z kontrolki TextBox
W tym przykładzie pokazano, jak pobrać kolekcję linii tekstu z <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono proste metody, która przyjmuje <xref:System.Windows.Controls.TextBox> jako argument i zwraca <xref:System.Collections.Specialized.StringCollection> zawierające wiersze tekstu **TextBox**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Właściwość jest używana do określenia, ile wierszy jest obecnie oferowana **TextBox**i <xref:System.Windows.Controls.TextBox.GetLineText%2A> metody jest następnie używany do wyodrębniania w każdym wierszu i dodaj go do kolekcji wierszy.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Zobacz także

- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
