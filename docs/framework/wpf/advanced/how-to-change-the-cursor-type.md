---
title: Jak zmienić typ kursora
description: Zmień kursor wskaźnika myszy dla elementu i dla aplikacji w Windows Presentation Foundation. Ten przykład składa się z kodu XAML i pliku związanego z kodem.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165961"
---
# <a name="how-to-change-the-cursor-type"></a>Jak zmienić typ kursora
Ten przykład pokazuje, jak zmienić <xref:System.Windows.Input.Cursor> wskaźnik myszy dla określonego elementu i dla aplikacji.  
  
 Ten przykład zawiera plik [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i plik związany z kodem.  
  
## <a name="example"></a>Przykład  
 Interfejs użytkownika jest tworzony, który składa się z, <xref:System.Windows.Controls.ComboBox> Aby wybrać odpowiednią <xref:System.Windows.Input.Cursor> , parę <xref:System.Windows.Controls.RadioButton> obiektów do określenia, czy zmiana kursora dotyczy tylko pojedynczego elementu, czy ma zastosowanie do całej aplikacji, a także do elementu, <xref:System.Windows.Controls.Border> do którego zostanie zastosowany nowy kursor.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Poniższy kod w tle tworzy <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> procedurę obsługi zdarzeń, która jest wywoływana, gdy typ kursora zostanie zmieniony w <xref:System.Windows.Controls.ComboBox> .  Instrukcja Switch filtruje nazwę kursora i ustawia <xref:System.Windows.FrameworkElement.Cursor%2A> Właściwość o <xref:System.Windows.Controls.Border> nazwie *DisplayArea*.  
  
 Jeśli dla zmiany kursora zostanie ustawiona wartość "Cała aplikacja", <xref:System.Windows.Input.Mouse.OverrideCursor%2A> Właściwość jest ustawiana na <xref:System.Windows.FrameworkElement.Cursor%2A> Właściwość <xref:System.Windows.Controls.Border> kontrolki.  Wymusza to zmianę kursora dla całej aplikacji.  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Dane wejściowe](input-overview.md)
