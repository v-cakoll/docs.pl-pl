---
title: Jak utworzyć element siatki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: b93bb859c4a0df50da2fa00587a28fda3776fd09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185787"
---
# <a name="how-to-create-a-grid-element"></a>Jak utworzyć element siatki
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć i używać wystąpienia <xref:System.Windows.Controls.Grid> przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu. W tym przykładzie użyto trzy <xref:System.Windows.Controls.ColumnDefinition> obiektów i trzy <xref:System.Windows.Controls.RowDefinition> obiekty, do tworzenia jest siatka z dziewięciu komórek, takich jak arkusz. Każda komórka zawiera <xref:System.Windows.Controls.TextBlock> element, który reprezentuje dane i górny wiersz zawiera <xref:System.Windows.Controls.TextBlock> z <xref:System.Windows.Controls.Grid.ColumnSpan%2A> właściwości stosowane. Aby wyświetlić granice każdej komórki <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwość jest włączona.  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  Każda z tych metod, spowoduje wygenerowanie interfejsu użytkownika, który znacznie wygląda tak samo, jak poniżej.

  ![Zrzut ekranu przedstawia interfejs użytkownika WPF, zawierającą podzielone na trzy kolumny siatki.  Posiada nagłówek "2018 produktów wydane" obejmujące wszystkie kolumny w górnym wierszu i zawiera trzy kolumny przy użyciu wartości sprzedaży dla niektórych kwartału.  Dolny wiersz zawiera tekst obejmujące dwie kolumny z komunikatem "Całkowita liczba jednostek: 300 000'](./media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
