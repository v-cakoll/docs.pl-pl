---
title: "Konstruowanie typów (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8a6ae2334c879733e964014716c2b67e77f271d5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="constructing-types-entity-sql"></a>Konstruowanie typów (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia trzy rodzaje konstruktory: wiersz konstruktorów, typ nazwany konstruktorów i konstruktorów kolekcji.  
  
## <a name="row-constructors"></a>Konstruktory wiersza  
 Użyj konstruktorów wiersza w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do skonstruowania anonimowe, strukturę maszynowy rekordy z co najmniej jedną wartość. Typ wyniku konstruktorze wierszy jest typu wiersza, których typy pól odpowiadają typy wartości używane do utworzenia wiersza. Na przykład poniższe wyrażenie tworzy wartość typu `Record(a int, b string, c int)`:  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Jeśli nie zostanie określona alias dla wyrażenia w Konstruktorze row, programu Entity Framework próbuje wygenerować. Aby uzyskać więcej informacji, zobacz sekcję "Zasady aliasowania" w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Wyrażenie aliasów w Konstruktorze row mają zastosowanie następujące reguły:  
  
-   Wyrażenia w Konstruktorze row nie może odwoływać się do innych aliasów w tej samej konstruktora.  
  
-   Dwóch wyrażeń w tym samym Konstruktor row nie może mieć takiego samego aliasu.  
  
 Aby uzyskać więcej informacji na temat konstruktorów wiersza, zobacz [wiersza](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Konstruktory kolekcji  
 Użyj konstruktorów kolekcji w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można utworzyć wystąpienia zestaw wielokrotny z listy wartości. Wszystkie wartości w Konstruktorze musi być typu wzajemnie zgodne `T`, i konstruktora tworzy kolekcję typu `Multiset<T>`. Na przykład poniższe wyrażenie tworzy kolekcję liczb całkowitych:  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Pusty zestaw wielokrotny konstruktory nie są dozwolone, ponieważ nie można określić typu elementów. Następujący ciąg nie jest prawidłowy:  
  
 `multiset() {}`  
  
 Aby uzyskać więcej informacji, zobacz [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Konstruktory typu nazwanego (NamedType inicjatory)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Umożliwia konstruktorów typu (inicjatory), można utworzyć wystąpienia nazwanego typy złożone i typy jednostek. Na przykład poniższe wyrażenie tworzy wystąpienie `Person` typu.  
  
 `Person("abc", 12)`  
  
 Poniższe wyrażenie powoduje utworzenie wystąpienia typu złożonego.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Poniższe wyrażenie tworzy wystąpienie zagnieżdżonego typu złożonego.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Poniższe wyrażenie tworzy wystąpienie obiektu zagnieżdżonego typu złożonego.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego do wartości null. `MyModel.ZipCode(‘98118’, null)`  
  
 Argumenty konstruktora są rozpatrywane w takiej samej kolejności jak deklaracja atrybuty typu.  
  
 Aby uzyskać więcej informacji, zobacz [konstruktora typu o nazwie](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
