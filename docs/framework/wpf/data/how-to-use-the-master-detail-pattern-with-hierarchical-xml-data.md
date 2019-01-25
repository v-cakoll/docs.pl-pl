---
title: 'Instrukcje: Użyj wzorca szczegółowego z danymi hierarchicznymi XML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 4beb2377fa9740e5103df0a82cfda9bd5f6f4769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550078"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Instrukcje: Użyj wzorca szczegółowego z danymi hierarchicznymi XML
W tym przykładzie pokazano, jak implementować scenariusza wzorzec / szczegół za pomocą [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] wersja danych przykład omówione w [Użyj wzorca szczegółowego z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). W tym przykładzie dane są z pliku `League.xml`. Uwaga jak trzeci <xref:System.Windows.Controls.ListBox> kontroli śledzi zmiany zaznaczenia w drugim <xref:System.Windows.Controls.ListBox> przez powiązanie jej <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości.  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.HierarchicalDataTemplate>
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
