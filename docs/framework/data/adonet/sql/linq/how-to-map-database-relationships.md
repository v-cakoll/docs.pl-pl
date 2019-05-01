---
title: 'Instrukcje: Mapowanie relacji w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 40e376f2c2584490273ec27b78fe5315cbb0315e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033725"
---
# <a name="how-to-map-database-relationships"></a>Instrukcje: Mapowanie relacji w bazie danych
Możesz zakodować jako właściwość odwołuje się w klasie jednostki relacji między danymi, które będą zawsze takie same. W bazie danych Northwind na przykład, ponieważ klienci zwykle składanie zamówień, istnieje relacja zawsze w modelu od klientów i zamówienia.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definiuje <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu w celu reprezentowania takich relacji. Ten atrybut jest używany razem z <xref:System.Data.Linq.EntitySet%601> i <xref:System.Data.Linq.EntityRef%601> typów do reprezentowania, jaki byłyby relacji klucza obcego w bazie danych. Aby uzyskać więcej informacji, zobacz sekcję atrybut skojarzenia [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  Wartości właściwości AssociationAttribute i ColumnAttribute magazynu uwzględniają wielkość liter. Na przykład upewnij się, że wartości używanych w atrybucie właściwości AssociationAttribute.Storage odpowiadać wielkości liter dla odpowiedniej nazwy właściwości używane w innych miejscach w kodzie. Dotyczy to wszystkich języków programowania .NET, nawet te, które nie są zwykle z uwzględnieniem wielkości liter, w tym Visual Basic. Aby uzyskać więcej informacji na temat właściwości magazynu zobacz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 Większość relacje są jeden do wielu, tak jak w przykładzie w dalszej części tego tematu. Może również reprezentować relacji jeden do jednego i wiele do wielu w następujący sposób:  
  
- Jeden do jednego: Reprezentuje tego rodzaju relacji, umieszczając <xref:System.Data.Linq.EntitySet%601> po obu stronach.  
  
     Na przykład, rozważmy `Customer` - `SecurityCode` relacji, utworzony kod zabezpieczeń klienta nie zostanie znaleziony w `Customer` tabeli i może mieć dostęp tylko upoważnione osoby.  
  
- Wiele do wielu: W relacji wiele do wielu, klucz podstawowy w tabeli linku (o nazwie *Rozgałęzienie* tabeli) często jest tworzony przez złożonego klucze obce w dwóch tabelach.  
  
     Na przykład, rozważmy `Employee` - `Project` relacji wiele do wielu utworzone za pomocą tabela łączy `EmployeeProject`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wymaga, że takiej relacji jest modelowane przy użyciu trzech klas: `Employee`, `Project`, i `EmployeeProject`. W tym przypadku zmiana relacji między `Employee` i `Project` może okazać się wymagają aktualizacji klucza podstawowego `EmployeeProject`. Jednak ta sytuacja jest najlepiej formę usunięcie istniejącej `EmployeeProject` i utworzenie nowego `EmployeeProject`.  
  
    > [!NOTE]
    >  Relacji w relacyjnych baz danych zwykle są modelowane jako wartości klucza obcego, które odwołują się do kluczy podstawowych w innych tabelach. Przechodzenie między nimi przy użyciu relacyjną skojarzysz jest jawnie dwie tabele *sprzężenia* operacji.  
    >   
    >  Obiekty w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], z drugiej strony, zapoznaj się ze sobą za pomocą odwołania do właściwości lub kolekcji odwołań, które można nawigować przy użyciu *kropka* notacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jeden do wielu `Customer` klasa ma właściwość, która deklaruje relacji między klientów i zamówienia.  `Orders` Właściwość jest typu <xref:System.Data.Linq.EntitySet%601>. Ten typ oznacza, że ta relacja jest jeden do wielu (jednego klienta do wielu zamówienia). <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Właściwość jest używana do opisywania, jak to skojarzenie jest realizowane, mianowicie, określając nazwę właściwości w klasie powiązanych ma być porównywana z tą wersją. W tym przykładzie `CustomerID` porównywana właściwość, podobnie jak bazy danych *sprzężenia* będzie porównania wartości tej kolumny.  
  
> [!NOTE]
>  Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia skojarzenia między klasami.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Można również wycofać sytuacji. Zamiast używania `Customer` klas do opisania skojarzenie między klienci i zamówienia, można użyć `Order` klasy. `Order` Klasy używa <xref:System.Data.Linq.EntityRef%601> typu do opisywania relacji do klienta, jak w poniższym przykładzie kodu.  
  
> [!NOTE]
>  <xref:System.Data.Linq.EntityRef%601> Klasy obsługuje *odroczone ładowanie*. Aby uzyskać więcej informacji *zobacz* [odroczone a ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
