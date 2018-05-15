---
title: Jak implementować CompositeCollection
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: f8af8d806b8c889be11533392ee3c831399e9ab7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="f6951-102">Jak implementować CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="f6951-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="f6951-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6951-103">Example</span></span>  
 <span data-ttu-id="f6951-104">Poniższy przykład przedstawia sposób wyświetlania wielu kolekcji i elementów jako go przy użyciu listy <xref:System.Windows.Data.CompositeCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="f6951-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="f6951-105">W tym przykładzie `GreekGods` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` niestandardowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="f6951-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="f6951-106">Szablony dane są zdefiniowane tak, że `GreekGod` obiektów i `GreekHero` obiekty są wyświetlane z złota i kolor pierwszego planu błękitnego odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f6951-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f6951-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6951-107">See Also</span></span>  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [<span data-ttu-id="f6951-108">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="f6951-108">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="f6951-109">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="f6951-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
