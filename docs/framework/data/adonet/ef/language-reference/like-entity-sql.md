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
ms.workload: dotnet
ms.openlocfilehash: f7118637671dbc18c1385b71cc492b5307a377c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="like-entity-sql"></a><span data-ttu-id="865fa-102">Podobnie jak (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="865fa-102">LIKE (Entity SQL)</span></span>
<span data-ttu-id="865fa-103">Określa, czy określony znak `String` jest zgodna z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="865fa-103">Determines whether a specific character `String` matches a specified pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="865fa-104">Syntax</span></span>  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a><span data-ttu-id="865fa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="865fa-105">Arguments</span></span>  
 `match`  
 <span data-ttu-id="865fa-106">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Wyrażenie obliczane do `String`.</span><span class="sxs-lookup"><span data-stu-id="865fa-106">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression that evaluates to a `String`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="865fa-107">Wzorzec do dopasowania do określonego `String`.</span><span class="sxs-lookup"><span data-stu-id="865fa-107">A pattern to match to the specified `String`.</span></span>  
  
 `escape`  
 <span data-ttu-id="865fa-108">Znak ucieczki.</span><span class="sxs-lookup"><span data-stu-id="865fa-108">An escape character.</span></span>  
  
 <span data-ttu-id="865fa-109">NIE</span><span class="sxs-lookup"><span data-stu-id="865fa-109">NOT</span></span>  
 <span data-ttu-id="865fa-110">Określa, czy można zanegowane wynik LIKE.</span><span class="sxs-lookup"><span data-stu-id="865fa-110">Specifies that the result of LIKE be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="865fa-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="865fa-111">Return Value</span></span>  
 <span data-ttu-id="865fa-112">`true`Jeśli `string` zgodny z wzorcem; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="865fa-112">`true` if the `string` matches the pattern; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="865fa-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="865fa-113">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="865fa-114">wyrażeń, które używają LIKE operator są oceniane w taki sam sposób jak wyrażeń równości jako kryteria filtrowania.</span><span class="sxs-lookup"><span data-stu-id="865fa-114"> expressions that use the LIKE operator are evaluated in much the same way as expressions that use equality as the filter criteria.</span></span> <span data-ttu-id="865fa-115">Jednak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażeń LIKE operator może obejmować zarówno literały i symbole wieloznaczne.</span><span class="sxs-lookup"><span data-stu-id="865fa-115">However, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator can include both literals and wildcard characters.</span></span>  
  
 <span data-ttu-id="865fa-116">W poniższej tabeli opisano składnię wzorca `string`.</span><span class="sxs-lookup"><span data-stu-id="865fa-116">The following table describes the syntax of the pattern `string`.</span></span>  
  
|<span data-ttu-id="865fa-117">Symbol wieloznaczny</span><span class="sxs-lookup"><span data-stu-id="865fa-117">Wildcard Character</span></span>|<span data-ttu-id="865fa-118">Opis</span><span class="sxs-lookup"><span data-stu-id="865fa-118">Description</span></span>|<span data-ttu-id="865fa-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="865fa-119">Example</span></span>|  
|------------------------|-----------------|-------------|  
|%|<span data-ttu-id="865fa-120">Wszelkie `string` zero lub więcej znaków.</span><span class="sxs-lookup"><span data-stu-id="865fa-120">Any `string` of zero or more characters.</span></span>|<span data-ttu-id="865fa-121">`title like '%computer%'`znajduje wszystkie tytuły z wyraz `"computer"` dowolne miejsce w tytule.</span><span class="sxs-lookup"><span data-stu-id="865fa-121">`title like '%computer%'` finds all titles with the word `"computer"` anywhere in the title.</span></span>|  
|<span data-ttu-id="865fa-122">_ (podkreślenie)</span><span class="sxs-lookup"><span data-stu-id="865fa-122">_ (underscore)</span></span>|<span data-ttu-id="865fa-123">Dowolny pojedynczy znak.</span><span class="sxs-lookup"><span data-stu-id="865fa-123">Any single character.</span></span>|<span data-ttu-id="865fa-124">`firstname like '_ean'`znajduje wszystkie cztery imiona z `"ean`, "przykład Dean lub Piotr.</span><span class="sxs-lookup"><span data-stu-id="865fa-124">`firstname like '_ean'` finds all four-letter first names that end with `"ean`," such as Dean or Sean.</span></span>|  
|<span data-ttu-id="865fa-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="865fa-125">[ ]</span></span>|<span data-ttu-id="865fa-126">Wszelkie jeden znak z określonego zakresu ([a-f]) lub zestawu ([abcdef]).</span><span class="sxs-lookup"><span data-stu-id="865fa-126">Any single character in the specified range ([a-f]) or set ([abcdef]).</span></span>|<span data-ttu-id="865fa-127">`lastname like '[C-P]arsen'`Wyszukuje nazwiska kończą się ciągiem "arsen", a począwszy od dowolny pojedynczy znak między C i P, takie jak Carsen lub JK.</span><span class="sxs-lookup"><span data-stu-id="865fa-127">`lastname like '[C-P]arsen'` finds last names ending with "arsen" and beginning with any single character between C and P, such as Carsen or Larsen.</span></span>|  
|<span data-ttu-id="865fa-128">[^]</span><span class="sxs-lookup"><span data-stu-id="865fa-128">[^]</span></span>|<span data-ttu-id="865fa-129">Dowolny znak spoza określonego zakresu ([^ a-f]) lub ustawić ([^ abcdef]).</span><span class="sxs-lookup"><span data-stu-id="865fa-129">Any single character not in the specified range ([^a-f]) or set ([^abcdef]).</span></span>|<span data-ttu-id="865fa-130">`lastname like 'de[^l]%'`znajduje wszystkie nazwiska rozpoczyna się od "de" i nie dołączaj "l" jako następującą literę.</span><span class="sxs-lookup"><span data-stu-id="865fa-130">`lastname like 'de[^l]%'` finds all last names that begin with "de" and do not include "l" as the following letter.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="865fa-131">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Jak operator i klauzuli UCIECZKI nie można zastosować do `System.DateTime` lub `System.Guid` wartości.</span><span class="sxs-lookup"><span data-stu-id="865fa-131">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE operator and ESCAPE clause cannot be applied to `System.DateTime` or `System.Guid` values.</span></span>  
  
 <span data-ttu-id="865fa-132">Podobnie jak dopasowywania do wzorca obsługuje ASCII i Unicode.</span><span class="sxs-lookup"><span data-stu-id="865fa-132">LIKE supports ASCII pattern matching and Unicode pattern matching.</span></span> <span data-ttu-id="865fa-133">Wszystkie parametry są znaki ASCII, dopasowanie wzorca ASCII jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="865fa-133">When all parameters are ASCII characters, ASCII pattern matching is performed.</span></span> <span data-ttu-id="865fa-134">Jeśli co najmniej jeden z argumentów jest Unicode, wszystkie argumenty są konwertowane na Unicode i dopasowywanie do wzorca Unicode jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="865fa-134">If one or more of the arguments are Unicode, all arguments are converted to Unicode and Unicode pattern matching is performed.</span></span> <span data-ttu-id="865fa-135">Gdy używasz Unicode o PODOBNYCH spacjami są istotne; jednak inne non-Unicode, spacjami nie są istotne.</span><span class="sxs-lookup"><span data-stu-id="865fa-135">When you use Unicode with LIKE, trailing blanks are significant; however, for non-Unicode, trailing blanks are not significant.</span></span> <span data-ttu-id="865fa-136">Składnia ciągu wzorca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest taka sama, jak te [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="865fa-136">The pattern string syntax of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is the same as that of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="865fa-137">Wzorzec może zawierać zwykłe znaki oraz symbole wieloznaczne.</span><span class="sxs-lookup"><span data-stu-id="865fa-137">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="865fa-138">Podczas dopasowywania do wzorca zwykłe znaki musi dokładnie pasować do znaków określony w znak `string`.</span><span class="sxs-lookup"><span data-stu-id="865fa-138">During pattern matching, regular characters must exactly match the characters specified in the character `string`.</span></span> <span data-ttu-id="865fa-139">Jednak symboli wieloznacznych można dopasować do dowolnych fragmentów ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="865fa-139">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="865fa-140">Gdy jest używany z symbolami wieloznacznymi, LIKE operator jest bardziej elastyczna niż = i! = operatorów porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="865fa-140">When it is used with wildcard characters, the LIKE operator is more flexible than the = and != string comparison operators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="865fa-141">Jeśli zostanie rozpoczęta dla określonego dostawcy, może używać rozszerzeń specyficznego dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="865fa-141">You may use provider-specific extensions if you target a specific provider.</span></span> <span data-ttu-id="865fa-142">Jednak takie konstrukcje mogą być traktowane inaczej przez innych dostawców, np.</span><span class="sxs-lookup"><span data-stu-id="865fa-142">However, such constructs may be treated differently by other providers, for example.</span></span> <span data-ttu-id="865fa-143">SqlServer obsługuje [pierwszego do ostatniego] i [^ pierwszym i ostatnim] wzorców, jeśli pierwsza odpowiada dokładnie jeden znak między pierwszym i ostatnim i dokładnie jeden znak ostatnie dopasowań, który nie jest między pierwszym i ostatnim.</span><span class="sxs-lookup"><span data-stu-id="865fa-143">SqlServer supports [first-last] and [^first-last] patterns where the former matches exactly one character between first and last, and the latter matches exactly one character that is not between first and last.</span></span>  
  
### <a name="escape"></a><span data-ttu-id="865fa-144">Escape</span><span class="sxs-lookup"><span data-stu-id="865fa-144">Escape</span></span>  
 <span data-ttu-id="865fa-145">Za pomocą klauzuli ZWALNIAJĄCEJ, możesz wyszukać ciągów znaków, które obejmują jeden lub więcej specjalnych symboli wieloznacznych opisano w tabeli w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="865fa-145">By using the ESCAPE clause, you can search for character strings that include one or more of the special wildcard characters described in the table in the previous section.</span></span> <span data-ttu-id="865fa-146">Załóżmy na przykład, kilka dokumentów obejmują literału "100%" w tytule i chcesz wyszukać dla wszystkich tych dokumentów.</span><span class="sxs-lookup"><span data-stu-id="865fa-146">For example, assume several documents include the literal "100%" in the title and you want to search for all of those documents.</span></span> <span data-ttu-id="865fa-147">Ponieważ znaku procentu (%) jest symbolem wieloznacznym, musi wprowadzić go za pomocą [!INCLUDE[esql](../../../../../../includes/esql-md.md)] klauzuli ESCAPE, aby pomyślnie wykonać wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="865fa-147">Because the percent (%) character is a wildcard character, you must escape it using the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE clause to successfully execute the search.</span></span> <span data-ttu-id="865fa-148">Oto przykład tego filtru.</span><span class="sxs-lookup"><span data-stu-id="865fa-148">The following is an example of this filter.</span></span>  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 <span data-ttu-id="865fa-149">W tym wyrażeniu wyszukiwania znaku wieloznacznego procentu (%), bezpośrednio po znaku wykrzyknika (!) jest traktowany jako literału, a nie jako symbolu wieloznacznego.</span><span class="sxs-lookup"><span data-stu-id="865fa-149">In this search expression, the percent wildcard character (%) immediately following the exclamation point character (!) is treated as a literal, instead of as a wildcard character.</span></span> <span data-ttu-id="865fa-150">Można użyć dowolnego znaku jako znak ucieczki, z wyjątkiem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] symboli wieloznacznych i kwadratu nawiasów (`[ ]`) znaków.</span><span class="sxs-lookup"><span data-stu-id="865fa-150">You can use any character as an escape character except for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wildcard characters and the square bracket (`[ ]`) characters.</span></span> <span data-ttu-id="865fa-151">W poprzednim przykładzie znakiem wykrzyknika (!) jest znak ucieczki.</span><span class="sxs-lookup"><span data-stu-id="865fa-151">In the previous example, the exclamation point (!) character is the escape character.</span></span>  
  
## <a name="example"></a><span data-ttu-id="865fa-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="865fa-152">Example</span></span>  
 <span data-ttu-id="865fa-153">Następujące dwa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania przy użyciu PODOBNYCH a operatory UCIECZKI do ustalenia, czy dany ciąg znaków pasuje do określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="865fa-153">The following two [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries use the LIKE and ESCAPE operators to determine whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="865fa-154">Pierwsze zapytanie szuka `Name` zaczynającym się od znaków `Down_`.</span><span class="sxs-lookup"><span data-stu-id="865fa-154">The first query searches for the `Name` that starts with the characters `Down_`.</span></span> <span data-ttu-id="865fa-155">To zapytanie używa opcji ANULOWANIA, ponieważ znak podkreślenia (`_`) jest symbol wieloznaczny.</span><span class="sxs-lookup"><span data-stu-id="865fa-155">This query uses the ESCAPE option because the underscore (`_`) is a wildcard character.</span></span> <span data-ttu-id="865fa-156">Bez użycia opcji ANULOWANIA, zapytanie będzie wyszukiwać dowolne `Name` wartości rozpoczynające się od słowa `Down` następuje dowolny pojedynczy znak niż znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="865fa-156">Without specifying the ESCAPE option, the query would search for any `Name` values that start with the word `Down` followed by any single character other than the underscore character.</span></span> <span data-ttu-id="865fa-157">Zapytania są oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="865fa-157">The queries are based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="865fa-158">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="865fa-158">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="865fa-159">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="865fa-159">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="865fa-160">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="865fa-160">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a><span data-ttu-id="865fa-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="865fa-161">See Also</span></span>  
 [<span data-ttu-id="865fa-162">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="865fa-162">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
