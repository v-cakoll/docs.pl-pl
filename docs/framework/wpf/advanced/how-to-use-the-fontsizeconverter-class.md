---
title: Jak użyć klasy FontSizeConverter
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 625beb06b526e2753abc6f982cf5834bfae1f202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545129"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Jak użyć klasy FontSizeConverter
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.FontSizeConverter> i użyj go, aby zmienić rozmiar czcionki.  
  
 W przykładzie zdefiniowano niestandardowe metodę o nazwie `changeSize` Konwertuje zawartość <xref:System.Windows.Controls.ListBoxItem>, zgodnie z definicją w oddzielnej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, aby wystąpienie <xref:System.Double>lub nowszy w <xref:System.String>. Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.FontSizeConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na wystąpienie <xref:System.Double>. Ta wartość jest następnie przekazywany z powrotem jako wartość <xref:System.Windows.Controls.TextBlock.FontSize%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.  
  
 W tym przykładzie zdefiniowano także drugi niestandardowej metody, która jest wywoływana `changeFamily`. Ta metoda konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do <xref:System.String>, a następnie przekazuje tę wartość do <xref:System.Windows.Controls.TextBlock.FontFamily%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.  
  
 W tym przykładzie nie działa.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FontSizeConverter>
