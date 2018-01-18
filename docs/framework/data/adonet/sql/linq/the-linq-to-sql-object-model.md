---
title: "LINQ do SQL modelu obiektów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0bfaf7b08b3725f1c1cc2f0985c7612aa47a6cb4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="the-linq-to-sql-object-model"></a>LINQ do SQL modelu obiektów
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], model obiektowy wyrażone w języku programowania dewelopera jest zamapowana do modelu danych relacyjnej bazy danych. Operacje na danych następnie są przeprowadzane zgodnie z modelem obiektu.  
  
 W tym scenariuszu nie wydają polecenia bazy danych (na przykład `INSERT`) w bazie danych. Zamiast tego zmienić wartości i wykonywanie metod w modelu obiektu. Aby zapytanie bazy danych lub wysyłania zmienia, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy żądań na poprawne polecenia SQL i wysyła te polecenia w bazie danych.  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Większość podstawowych elementów w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] model obiektów i ich związek z elementów w modelu danych relacyjnych podsumowano w poniższej tabeli:  
  
|LINQ do SQL modelu obiektów|Model danych relacyjnych|  
|------------------------------|---------------------------|  
|Klasa jednostki|tabela|  
|Element członkowski klasy|Kolumny|  
|Skojarzenie|Klucz obcy relacji|  
|Metoda|Procedura składowana lub funkcja|  
  
> [!NOTE]
>  Poniższe opisy założono, że masz podstawową wiedzę na temat modelu danych relacyjnych i reguł.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ do SQL klas jednostek i tabel bazy danych  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], tabeli bazy danych jest reprezentowana przez *klasy jednostka*. Klasa jednostki przypomina innej klasy, które można tworzyć z tą różnicą, że adnotacji klasy przy użyciu informacji specjalne, które kojarzy klasy z tabeli bazy danych. Upewnij się ta adnotacja przez dodanie atrybutu niestandardowego (<xref:System.Data.Linq.Mapping.TableAttribute>) do sieci deklaracji klasy, jak w poniższym przykładzie:  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Tylko wystąpienia klasy zadeklarowany jako tabele (to znaczy klas jednostek) można zapisać w bazie danych.  
  
 Aby uzyskać więcej informacji, zobacz sekcję atrybutu tabeli [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>LINQ do SQL elementów członkowskich klasy i kolumny bazy danych  
 Oprócz kojarzenie klasy z tabel, możesz określić pola lub właściwości do reprezentowania kolumnach bazy danych. W tym celu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definiuje <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, jak w poniższym przykładzie:  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Tylko pola i właściwości zamapowanych do kolumn są utrwalone lub pobrać z bazy danych. Te nie deklarowane jako kolumn są traktowane jako przejściowa części logiki aplikacji.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> Atrybut ma wiele właściwości, których można użyć w celu dostosowania tych elementów członkowskich, które reprezentują kolumn (na przykład wyznaczenie członka reprezentujące kolumna klucza podstawowego). Aby uzyskać więcej informacji, zobacz sekcję atrybut kolumny [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ do SQL skojarzenia i relacje klucza obcego bazy danych  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], reprezentują skojarzenia bazy danych (na przykład klucza obcego klucza podstawowego relacji), stosując <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu. W poniższych segment kodu `Order` klasa zawiera `Customer` właściwość, która ma <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu. Ta właściwość i jej atrybutu zapewniają `Order` klasy, które mają relację `Customer` klasy.  
  
 Poniższy kod przedstawia przykład `Customer` właściwość z `Order` klasy.  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz sekcję atrybut skojarzenia [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>Procedury składowane LINQ do SQL metod i bazy danych  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje procedury składowane i funkcje zdefiniowane przez użytkownika. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], mapować te obiekty abstrakcyjne zdefiniowane bazy danych do obiektów klienta, dzięki czemu będą dostępne w sposób jednoznaczny z kodu klienta. Podpisy metod przypominać możliwie podpisów procedur i funkcji definiowanych w bazie danych. IntelliSense służy do odnajdywania tych metod.  
  
 Oznacza to zestaw wyników zwrócony przez wywołanie do mapowanej procedury jest silnie typizowaną kolekcją.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje procedury składowane i funkcje do metod za pomocą <xref:System.Data.Linq.Mapping.FunctionAttribute> i <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutów. Metody reprezentujący procedur składowanych różnią się od tych, które stanowią funkcje zdefiniowane przez użytkownika, przez <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> właściwości. Jeśli ta właściwość jest ustawiona na `false` (domyślnie), metoda reprezentuje procedury składowanej. Jeśli wartość jest ustawiona na `true`, metoda reprezentuje funkcji bazy danych.  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] można utworzyć metody mapowane na procedury składowane i funkcje zdefiniowane przez użytkownika.  
  
### <a name="example"></a>Przykład  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Aby uzyskać więcej informacji, zobacz sekcje atrybut funkcji, przechowywane procedury atrybut i atrybut parametru [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) i [procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
