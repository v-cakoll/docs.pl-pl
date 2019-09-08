---
title: Powiązanie danych i LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 563d57249daa3aa720da1d9654866727f770afb3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786701"
---
# <a name="data-binding-and-linq-to-dataset"></a>Powiązanie danych i LINQ to DataSet
*Powiązanie danych* to proces, który ustanawia połączenie między interfejsem użytkownika aplikacji i logiką biznesową. Jeśli powiązanie ma poprawne ustawienia, a dane udostępniają odpowiednie powiadomienia, gdy zmieniają się dane, elementy, które są powiązane z danymi, odzwierciedlają zmiany automatycznie. <xref:System.Data.DataSet> Jest reprezentacja danych w pamięci, która zapewnia spójny relacyjny model programowania, niezależnie od źródła danych, które zawiera. ADO.NET 2,0 <xref:System.Data.DataView> pozwala sortować i filtrować dane przechowywane <xref:System.Data.DataTable>w. Ta funkcja jest często używana w aplikacjach do wiązania danych. Za pomocą <xref:System.Data.DataView>, można uwidocznić dane w tabeli z różnymi kolejności sortowania i można filtrować dane według stanu wiersza lub w oparciu o wyrażenie filtru. Aby uzyskać więcej informacji na <xref:System.Data.DataView> temat obiektu, zobacz [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet pozwala deweloperom na tworzenie złożonych, zaawansowanych zapytań w <xref:System.Data.DataSet> odniesieniu do programu przy użyciu. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Jednak zapytanie LINQ to DataSet zwraca Wyliczenie <xref:System.Data.DataRow> obiektów, które nie jest łatwo używane w scenariuszu powiązania. Aby ułatwić tworzenie powiązań, można utworzyć <xref:System.Data.DataView> zapytanie na podstawie LINQ to DataSet. Powoduje <xref:System.Data.DataView> to użycie filtrowania i sortowania określonego w zapytaniu, ale jest lepiej dopasowane do powiązania danych. LINQ to DataSet rozszerza funkcje <xref:System.Data.DataView> programu, dostarczając [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] oparte na wyrażeniach filtrowanie i sortowanie, które pozwala na znacznie bardziej złożone i zaawansowane operacje filtrowania i sortowania niż oparte na ciągach filtrowanie i sortowanie.  
  
 Należy zauważyć, <xref:System.Data.DataView> że reprezentuje kwerendę i nie jest widokiem na górze zapytania. Jest powiązany z kontrolką interfejsu użytkownika, taką <xref:System.Windows.Forms.DataGrid> jak lub <xref:System.Windows.Forms.DataGridView>, dostarczając prosty model powiązań danych. <xref:System.Data.DataView> Można również utworzyć <xref:System.Data.DataTable>z, dostarczając widok domyślny tej tabeli. <xref:System.Data.DataView>  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie obiektu widoku danych](creating-a-dataview-object-linq-to-dataset.md)  
 Zawiera informacje na <xref:System.Data.DataView>temat tworzenia.  
  
 [Filtrowanie za pomocą widoku danych.](filtering-with-dataview-linq-to-dataset.md)  
 Opisuje sposób filtrowania przy użyciu <xref:System.Data.DataView>.  
  
 [Sortowanie za pomocą widoku danych.](sorting-with-dataview-linq-to-dataset.md)  
 Opisuje sposób sortowania przy użyciu <xref:System.Data.DataView>.  
  
 [Wykonywanie zapytania do kolekcji DataRowView w widoku danych](querying-the-datarowview-collection-in-a-dataview.md)  
 Zawiera informacje o wysyłaniu zapytań <xref:System.Data.DataRowView> do kolekcji uwidocznionej przez <xref:System.Data.DataView>program.  
  
 [Wydajność widoku danych](dataview-performance.md)  
 Zawiera informacje o <xref:System.Data.DataView> wydajności i.  
  
 [Instrukcje: Powiązywanie obiektu DataView z Windows Forms formantem DataGridView](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Opisuje sposób powiązania <xref:System.Data.DataView> obiektu <xref:System.Windows.Forms.DataGridView>z.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](programming-guide-linq-to-dataset.md)
