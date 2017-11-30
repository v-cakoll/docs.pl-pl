---
title: "Grupuj według (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb19589fbba12bba710638e061defa198f9fa169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="group-by-entity-sql"></a>Grupuj według (jednostka SQL)
Określa grupę, do których obiektów zwróconych przez kwerendę ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) zostaną umieszczone wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `aliasedExpression`  
 Dowolne wyrażenie prawidłowe zapytanie wykonane grupowanie. `expression`może być właściwością lub wyrażenie niedotyczących agregacji, które odwołuje się do właściwości zwrócony przez klauzuli FROM. Każde wyrażenie w klauzuli GROUP BY musi mieć typ, który można porównywać pod względem równości. Te typy są zazwyczaj skalarne w nim elementów podstawowych, takich jak liczby, ciągi i daty. Nie można grupować według kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcje agregujące są uwzględnione w klauzuli SELECT \<listy wyboru >, GROUP BY oblicza wartość podsumowania dla każdej grupy. Gdy GROUP BY jest określona, nazwy właściwości w dowolne inne niż zbiorcze wyrażenie na liście wyboru powinny uwzględnione na liście GROUP BY lub wyrażenie GROUP BY musi dokładnie odpowiadać wyrażenie listy wyboru.  
  
> [!NOTE]
>  Jeśli nie określono klauzuli ORDER BY, grup zwracane przez klauzulę GROUP BY nie są w określonej kolejności. Aby określić konkretnego porządkowanie danych, zaleca się zawsze używać klauzuli ORDER BY.  
  
 W przypadku klauzuli GROUP BY albo jawnie lub niejawnie (na przykład w klauzuli HAVING w zapytaniu) bieżącego zakresu jest ukryta i wprowadzono nowy zakres.  
  
 W klauzuli SELECT w klauzuli HAVING i klauzuli ORDER BY będzie już można odwoływać się do nazwy elementu określone w klauzuli FROM. Tylko mogą odwoływać się do siebie wyrażenia grupowania. Aby to zrobić, można przypisać nowe nazwy (aliasy) do każdego wyrażenia grupowania. Jeśli jest określony żaden alias wyrażenia grupowania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować za pomocą reguł generowania aliasu, jak pokazano w poniższym przykładzie.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 Wyrażenia w klauzuli GROUP BY nie może odwoływać się do nazwy zdefiniowanej wcześniej w tej samej klauzuli GROUP BY.  
  
 Oprócz nazwy grupowania można również określić wartości zagregowanych w klauzuli SELECT, klauzuli HAVING i klauzuli ORDER BY. Wartość zagregowana zawiera wyrażenie, które jest obliczane dla każdego elementu grupy. Operator zagregowany zmniejsza wartości tych wyrażeń (zwykle, ale nie zawsze pojedynczej wartości). Wyrażenie agregujące można odwołuje się do oryginalnej nazwy elementu widoczne w zakresie nadrzędnym lub dowolnych nowych nazw wprowadzonego w klauzuli GROUP BY samej siebie. Chociaż zagregowanych danych występują w klauzuli SELECT, klauzuli HAVING i klauzuli ORDER BY, są one faktycznie obliczane, w tym samym zakresie co wyrażenia grupowania, jak pokazano w poniższym przykładzie.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 To zapytanie używa klauzuli GROUP BY, aby wygenerować raport koszt wszystkich produktów zamówionych, według produktu. Zawiera nazwę `name` produktu jako część wyrażenia grupowania, a następnie odwołania, których nazwy na liście wyboru. Określa również zagregowanej `sum` na liście wyboru wewnętrznie odwołujących się do ceny i ilość wiersza zamówienia.  
  
 Każde wyrażenie GROUP By klucza musi mieć co najmniej jedno odwołanie do zakresu wejściowego:  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 Na przykład przy użyciu GROUP BY, zobacz [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto operatora GROUP BY do określenia grup, w których obiekty są zwracane przez zapytanie. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Wyrażenia zapytań](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
