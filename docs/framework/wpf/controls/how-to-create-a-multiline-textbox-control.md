---
title: "Jak utworzyć wieloliniowy formant TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a6885a594e5fcd747f85dedf1afbd39ec644717
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Jak utworzyć wieloliniowy formant TextBox
Ten przykład przedstawia sposób użycia [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formant, który automatycznie zostanie rozwinięty w celu uwzględnienia wiele wierszy tekstu.  
  
## <a name="example"></a>Przykład  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu **zawijanie** spowoduje, że wprowadzony tekst, który ma być zawijany do nowego wiersza w przypadku krawędzi <xref:System.Windows.Controls.TextBox> osiągnięciu kontroli automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> formantu, aby uwzględnić miejsce dla nowego wiersza, jeśli niezbędne.  
  
 Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu **true** powoduje, że nowy wiersz do wstawienia, gdy zostanie naciśnięty klawisz RETURN ponownie automatycznie rozszerzanie <xref:System.Windows.Controls.TextBox> uwzględnienie miejsce dla nowego wiersza, jeśli to konieczne.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Atrybutu dodaje pasek przewijania, aby <xref:System.Windows.Controls.TextBox>, tak aby zawartość <xref:System.Windows.Controls.TextBox> mogą być przewijane Jeśli <xref:System.Windows.Controls.TextBox> rozszerza się poza rozmiaru ramki lub okna ograniczający go.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.TextWrapping>  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
