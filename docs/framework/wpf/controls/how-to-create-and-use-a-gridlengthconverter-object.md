---
title: 'Instrukcje: Tworzenie i używanie obiektu GridLengthConverter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: 498d2b9c531f391f4cbeb1478469a99d381deec7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206788"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>Instrukcje: Tworzenie i używanie obiektu GridLengthConverter
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć i używać wystąpienia <xref:System.Windows.GridLengthConverter>. W przykładzie zdefiniowano niestandardową metodę o nazwie `changeCol`, które przechodzą <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.GridLengthConverter> konwertująca <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do wystąpienia <xref:System.Windows.GridLength>. Przekonwertowana wartości jest następnie przekazywany jako wartość <xref:System.Windows.Controls.ColumnDefinition.Width%2A> właściwość <xref:System.Windows.Controls.ColumnDefinition> elementu.  
  
 W przykładzie zdefiniowano też druga metoda niestandardowej o nazwie `changeColVal`. Ta metoda niestandardowe konwertuje <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> z <xref:System.Windows.Controls.Slider> do <xref:System.String> i przekazuje następnie, w których wartość z powrotem na <xref:System.Windows.Controls.ColumnDefinition> jako <xref:System.Windows.Controls.ColumnDefinition.Width%2A> elementu.  
  
 Należy pamiętać, że oddzielnego [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plik definiuje zawartość <xref:System.Windows.Controls.ListBoxItem>.  
  
 [!code-csharp[gridlengthConverterGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
