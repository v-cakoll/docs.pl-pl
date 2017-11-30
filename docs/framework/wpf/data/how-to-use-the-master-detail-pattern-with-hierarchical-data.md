---
title: "Jak użyć wzorca szczegółowego z danymi hierarchicznymi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb546a3429012a49ee7652a3470460935fc76d70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Jak użyć wzorca szczegółowego z danymi hierarchicznymi
W tym przykładzie pokazano, jak wdrożyć scenariusz główny szczegółowy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `LeagueList` jest kolekcją `Leagues`. Każdy `League` ma `Name` i Kolekcja `Divisions`i każdego `Division` ma nazwę oraz zbiór `Teams`. Każdy `Team` ma nazwę zespołu.  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Poniżej przedstawiono zrzut ekranu przykładu. `Divisions` <xref:System.Windows.Controls.ListBox> Automatyczne śledzenie zaznaczenia w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetlić odpowiednie dane. `Teams` <xref:System.Windows.Controls.ListBox> Śledzi opcje dla pozostałych <xref:System.Windows.Controls.ListBox> kontrolki.  
  
 ![&#45;wzorca; przykład szczegółów](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 Dostępne są następujące dwie rzeczy Zwróć uwagę, w tym przykładzie:  
  
1.  Trzy <xref:System.Windows.Controls.ListBox> formanty powiązać z tego samego źródła. Możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwości powiązania, aby określić poziom danych, <xref:System.Windows.Controls.ListBox> do wyświetlenia.  
  
2.  Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` na <xref:System.Windows.Controls.ListBox> formantów, które są śledzone zaznaczenie. Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony na <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera on dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizowane wybór i waluty.  
  
 Technika jest nieco inne w przypadku korzystania z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych. Na przykład zobacz [wzorzec wzorzec-szczegół za pomocą hierarchiczne dane XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [Powiązania w kolekcji i wyświetlania informacji na podstawie zaznaczenia](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
