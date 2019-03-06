---
title: 'Instrukcje: Twórz tabele za pomocą programowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 3848032bf527f64ce591eb2cda98028c835d79f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371939"
---
# <a name="how-to-build-a-table-programmatically"></a>Instrukcje: Twórz tabele za pomocą programowania
W poniższych przykładach pokazano, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnianie jej zawartości. Zawartość tej tabeli są rozdzielone na pięć wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiektów zawartych w <xref:System.Windows.Documents.Table.RowGroups%2A> obiekt) i 6 kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> obiektów). Wiersze są używane do celów innej prezentacji, w tym wiersz tytułu przeznaczone do tytułu całą tabelę, wiersz nagłówka do opisania kolumn danych w tabeli i wiersz stopki z podsumowaniem.  Należy pamiętać, że pojęcie "title", "header" i "stopka" wierszy nie są wbudowane w tabeli; są to po prostu wiersze o różnej charakterystyce. Komórki tabeli zawierają rzeczywistej zawartości może składać się z tekstu, obrazów lub niemal każdy inny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
## <a name="example"></a>Przykład  
 Najpierw <xref:System.Windows.Documents.FlowDocument> jest tworzona na hoście <xref:System.Windows.Documents.Table>, nowy <xref:System.Windows.Documents.Table> zostanie utworzony i dodany do zawartości <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Przykład  
 Następnie sześciu <xref:System.Windows.Documents.TableColumn> obiekty są tworzone i dodawane do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji z niektórych zastosowanym formatowaniem.  
  
> [!NOTE]
>  Należy pamiętać, że tabela <xref:System.Windows.Documents.Table.Columns%2A> kolekcja używa standardowych indeksowania zaczynającego się od zera.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz tytułu jest tworzone i dodawane do tabeli za pomocą niektórych zastosowanym formatowaniem.  Wiersz tytułu odbywa się zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz nagłówka zostanie utworzony i dodany do tabeli i komórki w wierszu nagłówka są tworzone i wypełniane zawartością.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz danych zostanie utworzony i dodany do tabeli i komórek w tym wierszu są tworzone i wypełniane zawartością.  Tworzenie tego wiersza jest podobne do tworzenia wiersz nagłówka z zastosowanym formatowaniem nieco inne.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Przykład  
 Na koniec wiersza stopki utworzone, dodać i sformatowany.  Podobnie jak wiersz tytułu stopki zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd tabeli](table-overview.md)
