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
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="625a4-102">Jak implementować CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="625a4-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="625a4-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="625a4-103">Example</span></span>  
 <span data-ttu-id="625a4-104">Poniższy przykład pokazuje, jak wyświetlić wiele kolekcji i elementów jako jedną listę przy użyciu klasy <xref:System.Windows.Data.CompositeCollection>.</span><span class="sxs-lookup"><span data-stu-id="625a4-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="625a4-105">W tym przykładzie `GreekGods` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> `GreekGod` obiektów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="625a4-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="625a4-106">Szablony danych są definiowane, aby obiekty `GreekGod` i obiekty `GreekHero` były wyświetlane z użyciem koloru złota i Błękitnego pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="625a4-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="625a4-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="625a4-107">See also</span></span>

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="625a4-108">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="625a4-108">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="625a4-109">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="625a4-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
