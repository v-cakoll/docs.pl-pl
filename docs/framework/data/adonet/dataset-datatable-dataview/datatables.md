---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 439b951779393d6ac232e6a1a622515905e837ad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="datatables"></a>DataTables
A <xref:System.Data.DataSet> składa się z kolekcją tabel, zależności i ograniczeń. W ADO.NET <xref:System.Data.DataTable> obiekty są wykorzystywane do reprezentowania tabele w **zestawu danych**. A **DataTable** reprezentuje jednej tabeli w pamięci danych relacyjnych; dane są lokalne. Aplikacji opartej na sieci, w którym znajduje się, lecz można wypełniać ze źródła danych, takich jak Microsoft SQL Server przy użyciu **element DataAdapter** uzyskać więcej informacji, zobacz [wypełnianie zestawu danych z element DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 **DataTable** klasa jest elementem członkowskim **system.dane** przestrzeni nazw w bibliotece klas programu .NET Framework. Można tworzyć i używać **DataTable** niezależnie lub jako członek **DataSet**, i **DataTable** obiekty mogą być również używane w połączeniu z innymi obiektami środowiska .NET Framework w tym <xref:System.Data.DataView>. Możesz uzyskać dostępu do kolekcji tabel w **zestawu danych** za pośrednictwem **tabel** właściwość **DataSet** obiektu.  
  
 Schemat lub struktura tabeli jest reprezentowana przez kolumn i ograniczeń. Zdefiniuj schemat **DataTable** przy użyciu <xref:System.Data.DataColumn> obiektów oraz <xref:System.Data.ForeignKeyConstraint> i <xref:System.Data.UniqueConstraint> obiektów. Kolumn w tabeli można mapować do kolumn w źródle danych, zawierać obliczone wartości w wyrażeniach, automatycznie zwiększyć ich wartości lub wartości klucza podstawowego.  
  
 Oprócz schemat **DataTable** musi mieć również wierszy, które zawierają i kolejność danych. <xref:System.Data.DataRow> Klasa reprezentuje rzeczywisty danych zawartych w tabeli. Możesz użyć **DataRow** i jego właściwości i metody, aby pobrać, oceny i manipulowanie danymi w tabeli. Jak dostępu i zmiany danych w wierszu, a **DataRow** obiekt zachowuje jego bieżące i oryginalne stanu.  
  
 Nadrzędny podrzędny można utworzyć relacji między tabelami, używając jednego lub więcej powiązanych kolumn w tabelach. Utwórz relację między **DataTable** obiektów przy użyciu <xref:System.Data.DataRelation>. **DataRelation** obiektów następnie może służyć do zwrócenia powiązane podrzędnej lub nadrzędnej wiersze określonego wiersza. Aby uzyskać więcej informacji, zobacz [Dodawanie DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementów DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Wyjaśnia sposób tworzenia **DataTable** i dodaj go do **zestawu danych**.  
  
 [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Informacje na temat tworzenia i używania **DataColumn** obiektów i ograniczeń.  
  
 [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Opisano sposób dodawania, modyfikowania i usuwania danych w tabeli. Wyjaśniono, jak używać **DataTable** zdarzeń w celu zbadania zmian danych w tabeli.  
  
 [Obsługa zdarzeń elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Zawiera informacje o zdarzeniach, które są dostępne do użycia z **DataTable**, w tym zdarzenia, gdy wartości w kolumnach są modyfikowane, a wiersze są dodawane lub usuwane.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 W tym artykule opisano ADO.NET architektury i składników oraz sposób ich używać do dostęp do istniejących źródeł danych i zarządzanie danych aplikacji.  
  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Informacje na temat ADO.NET **DataSet** łącznie ze sposobem tworzenia relacji między tabelami.  
  
 <xref:System.Data.Constraint>  
 Zawiera informacje na temat **ograniczenia** obiektu.  
  
 <xref:System.Data.DataColumn>  
 Zawiera informacje na temat **DataColumn** obiektu.  
  
 <xref:System.Data.DataSet>  
 Zawiera informacje na temat **DataSet** obiektu.  
  
 <xref:System.Data.DataTable>  
 Zawiera informacje na temat **DataTable** obiektu.  
  
 [Omówienie biblioteki klas](../../../../../docs/standard/class-library-overview.md)  
 Zawiera omówienie bibliotece klas programu .NET Framework w tym **systemu** przestrzeni nazw oraz jego nazw drugiego poziomu **system.dane**.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
