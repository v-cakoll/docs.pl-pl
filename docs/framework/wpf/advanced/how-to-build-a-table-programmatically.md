---
title: 'Instrukcje: Programowe tworzenie tabeli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 9c9061d3c4d6b3de5e1ab42a6b98c20813835ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964158"
---
# <a name="how-to-build-a-table-programmatically"></a>Instrukcje: Programowe tworzenie tabeli
W poniższych przykładach pokazano, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnić zawartość. Zawartość tabeli jest przydzielona do pięciu wierszy (reprezentowanych przez <xref:System.Windows.Documents.TableRow> obiekty zawarte <xref:System.Windows.Documents.Table.RowGroups%2A> w obiekcie) i sześciu kolumn (reprezentowanych <xref:System.Windows.Documents.TableColumn> przez obiekty). Wiersze są używane do różnych celów prezentacji, łącznie z wierszem tytułu, który ma tytuł całej tabeli, wiersz nagłówka opisujący kolumny danych w tabeli oraz wiersz stopki z informacjami podsumowującymi.  Należy zauważyć, że pojęcie wierszy "title", "Header" i "Stopka" nie jest związane z tabelą; są to po prostu wiersze o różnej charakterystyce. Komórki tabeli zawierają rzeczywistą zawartość, która może składać się z tekstu, obrazów lub niemal dowolnego innego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
## <a name="example"></a>Przykład  
 Najpierw jest tworzony w celu <xref:System.Windows.Documents.Table>hostowania, a nowy <xref:System.Windows.Documents.Table> jest <xref:System.Windows.Documents.FlowDocument>tworzony i dodawany do zawartości. <xref:System.Windows.Documents.FlowDocument>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Przykład  
 Następnie do <xref:System.Windows.Documents.Table.Columns%2A> kolekcji <xref:System.Windows.Documents.TableColumn> tabel są tworzone i dodawane sześć obiektów z zastosowaniem formatowania.  
  
> [!NOTE]
> Należy zauważyć, że <xref:System.Windows.Documents.Table.Columns%2A> kolekcja tabeli używa standardowego indeksowania opartego na zero.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz tytułu zostanie utworzony i dodany do tabeli z zastosowaniem formatowania.  Wiersz tytułu ma zawierać pojedynczą komórkę obejmującą wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz nagłówka jest tworzony i dodawany do tabeli, a komórki w wierszu nagłówka są tworzone i wypełniane zawartością.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Przykład  
 Następnie wiersz danych jest tworzony i dodawany do tabeli, a komórki w tym wierszu są tworzone i wypełniane zawartością.  Kompilowanie tego wiersza jest podobne do tworzenia wiersza nagłówka z niewielkim innym formatowaniem.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Przykład  
 Na koniec wiersz stopki jest tworzony, dodawany i sformatowany.  Podobnie jak w przypadku wiersza tytułu, stopka zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd tabeli](table-overview.md)
