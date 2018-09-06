---
title: konwencje kodowania C# (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 430cf3f1bc5e0b5ebe1a05530059516f36a473a1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43805120"
---
# <a name="c-coding-conventions-c-programming-guide"></a>konwencje kodowania C# (Przewodnik programowania w języku C#)
 Konwencje kodowania służą do następujących celów:  
  
-   Tworzą spójnego wyglądu w kodzie, dzięki czemu czytelnicy można skupić się na treści, a nie na układzie.  
  
-   Umożliwiają one odbiorcy zrozumieć kod szybciej, wprowadzając założenia na podstawie poprzednich doświadczeń.  
  
-   Ułatwiają one, kopiowanie, zmienianie i utrzymanie kodu.  
  
-   Pokazują one języka C# najlepszych rozwiązań.  

 Wskazówki zawarte w tym temacie są używane przez firmę Microsoft do tworzenia, przykłady i dokumentację.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa  
  
-   W przykładach krótki, które nie zawierają [dyrektywy using](../../../csharp/language-reference/keywords/using-directive.md), użyj kwalifikacji przestrzeni nazw. Jeśli wiesz, że przestrzeń nazw jest importowana domyślnie w projekcie, nie masz do pełnej kwalifikacji nazwy z tego obszaru nazw. Kwalifikowane nazwy może być uszkodzone po pojedynczego znaku kropki (.) są zbyt długi dla pojedynczego wiersza, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   Nie masz zmiany nazw obiektów, które zostały utworzone przy użyciu narzędzia projektanta programu Visual Studio, aby je dopasować przejść do pozostałych wskazówek.  
  
## <a name="layout-conventions"></a>Konwencje układu  
 Układ dobre używa formatowania do podkreślić strukturę kodu i czytelność kodu. Przykłady firmy Microsoft i przykłady są zgodne z następujących konwencji:  
  
-   Użyj domyślnych ustawień edytora kodu (inteligentne tworzenie wcięć, wcięcia Czteroznakowy kartach, zapisane jako miejsca do magazynowania). Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstu, C#, formatowanie](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
-   Zapis tylko jednej instrukcji na wiersz.  
  
-   Zapis tylko jednej deklaracji na wiersz.  
  
-   Jeśli wierszy kontynuacji nie są przeznaczone automatycznie, wcięcie ich jedną pozycję tabulatora (czterech spacji).  
  
-   Dodaj co najmniej jeden pusty wiersz między definicje metod i definicjach właściwości.  
  
-   Użyj nawiasów, aby wprowadzić klauzule w wyrażeniu oczywista, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Konwencje komentowania  
  
-   Umieść komentarz w osobnym wierszu, a nie na końcu wiersza kodu.  
  
-   Rozpocznij tekst komentarza wielką literą.  
  
-   Tekst komentarza zakończenia kropką.  
  
-   Wstaw jedną spację między ogranicznik komentarza (/ /) i tekst komentarza, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   Nie należy tworzyć sformatowanymi blokami ani gwiazdkami wokół komentarzy.  
  
## <a name="language-guidelines"></a>Wytyczne dotyczące języka  
 W poniższych sekcjach opisano rozwiązania, aby przygotować przykłady kodu i przykłady z zespołu C#.  
  
### <a name="string-data-type"></a>Typ danych ciągu  
  
-   Użyj [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) do łączenia krótkich ciągów, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   Aby dołączyć ciągi w pętli, szczególnie w przypadku, gdy pracujesz z dużych ilości tekstu, należy użyć <xref:System.Text.StringBuilder> obiektu.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Jawnie wpisana zmienna lokalna  
  
-   Użyj [niejawnego wpisywania](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) dla zmiennych lokalnych, gdy typ zmiennej jest oczywisty z prawej strony przypisania lub gdy dokładny typ nie jest istotna.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   Nie używaj [var](../../../csharp/language-reference/keywords/var.md) gdy typ nie jest jasne, z prawej strony przypisania.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   Nie należy polegać na nazwę zmiennej, aby określić typ zmiennej. Być może nie być poprawne.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   Unikaj stosowania `var` zamiast [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md).  
  
-   Użyć niejawnego wpisywania, aby określić typ zmiennej pętli w [dla](../../../csharp/language-reference/keywords/for.md) i [foreach](../../../csharp/language-reference/keywords/foreach-in.md) pętli.  
  
     W poniższym przykładzie użyto niejawnego wpisywania w `for` instrukcji.  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     W poniższym przykładzie użyto niejawnego wpisywania w `foreach` instrukcji.  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a>Typ danych bez znaku  
  
-   Ogólnie rzecz biorąc, użyj `int` zamiast niepodpisanych typów. Korzystanie z `int` często w języku C# i łatwiej wchodzić w interakcje z innymi bibliotekami, gdy używasz `int`.  
  
### <a name="arrays"></a>Tablice  
  
-   Podczas inicjowania tablic w wierszu deklaracji, należy użyć zwięzłej składni.  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Delegaty  
  
-   Aby utworzyć wystąpienia typu delegata, należy użyć składni zwięzły.  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Blok try-catch i przy użyciu instrukcji obsługi wyjątków  
  
-   Użyj [try-catch —](../../../csharp/language-reference/keywords/try-catch.md) poufności informacji dla większości wyjątków.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   Uprość kod przy użyciu języka C# [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md). Jeśli masz [try-finally](../../../csharp/language-reference/keywords/try-finally.md) instrukcji, w którym tylko kod w `finally` bloku jest wywołaniem <xref:System.IDisposable.Dispose%2A> metody, użyj `using` instrukcji zamiast tego.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>& & i &#124; &#124; operatorów  
  
-   Aby uniknąć wyjątków i zwiększyć wydajność przez pominięcie niepotrzebnych porównań, należy użyć [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) zamiast [ & ](../../../csharp/language-reference/operators/and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)zamiast [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) podczas wykonywania porównań, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Nowy operator  
  
-   Za pomocą zwięzłe formularza w przypadku tworzenia wystąpienia obiektu niejawnego wpisywania, jak pokazano w poniższej deklaracji.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Poprzedniego wiersza jest równoważna następującej deklaracji.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   Użyj inicjatorów obiektów, aby uprościć tworzenie obiektów.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Obsługa zdarzeń  
  
-   Jeśli zamierzasz zdefiniować program obsługi zdarzeń, że nie musisz usunąć później, należy użyć wyrażenia lambda.  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statyczne elementy członkowskie  
  
-   Wywołaj [statyczne](../../../csharp/language-reference/keywords/static.md) elementów członkowskich przy użyciu nazwy klasy: *ClassName.StaticMember*. Tej praktyką sprawia, że kod jest bardziej czytelny, dzięki czemu dostęp do statycznych, wyczyść.  Nie można rozwiązać członka statycznego zdefiniowana w klasie bazowej o nazwie klasy pochodnej.  Gdy kompiluje kod, jest mylące czytelność kodu i kodu mogą przestać działać w przyszłości w przypadku dodania statyczny element członkowski o takiej samej nazwie do klasy pochodnej.  
  
### <a name="linq-queries"></a>Zapytania LINQ  
  
-   Użyj nazw opisowych dla zmiennych kwerendy. W poniższym przykładzie użyto `seattleCustomers` dla klientów, którzy znajdują się w Seattle.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Należy stosować aliasy, aby upewnić się, że nazwy właściwości anonimowych typów są kapitalizowane poprawnie, przy użyciu obudowy Pascal wielkość liter w wyrazie.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłby niejednoznaczne. Na przykład, jeśli zapytanie zwraca klienta, nazwy i Identyfikatora dystrybutora, zamiast pozostawiania je jako `Name` i `ID` w wyniku, zmienić ich nazwy, które informuje, że `Name` nazywa się klient, oraz `ID` to identyfikator dystrybutora.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   Należy użyć niejawnego wpisywania w deklaracji zmiennych kwerendy i zmiennych zakresu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Wyrównaj klauzule zapytania pod [z](../../../csharp/language-reference/keywords/from-clause.md) klauzuli, jak pokazano w poprzednich przykładach.  
  
-   Użyj [gdzie](../../../csharp/language-reference/keywords/where-clause.md) klauzule przed inne klauzule zapytania, aby upewnić się, że późniejsze klauzule kwerend działają na mniejsze, filtrowany zestaw danych.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   Używanych jest wiele `from` klauzule zamiast [sprzężenia](../../../csharp/language-reference/keywords/join-clause.md) klauzuli do dostępu do kolekcji wewnętrznego. Na przykład zbiór `Student` każdego obiektów może zawierać zbiór wyniki testów. Po wykonaniu następujące zapytanie zwraca każdy wynik, który jest ponad 90, wraz z Nazwisko ucznia, który otrzymał wynik.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Zabezpieczenia  
 Postępuj zgodnie z wytycznymi podanymi w [Secure wytycznych kodowania](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Zobacz też

- [Visual Basic — konwencje kodowania](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
- [Wytyczne dotyczące bezpiecznego programowania](../../../standard/security/secure-coding-guidelines.md)
