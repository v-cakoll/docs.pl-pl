---
title: 'Instrukcje: Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru'
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
ms.openlocfilehash: bb7d4c89e63982a3052857dcb50d04d36d9517dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314397"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Instrukcje: Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru
W prostym scenariuszu wzorzec / szczegół mają powiązane z danymi <xref:System.Windows.Controls.ItemsControl> takich jak <xref:System.Windows.Controls.ListBox>. Na podstawie wyboru użytkownik możesz wyświetlić więcej informacji na temat wybranego elementu. W tym przykładzie pokazano, jak wdrożyć ten scenariusz.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `People` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `Person` klasy. To `Person` klasa zawiera trzy właściwości: `FirstName`, `LastName`, i `HomeTown`, typ `string`.  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> Korzysta z następujących <xref:System.Windows.DataTemplate> definiuje sposób informacje o `Person` zobaczy:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Poniżej przedstawiono zrzut ekranu przedstawiający przykład generuje. <xref:System.Windows.Controls.ContentControl> Pokazuje właściwości osoby wybrane.  
  
 ![Tworzenie powiązania z kolekcją](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Dostępne są następujące dwie czynności należy zwrócić uwagę, w tym przykładzie:  
  
1. <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ContentControl> powiązania z tym samym źródłem. <xref:System.Windows.Data.Binding.Path%2A> Właściwości zarówno powiązania nie są określone, ponieważ obie kontrolki dokonywane jest wiązanie obiektu całą kolekcję.  
  
2. Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwość `true` Aby to działało. Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera ona dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i aktualność.  
  
 Należy pamiętać, że `Person` klasy zastąpienia `ToString` metody w następujący sposób. Domyślnie <xref:System.Windows.Controls.ListBox> wywołania `ToString` i wyświetla reprezentację ciągu każdego obiektu w powiązanej kolekcji. Dlatego każdego `Person` pojawia się jako nazwę pierwszego <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie wzorca szczegółowego z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Używanie wzorca szczegółowego z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Przegląd Wiązanie danych](data-binding-overview.md)
- [Przegląd Szablonowanie danych](data-templating-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
