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
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459142"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór
W prostym scenariuszu wzorca szczegółowości masz <xref:System.Windows.Controls.ItemsControl> powiązane z danymi, takie jak <xref:System.Windows.Controls.ListBox>. W oparciu o wybór użytkownika można wyświetlić więcej informacji na temat wybranego elementu. Ten przykład pokazuje, jak zaimplementować ten scenariusz.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `People` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> klas `Person`. Ta klasa `Person` zawiera trzy właściwości: `FirstName`, `LastName`i `HomeTown`wszystkie typy `string`.  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> używa następujących <xref:System.Windows.DataTemplate>, które definiują sposób przedstawiania informacji `Person`:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Poniżej znajduje się zrzut ekranu przedstawiający sposób tworzenia przykładu. W <xref:System.Windows.Controls.ContentControl> są wyświetlane inne właściwości wybranej osoby.  
  
 ![Powiązanie z kolekcją](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Oto dwie rzeczy do zauważenia w tym przykładzie:  
  
1. <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ContentControl> powiązać z tym samym źródłem. Nie określono właściwości <xref:System.Windows.Data.Binding.Path%2A> obu powiązań, ponieważ obydwie kontrolki są powiązane z całym obiektem kolekcji.  
  
2. Aby ta wartość działała, należy ustawić `true` Właściwość <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>. Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiany jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatywnie, jeśli <xref:System.Windows.Controls.ListBox> pobiera dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i walutę.  
  
 Należy zauważyć, że Klasa `Person` przesłania metodę `ToString` w następujący sposób. Domyślnie <xref:System.Windows.Controls.ListBox> wywołuje `ToString` i wyświetla reprezentację ciągu dla każdego obiektu w powiązanej kolekcji. To dlatego, że każdy `Person` pojawia się jako imię w <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie wzorca szczegółowego z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Używanie wzorca szczegółowego z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](data-templating-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
