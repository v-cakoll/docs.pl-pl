---
title: 'Instrukcje: Używanie wzorca szczegółowego z danymi hierarchicznymi XML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: ba6c932f519ffa5c3c70ecb21eb9b5d08c40fb28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086263"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Instrukcje: Używanie wzorca szczegółowego z danymi hierarchicznymi XML
W tym przykładzie pokazano, jak implementować scenariusza wzorzec / szczegół za pomocą [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] wersja danych przykład omówione w [Użyj wzorca szczegółowego z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md). W tym przykładzie dane są z pliku `League.xml`. Uwaga jak trzeci <xref:System.Windows.Controls.ListBox> kontroli śledzi zmiany zaznaczenia w drugim <xref:System.Windows.Controls.ListBox> przez powiązanie jej <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.HierarchicalDataTemplate>
- [— Tematy porad](data-binding-how-to-topics.md)
