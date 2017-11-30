---
title: Podobnie jak (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 773547b097bad80e82350b473b6e59d0d84aa6dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="like-entity-sql"></a>Podobnie jak (jednostka SQL)
Określa, czy określony znak `String` jest zgodna z określonym wzorcem.  
  
## <a name="syntax"></a>Składnia  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Argumenty  
 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Wyrażenie obliczane do `String`.  
  
 `pattern`  
 Wzorzec do dopasowania do określonego `String`.  
  
 `escape`  
 Znak ucieczki.  
  
 NIE  
 Określa, czy można zanegowane wynik LIKE.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `string` zgodny z wzorcem; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]wyrażeń, które używają LIKE operator są oceniane w taki sam sposób jak wyrażeń równości jako kryteria filtrowania. Jednak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażeń LIKE operator może obejmować zarówno literały i symbole wieloznaczne.  
  
 W poniższej tabeli opisano składnię wzorca `string`.  
  
|Symbol wieloznaczny|Opis|Przykład|  
|------------------------|-----------------|-------------|  
|%|Wszelkie `string` zero lub więcej znaków.|`title like '%computer%'`znajduje wszystkie tytuły z wyraz `"computer"` dowolne miejsce w tytule.|  
|_ (podkreślenie)|Dowolny pojedynczy znak.|`firstname like '_ean'`znajduje wszystkie cztery imiona z `"ean`, "przykład Dean lub Piotr.|  
|[ ]|Wszelkie jeden znak z określonego zakresu ([a-f]) lub zestawu ([abcdef]).|`lastname like '[C-P]arsen'`Wyszukuje nazwiska kończą się ciągiem "arsen", a począwszy od dowolny pojedynczy znak między C i P, takie jak Carsen lub JK.|  
|[^]|Dowolny znak spoza określonego zakresu ([^ a-f]) lub ustawić ([^ abcdef]).|`lastname like 'de[^l]%'`znajduje wszystkie nazwiska rozpoczyna się od "de" i nie dołączaj "l" jako następującą literę.|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Jak operator i klauzuli UCIECZKI nie można zastosować do `System.DateTime` lub `System.Guid` wartości.  
  
 Podobnie jak dopasowywania do wzorca obsługuje ASCII i Unicode. Wszystkie parametry są znaki ASCII, dopasowanie wzorca ASCII jest wykonywane. Jeśli co najmniej jeden z argumentów jest Unicode, wszystkie argumenty są konwertowane na Unicode i dopasowywanie do wzorca Unicode jest wykonywana. Gdy używasz Unicode o PODOBNYCH spacjami są istotne; jednak inne non-Unicode, spacjami nie są istotne. Składnia ciągu wzorca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest taka sama, jak te [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
 Wzorzec może zawierać zwykłe znaki oraz symbole wieloznaczne. Podczas dopasowywania do wzorca zwykłe znaki musi dokładnie pasować do znaków określony w znak `string`. Jednak symboli wieloznacznych można dopasować do dowolnych fragmentów ciągu znaków. Gdy jest używany z symbolami wieloznacznymi, LIKE operator jest bardziej elastyczna niż = i! = operatorów porównywania ciągów.  
  
> [!NOTE]
>  Jeśli zostanie rozpoczęta dla określonego dostawcy, może używać rozszerzeń specyficznego dla dostawcy. Jednak takie konstrukcje mogą być traktowane inaczej przez innych dostawców, np. SqlServer obsługuje [pierwszego do ostatniego] i [^ pierwszym i ostatnim] wzorców, jeśli pierwsza odpowiada dokładnie jeden znak między pierwszym i ostatnim i dokładnie jeden znak ostatnie dopasowań, który nie jest między pierwszym i ostatnim.  
  
### <a name="escape"></a>Escape  
 Za pomocą klauzuli ZWALNIAJĄCEJ, możesz wyszukać ciągów znaków, które obejmują jeden lub więcej specjalnych symboli wieloznacznych opisano w tabeli w poprzedniej sekcji. Załóżmy na przykład, kilka dokumentów obejmują literału "100%" w tytule i chcesz wyszukać dla wszystkich tych dokumentów. Ponieważ znaku procentu (%) jest symbolem wieloznacznym, musi wprowadzić go za pomocą [!INCLUDE[esql](../../../../../../includes/esql-md.md)] klauzuli ESCAPE, aby pomyślnie wykonać wyszukiwanie. Oto przykład tego filtru.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 W tym wyrażeniu wyszukiwania znaku wieloznacznego procentu (%), bezpośrednio po znaku wykrzyknika (!) jest traktowany jako literału, a nie jako symbolu wieloznacznego. Można użyć dowolnego znaku jako znak ucieczki, z wyjątkiem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] symboli wieloznacznych i kwadratu nawiasów (`[ ]`) znaków. W poprzednim przykładzie znakiem wykrzyknika (!) jest znak ucieczki.  
  
## <a name="example"></a>Przykład  
 Następujące dwa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania przy użyciu PODOBNYCH a operatory UCIECZKI do ustalenia, czy dany ciąg znaków pasuje do określonego wzorca. Pierwsze zapytanie szuka `Name` zaczynającym się od znaków `Down_`. To zapytanie używa opcji ANULOWANIA, ponieważ znak podkreślenia (`_`) jest symbol wieloznaczny. Bez użycia opcji ANULOWANIA, zapytanie będzie wyszukiwać dowolne `Name` wartości rozpoczynające się od słowa `Down` następuje dowolny pojedynczy znak niż znaku podkreślenia. Zapytania są oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
