---
title: C#Konwencje kodowania C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 42e1814af38fa442255f6da79fb4862ce3d0f361
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423207"
---
# <a name="c-coding-conventions-c-programming-guide"></a>konwencje kodowania C# (Przewodnik programowania w języku C#)
 Konwencje kodowania mają następujące cele:  
  
- Tworzą one spójny wygląd kodu, dzięki czemu czytelnicy mogą skupić się na zawartości, a nie w układzie.  
  
- Umożliwiają one czytelnikom szybsze zrozumienie kodu dzięki założeniu założeń na podstawie poprzedniego środowiska.  
  
- Ułatwiają one kopiowanie, zmienianie i utrzymywanie kodu.  
  
- Przedstawiają C# one najlepsze rozwiązania.  

 Wskazówki zawarte w tym temacie są używane przez firmę Microsoft do tworzenia przykładów i dokumentacji.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa  
  
- W krótkich przykładach, które nie obejmują [dyrektywy using](../../language-reference/keywords/using-directive.md), należy używać kwalifikacji przestrzeni nazw. Jeśli wiesz, że przestrzeń nazw jest domyślnie importowana w projekcie, nie musisz w pełni kwalifikować nazw z tej przestrzeni nazw. Kwalifikowane nazwy mogą być uszkodzone po kropce (.), jeśli są zbyt długie dla pojedynczego wiersza, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- Nie trzeba zmieniać nazw obiektów, które zostały utworzone przy użyciu narzędzi projektanta programu Visual Studio, aby dopasować je do innych wytycznych.  
  
## <a name="layout-conventions"></a>Konwencje układu  
 Dobry układ używa formatowania, aby wyróżnić strukturę kodu i ułatwić odczytywanie kodu. Przykłady i próbki firmy Microsoft są zgodne z następującymi konwencjami:  
  
- Użyj domyślnych ustawień edytora kodu (inteligentne wcięcia, cztery znaki wcięcia, karty zapisane jako spacje). Aby uzyskać więcej informacji, zobacz [Opcje, Edytor tekstu C#, formatowanie](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
- Napisz tylko jedną instrukcję na wiersz.  
  
- Napisz tylko jedną deklarację na wiersz.  
  
- Jeśli linie kontynuacji nie mają wcięcia automatycznie, Zwiększ wcięcie z jednego tabulatora (cztery spacje).  
  
- Dodaj co najmniej jeden pusty wiersz między definicjami metod i definicjami właściwości.  
  
- Użyj nawiasów, aby tworzyć klauzule w wyrażeniu, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Konwencje komentowania  
  
- Umieść komentarz w osobnym wierszu, a nie na końcu wiersza kodu.  
  
- Zacznij komentować tekst, używając wielkiej litery.  
  
- Koniec tekstu komentarza z kropką.  
  
- Wstaw jedną spację między ogranicznikiem komentarza (//) i tekstem komentarza, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- Nie twórz sformatowanych bloków gwiazdek wokół komentarzy.  
  
## <a name="language-guidelines"></a>Wytyczne dotyczące języka  
 W poniższych sekcjach opisano sposób, C# w jaki zespół postępuje zgodnie z przygotowaniem przykładów i przykładów kodu.  
  
### <a name="string-data-type"></a>Typ danych ciągu  
  
- Użyj [interpolacji ciągów](../../language-reference/tokens/interpolated.md) , aby połączyć krótkie ciągi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- Aby dołączyć ciągi w pętlach, szczególnie podczas pracy z dużymi ilościami tekstu, użyj obiektu <xref:System.Text.StringBuilder>.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Jawnie wpisana zmienna lokalna  
  
- Użyj [niejawnego wpisywania](../classes-and-structs/implicitly-typed-local-variables.md) zmiennych lokalnych, gdy typ zmiennej jest oczywisty z prawej strony przypisania lub jeśli dokładny typ nie jest ważny.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- Nie należy używać [var](../../language-reference/keywords/var.md) , gdy typ nie jest widoczny po prawej stronie przypisania.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- Nie należy polegać na nazwie zmiennej, aby określić typ zmiennej. Może nie być poprawna.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- Unikaj stosowania `var` zamiast [dynamicznych](../../language-reference/builtin-types/reference-types.md).  
  
- Użyj niejawnego wpisywania, aby określić typ zmiennej pętli w pętlach [for](../../language-reference/keywords/for.md) i [foreach](../../language-reference/keywords/foreach-in.md) .  
  
     Poniższy przykład używa niejawnego wpisywania w instrukcji `for`.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
     Poniższy przykład używa niejawnego wpisywania w instrukcji `foreach`.  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a>Typ danych bez znaku  
  
- Ogólnie rzecz biorąc, użyj `int`, a nie niepodpisanych typów. Korzystanie z `int` jest wspólne w całym C#systemie i ułatwia korzystanie z innych bibliotek przy użyciu `int`.  
  
### <a name="arrays"></a>Tablice  
  
- Użyj zwięzłej składni podczas inicjowania tablic w wierszu deklaracji.  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Delegaty  
  
- Użyj zwięzłej składni, aby utworzyć wystąpienia typu delegata.  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Blok try-catch i przy użyciu instrukcji obsługi wyjątków  
  
- Użyj instrukcji [try-catch](../../language-reference/keywords/try-catch.md) dla większości obsługi wyjątków.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- Uprość kod przy użyciu C# [instrukcji using](../../language-reference/keywords/using-statement.md). Jeśli masz instrukcję [try-finally](../../language-reference/keywords/try-finally.md) , w której jedyny kod w bloku `finally` jest wywołaniem metody <xref:System.IDisposable.Dispose%2A>, zamiast tego należy użyć instrukcji `using`.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>& & i &#124; &#124; operatory  
  
- Aby uniknąć wyjątków i zwiększyć wydajność przez pominięcie niepotrzebnych porównań [](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) , użyj&&[](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) zamiast&[ &#124; ](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) i zamiast [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) przeprowadzania porównań, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Nowy operator  
  
- Użyj zwięzłej formy tworzenia wystąpień obiektów z niejawnym wpisywaniem, jak pokazano w poniższej deklaracji.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Poprzedni wiersz jest równoważny z następującą deklaracją.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- Użyj inicjatorów obiektów, aby uprościć tworzenie obiektów.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Obsługa zdarzeń  
  
- W przypadku definiowania programu obsługi zdarzeń, którego nie trzeba później usuwać, należy użyć wyrażenia lambda.  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statyczne elementy członkowskie  
  
- Wywołaj [statyczne](../../language-reference/keywords/static.md) elementy członkowskie przy użyciu nazwy klasy: *ClassName. StaticMember*. Dzięki temu kod jest bardziej czytelny, co oznacza, że statyczny dostęp jest czyszczony.  Nie kwalifikuj statycznej składowej zdefiniowanej w klasie bazowej z nazwą klasy pochodnej.  Podczas kompilowania kodu, czytelność kodu jest myląca, a kod może ulec przerwie w przyszłości, jeśli dodasz statyczną składową o tej samej nazwie do klasy pochodnej.  
  
### <a name="linq-queries"></a>Zapytania LINQ  
  
- Użyj znaczących nazw zmiennych zapytania. Poniższy przykład używa `seattleCustomers` dla klientów, którzy znajdują się w Seattle.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Użyj aliasów, aby upewnić się, że nazwy właściwości typów anonimowych są prawidłowo pisane wielkimi literami przy użyciu wielkości liter w Pascalu.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłyby niejednoznaczne. Na przykład, jeśli zapytanie zwróci nazwę klienta i identyfikator dystrybutora, zamiast opuszczania ich jako `Name` i `ID` w wyniku, należy zmienić ich nazwy, aby wyjaśnić, że `Name` jest nazwą klienta, a `ID` jest IDENTYFIKATORem dystrybutora.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- Użyj niejawnego wpisywania w deklaracji zmiennych zapytania i zmiennych zakresów.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Wyrównaj klauzule kwerendy pod klauzulą [from](../../language-reference/keywords/from-clause.md) , jak pokazano w poprzednich przykładach.  
  
- Użyj klauzul [WHERE](../../language-reference/keywords/where-clause.md) przed innymi klauzulami zapytania, aby upewnić się, że późniejsze klauzule zapytań działają na zmniejszonym, filtrowanym zestawie danych.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- Do uzyskiwania dostępu do kolekcji wewnętrznych używaj wielu klauzul `from` zamiast klauzuli [Join](../../language-reference/keywords/join-clause.md) . Na przykład kolekcja obiektów `Student` może zawierać kolekcję wyników testu. Gdy wykonywane jest następujące zapytanie, zwraca każdy wynik o wartości ponad 90, a także nazwisko studenta, który otrzymał wynik.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Zabezpieczenia  
 Postępuj zgodnie z wytycznymi w temacie [zasady bezpiecznego kodowania](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Zobacz także

- [Visual Basic konwencji kodowania](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [Wytyczne dotyczące bezpiecznego programowania](../../../standard/security/secure-coding-guidelines.md)
