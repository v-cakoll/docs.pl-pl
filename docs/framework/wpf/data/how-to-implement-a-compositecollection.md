---
title: 'Instrukcje: Zaimplementuj CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 2021ed83a8f2a6896631fa69d5dd55a74cad8a8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691869"
---
# <a name="how-to-implement-a-compositecollection"></a>Instrukcje: Zaimplementuj CompositeCollection
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyświetlić wiele kolekcji i elementów jako ją przy użyciu listy <xref:System.Windows.Data.CompositeCollection> klasy. W tym przykładzie `GreekGods` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` niestandardowych obiektów. Szablony danych są zdefiniowane tak, aby `GreekGod` obiektów i `GreekHero` obiekty są wyświetlane z gold i kolor pierwszego planu cyjan odpowiednio.  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
