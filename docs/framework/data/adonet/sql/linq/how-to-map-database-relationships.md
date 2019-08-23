---
title: 'Instrukcje: Mapowanie relacji w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 42e7a715c8137574bff617715c1f174314080131
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943612"
---
# <a name="how-to-map-database-relationships"></a>Instrukcje: Mapowanie relacji w bazie danych
Można kodować jako odwołania do właściwości w klasie Entity, wszelkie relacje danych, które zawsze będą takie same. W przykładowej bazie danych Northwind, ponieważ klienci zwykle umieszczają zamówienia, zawsze istnieje relacja między klientami a ich zamówieniami.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.AssociationAttribute> definiuje atrybut, który pomaga reprezentować takie relacje. Ten atrybut jest używany razem z <xref:System.Data.Linq.EntitySet%601> typami i <xref:System.Data.Linq.EntityRef%601> , aby reprezentować, co byłoby relacją klucza obcego w bazie danych. Aby uzyskać więcej informacji, zobacz sekcję atrybut skojarzenia w [mapowaniu opartym na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
> W wartościach właściwości magazynu AssociationAttribute i ColumnAttribute jest uwzględniana wielkość liter. Na przykład upewnij się, że wartości używane w atrybucie właściwości AssociationAttribute. Storage pasują do wielkości liter dla odpowiednich nazw właściwości używanych w innym miejscu w kodzie. Dotyczy to wszystkich języków programowania .NET, nawet tych, które nie są zazwyczaj rozróżniane wielkości liter, w tym Visual Basic. Aby uzyskać więcej informacji na temat właściwości Storage, <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>Zobacz.  
  
 Większość relacji to jeden-do-wielu, jak w przykładzie w dalszej części tego tematu. Istnieje również możliwość reprezentowania relacji jeden-do-jednego i wiele-do-wielu w następujący sposób:  
  
- Jeden do jednego: Reprezentuje ten rodzaj relacji przez uwzględnienie <xref:System.Data.Linq.EntitySet%601> obu stron.  
  
     Rozważmy `Customer` - `Customer` na przykład relację utworzoną w taki sposób, że kod zabezpieczający klienta nie zostanie znaleziony w tabeli i dostęp do niego mają tylko autoryzowani osoby. `SecurityCode`  
  
- Wiele do wielu: W przypadku relacji wiele-do-wielu klucz podstawowy tabeli łączy (nazywany również tabelą skrzyżowań ) jest często tworzony przez złożone klucze obce z pozostałych dwóch tabel.  
  
     Rozważmy `Employee` - `EmployeeProject`na przykład relację wiele-do-wielu utworzoną za pomocą tabeli linków. `Project` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wymaga, aby taka relacja była modelowana przy użyciu trzech klas `Employee`: `Project`,, `EmployeeProject`i. W takim przypadku zmiana relacji między `Employee` `Project` i a może wydawać się, że wymaga aktualizacji klucza `EmployeeProject`podstawowego. Ta sytuacja jest jednak najlepszym modelem jako usunięcie istniejącej `EmployeeProject` i nowej. `EmployeeProject`  
  
    > [!NOTE]
    > Relacje w relacyjnych bazach danych są zwykle modelowane jako wartości klucza obcego, które odwołują się do kluczy podstawowych w innych tabelach. Aby poruszać się między nimi, można jawnie skojarzyć dwie tabele przy użyciu operacji sprzężenia relacyjnego.  
    >   
    >  Obiekty w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], z drugiej strony, odnoszą się do siebie nawzajem przy użyciu odwołań do właściwości lub kolekcji odwołań, które przechodź przy użyciu notacji kropkowej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Customer` jeden-do-wielu Klasa ma właściwość, która deklaruje relację między klientami a ich zamówieniami.  Właściwość jest typu <xref:System.Data.Linq.EntitySet%601>. `Orders` Ten typ oznacza, że ta relacja jest "jeden do wielu" (jeden klient do wielu zamówień). <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Właściwość służy do opisywania, w jaki sposób to skojarzenie jest realizowane, a mianowicie, poprzez określenie nazwy właściwości w powiązanej klasie, która ma zostać porównana z tym elementem. W tym przykładzie `CustomerID` właściwość jest porównywana, podobnie jak sprzężenie bazy danych będzie porównywać tę wartość kolumny.  
  
> [!NOTE]
> Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby utworzyć skojarzenie między klasami.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Możesz również odwrócić sytuację. Zamiast używać `Order` klasy do opisywania skojarzenia między klientami i zamówieniami, można użyć klasy. `Customer` `Order` Klasa<xref:System.Data.Linq.EntityRef%601> używa typu do opisywania relacji z powrotem do klienta, jak w poniższym przykładzie kodu.  
  
> [!NOTE]
> Klasa obsługuje *ładowanie odroczone.* <xref:System.Data.Linq.EntityRef%601> Aby uzyskać więcej informacji, *Zobacz* [odroczone względem natychmiastowego ładowania](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
