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
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="0fdf0-102">Instrukcje: Implementowanie CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="0fdf0-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="0fdf0-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fdf0-103">Example</span></span>  
 <span data-ttu-id="0fdf0-104">Poniższy przykład pokazuje, jak wyświetlić wiele kolekcji i elementów jako ją przy użyciu listy <xref:System.Windows.Data.CompositeCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="0fdf0-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="0fdf0-105">W tym przykładzie `GreekGods` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` niestandardowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="0fdf0-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="0fdf0-106">Szablony danych są zdefiniowane tak, aby `GreekGod` obiektów i `GreekHero` obiekty są wyświetlane z gold i kolor pierwszego planu cyjan odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0fdf0-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0fdf0-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fdf0-107">See also</span></span>

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="0fdf0-108">Przegląd Wiązanie danych</span><span class="sxs-lookup"><span data-stu-id="0fdf0-108">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="0fdf0-109">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="0fdf0-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
