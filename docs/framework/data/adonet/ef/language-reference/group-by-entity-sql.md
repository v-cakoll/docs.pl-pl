---
title: Grupuj według (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: d9074b1c2ea4f8f9206c8de1e658c1aac762a74f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936092"
---
# <a name="group-by-entity-sql"></a>Grupuj według (Entity SQL)
Określa grupy, do których obiekty zwracane przez zapytanie ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) mają zostać umieszczone.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `aliasedExpression`  
 Dowolne prawidłowe wyrażenie zapytania, w którym jest wykonywane grupowanie. `expression`może być właściwością lub wyrażeniem nieagregującym, które odwołuje się do właściwości zwróconej przez klauzulę FROM. Każde wyrażenie w klauzuli GROUP BY musi być szacowane do typu, który można porównać pod kątem równości. Te typy są ogólnie skalarnymi typami podstawowymi, takimi jak liczby, ciągi i daty. Nie można grupować według kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja agregująca jest uwzględniona w klauzuli \<SELECT, wybierz opcję list >, Group by oblicza wartość podsumowania dla każdej grupy. Gdy Grupuj według jest określony, każda nazwa właściwości w dowolnym niezagregowanym wyrażeniu na liście wyboru powinna być uwzględniona na liście Grupuj według lub wyrażenie GROUP BY musi być dokładnie zgodne z wyrażeniem Select list.  
  
> [!NOTE]
> Jeśli klauzula ORDER BY nie jest określona, grupy zwracane przez klauzulę GROUP BY nie są w żadnej określonej kolejności. Aby określić konkretną kolejność danych, zaleca się, aby zawsze używać klauzuli ORDER BY.  
  
 Gdy klauzula GROUP BY jest określona, jawnie lub niejawnie (na przykład przez klauzulę HAVING w zapytaniu), bieżący zakres jest ukryty i wprowadzany jest nowy zakres.  
  
 Klauzula SELECT, klauzula HAVING i klauzula ORDER BY nie będą już mogły odwoływać się do nazw elementów określonych w klauzuli FROM. Można odwoływać się tylko do samych wyrażeń grupowania. W tym celu można przypisać nowe nazwy (aliasy) do każdego wyrażenia grupowania. Jeśli nie określono aliasu dla wyrażenia grupowania, program [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować jeden przy użyciu reguł generacji aliasów, jak pokazano w poniższym przykładzie.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 Wyrażenia w klauzuli GROUP BY nie mogą odwoływać się do nazw zdefiniowanych wcześniej w tej samej klauzuli GROUP BY.  
  
 Oprócz nazw grupowania można także określić wartości zagregowane w klauzuli SELECT, klauzuli HAVING i klauzuli ORDER BY. Agregacja zawiera wyrażenie, które jest oceniane dla każdego elementu grupy. Operator agregujący redukuje wartości wszystkich tych wyrażeń (zwykle, ale nie zawsze, do pojedynczej wartości). Wyrażenie agregujące może tworzyć odwołania do oryginalnych nazw elementów widocznych w zakresie nadrzędnym lub do dowolnych nowych nazw wprowadzonych przez samą klauzulę GROUP BY. Chociaż agregacje pojawiają się w klauzuli SELECT, klauzuli HAVING i klauzuli ORDER BY, są faktycznie oceniane w tym samym zakresie co wyrażenia grupowania, jak pokazano w poniższym przykładzie.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 To zapytanie używa klauzuli GROUP BY do tworzenia raportu o kosztach wszystkich produktów uporządkowanych według produktu. Zawiera nazwę `name` produktu jako część wyrażenia grupowania, a następnie odwołuje się do tej nazwy na liście wyboru. Określa również wartość zagregowaną `sum` na liście wyboru, która wewnętrznie odwołuje się do ceny i ilości wiersza zamówienia.  
  
 Każde wyrażenie GROUP by key musi mieć co najmniej jedno odwołanie do zakresu wejściowego:  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 Aby zapoznać się z przykładem użycia opcji Grupuj [](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)według, zobacz.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora Grupuj według, aby określić grupy, do których obiekty są zwracane przez zapytanie. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.  
  
2. Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
