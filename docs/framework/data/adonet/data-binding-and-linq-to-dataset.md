---
title: Powiązanie danych i LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 2b49e2a3ff0d95dcbceff8099f51993c0f08d64e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634875"
---
# <a name="data-binding-and-linq-to-dataset"></a>Powiązanie danych i LINQ to DataSet
*Powiązanie danych* to proces, który ustanawia połączenie między interfejsem użytkownika aplikacji i logiką biznesową. Jeśli powiązanie ma poprawne ustawienia, a dane udostępniają odpowiednie powiadomienia, gdy zmieniają się dane, elementy, które są powiązane z danymi, odzwierciedlają zmiany automatycznie. <xref:System.Data.DataSet> to reprezentacja danych w pamięci, która zapewnia spójny relacyjny model programowania, niezależnie od źródła danych, które zawiera. ADO.NET 2,0 <xref:System.Data.DataView> umożliwia sortowanie i filtrowanie danych przechowywanych w <xref:System.Data.DataTable>. Ta funkcja jest często używana w aplikacjach do wiązania danych. Za pomocą <xref:System.Data.DataView>można uwidocznić dane w tabeli z różnymi kolejności sortowania i można filtrować dane według stanu wiersza lub w oparciu o wyrażenie filtru. Aby uzyskać więcej informacji na temat obiektu <xref:System.Data.DataView>, zobacz [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet umożliwia deweloperom tworzenie złożonych, zaawansowanych zapytań w ramach <xref:System.Data.DataSet> przy użyciu języka CLR (Language-Integrated Query). Jednak zapytanie LINQ to DataSet zwraca Wyliczenie obiektów <xref:System.Data.DataRow>, które nie jest łatwo używane w scenariuszu powiązania. Aby ułatwić tworzenie powiązań, można utworzyć <xref:System.Data.DataView> z kwerendy LINQ to DataSetowej. Ten <xref:System.Data.DataView> używa filtrowania i sortowania określonego w zapytaniu, ale jest lepiej dostosowany do powiązania danych. LINQ to DataSet rozszerza funkcjonalność <xref:System.Data.DataView>, zapewniając filtrowanie i sortowanie oparte na wyrażeniach LINQ, które pozwala na znacznie bardziej złożone i zaawansowane operacje filtrowania i sortowania niż oparte na ciągach filtrowanie i sortowanie.  
  
 Należy zauważyć, że <xref:System.Data.DataView> reprezentuje samo zapytanie i nie jest widokiem na górze zapytania. <xref:System.Data.DataView> jest powiązany z kontrolką interfejsu użytkownika, taką jak <xref:System.Windows.Forms.DataGrid> lub <xref:System.Windows.Forms.DataGridView>, zapewniając prosty model powiązań danych. <xref:System.Data.DataView> można również utworzyć na podstawie <xref:System.Data.DataTable>, dostarczając widok domyślny tej tabeli.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie obiektu widoku danych](creating-a-dataview-object-linq-to-dataset.md)  
 Zawiera informacje dotyczące tworzenia <xref:System.Data.DataView>.  
  
 [Filtrowanie za pomocą widoku danych.](filtering-with-dataview-linq-to-dataset.md)  
 Opisuje sposób filtrowania przy użyciu <xref:System.Data.DataView>.  
  
 [Sortowanie za pomocą widoku danych.](sorting-with-dataview-linq-to-dataset.md)  
 Opisuje sposób sortowania przy użyciu <xref:System.Data.DataView>.  
  
 [Wykonywanie zapytania do kolekcji DataRowView w widoku danych](querying-the-datarowview-collection-in-a-dataview.md)  
 Zawiera informacje o wysyłaniu zapytań do kolekcji <xref:System.Data.DataRowView> uwidocznionej przez <xref:System.Data.DataView>.  
  
 [Wydajność widoku danych](dataview-performance.md)  
 Zawiera informacje o <xref:System.Data.DataView> i wydajności.  
  
 [Instrukcje: Powiązanie obiektu widoku danych z kontrolką DataGridView formularzy systemu Windows](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Opisuje sposób powiązania obiektu <xref:System.Data.DataView> z <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](programming-guide-linq-to-dataset.md)
