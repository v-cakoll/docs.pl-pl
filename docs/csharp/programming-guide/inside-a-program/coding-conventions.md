---
title: C# Konwencje kodowania — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399736"
---
# <a name="c-coding-conventions-c-programming-guide"></a>konwencje kodowania C# (Przewodnik programowania w języku C#)

Konwencje kodowania służą następującym celom:  
  
- Tworzą spójny wygląd kodu, dzięki czemu czytelnicy mogą skupić się na zawartości, a nie na układzie.  
  
- Umożliwiają one czytelnikom szybciej zrozumieć kod, dokonując założeń na podstawie wcześniejszego doświadczenia.  
  
- Ułatwiają one kopiowanie, zmienianie i obsługa kodu.  
  
- Wykazują one C# najlepszych rozwiązań.  

Wskazówki w tym artykule są używane przez firmę Microsoft do tworzenia przykładów i dokumentacji.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa  
  
- W krótkich przykładach, które nie obejmują [przy użyciu dyrektyw,](../../language-reference/keywords/using-directive.md)użyj kwalifikacji przestrzeni nazw. Jeśli wiesz, że obszar nazw jest importowany domyślnie w projekcie, nie trzeba w pełni kwalifikować nazwy z tego obszaru nazw. Kwalifikowane nazwy mogą zostać przerwane po kropka (.), jeśli są one zbyt długie dla pojedynczego wiersza, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- Nie trzeba zmieniać nazwy obiektów, które zostały utworzone przy użyciu narzędzi projektanta programu Visual Studio, aby dopasować je do innych wytycznych.  
  
## <a name="layout-conventions"></a>Konwencje układu  

Dobry układ używa formatowania, aby podkreślić strukturę kodu i ułatwić odczytanie kodu. Przykłady i przykłady firmy Microsoft są zgodne z następującymi konwencjami:  
  
- Użyj domyślnych ustawień Edytora kodu (inteligentne wcięcia, czteroznakowe wcięcia, karty zapisane jako spacje). Aby uzyskać więcej informacji, zobacz [Opcje, Edytor tekstu, C#, Formatowanie](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
- Napisz tylko jedną instrukcję na wiersz.  
  
- Napisz tylko jedną deklarację na wiersz.  
  
- Jeśli wiersze kontynuacji nie są wcięte automatycznie, wcięcie ich jeden tabulator (cztery spacje).  
  
- Dodaj co najmniej jedną pustą linię między definicjami metod a definicjami właściwości.  
  
- Nawiasy służy do klauzul w wyrażeniu widoczne, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Konwencje komentowania  
  
- Umieść komentarz w osobnym wierszu, a nie na końcu wiersza kodu.  
  
- Rozpocznij tekst komentarza z literą wielkie.  
  
- Zakończ tekst komentarza kropką.  
  
- Wstaw jedną spcję między ogranicznikiem komentarza (//) a tekstem komentarza, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- Nie należy tworzyć sformatowanych bloków gwiazdek wokół komentarzy.  
  
## <a name="language-guidelines"></a>Wytyczne dotyczące języka  

W poniższych sekcjach opisano praktyki, które zespół C# następuje do przygotowania przykładów kodu i przykłady.  
  
### <a name="string-data-type"></a>Typ danych ciągu  
  
- Interpolacja [ciągów służy](../../language-reference/tokens/interpolated.md) do łączenia krótkich ciągów, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- Aby dołączać ciągi w pętlach, szczególnie podczas pracy z <xref:System.Text.StringBuilder> dużą ilością tekstu, należy użyć obiektu.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Jawnie wpisana zmienna lokalna  
  
- Użyj [niejawnego wpisywania](../classes-and-structs/implicitly-typed-local-variables.md) dla zmiennych lokalnych, gdy typ zmiennej jest oczywisty po prawej stronie przypisania lub gdy dokładny typ nie jest ważny.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- Nie należy używać [var,](../../language-reference/keywords/var.md) gdy typ nie jest widoczny po prawej stronie przypisania.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- Nie należy polegać na nazwę zmiennej, aby określić typ zmiennej. To może nie być poprawne.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- Unikaj używania `var` w miejsce [dynamicznego](../../language-reference/builtin-types/reference-types.md).  
  
- Użyj niejawnego pisania, aby określić typ zmiennej pętli w [pętli.](../../language-reference/keywords/for.md)  
  
     W poniższym przykładzie użyto `for` niejawnego wpisywania w instrukcji.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- Nie należy używać niejawnego pisania, aby określić typ zmiennej pętli w [pętlach foreach.](../../language-reference/keywords/foreach-in.md)

     W poniższym przykładzie użyto `foreach` jawnego wpisywania w instrukcji.

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > Należy uważać, aby nie przypadkowo zmienić typ elementu iterable kolekcji. Na przykład jest łatwe przełączenie <xref:System.Collections.IEnumerable?displayProperty=nameWithType> z `foreach` <xref:System.Linq.IQueryable?displayProperty=nameWithType> w instrukcji, która zmienia wykonanie kwerendy.

### <a name="unsigned-data-type"></a>Typ danych bez znaku  
  
Ogólnie rzecz `int` biorąc użyj zamiast niepodpisanych typów. Użycie `int` jest wspólne w całym języku C#, i łatwiej jest `int`wchodzić w interakcje z innymi bibliotekami podczas korzystania .  
  
### <a name="arrays"></a>Tablice  
  
Użyj zwięzłej składni podczas inicjowania tablic w wierszu deklaracji.  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Delegaty  
  
Składnia zwięzła służy do tworzenia wystąpień typu delegata.  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Blok try-catch i przy użyciu instrukcji obsługi wyjątków  
  
- Użyj instrukcji [try-catch](../../language-reference/keywords/try-catch.md) dla większości obsługi wyjątków.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- Uprość kod przy użyciu instrukcji C# [.](../../language-reference/keywords/using-statement.md) Jeśli masz [instrukcję try-finally,](../../language-reference/keywords/try-finally.md) w której `finally` jedynym kodem <xref:System.IDisposable.Dispose%2A> w bloku `using` jest wywołanie metody, należy użyć instrukcji zamiast tego.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>Operatorzy && i &#124;&#124;   
  
Aby uniknąć wyjątków i zwiększyć wydajność, [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) pomijając [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) niepotrzebne porównania, należy użyć zamiast i [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) zamiast [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) podczas wykonywania porównań, jak pokazano w poniższym przykładzie.  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Nowy operator  
  
- Użyj zwięzłej formy wystąpienia obiektu z niejawnym wpisywaniem, jak pokazano w poniższej deklaracji.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Poprzedni wiersz jest odpowiednikiem następującej deklaracji.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- Użyj inicjatorów obiektów, aby uprościć tworzenie obiektów.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Obsługa zdarzeń  
  
Jeśli definiujesz program obsługi zdarzeń, którego nie trzeba później usuwać, użyj wyrażenia lambda.  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statyczne elementy członkowskie  
  
Wywołaj [elementy statyczne](../../language-reference/keywords/static.md) przy użyciu nazwy klasy: *ClassName.StaticMember*. Ta praktyka sprawia, że kod jest bardziej czytelny, dzięki czemu dostęp statyczny jest przejrzysty.  Nie należy kwalifikować statyczny element członkowski zdefiniowany w klasie podstawowej o nazwie klasy pochodnej.  Podczas gdy ten kod kompiluje, czytelność kodu jest mylące, a kod może zostać przerwany w przyszłości, jeśli dodasz statyczny element członkowski o tej samej nazwie do klasy pochodnej.  
  
### <a name="linq-queries"></a>Zapytania LINQ  
  
- Użyj znaczących nazw dla zmiennych kwerend. Poniższy przykład `seattleCustomers` używa dla klientów, którzy znajdują się w Seattle.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Użyj aliasów, aby upewnić się, że nazwy właściwości typów anonimowych są poprawnie kapitalizowane przy użyciu wielkości liter Pascala.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- Zmień nazwy właściwości, gdy nazwy właściwości w wyniku będzie niejednoznaczny. Na przykład jeśli kwerenda zwraca nazwę klienta i identyfikator dystrybutora, `ID` zamiast pozostawiać je jako `Name` `Name` wynik, zmień ich nazwę, aby wyjaśnić, że jest to nazwa klienta i `ID` jest identyfikatorem dystrybutora.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- Użyj niejawnego wpisywania w deklaracji zmiennych zapytania i zmiennych zakresu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Wyrównaj klauzule zapytania zgodnie z klauzulą [from,](../../language-reference/keywords/from-clause.md) jak pokazano w poprzednich przykładach.  
  
- Użyj [where](../../language-reference/keywords/where-clause.md) klauzule przed innymi klauzulami kwerendy, aby upewnić się, że później klauzule kwerendy działają na zredukowanym, filtrowanym zestawie danych.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- Użyj `from` wielu klauzul zamiast [join](../../language-reference/keywords/join-clause.md) klauzuli, aby uzyskać dostęp do kolekcji wewnętrznych. Na przykład kolekcja `Student` obiektów może zawierać kolekcję wyników testów. Po wykonaniu następującego zapytania zwraca każdy wynik, który jest powyżej 90, wraz z nazwiskiem studenta, który otrzymał wynik.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Zabezpieczenia  

Postępuj zgodnie z wytycznymi w [Wytycznych bezpiecznego kodowania](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Zobacz też

- [Visual Basic — Konwencje kodowania](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [Wytyczne dotyczące bezpiecznego programowania](../../../standard/security/secure-coding-guidelines.md)
