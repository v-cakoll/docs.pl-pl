---
title: 'Instrukcje: Użyj klasy FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 7cb76ad4ffe4b4574a48212240b852e1f2253088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741902"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Instrukcje: Użyj klasy FontSizeConverter
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.FontSizeConverter> i przy jego użyciu, aby zmienić rozmiar czcionki.  
  
 W przykładzie zdefiniowano niestandardową metodę o nazwie `changeSize` Konwertuje zawartość <xref:System.Windows.Controls.ListBoxItem>, zgodnie z definicją w osobnym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku do wystąpienia <xref:System.Double>i nowsze w <xref:System.String>. Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.FontSizeConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do wystąpienia <xref:System.Double>. Ta wartość jest następnie przekazywany jako wartość <xref:System.Windows.Controls.TextBlock.FontSize%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.  
  
 W tym przykładzie definiuje również druga metoda niestandardowej, która jest wywoływana `changeFamily`. Ta metoda konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do <xref:System.String>, a następnie przekazuje tę wartość do <xref:System.Windows.Controls.TextBlock.FontFamily%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.  
  
 W tym przykładzie nie działa.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.FontSizeConverter>
