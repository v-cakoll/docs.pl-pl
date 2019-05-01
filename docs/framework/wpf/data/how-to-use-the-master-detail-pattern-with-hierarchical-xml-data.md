---
title: 'Instrukcje: Używanie wzorca szczegółowego z danymi hierarchicznymi XML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: ba6c932f519ffa5c3c70ecb21eb9b5d08c40fb28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931758"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="22651-102">Instrukcje: Używanie wzorca szczegółowego z danymi hierarchicznymi XML</span><span class="sxs-lookup"><span data-stu-id="22651-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="22651-103">W tym przykładzie pokazano, jak implementować scenariusza wzorzec / szczegół za pomocą [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.</span><span class="sxs-lookup"><span data-stu-id="22651-103">This example shows how to implement the master-detail scenario with [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22651-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="22651-104">Example</span></span>  
 <span data-ttu-id="22651-105">W tym przykładzie jest [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] wersja danych przykład omówione w [Użyj wzorca szczegółowego z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span><span class="sxs-lookup"><span data-stu-id="22651-105">This example is the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="22651-106">W tym przykładzie dane są z pliku `League.xml`.</span><span class="sxs-lookup"><span data-stu-id="22651-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="22651-107">Uwaga jak trzeci <xref:System.Windows.Controls.ListBox> kontroli śledzi zmiany zaznaczenia w drugim <xref:System.Windows.Controls.ListBox> przez powiązanie jej <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="22651-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="22651-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22651-108">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="22651-109">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="22651-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
