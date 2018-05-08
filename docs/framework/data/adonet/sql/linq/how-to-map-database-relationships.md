---
title: 'Porady: Mapowanie relacji w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: c3ae138134682f35ae42c99cc6434dae9ec1103d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-map-database-relationships"></a>Porady: Mapowanie relacji w bazie danych
Może zakodować jako właściwość odwołuje się w klasie jednostki relacji między danymi, które będą zawsze taki sam. W bazie danych Northwind na przykład, ponieważ klienci zwykle składanie zamówień, istnieje zawsze relacja modelu między klientów i zamówienia.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definiuje <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu ułatwiające reprezentują takich relacji. Ten atrybut jest używany razem z <xref:System.Data.Linq.EntitySet%601> i <xref:System.Data.Linq.EntityRef%601> typy do reprezentowania, jakie byłyby relacji klucza obcego w bazie danych. Aby uzyskać więcej informacji, zobacz sekcję atrybut skojarzenia [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  Wartości właściwości AssociationAttribute i klasy ColumnAttribute magazynu jest uwzględniana wielkość liter. Na przykład upewnij się, czy wartości używanych w atrybucie dla właściwości AssociationAttribute.Storage zgodne w przypadku odpowiadających im nazw właściwości używane w innym miejscu w kodzie. Dotyczy to wszystkich .NET języków programowania, nawet te, które nie są zwykle z uwzględnieniem wielkości liter, w tym Visual Basic. Aby uzyskać więcej informacji na temat właściwości magazynu, zobacz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 Większość relacje są jeden do wielu, jak pokazano w przykładzie w dalszej części tego tematu. Relacje jeden do jednego oraz wiele do wielu może także reprezentować w następujący sposób:  
  
-   Jeden do jednego: Reprezentują tego typu relacji, umieszczając w niej <xref:System.Data.Linq.EntitySet%601> po obu stronach.  
  
     Rozważmy na przykład `Customer` - `SecurityCode` relacji tworzone, dzięki czemu kod zabezpieczeń klienta nie zostaną znalezione w `Customer` tabeli i może mieć dostęp tylko upoważnione osoby.  
  
-   Wiele do wielu: W relacji wiele do wielu, klucz podstawowy tabeli Powiązanie (o nazwie *Rozgałęzienie* tabeli) często jest tworzony przez złożone kluczy obcych z dwóch tabel.  
  
     Rozważmy na przykład `Employee` - `Project` relacji wiele do wielu utworzone za pomocą łącza tabeli `EmployeeProject`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wymaga, aby takiej relacji należy modelować przy użyciu trzech klas: `Employee`, `Project`, i `EmployeeProject`. W takim przypadku zmiana relacji między `Employee` i `Project` mogą być wyświetlane, aby wymagać aktualizacji klucza podstawowego `EmployeeProject`. Jednak taka sytuacja jest najlepiej formę usunięcie istniejącego `EmployeeProject` i tworzenia nowego `EmployeeProject`.  
  
    > [!NOTE]
    >  Relacje w relacyjnych baz danych są zazwyczaj modelowane jako wartości kluczy obcych, które odwołują się do kluczy podstawowych w innych tabelach. Do przechodzenia między nimi należy jawnie powiązać dwóch tabel za pomocą relacyjne *sprzężenia* operacji.  
    >   
    >  Obiekty w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], w drugim ręcznie, zapoznaj się ze sobą za pomocą odwołań do właściwości lub kolekcji odwołań, które przejść za pomocą *kropka* notacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jeden do wielu `Customer` klasa ma właściwość, która deklaruje relacji między klientów i zamówienia.  `Orders` Właściwość jest typu <xref:System.Data.Linq.EntitySet%601>. Ten typ oznacza, że ta relacja jest jeden do wielu (jednego klienta na wiele zamówienia). <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Właściwość jest używana do opisu, jak to skojarzenie odbywa się, a mianowicie, określając nazwę właściwości w klasie powiązanych ma zostać porównane z tego. W tym przykładzie `CustomerID` porównywana właściwość, podobnie jak bazy danych *sprzężenia* może porównać wartości tej kolumny.  
  
> [!NOTE]
>  Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia skojarzenia między klasami.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Można także cofnąć sytuacji. Zamiast `Customer` klasy do opisywania skojarzenie między klienci i zamówienia, możesz użyć `Order` klasy. `Order` Klasy używa <xref:System.Data.Linq.EntityRef%601> typu w celu opisania relacji do klienta, jak w poniższym przykładzie kodu.  
  
> [!NOTE]
>  <xref:System.Data.Linq.EntityRef%601> Klasy obsługuje *odroczonego ładowania*. Aby uzyskać więcej informacji *zobacz* [odroczone i ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
