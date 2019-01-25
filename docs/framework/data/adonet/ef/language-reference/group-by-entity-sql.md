---
title: Grupuj według (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 4dffc88866721bde0d4e846fa805bb60c6855b5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740570"
---
# <a name="group-by-entity-sql"></a>Grupuj według (jednostka SQL)
Określa grupy, do których obiektów zwróconych przez zapytanie ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) wyrażenie, które mają być umieszczone.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `aliasedExpression`  
 Dowolne wyrażenie prawidłowe zapytanie, na którym odbywa się grupowania. `expression` może być właściwością lub wyrażenie agregacji, które odwołuje się do właściwości zwrócony przez klauzuli FROM. Każde wyrażenie w klauzuli GROUP BY musi być typem, który można porównać pod kątem równości. Te typy są zazwyczaj skalarną w nim elementów podstawowych, takich jak liczby, ciągi i daty. Nie można grupować według kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcje agregujące są uwzględnione w klauzuli SELECT \<listy wyboru >, GROUP BY oblicza wartość podsumowania dla każdej grupy. Kiedy GROUP BY jest określona, nazwy właściwości w inne niż zbiorcze dowolne wyrażenie, które są dostępne na liście wyboru powinny być objęte listy GROUP BY lub wyrażenie GROUP BY musi dokładnie odpowiadać wyrażeniu listy wyboru.  
  
> [!NOTE]
>  Jeśli nie określono klauzuli ORDER BY, grup zwracane przez klauzulę GROUP BY nie są w określonej kolejności. Aby określić kolejność określoną w danych, zalecamy zawsze używać klauzuli ORDER BY.  
  
 Gdy klauzula GROUP BY jest określona, albo jawnie lub niejawnie (na przykład w klauzuli HAVING w zapytaniu) jest ukryta w bieżącym zakresie i wprowadzono nowy zakres.  
  
 Klauzuli SELECT, klauzula HAVING i ORDER BY — klauzula nie będzie już mógł odwoływać się do nazwy elementów określony w klauzuli FROM. Użytkownik może odwoływać się tylko do wyrażenia grupowania, samodzielnie. Aby to zrobić, można przypisać nowe nazwami (aliasami) do każdego wyrażenia grupowania. Jeśli określono Brak aliasu dla wyrażenia grupowania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje wygenerować za pomocą reguł generowania aliasu, jak pokazano w poniższym przykładzie.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 Wyrażenia w klauzuli GROUP BY nie może odwoływać się do nazw zdefiniowanych wcześniej w tym samym klauzuli GROUP BY.  
  
 Oprócz nazwy grupowań można również określić wartości zagregowanych w klauzuli SELECT, klauzula HAVING i ORDER BY — klauzula. Wartość zagregowana zawiera wyrażenie, które jest obliczane dla każdego elementu grupy. Aggregate-operator ogranicza wartości tych wyrażeń (zwykle, ale nie zawsze w jedną wartość). Wyrażenie agregujące można odwołuje się do oryginalnej nazwy elementów widoczne w zakresie nadrzędnym lub dowolnych nowych nazw wynikające z klauzuli GROUP BY, sam. Chociaż zagregowanych danych występują w klauzuli SELECT, klauzula HAVING i ORDER BY — klauzula, ocenia się je faktycznie w taki sam zakres jak wyrażenia grupowania, jak pokazano w poniższym przykładzie.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 To zapytanie używa klauzuli GROUP BY aby wygenerować raport kosztów wszystkie produkty, uporządkowanych według produktu. Daje ona nazwę `name` produktu jako część wyrażenia grupowania, a następnie odwołań, które nazwy na liście wyboru. Określa również agregacji `sum` na liście WYBIERANIA, który wewnętrznie odwołuje się do ceny i ilości wiersza zamówienia.  
  
 Każde wyrażenie GROUP By klucza musi mieć co najmniej jedno odwołanie do zakresu wejściowego:  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 Na przykład przy użyciu grupy, zobacz [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora GROUP BY do określania grup, w których obiekty są zwracane przez zapytanie. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
