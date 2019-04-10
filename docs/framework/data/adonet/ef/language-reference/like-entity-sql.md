---
title: Podobnie jak (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 9463a5cb522a3d3dab7725c4b71a5970d1bdf19d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302260"
---
# <a name="like-entity-sql"></a>Podobnie jak (jednostka SQL)
Określa, czy określony znak `String` pasuje do określonego wzorca.  
  
## <a name="syntax"></a>Składnia  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Argumenty  
 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Wyrażenie zwracające `String`.  
  
 `pattern`  
 Wzorzec do dopasowania do określonego `String`.  
  
 `escape`  
 Znak ucieczki.  
  
 NIE  
 Określa, że wynik podobny być ujemna.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `string` pasuje do wzorca; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażeniach, które używają LIKE operator są obliczane w taki taki sam sposób jak wyrażeniach, które używają równości jako kryteria filtrowania. Jednak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażeniach, które używają LIKE operator mogą obejmować zarówno literały i symbole wieloznaczne.  
  
 W poniższej tabeli opisano składnię wzorzec `string`.  
  
|Symbol wieloznaczny|Opis|Przykład|  
|------------------------|-----------------|-------------|  
|%|Wszelkie `string` zero lub więcej znaków.|`title like '%computer%'` znajduje wszystkie tytuły wyrazami `"computer"` gdziekolwiek w tytule.|  
|_ (podkreślenie)|Dowolny pojedynczy znak.|`firstname like '_ean'` znajduje wszystkie cztery imiona kończących się ciągiem `"ean`, "takich jak Dean lub Piotra.|  
|[ ]|Dowolnego pojedynczego znaku w określonym zakresie ([a-f]) lub zestawu ([abcdef]).|`lastname like '[C-P]arsen'` znajduje nazwiska kończą się ciągiem "arsen", a począwszy od dowolny pojedynczy znak między C i P, takie jak Carsen lub Larsen.|  
|[^]|Dowolny pojedynczy znak nie jest w określonym zakresie ([^ a-f]) lub ustawić ([^ abcdef]).|`lastname like 'de[^l]%'` Umożliwia znalezienie wszystkich nazwisk, które zaczynają się od "de" i nie obejmują "l" jako następującą literę.|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Takich jak operator i klauzuli UCIECZKI nie można zastosować do `System.DateTime` lub `System.Guid` wartości.  
  
 Podobnie jak dopasowywania do wzorca obsługuje ASCII i Unicode. Jeśli wszystkie parametry są znaki ASCII, dopasowanie wzorca ASCII jest przeprowadzane. Jeśli co najmniej jeden z argumentów Unicode, wszystkie argumenty są konwertowane na Unicode i odbywa się dopasowanie wzorca Unicode. Gdy używasz Unicode przy użyciu NOTACJI końcowe spacje są istotne; jednak innego niż Unicode, końcowe spacje nie są istotne. Składnia ciągu wzorca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest taka sama jak w przypadku [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
 Wzorzec może zawierać zwykłe znaki oraz znaki symboli wieloznacznych. Podczas dopasowywania do wzorca zwykłe znaki muszą dokładnie odpowiadać znaków określonych w znaku `string`. Jednak symboli wieloznacznych można dopasować do dowolnych fragmentów ciągu znaków. Gdy jest używany z symbolami wieloznacznymi, LIKE operator jest bardziej elastyczny niż = i! = operatorów porównywania ciągów.  
  
> [!NOTE]
>  Może używać właściwe dla dostawcy rozszerzeń, jeśli platformą docelową jest program określonego dostawcy. Jednak takie konstrukcje mogą być traktowane inaczej przez innych dostawców, na przykład. SqlServer obsługuje [pierwszego do ostatniego] i [^ pierwszej i ostatniej] wzorców, jeśli pierwsza odpowiada dokładnie jeden znak między pierwszym i ostatnim i ostatniego dopasowania dokładnie jeden znak, który nie jest między pierwszym i ostatnim.  
  
### <a name="escape"></a>Escape  
 Za pomocą klauzuli UCIECZKI, można wyszukiwać ciągi znaków, które zawierają jeden lub więcej specjalnych symboli wieloznacznych opisano w tabeli w poprzedniej sekcji. Załóżmy na przykład, kilku dokumentów zawierają literału "100%" w tytule i chcesz wyszukać wszystkie te dokumenty. Ponieważ procentu (%) znak jest symbolem wieloznacznym, musisz wyjść z niego przy użyciu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] klauzuli UCIECZKI, aby pomyślnie wykonać wyszukiwanie. Oto przykład tego filtru.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 W tym wyrażeniu wyszukiwania znaku wieloznacznego procentu (%) bezpośrednio po znaku wykrzyknika (!) jest traktowany jako literał, a nie jako symbolu wieloznacznego. Można użyć dowolnego znaku z wyjątkiem znaku ucieczki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] symboli wieloznacznych i kwadrat dopasowywanie (`[ ]`) znaków. W poprzednim przykładzie znak wykrzyknika (!) jest znakiem ucieczki.  
  
## <a name="example"></a>Przykład  
 Następujące dwa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytań użyj LIKE i operatory UCIECZKI, aby określić, czy dany ciąg znaków jest zgodny ze wzorcem określonym. Wyszukuje pierwsze zapytanie `Name` , rozpoczyna się od znaków `Down_`. To zapytanie używa opcji ANULOWANIA, ponieważ znak podkreślenia (`_`) jest symbolem wieloznacznym. Bez określania opcji ANULOWANIA, zapytanie będzie wyszukiwać `Name` wartości rozpoczynających się od słowa `Down` następuje dowolny pojedynczy znak inny niż znak podkreślenia. Zapytania są oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
