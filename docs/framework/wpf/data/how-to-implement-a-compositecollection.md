---
title: 'Instrukcje: Implementowanie CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 8361c2bfa9c125aeadf0a62ca86af1855e5c3dbc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091168"
---
# <a name="how-to-implement-a-compositecollection"></a>Instrukcje: Implementowanie CompositeCollection
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyświetlić wiele kolekcji i elementów jako ją przy użyciu listy <xref:System.Windows.Data.CompositeCollection> klasy. W tym przykładzie `GreekGods` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` niestandardowych obiektów. Szablony danych są zdefiniowane tak, aby `GreekGod` obiektów i `GreekHero` obiekty są wyświetlane z gold i kolor pierwszego planu cyjan odpowiednio.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Przegląd Wiązanie danych](data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
