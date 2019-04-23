---
title: Model obiektu LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: 7ce759de004d479f5162d2ce3a965f5c40afa450
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110796"
---
# <a name="the-linq-to-sql-object-model"></a>Model obiektu LINQ to SQL
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], na model obiektów wyrażony w języku programowania, który jest mapowany na model danych relacyjnej bazy danych. Operacje na danych, następnie są przeprowadzane zgodnie z modelem obiektów.  
  
 W tym scenariuszu nie wydaje polecenia bazy danych (na przykład `INSERT`) w bazie danych. Zamiast tego zmienić wartości i wykonywanie metod w modelu obiektu. Gdy chcesz wykonać zapytanie w bazie danych lub zmienia się, Wyślij [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy żądania na prawidłowe polecenia SQL, a następnie wysyła te polecenia w bazie danych.  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Większość podstawowych elementów w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów i ich związek z elementów w modelu opartego na danych relacyjnych, które są podsumowane w poniższej tabeli:  
  
|LINQ to SQL Model obiektów|Dane relacyjne modelu|  
|------------------------------|---------------------------|  
|Klasa jednostki|tabela|  
|Składowa klasy|Kolumna|  
|Skojarzenie|Klucz obcy relacji|  
|Metoda|Procedura składowana lub funkcja|  
  
> [!NOTE]
>  Poniższe opisy przyjęto założenie, że masz podstawową wiedzę na temat modelu opartego na danych relacyjnych i reguł.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL klas jednostek i tabel bazy danych  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], tabeli bazy danych jest reprezentowany przez *Klasa jednostki*. Klasa jednostki przypomina innej klasy, które można tworzyć z tą różnicą, że możesz dodawać adnotacje do klasy za pomocą specjalnych informacje, które kojarzy klasy z tabeli bazy danych. Wprowadź tę adnotację, dodając atrybut niestandardowy (<xref:System.Data.Linq.Mapping.TableAttribute>) do swojej deklaracji klasy, jak w poniższym przykładzie:  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Tylko wystąpienia klasy zadeklarowane jako tabele (to znaczy klas jednostek) można zapisać w bazie danych.  
  
 Aby uzyskać więcej informacji, zobacz sekcję atrybutów tabeli [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>LINQ to SQL składowych klasy i kolumny bazy danych  
 Oprócz kojarzenie klas z tabel, należy wyznaczyć pól lub właściwości do reprezentowania kolumny bazy danych. W tym celu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definiuje <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, jak w poniższym przykładzie:  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Tylko pola i właściwości zamapowanych do kolumn są utrwalone lub pobierane z bazy danych. Te nie zadeklarowane jako kolumny będą traktowane jako przejściowe części logiki aplikacji.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> Atrybut ma wiele właściwości, których można użyć, aby dostosować te elementy członkowskie, które reprezentują kolumn (na przykład wyznaczanie członka jako kolumna klucza podstawowego). Aby uzyskać więcej informacji, zobacz sekcję atrybut kolumny [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ to SQL skojarzenia i relacje klucza obcego bazy danych  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], reprezentuje skojarzenia bazy danych (np. klucza obcego relacji klucza podstawowego), stosując <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu. W poniższym segment kodu `Order` klasa zawiera `Customer` właściwość, która ma <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu. Ta właściwość i jego atrybut zapewniają `Order` klasy relację z `Customer` klasy.  
  
 Poniższy kod przedstawia przykład `Customer` właściwość `Order` klasy.  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz sekcję atrybut skojarzenia [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>Procedury składowane programu LINQ to SQL metody i bazy danych  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje procedur przechowywanych i funkcji zdefiniowanych przez użytkownika. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], mapowanie tych abstrakcje zdefiniowane bazy danych na obiekty klienta tak, aby mogli je w silnie typizowany sposób z poziomu kodu klienta. Podpisy metod przypominają możliwie jak najbliżej sygnatury procedury składowane i funkcje zdefiniowane w bazie danych. Technologia IntelliSense można użyć tych metod odnajdywania.  
  
 Oznacza to zestaw wyników zwrócony przez wywołanie procedury zmapowanego jest silnie typizowaną kolekcją.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapowania procedur przechowywanych i funkcji do metod przy użyciu <xref:System.Data.Linq.Mapping.FunctionAttribute> i <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutów. Metody reprezentująca procedur składowanych różnią się od tych, które stanowią funkcje zdefiniowane przez użytkownika przez <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> właściwości. Jeśli ta właściwość jest ustawiona `false` (ustawienie domyślne), metoda reprezentuje procedury składowanej. Jeśli jest równa `true`, metoda reprezentuje funkcji bazy danych.  
  
> [!NOTE]
>  Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do utworzenia metody mapowany do procedur przechowywanych i funkcji zdefiniowanych przez użytkownika.  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Aby uzyskać więcej informacji, zobacz sekcje atrybut funkcji, przechowywane procedury atrybut i atrybut Parameter [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) i [procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
