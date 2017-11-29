---
title: "Powiązanie danych i LINQ do DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b3b097f9bca790d1f19da9d75f834c6277507d8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-and-linq-to-dataset"></a>Powiązanie danych i LINQ do DataSet
*Powiązanie danych* proces, który nawiązuje połączenie między aplikacją interfejsu użytkownika i logiki biznesowej. Jeśli powiązanie ma poprawne ustawienia i dane zawiera odpowiednie powiadomienia, zmiana danych jego wartości, elementy, które są powiązane z danymi automatycznie odzwierciedlenia zmian. <xref:System.Data.DataSet> Reprezentacja w pamięci zapewnia spójne relacyjne model programowania, niezależnie od tego źródła danych zawiera dane. ADO.NET 2.0 <xref:System.Data.DataView> umożliwia filtrowanie i sortowanie danych przechowywanych w <xref:System.Data.DataTable>. Ta funkcja jest często używane w aplikacjach powiązania danych. Przy użyciu <xref:System.Data.DataView>, można udostępnić dane w tabeli z innego sortowania i dane można filtrować według wierszy stanu lub w oparciu o wyrażenie filtru. Aby uzyskać więcej informacji na temat <xref:System.Data.DataView> obiektów, zobacz [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]Umożliwia deweloperom tworzenie zapytań złożone, zaawansowane <xref:System.Data.DataSet> przy użyciu [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]. Jednak [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie zwraca wyliczenie <xref:System.Data.DataRow> obiektów, które łatwo nie jest używany w scenariuszu powiązania. Aby ułatwić powiązanie, można utworzyć <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. To <xref:System.Data.DataView> jest używane filtrowanie i sortowanie określone w zapytaniu, ale lepiej jest odpowiedni dla powiązania danych. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]rozszerza funkcjonalność <xref:System.Data.DataView> zapewniając [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] oparte na wyrażeniach filtrowanie i sortowanie, co pozwala na znacznie bardziej złożone i zaawansowane filtrowanie i sortowanie operacji niż oparte na ciągach filtrowanie i sortowanie.  
  
 Należy pamiętać, że <xref:System.Data.DataView> reprezentuje zapytanie się i nie jest widokiem na podstawie zapytania. <xref:System.Data.DataView> Jest powiązany z formantu interfejsu użytkownika, takich jak <xref:System.Windows.Forms.DataGrid> lub <xref:System.Windows.Forms.DataGridView>, zapewniając modelu danych proste powiązania. A <xref:System.Data.DataView> można także utworzyć z <xref:System.Data.DataTable>, zapewniając domyślny widok tej tabeli.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie obiektu widoku danych.](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 Zawiera informacje o tworzeniu <xref:System.Data.DataView>.  
  
 [Filtrowanie z widoku danych.](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 Opisuje sposób filtrowania z <xref:System.Data.DataView>.  
  
 [Sortowania z widoku danych.](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 Opisuje sposób sortowania z <xref:System.Data.DataView>.  
  
 [Wykonywanie zapytania do kolekcji DataRowView w elemencie DataView](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 Zawiera informacje o zapytaniach dotyczących <xref:System.Data.DataRowView> kolekcji udostępnianych przez <xref:System.Data.DataView>.  
  
 [Widok danych wydajności](../../../../docs/framework/data/adonet/dataview-performance.md)  
 Zawiera informacje na temat <xref:System.Data.DataView> i wydajność.  
  
 [Porady: powiązanie obiektu DataView do formantu DataGridView formularzy systemu Windows](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Opisuje sposób wiązania <xref:System.Data.DataView> do obiektu <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
