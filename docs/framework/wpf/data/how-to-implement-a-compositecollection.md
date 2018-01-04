---
title: "Jak implementować CompositeCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b33e3a61b91c2f9e2362a270216038d61770b815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="9ef85-102">Jak implementować CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="9ef85-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="9ef85-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ef85-103">Example</span></span>  
 <span data-ttu-id="9ef85-104">Poniższy przykład przedstawia sposób wyświetlania wielu kolekcji i elementów jako go przy użyciu listy <xref:System.Windows.Data.CompositeCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="9ef85-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="9ef85-105">W tym przykładzie `GreekGods` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` niestandardowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="9ef85-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="9ef85-106">Szablony dane są zdefiniowane tak, że `GreekGod` obiektów i `GreekHero` obiekty są wyświetlane z złota i kolor pierwszego planu błękitnego odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9ef85-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9ef85-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ef85-107">See Also</span></span>  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [<span data-ttu-id="9ef85-108">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="9ef85-108">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="9ef85-109">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9ef85-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
