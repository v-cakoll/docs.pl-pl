---
title: Jak użyć wzorca szczegółowego z danymi hierarchicznymi XML
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 0fe42d57fcaf4acee09340fdb3f5df73d7291566
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733413"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Jak użyć wzorca szczegółowego z danymi hierarchicznymi XML
Ten przykład pokazuje, jak zaimplementować scenariusz wzorzec-szczegóły przy użyciu danych XML.  
  
## <a name="example"></a>Przykład  
 Ten przykład to wersja danych XML przykładu omówionego w temacie [USE master-detail wzorzec z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md). W tym przykładzie dane pochodzą z pliku `League.xml`. Zwróć uwagę, jak trzeci formant <xref:System.Windows.Controls.ListBox> śledzi zmiany wyboru w drugim <xref:System.Windows.Controls.ListBox> przez powiązanie ze swoją właściwością <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.HierarchicalDataTemplate>
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
