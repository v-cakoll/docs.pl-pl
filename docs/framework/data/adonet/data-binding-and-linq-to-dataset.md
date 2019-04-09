---
title: Powiązanie danych i LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: b081a648023aa21eea3a20ec409600d3bcbe9878
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073562"
---
# <a name="data-binding-and-linq-to-dataset"></a>Powiązanie danych i LINQ to DataSet
*Powiązanie danych* to proces, który nawiązuje połączenie między aplikacją w interfejsie użytkownika i logikę biznesową. Jeśli wiązanie ma prawidłowych ustawień i danych udostępnia odpowiednie powiadomienia po zmianie danych jego wartości, elementy, które są powiązane z danymi automatycznie odzwierciedlają zmiany. <xref:System.Data.DataSet> To reprezentacja danych, który zapewnia spójne relacyjne modelu programowania, niezależnie od źródła danych, zawiera on w pamięci. ADO.NET w wersji 2.0 <xref:System.Data.DataView> pozwala na filtrowanie i sortowanie danych przechowywanych w <xref:System.Data.DataTable>. Ta funkcja jest często używany w aplikacjach powiązanie danych. Za pomocą <xref:System.Data.DataView>, może uwidaczniać dane w tabeli z zamówieniami sortowania i dane można filtrować według wierszy, stanu lub w zależności od wyrażenia filtru. Aby uzyskać więcej informacji na temat <xref:System.Data.DataView> obiektu, zobacz [DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Umożliwia deweloperom tworzyć złożone, zaawansowane zapytania <xref:System.Data.DataSet> przy użyciu [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]. Jednak [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie zwraca wyliczenie <xref:System.Data.DataRow> obiektów, które nie jest łatwo używana w przypadku powiązania. Aby ułatwić powiązania, można utworzyć <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. To <xref:System.Data.DataView> jest używane filtrowanie i sortowanie, określona w zapytaniu, ale lepiej jest odpowiedni do wiązania danych. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] rozszerza funkcjonalność <xref:System.Data.DataView> , zapewniając [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] oparte na wyrażeniach filtrowania i sortowania, co pozwala na znacznie bardziej złożone i zaawansowane operacji filtrowania i sortowania niż oparte na ciągach filtrowania i sortowania.  
  
 Należy pamiętać, że <xref:System.Data.DataView> reprezentuje samo zapytanie, a nie jest widokiem na podstawie zapytania. <xref:System.Data.DataView> Jest powiązany z kontrolki interfejsu użytkownika, takie jak <xref:System.Windows.Forms.DataGrid> lub <xref:System.Windows.Forms.DataGridView>, zapewniając proste powiązanie modelem. A <xref:System.Data.DataView> również można tworzyć na podstawie <xref:System.Data.DataTable>, zapewniając domyślny widok w tej tabeli.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie obiektu widoku danych](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 Zawiera informacje o tworzeniu <xref:System.Data.DataView>.  
  
 [Filtrowanie za pomocą widoku danych](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 W tym artykule opisano jak filtrować za pomocą <xref:System.Data.DataView>.  
  
 [Sortowanie za pomocą widoku danych](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 W tym artykule opisano sposób sortowania z <xref:System.Data.DataView>.  
  
 [Wykonywanie zapytania do kolekcji DataRowView w widoku danych](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 Informacje na temat wykonywania zapytań <xref:System.Data.DataRowView> kolekcji udostępnianych przez <xref:System.Data.DataView>.  
  
 [Wydajność widoku danych](../../../../docs/framework/data/adonet/dataview-performance.md)  
 Zawiera informacje na temat <xref:System.Data.DataView> i wydajności.  
  
 [Instrukcje: Wiązanie obiektu widoku danych z kontrolką DataGridView formularzy systemu Windows](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Opis sposobu tworzenia powiązania <xref:System.Data.DataView> obiekt <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
