---
title: Jak implementować CompositeCollection
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: b3450cdc476b7090251a06b5b2b2718d29e18209
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454028"
---
# <a name="how-to-implement-a-compositecollection"></a>Jak implementować CompositeCollection
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyświetlić wiele kolekcji i elementów jako jedną listę przy użyciu klasy <xref:System.Windows.Data.CompositeCollection>. W tym przykładzie `GreekGods` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> `GreekGod` obiektów niestandardowych. Szablony danych są definiowane, aby obiekty `GreekGod` i obiekty `GreekHero` były wyświetlane z użyciem koloru złota i Błękitnego pierwszego planu.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
