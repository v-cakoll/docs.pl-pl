---
title: 'Instrukcje: Zaimplementuj CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 71d55a23711b116a91386a537d5572e8506d4c6b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372675"
---
# <a name="how-to-implement-a-compositecollection"></a>Instrukcje: Zaimplementuj CompositeCollection
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyświetlić wiele kolekcji i elementów jako ją przy użyciu listy <xref:System.Windows.Data.CompositeCollection> klasy. W tym przykładzie `GreekGods` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` niestandardowych obiektów. Szablony danych są zdefiniowane tak, aby `GreekGod` obiektów i `GreekHero` obiekty są wyświetlane z gold i kolor pierwszego planu cyjan odpowiednio.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
