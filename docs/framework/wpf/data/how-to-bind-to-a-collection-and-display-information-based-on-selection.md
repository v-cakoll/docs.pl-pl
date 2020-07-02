---
title: Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór
description: Postępuj zgodnie z tym przykładem, aby dowiedzieć się, jak utworzyć powiązanie z kolekcją i wyświetlić informacje na podstawie wyboru w Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619614"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór
W prostym scenariuszu wzorca szczegółowości masz powiązane dane, <xref:System.Windows.Controls.ItemsControl> takie jak <xref:System.Windows.Controls.ListBox> . W oparciu o wybór użytkownika można wyświetlić więcej informacji na temat wybranego elementu. Ten przykład pokazuje, jak zaimplementować ten scenariusz.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `People` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` klasą. Ta `Person` Klasa zawiera trzy właściwości: `FirstName` , `LastName` , i `HomeTown` , wszystkie typu `string` .  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl>Program używa następujących <xref:System.Windows.DataTemplate> elementów, które definiują sposób wyświetlania informacji `Person` :  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Poniżej znajduje się zrzut ekranu przedstawiający sposób tworzenia przykładu. <xref:System.Windows.Controls.ContentControl>Pokazuje inne właściwości wybranej osoby.  
  
 ![Powiązanie z kolekcją](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Oto dwie rzeczy do zauważenia w tym przykładzie:  
  
1. <xref:System.Windows.Controls.ListBox>I <xref:System.Windows.Controls.ContentControl> powiązanie z tym samym źródłem. <xref:System.Windows.Data.Binding.Path%2A>Nie określono właściwości obu powiązań, ponieważ obydwie kontrolki są powiązane z całym obiektem kolekcji.  
  
2. Aby to działało, należy ustawić właściwość na wartość <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> `true` . Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiany jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> . Alternatywnie, jeśli <xref:System.Windows.Controls.ListBox> Pobiera z niego dane <xref:System.Windows.Data.CollectionViewSource> , automatycznie synchronizuje wybór i walutę.  
  
 Należy zauważyć, że `Person` Klasa zastępuje `ToString` metodę w następujący sposób. Domyślnie <xref:System.Windows.Controls.ListBox> wywołania `ToString` i wyświetlają ciąg reprezentujący każdy obiekt w powiązanej kolekcji. To dlatego, że każdy `Person` pojawia się jako imię i nazwisko w <xref:System.Windows.Controls.ListBox> .  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie wzorca szczegółów wzorca z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Używanie wzorca szczegółów wzorca z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](data-templating-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
