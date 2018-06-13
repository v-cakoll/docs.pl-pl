---
title: Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 154f4b9b6024d064e73d64c44e2398a5da47052c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557413"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór
W prosty scenariusz główny szczegółowy, masz z danymi <xref:System.Windows.Controls.ItemsControl> takich jak <xref:System.Windows.Controls.ListBox>. Oparte na wybór użytkownika, możesz wyświetlić więcej informacji na temat wybranego elementu. W tym przykładzie pokazano, jak wdrożyć ten scenariusz.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `People` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `Person` klasy. To `Person` klasa zawiera trzy właściwości: `FirstName`, `LastName`, i `HomeTown`, wszystkie typu `string`.  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> Są używane następujące <xref:System.Windows.DataTemplate> definiuje sposób informacje `Person` przedstawiono:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Poniżej przedstawiono przykład tworzy zrzut ekranu. <xref:System.Windows.Controls.ContentControl> Zawiera inne właściwości osoby wybrane.  
  
 ![Tworzenie powiązania z kolekcją](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Dostępne są następujące dwie rzeczy Zwróć uwagę, w tym przykładzie:  
  
1.  <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ContentControl> powiązać z tego samego źródła. <xref:System.Windows.Data.Binding.Path%2A> Nie podano właściwości zarówno powiązania, ponieważ oba formanty są powiązanie z obiektem całą kolekcję.  
  
2.  Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` Aby to zrobić. Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony na <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera on dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizowane wybór i waluty.  
  
 Należy pamiętać, że `Person` klasy zastąpienia `ToString` — metoda w następujący sposób. Domyślnie <xref:System.Windows.Controls.ListBox> wywołania `ToString` i wyświetla reprezentację ciągu każdego obiektu w powiązanej kolekcji. Dlatego każdy `Person` pojawia się jako pierwszej nazwy w <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie wzorca szczegółowego z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [Używanie wzorca szczegółowego z danymi hierarchicznymi XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Szablonowanie danych — omówienie](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
