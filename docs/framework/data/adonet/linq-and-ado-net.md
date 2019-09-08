---
title: LINQ i ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: d354e2e7f2696e90845edf0348340986fd7bb83c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795187"
---
# <a name="linq-and-adonet"></a>LINQ i ADO.NET
Obecnie wielu deweloperów firmy musi korzystać z dwóch (lub więcej) języków programowania: ogólnego języka dla logiki biznesowej i warstw prezentacji (takich jak wizualizacja C# lub Visual Basic) i języka zapytań do współpracy z bazą danych programu (na przykład Transact-SQL). . Wymaga to, aby deweloper był w kilku językach w skuteczny sposób, a także powodować niezgodność języka w środowisku deweloperskim. Na przykład aplikacja używająca interfejsu API dostępu do danych do wykonywania zapytania względem bazy danych określa zapytanie jako literał ciągu przy użyciu znaków cudzysłowu. Ten ciąg zapytania jest odczytany do kompilatora i nie jest sprawdzany pod kątem błędów, takich jak nieprawidłowa składnia lub czy kolumny lub wiersze, do których się odwołuje, faktycznie istnieją. Nie jest przeprowadzane sprawdzanie typu parametrów zapytania ani żadna `IntelliSense` pomoc techniczna.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]umożliwia deweloperom tworzenie zapytań opartych na zestawie w kodzie aplikacji bez konieczności używania oddzielnego języka zapytań. Można pisać [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania dotyczące różnych wyliczalnych źródeł danych (czyli źródła danych, które <xref:System.Collections.IEnumerable> implementuje interfejs), takich jak struktury danych w pamięci, dokumenty XML, bazy danych SQL i <xref:System.Data.DataSet> obiekty. Chociaż te wyliczalne źródła danych są implementowane na różne sposoby, to wszystkie te same konstrukcje składni i języka. Ponieważ zapytania mogą być tworzone w języku programowania, nie trzeba używać innego języka zapytań, który jest osadzony jako literały ciągów, których kompilator nie może zrozumieć ani zweryfikować. Integrowanie zapytań z językiem programowania umożliwia także deweloperom programu Visual Studio wydajniejszą pracę dzięki zapewnieniu typu i sprawdzania `IntelliSense`składni w czasie kompilacji oraz. Te funkcje zmniejszają potrzebę do debugowania zapytań i naprawiania błędów.  
  
 Transferowanie danych z tabel SQL do obiektów w pamięci jest często żmudnym i podatne na błędy. Dostawca zaimplementowany przez LINQ to DataSet i [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] konwertuje dane źródłowe na <xref:System.Collections.IEnumerable>kolekcje obiektów na podstawie. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Programista zawsze przegląda dane jako <xref:System.Collections.IEnumerable> kolekcję, zarówno podczas wykonywania zapytań, jak i podczas aktualizacji. Pełna `IntelliSense` pomoc techniczna jest świadczona w przypadku pisania zapytań względem tych kolekcji.  
  
 Istnieją trzy oddzielne technologie ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] : LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]i LINQ to Entities. LINQ to DataSet zapewnia bogatsze i zoptymalizowane zapytania dotyczące programu <xref:System.Data.DataSet> i [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umożliwia bezpośrednie wysyłanie zapytań do SQL Server schematów bazy danych, a LINQ to Entities umożliwia wykonywanie zapytań do Entity Data Model.  
  
 Poniższy diagram zawiera omówienie sposobu, w jaki technologie ADO.NET LINQ odnoszą się do języków programowania wysokiego poziomu i źródeł danych z obsługą LINQ.  
  
 ![Przegląd LINQ to ADO.NET](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Aby uzyskać więcej informacji na temat LINQ, zobacz [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Poniższe sekcje zawierają więcej informacji na temat LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]i LINQ to Entities.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet> Jest elementem klucza w odłączonym modelu programowania, który ADO.NET jest zbudowany i jest szeroko używany. LINQ to DataSet umożliwia deweloperom tworzenie bogatszych możliwości zapytań do <xref:System.Data.DataSet> programu przy użyciu tego samego mechanizmu formułowania zapytań, który jest dostępny dla wielu innych źródeł danych. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]jest użytecznym narzędziem dla deweloperów, którzy nie wymagają mapowania do modelu koncepcyjnego. Korzystając [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]z programu, można [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] użyć modelu programowania bezpośrednio przez istniejący schemat bazy danych. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]umożliwia deweloperom generowanie klas .NET Framework, które reprezentują dane. Zamiast mapowania na model danych koncepcyjnych, te wygenerowane klasy mapują się bezpośrednio do tabel bazy danych, widoków, procedur składowanych i funkcji zdefiniowanych przez użytkownika.  
  
 Dzięki [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]programowi deweloperzy mogą pisać kod bezpośrednio w schemacie magazynu przy użyciu [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] tego samego wzorca programowania co kolekcje w pamięci, <xref:System.Data.DataSet>a także do innych źródeł danych, takich jak XML. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Większość aplikacji jest obecnie zapisywana w relacyjnych bazach danych. W pewnym momencie te aplikacje będą musiały korzystać z danych przedstawionych w formie relacyjnej. Schematy bazy danych nie zawsze są idealne do kompilowania aplikacji, a modele pojęciowe aplikacji nie są takie same jak modele logiczne baz danych. Entity Data Model to koncepcyjny model danych, którego można użyć do modelowania danych konkretnej domeny, dzięki czemu aplikacje mogą współdziałać z danymi jako obiektami. Aby uzyskać więcej informacji, zobacz [ADO.NET Entity Framework](./ef/index.md) .  
  
 Za pomocą Entity Data Model dane relacyjne są ujawniane jako obiekty w środowisku .NET. Sprawia to, że obiekt jest idealnym celem [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] do obsługi, dzięki czemu deweloperzy mogą tworzyć zapytania względem bazy danych w języku używanym do tworzenia logiki biznesowej. Ta funkcja jest znana jako LINQ to Entities. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](./ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
