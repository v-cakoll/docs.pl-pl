---
title: Jak utworzyć wieloliniowy formant TextBox
description: Dowiedz się, jak używać języka XAML do definiowania kontrolki TextBox, która rozwija się w celu uwzględnienia wielu wierszy tekstu w aplikacji Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166249"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Jak utworzyć wieloliniowy formant TextBox
Ten przykład pokazuje, jak używać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formantu, który zostanie automatycznie rozszerzony w celu uwzględnienia wielu wierszy tekstu.  
  
## <a name="example"></a>Przykład  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu **zawijania** spowoduje, że wprowadzony tekst będzie zawijany do nowego wiersza po <xref:System.Windows.Controls.TextBox> osiągnięciu krawędzi kontrolki, automatycznie rozszerzając <xref:System.Windows.Controls.TextBox> formant, aby uwzględnić miejsce dla nowego wiersza, w razie potrzeby.  
  
 Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu na **wartość true** powoduje, że nowy wiersz zostanie wstawiony po naciśnięciu klawisza powrotu, po ponownym rozwinięciu automatycznie, <xref:System.Windows.Controls.TextBox> Aby uwzględnić miejsce w nowym wierszu, w razie potrzeby.  
  
 Ten <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atrybut dodaje pasek przewijania do <xref:System.Windows.Controls.TextBox> , tak aby zawartość <xref:System.Windows.Controls.TextBox> można przewijać w przypadku, gdy <xref:System.Windows.Controls.TextBox> rozszerza się poza rozmiar ramki lub okna.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.TextWrapping>
- [TextBox — Przegląd](textbox-overview.md)
- [RichTextBox — Przegląd](richtextbox-overview.md)
