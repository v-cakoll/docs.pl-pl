---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f9e33c78235f637e0aa0622d9d8cc30255722beb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319673"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
Określa, czy określony znak `String` jest zgodny z określonym wzorcem.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Argumenty  
 `match`  
 Wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zwracające wartość `String`.  
  
 `pattern`  
 Wzorzec do dopasowania do określonego `String`.  
  
 `escape`  
 Znak ucieczki.  
  
 NIEMOŻLIWE  
 Określa, że wynik LIKE ma być negacją.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`, jeśli `string` pasuje do wzorca; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 wyrażenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używające operatora LIKE są oceniane w taki sam sposób jak wyrażenia, które używają równości jako kryteriów filtrowania. Jednak wyrażenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używające operatora LIKE mogą zawierać zarówno literały, jak i symbole wieloznaczne.  
  
 W poniższej tabeli opisano składnię wzorca `string`.  
  
|Symbol wieloznaczny|Opis|Przykład|  
|------------------------|-----------------|-------------|  
|%|Dowolny `string` z zero lub więcej znaków.|`title like '%computer%'` znajduje wszystkie tytuły z wyrazem `"computer"` gdziekolwiek w tytule.|  
|_ (podkreślenie)|Dowolny pojedynczy znak.|`firstname like '_ean'` znajduje wszystkie cztery litery, które kończą się znakiem `"ean`, takie jak Dean lub Janusz.|  
|[ ]|Dowolny pojedynczy znak w określonym zakresie ([a-f]) lub Set ([abcdef]).|`lastname like '[C-P]arsen'` odnajduje nazwiska kończące się znakiem "Arsen" i Zaczynając od dowolnego pojedynczego znaku między C i P, na przykład Carsen lub Larsen.|  
|[^]|Dowolny pojedynczy znak spoza określonego zakresu ([^ a-f]) lub zestawu ([^ abcdef]).|`lastname like 'de[^l]%'` znajduje wszystkie nazwiska zaczynające się od "de" i nie zawierają "l" jako następującej litery.|  
  
> [!NOTE]
> Nie można zastosować operatora LIKE "[!INCLUDE[esql](../../../../../../includes/esql-md.md)]" i klauzuli UCIECZKi do wartości `System.DateTime` lub `System.Guid`.  
  
 Podobnie jak obsługa dopasowania wzorca ASCII i dopasowania do wzorca Unicode. Gdy wszystkie parametry są znakami ASCII, porównywanie wzorców ASCII jest wykonywane. Jeśli co najmniej jeden z argumentów jest w formacie Unicode, wszystkie argumenty są konwertowane na dopasowania do wzorca Unicode i Unicode. Gdy używasz Unicode z LIKE, końcowe puste są istotne. Jednak w przypadku wartości innych niż Unicode końcowe puste nie są istotne. Składnia ciągu wzorca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest taka sama jak w języku Transact-SQL.  
  
 Wzorzec może zawierać zwykłe znaki i symbole wieloznaczne. Podczas dopasowywania do wzorca zwykłe znaki muszą dokładnie pasować do znaków określonych w znaku `string`. Jednak symbole wieloznaczne można dopasować do dowolnego fragmentu ciągu znaków. Gdy jest używany z symbolami wieloznacznymi, operator LIKE jest bardziej elastyczny niż operatory porównania ciągów = i! =.  
  
> [!NOTE]
> Jeśli jest przeznaczony dla określonego dostawcy, można użyć rozszerzeń specyficznych dla dostawcy. Jednak takie konstrukcje mogą być traktowane inaczej przez innych dostawców, na przykład. Program SqlServer obsługuje wzorce [First-Last] i [^ First-Last], w których dawniej pasuje dokładnie jeden znak między pierwszym i ostatnim, a ostatni dopasowuje dokładnie jeden znak, który nie należy do zakresu od pierwszego do ostatniego.  
  
### <a name="escape"></a>Escape  
 Za pomocą klauzuli ESCAPE można wyszukiwać ciągi znaków zawierające co najmniej jedno specjalne znaki wieloznaczne opisane w tabeli w poprzedniej sekcji. Załóżmy na przykład, że kilka dokumentów zawiera literał "100%" w tytule i chcesz wyszukać wszystkie te dokumenty. Ponieważ procent (%) znak jest symbolem wieloznacznym, należy go wypróbować, używając klauzuli UCIECZKi [!INCLUDE[esql](../../../../../../includes/esql-md.md)], aby pomyślnie wykonać wyszukiwanie. Poniżej znajduje się przykład tego filtru.  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 W tym wyrażeniu wyszukiwania procentowy symbol wieloznaczny (%) bezpośrednio po znaku wykrzyknika (!) jest traktowany jako literał, a nie symbol wieloznaczny. Można użyć dowolnego znaku jako znaku ucieczki, z wyjątkiem symboli wieloznacznych [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i nawiasów kwadratowych (`[ ]`). W poprzednim przykładzie znak wykrzyknika (!) jest znakiem ucieczki.  
  
## <a name="example"></a>Przykład  
 Poniższe dwa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania używają operatorów LIKE i ESCAPE, aby określić, czy określony ciąg znaków jest zgodny z określonym wzorcem. Pierwsze zapytanie wyszukuje `Name` zaczynające się od znaków `Down_`. To zapytanie używa opcji UCIECZKi, ponieważ znak podkreślenia (`_`) jest symbolem wieloznacznym. Bez określania opcji UCIECZKi zapytanie wyszuka wszelkie wartości `Name`, które zaczynają się od słowa `Down`, po którym następuje dowolny pojedynczy znak inny niż znak podkreślenia. Zapytania są oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
