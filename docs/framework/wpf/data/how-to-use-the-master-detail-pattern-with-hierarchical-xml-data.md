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
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Jak użyć wzorca szczegółowego z danymi hierarchicznymi XML
W tym przykładzie pokazano, jak wdrożyć scenariusz wzorzec szczegół z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] wersji danych przykładu omówione w [Użyj wzorca wzorzec-szczegół z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). W tym przykładzie dane są z pliku `League.xml`. Uwaga jak trzeci <xref:System.Windows.Controls.ListBox> kontroli śledzi zmiany wyboru w ciągu sekundy <xref:System.Windows.Controls.ListBox> przez powiązanie do jego <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości.  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
