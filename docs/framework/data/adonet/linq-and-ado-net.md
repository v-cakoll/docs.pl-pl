---
title: LINQ i ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: e24473f68fe5ccd993c5d205660ea8f397b6f797
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980096"
---
# <a name="linq-and-adonet"></a>LINQ i ADO.NET
Obecnie wielu deweloperów w biznesie musi korzystać z dwóch (lub więcej) języków programowania: ogólnego języka dla logiki biznesowej i warstw prezentacji (takich jak wizualizacja C# lub Visual Basic) i języka zapytań do współpracy z bazą danych programu (na przykład Transact-SQL). Wymaga to, aby deweloper był w kilku językach w skuteczny sposób, a także powodować niezgodność języka w środowisku deweloperskim. Na przykład aplikacja używająca interfejsu API dostępu do danych do wykonywania zapytania względem bazy danych określa zapytanie jako literał ciągu przy użyciu znaków cudzysłowu. Ten ciąg zapytania jest odczytany do kompilatora i nie jest sprawdzany pod kątem błędów, takich jak nieprawidłowa składnia lub czy kolumny lub wiersze, do których się odwołuje, faktycznie istnieją. Nie jest przeprowadzane sprawdzanie typu parametrów zapytania i brak obsługi `IntelliSense`.  
  
 Funkcja Query-Integrated Language (LINQ) umożliwia deweloperom tworzenie zapytań opartych na zestawie w kodzie aplikacji bez konieczności używania oddzielnego języka zapytań. Zapytania LINQ można pisać względem różnych wyliczalnych źródeł danych (czyli źródła danych, które implementuje interfejs <xref:System.Collections.IEnumerable>), takich jak struktury danych w pamięci, dokumenty XML, bazy danych SQL i obiekty <xref:System.Data.DataSet>. Chociaż te wyliczalne źródła danych są implementowane na różne sposoby, to wszystkie te same konstrukcje składni i języka. Ponieważ zapytania mogą być tworzone w języku programowania, nie trzeba używać innego języka zapytań, który jest osadzony jako literały ciągów, których kompilator nie może zrozumieć ani zweryfikować. Integrowanie zapytań z językiem programowania umożliwia także deweloperom programu Visual Studio wydajniejszą pracę dzięki zapewnieniu typu czasu kompilacji i sprawdzania składni oraz `IntelliSense`. Te funkcje zmniejszają potrzebę do debugowania zapytań i naprawiania błędów.  
  
 Transferowanie danych z tabel SQL do obiektów w pamięci jest często żmudnym i podatne na błędy. Dostawca LINQ zaimplementowany przez LINQ to DataSet i [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] konwertuje dane źródłowe na kolekcje obiektów <xref:System.Collections.IEnumerable>. Programista zawsze przegląda dane jako kolekcje <xref:System.Collections.IEnumerable> zarówno podczas wykonywania zapytań, jak i podczas aktualizacji. Pełna pomoc techniczna `IntelliSense` jest dostępna do pisania zapytań względem tych kolekcji.  
  
 Istnieją trzy oddzielne technologie ADO.NET Language-Integrated Query (LINQ): LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]i LINQ to Entities. LINQ to DataSet zapewnia bogatsze, zoptymalizowane zapytania dotyczące <xref:System.Data.DataSet> i [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] pozwala bezpośrednio wykonywać zapytania dotyczące SQL Server schematów bazy danych, a LINQ to Entities pozwala na wykonywanie zapytań do Entity Data Model.  
  
 Poniższy diagram zawiera omówienie sposobu, w jaki technologie ADO.NET LINQ odnoszą się do języków programowania wysokiego poziomu i źródeł danych z obsługą LINQ.  
  
 ![Przegląd LINQ to ADO.NET](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Aby uzyskać więcej informacji na temat LINQ, zobacz [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Poniższe sekcje zawierają więcej informacji na temat LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]i LINQ to Entities.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> to kluczowy element modelu programowania rozłączonego, na którym ADO.NET jest zbudowany i jest szeroko używany. LINQ to DataSet umożliwia deweloperom tworzenie bogatszych możliwości zapytań do <xref:System.Data.DataSet> przy użyciu tego samego mechanizmu formułowania zapytań, który jest dostępny dla wielu innych źródeł danych. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to przydatne narzędzie dla deweloperów, którzy nie wymagają mapowania do modelu koncepcyjnego. Korzystając z [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], można użyć modelu programowania LINQ bezpośrednio przez istniejący schemat bazy danych. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umożliwia deweloperom generowanie klas .NET Framework, które reprezentują dane. Zamiast mapowania na model danych koncepcyjnych, te wygenerowane klasy mapują się bezpośrednio do tabel bazy danych, widoków, procedur składowanych i funkcji zdefiniowanych przez użytkownika.  
  
 Dzięki [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]deweloperzy mogą pisać kod bezpośrednio względem schematu magazynu przy użyciu tego samego wzorca programowania LINQ jak kolekcje w pamięci i <xref:System.Data.DataSet>, poza innymi źródłami danych, takimi jak XML. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Większość aplikacji jest obecnie zapisywana w relacyjnych bazach danych. W pewnym momencie te aplikacje będą musiały korzystać z danych przedstawionych w formie relacyjnej. Schematy bazy danych nie zawsze są idealne do kompilowania aplikacji, a modele pojęciowe aplikacji nie są takie same jak modele logiczne baz danych. Entity Data Model to koncepcyjny model danych, którego można użyć do modelowania danych konkretnej domeny, dzięki czemu aplikacje mogą współdziałać z danymi jako obiektami. Aby uzyskać więcej informacji, zobacz [ADO.NET Entity Framework](./ef/index.md) .  
  
 Za pomocą Entity Data Model dane relacyjne są ujawniane jako obiekty w środowisku .NET. Sprawia to, że obiekt jest idealnym miejscem docelowym dla obsługi LINQ, dzięki czemu deweloperzy mogą tworzyć zapytania względem bazy danych w języku używanym do tworzenia logiki biznesowej. Ta funkcja jest znana jako LINQ to Entities. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](./ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
