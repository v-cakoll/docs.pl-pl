---
title: 'Instrukcje: Użyj klasy FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 21050ae69ad834b56c70f40d85138714af334dab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364102"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Instrukcje: Użyj klasy FontSizeConverter
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.FontSizeConverter> i przy jego użyciu, aby zmienić rozmiar czcionki.  
  
 W przykładzie zdefiniowano niestandardową metodę o nazwie `changeSize` Konwertuje zawartość <xref:System.Windows.Controls.ListBoxItem>, zgodnie z definicją w osobnym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku do wystąpienia <xref:System.Double>i nowsze w <xref:System.String>. Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.FontSizeConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do wystąpienia <xref:System.Double>. Ta wartość jest następnie przekazywany jako wartość <xref:System.Windows.Controls.TextBlock.FontSize%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.  
  
 W tym przykładzie definiuje również druga metoda niestandardowej, która jest wywoływana `changeFamily`. Ta metoda konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do <xref:System.String>, a następnie przekazuje tę wartość do <xref:System.Windows.Controls.TextBlock.FontFamily%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.  
  
 W tym przykładzie nie działa.  
  
 [!code-csharp[FontSizeConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.FontSizeConverter>
