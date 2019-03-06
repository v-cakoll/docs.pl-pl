---
title: 'Instrukcje: Zdefiniuj tabelę przy użyciu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 7398af6fddae56238e1af3ee4e726420c01ab7ea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376926"
---
# <a name="how-to-define-a-table-with-xaml"></a>Instrukcje: Zdefiniuj tabelę przy użyciu XAML
Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Documents.Table> przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Przykładowa tabela ma cztery kolumny (reprezentowane przez <xref:System.Windows.Documents.TableColumn> elementy) i kilka wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> elementy) zawierające dane, a także jako title, nagłówek i informacje w stopce.  Wierszy musi być zawarty w <xref:System.Windows.Documents.TableRowGroup> elementu.  Każdy wiersz w tabeli składa się z co najmniej jedna komórka (reprezentowane przez <xref:System.Windows.Documents.TableCell> elementów).  Zawartość komórki tabeli muszą być zawarte w <xref:System.Windows.Documents.Block> elementu; w takim przypadku <xref:System.Windows.Documents.Paragraph> elementy są używane.  Tabela hostuje również hiperłącze (reprezentowane przez <xref:System.Windows.Documents.Hyperlink> elementu) w wierszu stopki.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 Na poniższej ilustracji przedstawiono, jak renderuje tabeli zdefiniowane w tym przykładzie.  
  
 ![Tabela renderowany. ](./media/tableeg.png "TableEG")
