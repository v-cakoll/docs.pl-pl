---
title: "Jak zdefiniować tabelę przy użyciu XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b932c7df822edabc5626f20af2bfc1eb3a7f93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-table-with-xaml"></a>Jak zdefiniować tabelę przy użyciu XAML
W poniższym przykładzie pokazano sposób definiowania <xref:System.Windows.Documents.Table> przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Przykładowa tabela ma cztery kolumny (reprezentowany przez <xref:System.Windows.Documents.TableColumn> elementy) i kilka wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> elementy) zawierające dane, a także jako tytuł, nagłówek i informacje stopki.  Wierszy musi być zawarty w <xref:System.Windows.Documents.TableRowGroup> elementu.  Każdy wiersz w tabeli składa się z co najmniej jedna komórka (reprezentowane przez <xref:System.Windows.Documents.TableCell> elementów).  Zawartość w komórce tabeli muszą być zawarte w <xref:System.Windows.Documents.Block> elementu; w takim przypadku <xref:System.Windows.Documents.Paragraph> elementy są używane.  Tabela hostuje również hiperłącza (reprezentowane przez <xref:System.Windows.Documents.Hyperlink> element) w wierszu stopki.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 Na poniższej ilustracji przedstawiono, jak renderuje tabeli zdefiniowane w tym przykładzie.  
  
 ![Tabela renderowany. ] (../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")
