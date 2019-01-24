---
title: 'Instrukcje: Użyj wzorca szczegółowego z danymi hierarchicznymi'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 36eded28085aec3aaea1a2351ae3babc6ad6c700
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689643"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Instrukcje: Użyj wzorca szczegółowego z danymi hierarchicznymi
W tym przykładzie pokazano, jak można implementować scenariusza wzorzec / szczegół.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `LeagueList` to zbiór `Leagues`. Każdy `League` ma `Name` i kolekcji `Divisions`i każdy `Division` ma nazwę oraz zbiór `Teams`. Każdy `Team` ma nazwę zespołu.  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Poniżej przedstawiono zrzut ekranu przykładu. `Divisions` <xref:System.Windows.Controls.ListBox> Automatyczne śledzenie zaznaczenia w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetlić odpowiednie dane. `Teams` <xref:System.Windows.Controls.ListBox> Śledzi wybory w dwóch pozostałych <xref:System.Windows.Controls.ListBox> kontrolki.  
  
 ![Wzorzec&#45;przykład szczegółów](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 Dostępne są następujące dwie czynności należy zwrócić uwagę, w tym przykładzie:  
  
1.  Trzy <xref:System.Windows.Controls.ListBox> kontrolki powiązania z tym samym źródłem. Możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwości powiązania, aby określić, której poziom danych <xref:System.Windows.Controls.ListBox> do wyświetlenia.  
  
2.  Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` na <xref:System.Windows.Controls.ListBox> kontrolek, których wybór są śledzone. Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera ona dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i aktualność.  
  
 Technika jest nieco inne w przypadku, gdy używasz [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych. Aby uzyskać przykład, zobacz [Użyj wzorca szczegółowego z danymi hierarchicznymi XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.HierarchicalDataTemplate>
- [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
