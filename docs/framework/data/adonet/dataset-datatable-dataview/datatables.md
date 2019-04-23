---
title: Elementy DataTable
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: f6509400d7f6633749155f778e3ba58ec6c27ec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207321"
---
# <a name="datatables"></a>Elementy DataTable
A <xref:System.Data.DataSet> składa się z kolekcją tabel, relacje i ograniczenia. W ADO.NET <xref:System.Data.DataTable> obiekty są używane do reprezentowania tabel w **zestawu danych**. A **DataTable** reprezentuje jedną tabelę danych relacyjnych w pamięci; dane są lokalne. Aplikacja oparta na NET, w którym to znajduje się, ale mogą zostać wypełnione ze źródła danych, takich jak Microsoft SQL Server przy użyciu **DataAdapter** Aby uzyskać więcej informacji, zobacz [wypełnianie zestawu danych z elementu DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 **DataTable** klasa jest elementem członkowskim **System.Data** przestrzeni nazw w bibliotece klas programu .NET Framework. Można tworzyć i używać **DataTable** niezależnie lub jako członek **DataSet**, i **DataTable** obiekty również mogą być używane w połączeniu z innymi obiektami .NET Framework w tym <xref:System.Data.DataView>. Możesz uzyskać dostęp do kolekcji tabel w **zestawu danych** za pośrednictwem **tabel** właściwość **zestawu danych** obiektu.  
  
 Schema i struktura tabeli jest reprezentowany przez kolumn i ograniczeń. Należy zdefiniować schemat **DataTable** przy użyciu <xref:System.Data.DataColumn> obiektów także <xref:System.Data.ForeignKeyConstraint> i <xref:System.Data.UniqueConstraint> obiektów. Kolumny w tabeli można zamapować do kolumny w źródle danych, zawierać obliczone wartości w wyrażeniach, automatycznie zwiększyć ich wartości lub wartości klucza podstawowego.  
  
 Oprócz schematu **DataTable** musi mieć również wierszy, które mają zawierać i kolejność danych. <xref:System.Data.DataRow> Klasa reprezentuje rzeczywisty danych zawartych w tabeli. Możesz użyć **DataRow** i jej właściwości i metody, aby pobrać, oceny i manipulowanie danymi w tabeli. Jak uzyskać dostęp i zmiany danych w wierszu, a **DataRow** obiekt zachowuje jego bieżąca i oryginalna stanu.  
  
 Można utworzyć hierarchiczne relacje między tabelami przy użyciu jednej lub więcej powiązanych kolumn w tabelach. Utwórz relację między **DataTable** obiektów przy użyciu <xref:System.Data.DataRelation>. **DataRelation —** obiektów, następnie może służyć do zwrócenia powiązane podrzędnej lub nadrzędnej wiersze określonego wiersza. Aby uzyskać więcej informacji, zobacz [Dodawanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementów DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Wyjaśnia sposób tworzenia **DataTable** i dodać go do **zestawu danych**.  
  
 [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Informacje na temat tworzenia i używania **DataColumn** obiektów i ograniczenia.  
  
 [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Opis sposobu dodawania, modyfikowania i usuwania danych w tabeli. Opis sposobu użycia **DataTable** zdarzeń w celu zbadania zmian danych w tabeli.  
  
 [Obsługa zdarzeń elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Zawiera informacje o zdarzeniach, które są dostępne do użytku z programem **DataTable**, w tym zdarzenia dotyczące po zmodyfikowaniu wartości kolumny i wiersze są dodawane lub usuwane.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 W tym artykule opisano ADO.NET architektura i składniki i sposób ich użycia, dostęp do istniejących źródeł danych i zarządzanie danymi aplikacji.  
  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Informacje na temat ADO.NET **DataSet** tym jak utworzyć relacje między tabelami.  
  
 <xref:System.Data.Constraint>  
 Zawiera informacje na temat **ograniczenie** obiektu.  
  
 <xref:System.Data.DataColumn>  
 Zawiera informacje na temat **DataColumn** obiektu.  
  
 <xref:System.Data.DataSet>  
 Zawiera informacje na temat **DataSet** obiektu.  
  
 <xref:System.Data.DataTable>  
 Zawiera informacje na temat **DataTable** obiektu.  
  
 [Omówienie biblioteki klas](../../../../../docs/standard/class-library-overview.md)  
 Zawiera omówienie biblioteki klas programu .NET Framework, w tym **systemu** przestrzeni nazw oraz jego przestrzeń nazw drugiego poziomu, **System.Data**.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
