---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 58828b812ce374a664e4d232b707f22d5ca438c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912285"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
Określa, czy określony znak `String` jest zgodny z określonym wzorcem.  
  
## <a name="syntax"></a>Składnia  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Argumenty  
 `match`  
 Wyrażenie, które daje w wyniku `String`. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
 `pattern`  
 Wzorzec do dopasowania do określonego `String`.  
  
 `escape`  
 Znak ucieczki.  
  
 NIEMOŻLIWE  
 Określa, że wynik LIKE ma być negacją.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli dopasowuje wzorzec; `false`w przeciwnym razie. `string`  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]wyrażenia wykorzystujące operator LIKE są oceniane w taki sam sposób jak wyrażenia, które używają równości jako kryteriów filtrowania. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Jednak wyrażenia, które używają operatora like mogą zawierać zarówno literały, jak i symbole wieloznaczne.  
  
 W poniższej tabeli opisano składnię wzorca `string`.  
  
|Symbol wieloznaczny|Opis|Przykład|  
|------------------------|-----------------|-------------|  
|%|Dowolny `string` z zero lub więcej znaków.|`title like '%computer%'`znajduje wszystkie tytuły z wyrazem `"computer"` gdziekolwiek w tytule.|  
|_ (podkreślenie)|Dowolny pojedynczy znak.|`firstname like '_ean'`znajduje wszystkie cztery litery, których nazwy kończą się znakiem `"ean`", takie jak Dean lub Janusz.|  
|[ ]|Dowolny pojedynczy znak w określonym zakresie ([a-f]) lub Set ([abcdef]).|`lastname like '[C-P]arsen'`znajduje nazwiska kończące się znakiem "Arsen" i Zaczynając od dowolnego pojedynczego znaku między C i P, na przykład Carsen lub Larsen.|  
|[^]|Dowolny pojedynczy znak spoza określonego zakresu ([^ a-f]) lub zestawu ([^ abcdef]).|`lastname like 'de[^l]%'`znajduje wszystkie nazwiska zaczynające się od "de" i nie zawierają "l" jako następującej litery.|  
  
> [!NOTE]
> Operator like i klauzula ucieczki nie mogą być stosowane `System.DateTime` do wartości ani `System.Guid`. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
 Podobnie jak obsługa dopasowania wzorca ASCII i dopasowania do wzorca Unicode. Gdy wszystkie parametry są znakami ASCII, porównywanie wzorców ASCII jest wykonywane. Jeśli co najmniej jeden z argumentów jest w formacie Unicode, wszystkie argumenty są konwertowane na dopasowania do wzorca Unicode i Unicode. Gdy używasz Unicode z LIKE, końcowe puste są istotne. Jednak w przypadku wartości innych niż Unicode końcowe puste nie są istotne. Składnia ciągu wzorca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest taka sama jak w języku Transact-SQL.  
  
 Wzorzec może zawierać zwykłe znaki i symbole wieloznaczne. Podczas dopasowywania do wzorca zwykłe znaki muszą dokładnie pasować do znaków określonych w znaku `string`. Jednak symbole wieloznaczne można dopasować do dowolnego fragmentu ciągu znaków. Gdy jest używany z symbolami wieloznacznymi, operator LIKE jest bardziej elastyczny niż operatory porównania ciągów = i! =.  
  
> [!NOTE]
> Jeśli jest przeznaczony dla określonego dostawcy, można użyć rozszerzeń specyficznych dla dostawcy. Jednak takie konstrukcje mogą być traktowane inaczej przez innych dostawców, na przykład. Program SqlServer obsługuje wzorce [First-Last] i [^ First-Last], w których dawniej pasuje dokładnie jeden znak między pierwszym i ostatnim, a ostatni dopasowuje dokładnie jeden znak, który nie należy do zakresu od pierwszego do ostatniego.  
  
### <a name="escape"></a>Escape  
 Za pomocą klauzuli ESCAPE można wyszukiwać ciągi znaków zawierające co najmniej jedno specjalne znaki wieloznaczne opisane w tabeli w poprzedniej sekcji. Załóżmy na przykład, że kilka dokumentów zawiera literał "100%" w tytule i chcesz wyszukać wszystkie te dokumenty. Ponieważ procent (%) znak jest symbolem wieloznacznym, należy go wypróbować, używając [!INCLUDE[esql](../../../../../../includes/esql-md.md)] klauzuli Escape, aby pomyślnie wykonać wyszukiwanie. Poniżej znajduje się przykład tego filtru.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 W tym wyrażeniu wyszukiwania procentowy symbol wieloznaczny (%) bezpośrednio po znaku wykrzyknika (!) jest traktowany jako literał, a nie symbol wieloznaczny. Można użyć dowolnego znaku jako znaku ucieczki, z wyjątkiem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] symboli wieloznacznych i kwadratowych (`[ ]`) znaków. W poprzednim przykładzie znak wykrzyknika (!) jest znakiem ucieczki.  
  
## <a name="example"></a>Przykład  
 Poniższe dwa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania używają operatorów like i Escape, aby określić, czy określony ciąg znaków jest zgodny z określonym wzorcem. Pierwsze zapytanie wyszukuje `Name` , które zaczyna się od znaków `Down_`. To zapytanie używa opcji ucieczki, ponieważ znak podkreślenia`_`() jest symbolem wieloznacznym. Bez określenia opcji ucieczki, zapytanie będzie wyszukiwać `Name` wartości, które zaczynają się od słowa `Down` , po którym następuje dowolny pojedynczy znak inny niż znak podkreślenia. Zapytania są oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.  
  
2. Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
