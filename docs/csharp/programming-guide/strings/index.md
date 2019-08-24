---
title: Ciągi — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: d9453f931bba9b1d3b5db3b4f80aa365677c0b76
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988422"
---
# <a name="strings-c-programming-guide"></a>Ciągi (Przewodnik programowania w języku C#)
Ciąg jest obiektem typu <xref:System.String> , którego wartością jest Text. Wewnętrznie tekst jest przechowywany jako sekwencyjna kolekcja <xref:System.Char> obiektów tylko do odczytu. Na końcu C# ciągu nie ma znaku zamykającego wartości null; w związku C# z tym ciąg może zawierać dowolną liczbę osadzonych znaków null (' \ 0 '). Właściwość ciągu reprezentuje `Char` liczbę obiektów, które zawiera, a nie liczbę znaków Unicode. <xref:System.String.Length%2A> Aby uzyskać dostęp do poszczególnych punktów kodu Unicode w ciągu, użyj <xref:System.Globalization.StringInfo> obiektu.  
  
## <a name="string-vs-systemstring"></a>ciąg a System.String  
 W programie C# <xref:System.String>słowo kluczowe jest aliasem dla. `string` W `String` związku z `string` tym i są równoważne i można użyć dowolnej preferowanej konwencji nazewnictwa. `String` Klasa zawiera wiele metod bezpiecznego tworzenia, manipulowania i porównywania ciągów. Ponadto C# język przeciążuje niektórych operatorów, aby uprościć Typowe operacje na ciągach. Aby uzyskać więcej informacji na temat słowa kluczowego, zobacz [ciąg](../../language-reference/keywords/string.md). Aby uzyskać więcej informacji na temat typu i jego metod, <xref:System.String>Zobacz.  
  
## <a name="declaring-and-initializing-strings"></a>Deklarowanie i Inicjowanie ciągów  
 Można zadeklarować i zainicjować ciągi na różne sposoby, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Należy zauważyć, że nie używasz operatora [New](../../language-reference/operators/new-operator.md) do tworzenia obiektu String, chyba że podczas inicjowania ciągu z tablicą znaków.  
  
 Zainicjuj ciąg z <xref:System.String.Empty> wartością stałą, aby utworzyć nowy <xref:System.String> obiekt, którego ciąg ma zerową długość. Literał ciągu reprezentujący ciąg o zerowej długości to "". Inicjując ciągi z <xref:System.String.Empty> wartością zamiast [wartości null](../../language-reference/keywords/null.md), można zmniejszyć prawdopodobieństwo <xref:System.NullReferenceException> wystąpienia. Użyj metody statycznej <xref:System.String.IsNullOrEmpty%28System.String%29> , aby zweryfikować wartość ciągu przed próbą uzyskania do niego dostępu.  
  
## <a name="immutability-of-string-objects"></a>Niezmienności obiektów String  
 Obiekty String są *niezmienne*: nie można ich zmienić po ich utworzeniu. Wszystkie metody i C# operatory, które pojawiają się w celu zmodyfikowania ciągu faktycznie zwracają wyniki w nowym obiekcie ciągu. <xref:System.String> W poniższym przykładzie, gdy zawartość `s1` i `s2` są łączone w celu utworzenia jednego ciągu, dwa oryginalne ciągi nie są modyfikowane. `+=` Operator tworzy nowy ciąg, który zawiera łączną zawartość. Nowy obiekt jest przypisany do zmiennej `s1`, a oryginalny obiekt, który został przypisany do `s1` , jest uwalniany do wyrzucania elementów bezużytecznych, ponieważ żadna inna zmienna nie przechowuje odwołania do niego.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Ponieważ ciąg "modyfikacja" jest w rzeczywistości nowym ciągiem, należy zachować ostrożność podczas tworzenia odwołań do ciągów. Jeśli utworzysz odwołanie do ciągu, a następnie "modyfikujesz" oryginalny ciąg, odwołanie będzie nadal wskazywało oryginalny obiekt zamiast nowego obiektu, który został utworzony podczas modyfikacji ciągu. Poniższy kod ilustruje to zachowanie:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Aby uzyskać więcej informacji na temat sposobu tworzenia nowych ciągów opartych na modyfikacjach, takich jak wyszukiwanie i zamienianie na oryginalnym ciągu, [zobacz How to: Modyfikuj zawartość](../../how-to/modify-string-contents.md)ciągu.  
  
## <a name="regular-and-verbatim-string-literals"></a>Zwykłe i Verbatim literały ciągu  
 Należy używać zwykłych literałów ciągów, gdy trzeba osadzić znaki ucieczki C#dostarczone przez, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Używaj ciągów Verbatim, aby wygodnie i lepsza czytelność, gdy tekst ciągu zawiera znaki ukośnika odwrotnego, na przykład w ścieżkach plików. Ponieważ ciągi Verbatim zachowują znaki nowego wiersza w ramach tekstu ciągu, mogą one służyć do inicjowania ciągów wielowierszowych. Użyj podwójnych cudzysłowów do osadzenia cudzysłowu wewnątrz ciągu Verbatim. W poniższym przykładzie przedstawiono niektóre typowe zastosowania ciągów Verbatim:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Sekwencje ucieczki ciągów  
  
|Sekwencja ucieczki|Nazwa znaku|Kodowanie Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|Pojedynczy cytat|0x0027|  
|\\"|Podwójny cudzysłów|0x0022|  
|\\\\ |Ukośnik odwrotny|0x005C|  
|\0|Null|0x0000|  
|\a|Alerty|0x0007|  
|\b|Backspace|0x0008|  
|\f|Kanał informacyjny formularza|0x000C|  
|\n|Nowy wiersz|0x000A|  
|\r|Znak powrotu karetki|0x000D|  
|\t|Tabulator poziomy|0x0009|  
|\v|Tabulator pionowy|0x000B|  
|\u|Sekwencja unikowa Unicode (UTF-16)|`\uHHHH`zakresu 0000 — FFFF; przykład: `\u00E7` = "ç")|  
|\U|Sekwencja unikowa Unicode (UTF-32)|`\U00HHHHHH`zakresu 000000 — 10FFFF; przykład: `\U0001F47D` = "&#x1F47D;")|  
|\x|Sekwencja unikowa Unicode podobna do "\u" z wyjątkiem zmiennej długości|`\xH[H][H][H]`zakresu 0 — FFFF; przykład: `\x00E7` or `\x0E7` lub `\xE7` = "ç")|  
  
> [!WARNING]
> Przy użyciu `\x` sekwencji unikowej i określania mniej niż 4 cyfry szesnastkowe, jeśli znaki, które bezpośrednio podążają za sekwencją ucieczki, są prawidłowymi cyframi szesnastkowymi (tj. 0-9, a-f i a-f), będą interpretowane jako część sekwencji ucieczki. Na przykład `\xA1` tworzy "&#161;", który jest punktem kodu U + 00A1. Jeśli jednak następny znak to "a" lub "a", wówczas sekwencja ucieczki będzie interpretowana jako `\xA1A` "&#x0A1A;", która jest punktem kodu U + 0A1A. W takich przypadkach, określenie wszystkich 4 cyfr szesnastkowych (np `\x00A1` .) uniemożliwi wszelkie możliwe Błędne interpretacje.  
  
> [!NOTE]
> W czasie kompilacji ciągi Verbatim są konwertowane na zwykłe ciągi ze wszystkimi tymi samymi sekwencjami ucieczki. W związku z tym, jeśli w oknie Czujka debugera zostanie wyświetlony ciąg Verbatim, zobaczysz znaki ucieczki, które zostały dodane przez kompilator, a nie wersję Verbatim z kodu źródłowego. Na przykład ciąg `@"C:\files.txt"` Verbatim pojawi się w oknie czujki jako "C:\\\files.txt".  
  
## <a name="format-strings"></a>Ciągi formatujące  
 Ciąg formatu jest ciągiem, którego zawartość jest określana dynamicznie w czasie wykonywania. Ciągi formatu są tworzone przez osadzanie *wyrażeń interpolowanych* lub symboli zastępczych wewnątrz nawiasów klamrowych w ciągu. Wszystkie elementy wewnątrz nawiasów klamrowych (`{...}`) zostaną rozpoznane jako ciąg sformatowany w czasie wykonywania. Istnieją dwie metody tworzenia ciągów formatowania: Interpolacja ciągów i formatowanie złożone.

### <a name="string-interpolation"></a>Interpolacja ciągów
Dostępne w C# 6,0 i nowszych, [interpolowane ciągi](../../language-reference/tokens/interpolated.md) są `$` identyfikowane przez znak specjalny i zawierają interpolowane wyrażenia w nawiasach klamrowych. Jeśli dopiero zaczynasz interpolację ciągów, zobacz Interpolacja [ciągów — C# Interaktywny samouczek](../../tutorials/exploration/interpolated-strings.yml) , aby zapoznać się z krótkim omówieniem.

Używaj interpolacji ciągów, aby zwiększyć czytelność i łatwość utrzymania kodu. Interpolacja ciągów osiąga te same wyniki co `String.Format` Metoda, ale poprawia łatwość użycia i inline.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Złożone formatowanie
Symbole <xref:System.String.Format%2A?displayProperty=nameWithType> zastępcze wykorzystują w nawiasach klamrowych, aby utworzyć ciąg formatu. Ten przykład skutkuje podobnym wyjściem do metody interpolacji ciągów użytej powyżej.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

Aby uzyskać więcej informacji na temat formatowania typów .NET, zobacz [Typy formatowania na platformie .NET](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Podciągów  
 Podciąg to dowolna sekwencja znaków, która jest zawarta w ciągu. Użyj metody <xref:System.String.Substring%2A> , aby utworzyć nowy ciąg z części oryginalnego ciągu. Można wyszukać jedno lub więcej wystąpień podciągu przy użyciu <xref:System.String.IndexOf%2A> metody. Użyj metody <xref:System.String.Replace%2A> , aby zastąpić wszystkie wystąpienia określonego podciągu nowym ciągiem. Podobnie jak <xref:System.String.Replace%2A> Metoda, faktycznie zwraca nowy ciąg i nie modyfikuje pierwotnego ciągu. <xref:System.String.Substring%2A> Aby uzyskać więcej informacji, zobacz [How to: Search String](../../how-to/search-strings.md) and [How to: Modyfikuj zawartość](../../how-to/modify-string-contents.md)ciągu.  
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#9)]  
  
## <a name="accessing-individual-characters"></a>Uzyskiwanie dostępu do pojedynczych znaków  
 Można użyć notacji Array z wartością indeksu, aby uzyskać dostęp tylko do odczytu do poszczególnych znaków, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 Jeśli metody nie zapewniają funkcjonalności, która musi być modyfikowana przez poszczególne znaki w ciągu, można <xref:System.Text.StringBuilder> użyć obiektu do modyfikacji pojedynczych znaków "w miejscu", a następnie utworzyć nowy ciąg do przechowywania wyników przy użyciu <xref:System.String> <xref:System.Text.StringBuilder> metody. W poniższym przykładzie Załóżmy, że należy zmodyfikować oryginalny ciąg w określony sposób, a następnie zapisać wyniki do użycia w przyszłości:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Ciągi o wartości null i puste ciągi  
 Pusty ciąg jest wystąpieniem <xref:System.String?displayProperty=nameWithType> obiektu, który zawiera znaki zerowe. Puste ciągi są często używane w różnych scenariuszach programistycznych do reprezentowania pustego pola tekstowego. Możesz wywoływać metody dla pustych ciągów, ponieważ są <xref:System.String?displayProperty=nameWithType> one prawidłowymi obiektami. Puste ciągi są inicjowane w następujący sposób:  
  
```  
string s = String.Empty;  
```  
  
 Z kolei ciąg o wartości null nie odwołuje się do wystąpienia <xref:System.String?displayProperty=nameWithType> obiektu, a jakakolwiek próba wywołania metody dla ciągu o wartości null <xref:System.NullReferenceException>powoduje. Można jednak używać ciągów o wartości null w operacjach łączenia i porównywania z innymi ciągami. Poniższe przykłady ilustrują niektóre przypadki, w których odwołanie do ciągu o wartości null i nie powoduje zgłoszenia wyjątku:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Używanie elementu StringBuilder do szybkiego tworzenia ciągów  
 Operacje na ciągach w programie .NET są wysoce zoptymalizowane i w większości przypadków nie mają znaczącego wpływu na wydajność. Jednak w niektórych scenariuszach, takich jak ścisłe pętle wykonujące wiele setek lub tysięcy razy, operacje na ciągach mogą mieć wpływ na wydajność. <xref:System.Text.StringBuilder> Klasa tworzy bufor ciągów, który zapewnia lepszą wydajność, jeśli program wykonuje wiele operacji manipulowania ciągami. Ten <xref:System.Text.StringBuilder> ciąg umożliwia również ponowne przypisanie pojedynczych znaków, co nie jest obsługiwane w przypadku typu danych, który jest wbudowany. Ten kod, na przykład, zmienia zawartość ciągu bez tworzenia nowego ciągu:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 W tym przykładzie <xref:System.Text.StringBuilder> obiekt jest używany do tworzenia ciągu z zestawu typów liczbowych:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Ciągi, metody rozszerzające i LINQ  
 Ponieważ typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, można użyć metod <xref:System.Linq.Enumerable> rozszerzających zdefiniowanych w klasie w ciągach. <xref:System.String> Aby uniknąć bałaganu wizualnego, te metody są wykluczone z <xref:System.String> IntelliSense dla typu, ale są one dostępne. Można również użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeń zapytania dla ciągów. Aby uzyskać więcej informacji, zobacz [LINQ i ciągi](../concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Instrukcje: Modyfikuj zawartość ciągu](../../how-to/modify-string-contents.md)|Ilustruje techniki przekształcania ciągów i modyfikowania zawartości ciągów.|  
|[Instrukcje: Porównaj ciągi](../../how-to/compare-strings.md)|Pokazuje, w jaki sposób wykonywać porównania ciągów liczbowych i kulturowych.|  
|[Instrukcje: Łączenie wielu ciągów](../../how-to/concatenate-multiple-strings.md)|Ilustruje różne sposoby sprzęgania wielu ciągów w jeden.|
|[Instrukcje: Analizowanie ciągów za pomocą ciągu. Split](../../how-to/parse-strings-using-split.md)|Zawiera przykłady kodu, które ilustrują sposób użycia `String.Split` metody do analizowania ciągów.|  
|[Instrukcje: Ciągi wyszukiwania](../../how-to/search-strings.md)|Wyjaśnia, jak używać wyszukiwania określonego tekstu lub wzorców w ciągach.|  
|[Instrukcje: Określanie, czy ciąg reprezentuje wartość liczbową](./how-to-determine-whether-a-string-represents-a-numeric-value.md)|Pokazuje, jak bezpiecznie analizować ciąg, aby sprawdzić, czy ma prawidłową wartość liczbową.|  
|[Interpolacja ciągów](../../language-reference/tokens/interpolated.md)|Opisuje funkcję interpolacji ciągów, która zapewnia wygodną składnię do formatowania ciągów.|
|[Podstawowe operacje na ciągach](../../../standard/base-types/basic-string-operations.md)|Zawiera łącza do tematów, które <xref:System.String?displayProperty=nameWithType> używają <xref:System.Text.StringBuilder?displayProperty=nameWithType> metod i do wykonywania podstawowych operacji na ciągach.|  
|[Analizowanie ciągów](../../../standard/base-types/parsing-strings.md)|W tym artykule opisano sposób konwertowania reprezentacji ciągów typów podstawowych na wystąpienia odpowiednich typów.|  
|[Analizowanie ciągów daty i godziny w programie .NET](../../../standard/base-types/parsing-datetime.md)|Pokazuje, jak przekonwertować ciąg, taki jak "01/24/2008", na <xref:System.DateTime?displayProperty=nameWithType> obiekt.|  
|[Porównywanie ciągów](../../../standard/base-types/comparing.md)|Zawiera informacje o sposobach porównywania ciągów i zawiera przykłady C# w i Visual Basic.|  
|[Używanie klasy StringBuilder](../../../standard/base-types/stringbuilder.md)|Opisuje sposób tworzenia i modyfikowania dynamicznych obiektów ciągów przy użyciu <xref:System.Text.StringBuilder> klasy.|  
|[LINQ i ciągi](../concepts/linq/linq-and-strings.md)|Zawiera informacje o sposobach wykonywania różnych operacji na ciągach przy użyciu zapytań LINQ.|  
|[Przewodnik programowania w języku C#](../index.md)|Zawiera łącza do tematów, które wyjaśniają konstrukcje C#programistyczne w programie.|  
