---
title: Jak użyć wzorca szczegółowego z danymi hierarchicznymi XML
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 5b3a9d83dcec169fd9607c84b0a66eab0098b238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555928"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="ae020-102">Jak użyć wzorca szczegółowego z danymi hierarchicznymi XML</span><span class="sxs-lookup"><span data-stu-id="ae020-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="ae020-103">W tym przykładzie pokazano, jak wdrożyć scenariusz wzorzec szczegół z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.</span><span class="sxs-lookup"><span data-stu-id="ae020-103">This example shows how to implement the master-detail scenario with [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae020-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae020-104">Example</span></span>  
 <span data-ttu-id="ae020-105">W tym przykładzie jest [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] wersji danych przykładu omówione w [Użyj wzorca wzorzec-szczegół z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span><span class="sxs-lookup"><span data-stu-id="ae020-105">This example is the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="ae020-106">W tym przykładzie dane są z pliku `League.xml`.</span><span class="sxs-lookup"><span data-stu-id="ae020-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="ae020-107">Uwaga jak trzeci <xref:System.Windows.Controls.ListBox> kontroli śledzi zmiany wyboru w ciągu sekundy <xref:System.Windows.Controls.ListBox> przez powiązanie do jego <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae020-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="ae020-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae020-108">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="ae020-109">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ae020-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
