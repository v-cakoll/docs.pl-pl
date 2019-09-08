---
title: Model obiektu LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: b73904e2347c501b21b2c5933d0b43c7abafeb7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792315"
---
# <a name="the-linq-to-sql-object-model"></a>Model obiektu LINQ to SQL
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie model obiektów wyrażony w języku programowania dewelopera jest mapowany na model danych relacyjnej bazy danych. Operacje na danych są następnie wykonywane zgodnie z modelem obiektów.  
  
 W tym scenariuszu do bazy danych nie są obsługiwane polecenia bazy danych programu `INSERT`(na przykład). Zamiast tego należy zmienić wartości i wykonać metody w modelu obiektów. Gdy chcesz wysyłać zapytania do bazy danych lub wysłać zmiany, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przetłumaczy żądania na poprawne polecenia SQL i wyśle te polecenia do bazy danych.  
  
 ![Zrzut ekranu pokazujący model obiektów LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Najbardziej podstawowe elementy w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów i ich relacje z elementami w modelu danych relacyjnych są podsumowane w poniższej tabeli:  
  
|LINQ to SQL model obiektów|Relacyjny model danych|  
|------------------------------|---------------------------|  
|Klasa jednostki|tabela|  
|Składowa klasy|Kolumna|  
|Skojarzenie|Relacja klucza obcego|  
|Metoda|Procedura składowana lub funkcja|  
  
> [!NOTE]
> W poniższych opisach przyjęto założenie, że masz podstawową wiedzę na temat relacyjnego modelu danych i reguł.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL klas jednostek i tabel bazy danych  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie tabela bazy danych jest reprezentowana przez *klasę Entity*. Klasa jednostki jest taka sama jak jakakolwiek inna Klasa, którą można utworzyć, z wyjątkiem dodawania adnotacji do klasy przy użyciu specjalnych informacji, które kojarzą klasę z tabelą bazy danych. Tę adnotację można utworzyć, dodając atrybut niestandardowy<xref:System.Data.Linq.Mapping.TableAttribute>() do deklaracji klasy, jak w poniższym przykładzie:  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Tylko wystąpienia klas zadeklarowanych jako tabele (czyli klasy jednostek) można zapisać w bazie danych.  
  
 Aby uzyskać więcej informacji, zobacz sekcję atrybut tabeli [mapowania opartego na atrybutach](attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>Elementy członkowskie klasy LINQ to SQL i kolumny bazy danych  
 Oprócz kojarzenia klas z tabelami należy wyznaczyć pola lub właściwości do reprezentowania kolumn bazy danych. W tym celu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> definiuje atrybut, jak w poniższym przykładzie:  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Tylko pola i właściwości zamapowane do kolumn są utrwalane lub pobierane z bazy danych. Te, które nie są zadeklarowane jako kolumny, są uznawane za przejściowe części logiki aplikacji.  
  
 Ten <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybut ma różne właściwości, których można użyć do dostosowania tych elementów członkowskich, które reprezentują kolumny (na przykład wyznaczanie elementu członkowskiego jako kolumny klucza podstawowego). Aby uzyskać więcej informacji, zobacz sekcję atrybut kolumny [mapowania opartego na atrybutach](attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>Powiązania LINQ to SQL i relacje klucza obcego bazy danych  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie reprezentowane są <xref:System.Data.Linq.Mapping.AssociationAttribute> skojarzenia bazy danych (takie jak klucz obcy z relacjami klucza podstawowego) przez zastosowanie atrybutu. W poniższym segmencie kodu `Order` Klasa `Customer` zawiera właściwość, która ma <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybut. Ta właściwość i jej atrybut zapewniają `Order` klasę z relacją `Customer` do klasy.  
  
 Poniższy przykład kodu pokazuje `Customer` Właściwość `Order` z klasy.  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz sekcję atrybut skojarzenia w [mapowaniu opartym na atrybutach](attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>Metody LINQ to SQL i procedury składowane bazy danych  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje procedury składowane i funkcje zdefiniowane przez użytkownika. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie należy mapować te abstrakcyjne zdefiniowane dla bazy danych na obiekty klienckie, aby można było uzyskać do nich dostęp w jednoznacznie określonym sposób z kodu klienta. Sygnatury metod przypominają możliwie najbliżej sygnatury procedur i funkcji zdefiniowanych w bazie danych. Aby poznać te metody, można użyć funkcji IntelliSense.  
  
 Zestaw wyników zwracany przez wywołanie procedury mapowanej jest kolekcją silną.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje procedury składowane i funkcje do metod przy <xref:System.Data.Linq.Mapping.FunctionAttribute> użyciu <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutów i. Metody reprezentujące procedury składowane różnią się od tych, <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> które reprezentują funkcje zdefiniowane przez użytkownika przez właściwość. Jeśli ta właściwość jest ustawiona na `false` (wartość domyślna), Metoda reprezentuje procedurę składowaną. Jeśli jest ustawiona na `true`, Metoda reprezentuje funkcję bazy danych.  
  
> [!NOTE]
> Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby utworzyć metody zamapowane na procedury składowane i funkcje zdefiniowane przez użytkownika.  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Aby uzyskać więcej informacji, zobacz sekcję atrybut funkcji, atrybut procedury składowanej i atrybuty parametrów dotyczące mapowań i [procedur składowanych](stored-procedures.md) [opartych na atrybutach](attribute-based-mapping.md) .  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie oparte na atrybutach](attribute-based-mapping.md)
- [Informacje uzupełniające](background-information.md)
