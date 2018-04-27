---
title: konwencje kodowania C# (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 697c3df3d418c57d58c42dc3cfb900de02146c80
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="c-coding-conventions-c-programming-guide"></a>konwencje kodowania C# (Przewodnik programowania w języku C#)
 Konwencje kodowania służą do następujących celów:  
  
-   Tak, aby czytelnicy mogą skupić się na zawartości, nie układu tworzenia spójny wygląd w kodzie.  
  
-   Umożliwiają one czytników zrozumienie kod szybciej przez założenie na podstawie doświadczeń w poprzedniej.  
  
-   Ułatwiają one kopiowanie, zmienianie i utrzymywanie kodu.  
  
-   Pokazują one C# najlepszych rozwiązań.  

 Wskazówki zawarte w tym temacie są używane przez firmę Microsoft do opracowywania przykłady i dokumentacja.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa  
  
-   W przykładach krótkie, które nie zawierają [przy użyciu dyrektyw](../../../csharp/language-reference/keywords/using-directive.md), użyj kwalifikacji przestrzeni nazw. Jeśli wiesz, że przestrzeń nazw jest importowany domyślnie w projekcie, nie masz do pełnej kwalifikacji nazwy z tego obszaru nazw. Kwalifikowane nazwy może być przerwane po kropkę (.) Jeśli są zbyt długi i jednym wierszu, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   Nie trzeba zmieniać nazwy obiektów, które zostały utworzone przy użyciu narzędzia projektanta programu Visual Studio, aby je dopasować pozostałych wskazówek.  
  
## <a name="layout-conventions"></a>Konwencje układu  
 Dobrym układu używa formatowania, aby wyróżnić struktura kodu i czytelność kodu. Przykłady i przykłady firmy Microsoft jest zgodna z następujących konwencji:  
  
-   Użyj domyślnych ustawień edytora kodu (inteligentne wcięcie, wcięcia czterech znaków, karty zapisane jako spacji). Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstu, C#, formatowanie](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
-   Napisać tylko jednej instrukcji w jednym wierszu.  
  
-   Napisać tylko jedna deklaracja w wierszu.  
  
-   Jeśli kontynuacji wierszy nie są przeznaczone automatycznie, wcięcie ich jedną pozycję tabulatora (czterech spacji).  
  
-   Dodaj co najmniej jeden pusty wiersz między definicji metody i właściwości definicji.  
  
-   Użyj nawiasów, aby klauzule w wyrażeniu oczywista, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Konwencje komentowania  
  
-   Umieść komentarz w osobnym wierszu, a nie na końcu wiersza kodu.  
  
-   Rozpocznij tekst komentarza na wielką literę.  
  
-   Tekst komentarza zakończenia kropką.  
  
-   Wstawienia jedną spację między ogranicznik komentarza (/ /), a tekst komentarza, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   Nie należy tworzyć sformatowany bloki gwiazdek wokół komentarze.  
  
## <a name="language-guidelines"></a>Wytyczne dotyczące języka  
 W poniższych sekcjach opisano wskazówki, które umożliwiają przygotowanie przykłady kodu i przykłady zespołu C#.  
  
### <a name="string-data-type"></a>Typ danych ciągu  
  
-   Użyj [ciągu interpolacji](../../language-reference/tokens/interpolated.md) do ciągów krótkich, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   Aby dołączyć ciągów w pętli, szczególnie w przypadku pracy z dużą ilością tekstu, należy użyć <xref:System.Text.StringBuilder> obiektu.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Jawnie wpisana zmienna lokalna  
  
-   Użyj [niejawne wpisując](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) dla zmiennych lokalnych, gdy typ zmiennej jest widoczne z prawej strony przypisania lub gdy dokładny typ nie jest istotna.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   Nie używaj [var](../../../csharp/language-reference/keywords/var.md) gdy typ nie jest widoczna z prawej strony przypisania.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   Nie należy polegać na nazwę zmiennej, aby określić typ zmiennej. Może nie być poprawne.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   Unikaj używania `var` zamiast [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md).  
  
-   Umożliwia wpisanie niejawne określają typ zmiennej pętli w [dla](../../../csharp/language-reference/keywords/for.md) i [foreach](../../../csharp/language-reference/keywords/foreach-in.md) pętli.  
  
     W poniższym przykładzie użyto niejawne wpisanie `for` instrukcji.  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     W poniższym przykładzie użyto niejawne wpisanie `foreach` instrukcji.  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a>Typ danych bez znaku  
  
-   Ogólnie rzecz biorąc, użyj `int` zamiast typy bez znaku. Korzystanie z `int` jest typowe w C# i możliwe jest łatwiejsze do interakcji z innych bibliotek, korzystając z `int`.  
  
### <a name="arrays"></a>Tablice  
  
-   Podczas inicjowania tablic w wierszu deklaracji, należy użyć składni zwięzły.  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Delegaty  
  
-   Umożliwia utworzenie wystąpienia typu delegata zwięzłą składnią.  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Blok try-catch i przy użyciu instrukcji obsługi wyjątków  
  
-   Użyj [try-catch](../../../csharp/language-reference/keywords/try-catch.md) instrukcji dla większości obsługi wyjątków.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   Uprościć kod przy użyciu języka C# [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md). Jeśli masz [try-finally](../../../csharp/language-reference/keywords/try-finally.md) instrukcji, w którym tylko kod w `finally` blok jest wywołanie <xref:System.IDisposable.Dispose%2A> metody, użyj `using` instrukcji zamiast tego.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>& & i &#124; &#124; operatory  
  
-   Aby uniknąć wyjątków i zwiększyć wydajność przez pominięcie niepotrzebnych porównań, użyj [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) zamiast [ & ](../../../csharp/language-reference/operators/and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)zamiast [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) po wykonaniu porównań, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Nowy operator  
  
-   Formularz zwięzły konkretyzacji obiektu w trakcie pisania niejawne, jak pokazano w poniższych deklaracji.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Następujące oświadczenie odpowiada poprzedniego wiersza.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   Inicjatory obiektów można użyć, aby uprościć tworzenie obiektów.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Obsługa zdarzeń  
  
-   Jeśli definiujesz program obsługi zdarzeń, które trzeba usunąć później, należy użyć wyrażenia lambda.  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statyczne elementy członkowskie  
  
-   Wywołanie [statycznych](../../../csharp/language-reference/keywords/static.md) elementy członkowskie przy użyciu nazwy klasy: *ClassName.StaticMember*. Takie rozwiązanie sprawia, że kod jest bardziej przejrzysta dokonując statycznych dostęp, wyczyść.  Nie można rozwiązać członka statycznego zdefiniowana w klasie podstawowej z nazwą klasy pochodnej.  Kompiluje kod, jest mylące czytelność kodu i kodu mogą być dzielone w przyszłości, jeśli dodasz statyczny element członkowski o takiej samej nazwie do klasy pochodnej.  
  
### <a name="linq-queries"></a>Zapytania LINQ  
  
-   Użyj łatwy do rozpoznania nazwy zmiennych zapytania. W poniższym przykładzie użyto `seattleCustomers` dla klientów, którzy znajdują się w Seattle.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Upewnij się, że nazwy właściwości typu anonimowego są poprawnie pisany wielkimi literami, przy użyciu Pascal za pomocą aliasów wielkości liter.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłoby niejednoznaczne. Na przykład, jeśli zapytanie zwraca klienta nazwa i identyfikator dystrybutora, zamiast zostawiać je jako `Name` i `ID` w wyniku, zmień ich wyjaśnienia, że `Name` nazywa się klient, oraz `ID` jest Identyfikatorem dystrybutora.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   Użycie niejawne, wpisując w deklaracji zmiennych zapytania i zmiennych zakresu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Dopasuj klauzule zapytań w obszarze [z](../../../csharp/language-reference/keywords/from-clause.md) klauzuli, jak pokazano w poprzednich przykładach.  
  
-   Użyj [gdzie](../../../csharp/language-reference/keywords/where-clause.md) klauzule przed inne klauzule zapytań, aby upewnić się, że nowsze klauzule zapytań działają na zmniejszenie, filtrowane zestawu danych.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   Używanych jest wiele `from` klauzule zamiast [sprzężenia](../../../csharp/language-reference/keywords/join-clause.md) klauzuli można uzyskać dostępu do kolekcji wewnętrznej. Na przykład kolekcja `Student` każdego obiekty mogą zawierać kolekcji wyniki testów. Po wykonaniu następujące zapytanie zwraca każdego wynik, który jest ponad 90, wraz z nazwisko studentów, który otrzymał wynik.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Zabezpieczenia  
 Postępuj zgodnie z wytycznymi w [Secure wytyczne kodowania](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Basic — konwencje kodowania](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 [Wytyczne dotyczące bezpiecznego programowania](../../../standard/security/secure-coding-guidelines.md)
