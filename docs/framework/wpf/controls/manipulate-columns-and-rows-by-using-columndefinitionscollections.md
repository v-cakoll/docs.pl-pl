---
title: Jak zarządzać kolumnami i wierszami przy użyciu ColumnDefinitionsCollections i RowDefinitionsCollections
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
ms.openlocfilehash: 6ff5ad4825bd9f683d895341dd084c00f68aa27b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553078"
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Jak zarządzać kolumnami i wierszami przy użyciu ColumnDefinitionsCollections i RowDefinitionsCollections
W tym przykładzie przedstawiono użycie metod w <xref:System.Windows.Controls.ColumnDefinitionCollection> i <xref:System.Windows.Controls.RowDefinitionCollection> klasy do wykonania akcji, takich jak dodawanie, czyszcząc lub zliczanie zawartość wierszy lub kolumn. Można na przykład <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, lub <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> elementy, które znajdują się w <xref:System.Windows.Controls.ColumnDefinition> lub <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Grid> element z <xref:System.Windows.FrameworkElement.Name%2A> z `grid1`. <xref:System.Windows.Controls.Grid> Zawiera <xref:System.Windows.Controls.StackPanel> przechowuje <xref:System.Windows.Controls.Button> elementów, każdy kontrolowane za pomocą metody innej kolekcji. Po kliknięciu <xref:System.Windows.Controls.Button>, zostaje uaktywniony wywołania metody w pliku CodeBehind.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 W tym przykładzie definiuje szereg metod niestandardowych każdego odpowiadającego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku. Można zmienić liczbę wierszy i kolumn w <xref:System.Windows.Controls.Grid> na kilka sposobów, w tym dodawanie lub usuwanie wierszy i kolumn; i całkowitej liczby wierszy i kolumn. Aby zapobiec <xref:System.ArgumentOutOfRangeException> i <xref:System.ArgumentException> wyjątków, można używać funkcji sprawdzania błędów który <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> udostępnia metody.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
