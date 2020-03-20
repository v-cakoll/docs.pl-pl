---
title: 'Instrukcje: Mapowanie relacji w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: c89fb3e11ae8e0f8ea37727446cdf65db9499a1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148377"
---
# <a name="how-to-map-database-relationships"></a>Instrukcje: Mapowanie relacji w bazie danych
Można zakodować jako odwołania do właściwości w klasie jednostki wszelkie relacje danych, które zawsze będą takie same. W przykładowej bazie danych Northwind, na przykład, ponieważ klienci zazwyczaj składają zamówienia, zawsze istnieje relacja w modelu między klientami a ich zamówieniami.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]definiuje atrybut, <xref:System.Data.Linq.Mapping.AssociationAttribute> aby pomóc w reprezentowaniu takich relacji. Ten atrybut jest używany <xref:System.Data.Linq.EntitySet%601> wraz <xref:System.Data.Linq.EntityRef%601> z i typów do reprezentowania, co byłoby relacji klucza obcego w bazie danych. Aby uzyskać więcej informacji, zobacz sekcję Atrybut skojarzenia [mapowania opartego na atrybutach](attribute-based-mapping.md).  
  
> [!NOTE]
> AssociationAttribute i ColumnAttribute Storage wartości właściwości są rozróżniane wielkość liter. Na przykład upewnij się, że wartości używane w atrybucie dla AssociationAttribute.Storage właściwości zgodne przypadku dla odpowiednich nazw właściwości używane w innym miejscu w kodzie. Dotyczy to wszystkich języków programowania platformy .NET, nawet tych, które zazwyczaj nie są uwzględniane wielkość liter, w tym języka Visual Basic. Aby uzyskać więcej informacji na <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>temat właściwości Storage, zobacz .  
  
 Większość relacji są jeden do wielu, jak w przykładzie w dalszej części tego tematu. Można również reprezentować relacje jeden-do-jednego i wiele do wielu w następujący sposób:  
  
- Jeden do jednego: Reprezentuj tego <xref:System.Data.Linq.EntitySet%601> rodzaju relacje, włączając w to obie strony.  
  
     Rozważmy na `Customer` - `SecurityCode` przykład relację utworzoną w taki sposób, aby `Customer` kod zabezpieczeń klienta nie został znaleziony w tabeli i był dostępny tylko dla osób autoryzowanych.  
  
- Wiele do wielu: W relacjach wiele-do-wielu klucz podstawowy tabeli łączy (również o nazwie tabela *skrzyżowań)* jest często tworzony przez złożony kluczy obcych z pozostałych dwóch tabel.  
  
     Rozważmy na `Employee` - `Project` przykład relację wiele-do-wielu `EmployeeProject`utworzoną przy użyciu tabeli łączy . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wymaga, aby taki związek był wzorowany `Employee` `Project`przy `EmployeeProject`użyciu trzech klas: , , i . W takim przypadku zmiana relacji `Employee` między `Project` an a a może wydawać `EmployeeProject`się wymagać aktualizacji klucza podstawowego . Jednak ta sytuacja jest najlepiej modelowane jako `EmployeeProject` usunięcie istniejącego `EmployeeProject`i tworzenia nowego .  
  
    > [!NOTE]
    > Relacje w relacyjnych bazach danych są zazwyczaj modelowane jako wartości klucza obcego, które odwołują się do kluczy podstawowych w innych tabelach. Aby przejść między nimi jawnie skojarzyć dwie tabele przy użyciu operacji *sprzężenia* relacyjnego.  
    >
    >  Obiekty [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]w , z drugiej strony, odnoszą się do siebie za pomocą odwołań do właściwości lub kolekcji odwołań, które można nawigować za pomocą notacji *kropkowej.*  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jeden do `Customer` wielu klasa ma właściwość, która deklaruje relację między klientami i ich zamówień.  Właściwość `Orders` jest <xref:System.Data.Linq.EntitySet%601>typu . Ten typ oznacza, że ta relacja jest jeden do wielu (jeden klient do wielu zamówień). Właściwość <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> jest używana do opisania, jak to skojarzenie jest realizowane, a mianowicie, określając nazwę właściwości w klasie pokrewnej, które mają być porównywane z tym. W tym przykładzie `CustomerID` właściwość jest porównywana, podobnie jak *sprzężenie* bazy danych będzie porównywać tę wartość kolumny.  
  
> [!NOTE]
> Jeśli używasz programu Visual Studio, można użyć Projektanta relacyjnego obiektu, aby utworzyć skojarzenie między klasami.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Można również odwrócić sytuację. Zamiast używać `Customer` klasy do opisania skojarzenia między klientami `Order` i zamówieniami, można użyć klasy. Klasa `Order` używa <xref:System.Data.Linq.EntityRef%601> typu do opisania relacji z powrotem do klienta, jak w poniższym przykładzie kodu.  
  
> [!NOTE]
> Klasa <xref:System.Data.Linq.EntityRef%601> obsługuje *odroczone ładowanie*. Aby uzyskać więcej informacji, *zobacz* [Odroczone i natychmiastowe ładowanie](deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
