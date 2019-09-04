---
title: Konstruowanie typów (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 7113aaf1c2caa982a8ab4751928856c1271570cb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251120"
---
# <a name="constructing-types-entity-sql"></a>Konstruowanie typów (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera trzy rodzaje konstruktorów: konstruktory wierszy, konstruktory nazwanych typów i konstruktory kolekcji.  
  
## <a name="row-constructors"></a>Konstruktory wierszy  
 Konstruktory wierszy w programie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] służą do konstruowania anonimowych, strukturalnie wpisanych rekordów z co najmniej jednej wartości. Typ wyniku konstruktora wierszy jest typem wiersza, którego typy pól odpowiadają typom wartości używanych do konstruowania wiersza. Na przykład następujące wyrażenie konstruuje wartość typu `Record(a int, b string, c int)`:  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Jeśli nie podasz aliasu dla wyrażenia w konstruktorze wierszy, Entity Framework podejmie próbę wygenerowania jednego. Aby uzyskać więcej informacji, zobacz sekcję "reguły aliasów" w temacie [identyfikatory](identifiers-entity-sql.md).  
  
 W konstruktorze wierszy są stosowane następujące reguły:  
  
- Wyrażenia w konstruktorze wierszy nie mogą odwoływać się do innych aliasów w tym samym konstruktorze.  
  
- Dwa wyrażenia w tym samym konstruktorze wierszy nie mogą mieć tego samego aliasu.  
  
 Aby uzyskać więcej informacji na temat konstruktorów wierszy, zobacz [wiersz](row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Konstruktory kolekcji  
 Za pomocą konstruktorów kolekcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w programie można utworzyć wystąpienie zestawu wielokrotnego z listy wartości. Wszystkie wartości w konstruktorze muszą być wzajemnie zgodnego typu `T`, a Konstruktor tworzy kolekcję typu. `Multiset<T>` Na przykład następujące wyrażenie tworzy kolekcję liczb całkowitych:  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Puste konstruktory wielokrotne są niedozwolone, ponieważ nie można określić typu elementów. Następujące elementy są nieprawidłowe:  
  
 `multiset() {}`  
  
 Aby uzyskać więcej informacji, zobacz zestaw [wielokrotny](multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Konstruktory nazwanych typów (inicjatory nazwanych)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zezwala na konstruktory typów (inicjatory) do tworzenia wystąpień o nazwanych typach złożonych i typów jednostek. Na przykład następujące wyrażenie tworzy wystąpienie `Person` typu.  
  
 `Person("abc", 12)`  
  
 Poniższe wyrażenie tworzy wystąpienie typu złożonego.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Poniższe wyrażenie tworzy wystąpienie zagnieżdżonego typu złożonego.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Poniższe wyrażenie tworzy wystąpienie jednostki z zagnieżdżonym typem złożonym.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego na wartość null. `MyModel.ZipCode(‘98118’, null)`  
  
 Argumenty konstruktora są założono, że są w tej samej kolejności co deklaracja atrybutów typu.  
  
 Aby uzyskać więcej informacji, zobacz [nazwany Konstruktor typów](named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
- [System typów](type-system-entity-sql.md)
