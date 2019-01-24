---
title: 'Instrukcje: Zmień typ kursora'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 2330cdd3be35dc4e4b555db6401dd55d9946ed1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745054"
---
# <a name="how-to-change-the-cursor-type"></a>Instrukcje: Zmień typ kursora
W tym przykładzie pokazano, jak zmienić <xref:System.Windows.Input.Cursor> wskaźnika myszy dla określonego elementu i aplikacji.  
  
 W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików i pliku CodeBehind.  
  
## <a name="example"></a>Przykład  
 Jest tworzony interfejs użytkownika, który składa się z <xref:System.Windows.Controls.ComboBox> wybrać żądaną <xref:System.Windows.Input.Cursor>, parę <xref:System.Windows.Controls.RadioButton> obiekty do ustalenia, czy zmiana kursora dotyczy tylko pojedynczy element lub ma zastosowanie do całej aplikacji i <xref:System.Windows.Controls.Border> czyli element, który nowy kursor jest stosowany do.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Poniższy kod tworzy <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> programu obsługi zdarzeń, które jest wywoływane, gdy typ kursora jest zmieniana w <xref:System.Windows.Controls.ComboBox>.  Filtr nazwy kursora i zestawy instrukcji switch <xref:System.Windows.FrameworkElement.Cursor%2A> właściwość <xref:System.Windows.Controls.Border> który nosi *DisplayArea*.  
  
 Jeśli zmiana kursora jest równa "Całą aplikację" <xref:System.Windows.Input.Mouse.OverrideCursor%2A> właściwość jest ustawiona na <xref:System.Windows.FrameworkElement.Cursor%2A> właściwość <xref:System.Windows.Controls.Border> kontroli.  Wymusza kursora, aby zmienić dla całej aplikacji.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd danych wejściowych](../../../../docs/framework/wpf/advanced/input-overview.md)
