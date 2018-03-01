---
title: "Jak tworzyć tabele za pomocą programowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fca6a304ea12dd90a71f8718fed5f1595f4cd4b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-table-programmatically"></a>Jak tworzyć tabele za pomocą programowania
W poniższych przykładach pokazano, jak utworzyć programowo <xref:System.Windows.Documents.Table> i wypełnianie jej zawartości. Zawartość tabeli są rozdzielone do pięciu wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiektów zawartych w <xref:System.Windows.Documents.Table.RowGroups%2A> obiektu) i sześć kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> obiektów). Wiersze są używane do przedstawienia różnych celów, w tym tytuł wiersz przeznaczony do title całą tabelę, wiersz nagłówka do opisywania kolumn danych w tabeli i wiersz stopki z podsumowaniem.  Należy pamiętać, że pojęcie "title", "header" i "stopka" wierszy nie są włączone do tabeli; są to po prostu wierszy o różnej charakterystyce. Komórki tabeli zawierają rzeczywistej zawartości, może składać się z tekstu, obrazów lub niemal każdy inny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
## <a name="example"></a>Przykład  
 Najpierw <xref:System.Windows.Documents.FlowDocument> jest tworzony na hoście <xref:System.Windows.Documents.Table>i nowy <xref:System.Windows.Documents.Table> jest tworzony i dodawany do zawartości <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Przykład  
 Następnie sześciu <xref:System.Windows.Documents.TableColumn> obiekty są tworzone i dodawane do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji z niektórych formatowanie zastosowane.  
  
> [!NOTE]
>  Należy pamiętać, że tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcja używa standardowych indeksowania liczony od zera.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz tytuł jest utworzony i dodane do tabeli z niektórych formatowanie zastosowane.  Wiersz tytułu odbywa się zawiera jedną komórkę, które obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz nagłówka jest tworzony i dodawany do tabeli i komórek w wierszu nagłówka są tworzone i wypełniane przy użyciu zawartości.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz danych jest tworzony i dodawany do tabeli i komórek w tym wierszu są tworzone i wypełniane przy użyciu zawartości.  Tworzenie tego wiersza jest podobny do budowania wiersz nagłówka z zastosowanym formatowaniem nieco inne.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Przykład  
 Na koniec wiersza stopki jest utworzony, dodane i sformatowany.  Podobnie jak wiersz tytuł stopki zawiera jedną komórkę, które obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd tabeli](../../../../docs/framework/wpf/advanced/table-overview.md)
