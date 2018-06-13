---
title: Jak użyć wzorca szczegółowego z danymi hierarchicznymi
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 46733b462861bdac3381cdacb8f2fbe0536d12eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556799"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Jak użyć wzorca szczegółowego z danymi hierarchicznymi
W tym przykładzie pokazano, jak wdrożyć scenariusz główny szczegółowy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `LeagueList` jest kolekcją `Leagues`. Każdy `League` ma `Name` i Kolekcja `Divisions`i każdego `Division` ma nazwę oraz zbiór `Teams`. Każdy `Team` ma nazwę zespołu.  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Poniżej przedstawiono zrzut ekranu przykładu. `Divisions` <xref:System.Windows.Controls.ListBox> Automatyczne śledzenie zaznaczenia w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetlić odpowiednie dane. `Teams` <xref:System.Windows.Controls.ListBox> Śledzi opcje dla pozostałych <xref:System.Windows.Controls.ListBox> kontrolki.  
  
 ![Wzorzec&#45;przykład szczegółów](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 Dostępne są następujące dwie rzeczy Zwróć uwagę, w tym przykładzie:  
  
1.  Trzy <xref:System.Windows.Controls.ListBox> formanty powiązać z tego samego źródła. Możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwości powiązania, aby określić poziom danych, <xref:System.Windows.Controls.ListBox> do wyświetlenia.  
  
2.  Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` na <xref:System.Windows.Controls.ListBox> formantów, które są śledzone zaznaczenie. Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony na <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera on dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizowane wybór i waluty.  
  
 Technika jest nieco inne w przypadku korzystania z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych. Na przykład zobacz [wzorzec wzorzec-szczegół za pomocą hierarchiczne dane XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Szablonowanie danych — omówienie](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
