---
title: Ciągi - Przewodnik programowania C#
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: dd76450c2a6a1726d630285f652d252c5f66183f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711912"
---
# <a name="strings-c-programming-guide"></a>Ciągi (Przewodnik programowania w języku C#)
Ciąg jest obiektem <xref:System.String> typu, którego wartością jest tekst. Wewnętrznie tekst jest przechowywany jako sekwencyjna kolekcja obiektów <xref:System.Char> tylko do odczytu. Nie ma żadnego znaku zakończenia zerowego na końcu ciągu C#; w związku z tym ciąg C# może zawierać dowolną liczbę osadzonych znaków null ('\0'). Właściwość <xref:System.String.Length%2A> ciągu reprezentuje liczbę `Char` obiektów, które zawiera, a nie liczbę znaków Unicode. Aby uzyskać dostęp do poszczególnych punktów kodu <xref:System.Globalization.StringInfo> Unicode w ciągu, należy użyć obiektu.  
  
## <a name="string-vs-systemstring"></a>ciąg a System.String  
 W języku `string` C#słowo kluczowe <xref:System.String>jest aliasem dla . W `String` związku `string` z tym i są równoważne i można użyć niezależnie od konwencji nazewnictwa wolisz. Klasa `String` zawiera wiele metod bezpiecznego tworzenia, manipulowania i porównywania ciągów. Ponadto język C# przeciąża niektóre operatory, aby uprościć typowe operacje ciągu. Aby uzyskać więcej informacji o suteku kluczowym, zobacz [ciąg .](../../language-reference/builtin-types/reference-types.md) Aby uzyskać więcej informacji na temat <xref:System.String>typu i jego metod, zobacz .  
  
## <a name="declaring-and-initializing-strings"></a>Deklarowanie i inicjowanie ciągów  
 Ciągi można deklarować i inicjować na różne sposoby, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Należy zauważyć, że nie należy używać [nowego](../../language-reference/operators/new-operator.md) operatora do tworzenia obiektu ciągu, z wyjątkiem inicjowania ciągu z tablicą znaków.  
  
 Inicjuj ciąg <xref:System.String.Empty> o stałej wartości, aby utworzyć nowy <xref:System.String> obiekt, którego ciąg ma zerową długość. Dosłowną reprezentacją ciągu ciągu ciągiem o zerowej długości jest "". Poprzez inicjowanie ciągów <xref:System.String.Empty> z wartością zamiast [null](../../language-reference/keywords/null.md), <xref:System.NullReferenceException> można zmniejszyć szanse wystąpienia. Użyj metody <xref:System.String.IsNullOrEmpty%28System.String%29> statycznej, aby zweryfikować wartość ciągu przed próbą uzyskania do niego dostępu.  
  
## <a name="immutability-of-string-objects"></a>Niezmienność obiektów ciągów  
 Obiekty ciągów są *niezmienne:* nie można ich zmienić po ich utworzeniu. Wszystkie <xref:System.String> metody i operatory Języka C#, które wydają się modyfikować ciąg faktycznie zwracają wyniki w nowym obiekcie ciągu. W poniższym przykładzie, gdy `s1` zawartość `s2` i są łączone w celu utworzenia jednego ciągu, dwa oryginalne ciągi są niezmodyfikowane. Operator `+=` tworzy nowy ciąg, który zawiera zawartość połączoną. Ten nowy obiekt jest przypisany do zmiennej, `s1`a `s1` oryginalny obiekt, który został przypisany do jest zwalniany do wyrzucania elementów bezużytecznych, ponieważ żadna inna zmienna nie zawiera odwołania do niego.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Ponieważ ciąg "modyfikacja" jest rzeczywiście nowe tworzenie ciągów, należy zachować ostrożność podczas tworzenia odwołań do ciągów. Jeśli utworzysz odwołanie do ciągu, a następnie "zmodyfikujesz" oryginalny ciąg, odwołanie będzie nadal wskazywać oryginalny obiekt zamiast nowego obiektu, który został utworzony podczas modyfikowania ciągu. Następujący kod ilustruje to zachowanie:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Aby uzyskać więcej informacji na temat tworzenia nowych ciągów opartych na modyfikacjach, takich jak wyszukiwanie i zastępowanie operacji w oryginalnym ciągu, zobacz [Jak modyfikować zawartość ciągu](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Dosłowne i dosłowne dosłowne dosłowne ciągi  
 Użyj zwykłych literału ciągów, gdy należy osadzić znaki ucieczki dostarczone przez C#, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Użyj ciągów dosłownych dla wygody i lepszej czytelności, gdy tekst ciągu zawiera znaki ukośnika odwrotnego, na przykład w ścieżkach plików. Ponieważ ciągi dosłowne zachowują nowe znaki wiersza jako część tekstu ciągu, mogą być używane do inicjowania ciągów wielowierszowych. Użyj podwójnych cudzysłowów, aby osadzić cudzysłów wewnątrz ciągu dosłownego. W poniższym przykładzie przedstawiono niektóre typowe zastosowania ciągów dosłownych:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Sekwencje ucieczki ciągów  
  
|Sekwencja ucieczki|Nazwa znaku|Kodowanie Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|Pojedyncza oferta|0x0027|  
|\\"|Podwójna oferta|0x0022|  
|\\\\ |Ukośnik odwrotny|0x005C|  
|\0|Null|0x0000|  
|\a|Alerty|0x0007|  
|\b|Backspace|0x0008|  
|\f|Źródło formularza|0x000C|  
|\n|Nowa linia|0x000A|  
|\r|Zwrot karetki|0x000D|  
|\t|Karta Pozioma|0x0009|  
|\v|Karta Pionowa|0x000B|  
|\u|Sekwencja ucieczki Unicode (UTF-16)|`\uHHHH`(zakres: 0000 - FFFF; przykład: `\u00E7` = "ç")|  
|\u|Sekwencja ucieczki Unicode (UTF-32)|`\U00HHHHHH`(zakres: 000000 - 10FFFF; przykład: `\U0001F47D` = "&#x1F47D;")|  
|\x|Sekwencja ucieczki Unicode podobna do "\u" z wyjątkiem zmiennej długości|`\xH[H][H][H]`(zakres: 0 - FFFF; `\x0E7` `\xE7` przykład: `\x00E7` lub = "ç")|  
  
> [!WARNING]
> W przypadku `\x` używania sekwencji ucieczki i określania mniej niż 4 cyfr szesnastkowych, jeśli znaki, które natychmiast podążają za sekwencją ucieczki, są prawidłowymi cyframi szesnastymi (tj. 0-9, A-F i a-f), będą one interpretowane jako część sekwencji ucieczki. Na przykład `\xA1` tworzy "&#161;", który jest punktem kodowym U +00A1. Jednak jeśli następny znak jest "A" lub "a", a następnie sekwencji ucieczki zamiast tego będą interpretowane jako `\xA1A` i produkować "&#x0A1A;", który jest punktem kodu U + 0A1A. W takich przypadkach określenie wszystkich 4 cyfr szesnastkowych (np. `\x00A1` ) zapobiegnie ewentualnej błędnej interpretacji.  
  
> [!NOTE]
> W czasie kompilacji ciągi dosłowne są konwertowane na zwykłe ciągi z tymi samymi sekwencjami ucieczki. W związku z tym jeśli zostanie wyświetlony ciąg dosłowny w oknie czujki debugera, zobaczysz znaki ucieczki, które zostały dodane przez kompilator, a nie dosłowną wersję z kodu źródłowego. Na przykład ciąg `@"C:\files.txt"` dosłowny pojawi się w oknie\\czujki jako "C: \files.txt".  
  
## <a name="format-strings"></a>Ciągi formatu  
 Ciąg formatu jest ciągiem, którego zawartość jest określana dynamicznie w czasie wykonywania. Ciągi formatu są tworzone przez osadzanie *interpolowanych wyrażeń* lub symboli zastępczych wewnątrz nawiasów klamrowych w ciągu. Wszystko wewnątrz nawiasów`{...}`klamrowych ( ) zostanie rozpoznane do wartości i danych wyjściowych jako sformatowany ciąg w czasie wykonywania. Istnieją dwie metody tworzenia ciągów formatu: interpolacja ciągów i formatowanie złożone.

### <a name="string-interpolation"></a>Interpolacja ciągów
Dostępne w języku C# 6.0 i [*nowszych, interpolowane ciągi*](../../language-reference/tokens/interpolated.md) są identyfikowane za pomocą znaku `$` specjalnego i zawierają interpolowane wyrażenia w nawiasach klamrowych. Jeśli jesteś nowym użytkownikiem interpolacji ciągów, zobacz [String interpolacji - C# interaktywny samouczek,](../../tutorials/exploration/interpolated-strings.yml) aby uzyskać szybki przegląd.

Użyj interpolacji ciągów, aby poprawić czytelność i łatwość konserwacji kodu. Interpolacja ciągów osiąga takie `String.Format` same wyniki jak metoda, ale poprawia łatwość użycia i przejrzystość w linii.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Złożone formatowanie
Wykorzystuje <xref:System.String.Format%2A?displayProperty=nameWithType> symbole zastępcze w nawiasach klamrowych, aby utworzyć ciąg formatu. W tym przykładzie wyniki w podobny wynik do metody interpolacji ciąg używany powyżej.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

Aby uzyskać więcej informacji na temat formatowania typów .NET, zobacz [Formatowanie typów w .NET](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Podciągów  
 Podciąg to dowolna sekwencja znaków, która jest zawarta w ciągu. Użyj <xref:System.String.Substring%2A> metody, aby utworzyć nowy ciąg z części oryginalnego ciągu. Można wyszukać co najmniej jedno wystąpienie podciągu <xref:System.String.IndexOf%2A> przy użyciu metody. Użyj <xref:System.String.Replace%2A> metody, aby zastąpić wszystkie wystąpienia określonego podciągu nowym ciągiem. Podobnie <xref:System.String.Substring%2A> jak <xref:System.String.Replace%2A> metoda, faktycznie zwraca nowy ciąg i nie modyfikuje oryginalny ciąg. Aby uzyskać więcej informacji, zobacz [Jak wyszukiwać ciągi](../../how-to/search-strings.md) i [Jak modyfikować zawartość ciągu](../../how-to/modify-string-contents.md).
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#9)]  
  
## <a name="accessing-individual-characters"></a>Uzyskiwanie dostępu do poszczególnych znaków  
 Notacji tablicowej z wartością indeksu można użyć do uzyskania dostępu tylko do odczytu do poszczególnych znaków, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 Jeśli <xref:System.String> metody nie zapewniają funkcji, które muszą być modyfikowane poszczególnych znaków w <xref:System.Text.StringBuilder> ciągu, można użyć obiektu do modyfikowania poszczególnych znaków "w miejscu", a następnie utworzyć nowy ciąg do przechowywania wyników przy użyciu <xref:System.Text.StringBuilder> metod. W poniższym przykładzie załóżmy, że należy zmodyfikować oryginalny ciąg w określony sposób, a następnie przechowywać wyniki do wykorzystania w przyszłości:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Ciągi zerowe i puste ciągi  
 Pusty ciąg jest wystąpieniem <xref:System.String?displayProperty=nameWithType> obiektu, który zawiera znaki zero. Puste ciągi są często używane w różnych scenariuszach programowania do reprezentowania pustego pola tekstowego. Metody można wywoływać na pustych ciągów, ponieważ są one prawidłowe <xref:System.String?displayProperty=nameWithType> obiekty. Puste ciągi są inicjowane w następujący sposób:  
  
```csharp  
string s = String.Empty;  
```  
  
 Natomiast ciąg zerowy nie odwołuje się do <xref:System.String?displayProperty=nameWithType> wystąpienia obiektu, a każda próba wywołania <xref:System.NullReferenceException>metody na ciąg zerowy powoduje . Można jednak użyć ciągów zerowych w operacjach łączenia i porównywania z innymi ciągami. Poniższe przykłady ilustrują niektóre przypadki, w których odwołanie do ciągu zerowego ma i nie powoduje wyjątek wyjątek:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Używanie StringBuilder do szybkiego tworzenia ciągów  
 Operacje ciągów w .NET są wysoce zoptymalizowane i w większości przypadków nie mają znaczącego wpływu na wydajność. Jednak w niektórych scenariuszach, takich jak wąskie pętle, które są wykonywane wiele setek lub tysięcy razy, operacje ciągu może mieć wpływ na wydajność. Klasa <xref:System.Text.StringBuilder> tworzy bufor ciągów, który oferuje lepszą wydajność, jeśli program wykonuje wiele manipulacji ciągami. Ciąg <xref:System.Text.StringBuilder> umożliwia również ponowne przypisywanie poszczególnych znaków, coś, czego nie obsługuje wbudowany typ danych ciągu. Ten kod, na przykład, zmienia zawartość ciągu bez tworzenia nowego ciągu:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 W tym przykładzie <xref:System.Text.StringBuilder> obiekt jest używany do tworzenia ciągu z zestawu typów liczbowych:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Ciągi, metody rozszerzenia i LINQ  
 Ponieważ <xref:System.String> typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, można użyć metod rozszerzenia <xref:System.Linq.Enumerable> zdefiniowanych w klasie na ciągi. Aby uniknąć bałaganu wizualnego, te metody są wyłączone <xref:System.String> z IntelliSense dla typu, ale są one jednak dostępne. Można również użyć wyrażeń zapytań LINQ na ciągach. Aby uzyskać więcej informacji, zobacz [LINQ i Strings](../concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Jak modyfikować zawartość ciągu](../../how-to/modify-string-contents.md)|Ilustruje techniki przekształcania ciągów i modyfikowania zawartości ciągów.|  
|[Jak porównać ciągi znaków](../../how-to/compare-strings.md)|Pokazuje, jak wykonywać porównania ciągów szeregowych i kulturowych.|  
|[Jak połączyć wiele ciągów](../../how-to/concatenate-multiple-strings.md)|Demonstruje różne sposoby łączenia wielu ciągów w jeden.|
|[Jak analizować ciągi za pomocą String.Split](../../how-to/parse-strings-using-split.md)|Zawiera przykłady kodu, które ilustrują sposób używania `String.Split` metody do analizowania ciągów.|  
|[Jak wyszukiwać ciągi](../../how-to/search-strings.md)|W tym artykule wyjaśniono, jak używać wyszukiwania dla określonego tekstu lub wzorców w ciągach.|  
|[Określanie, czy ciąg reprezentuje wartość numeryczną](./how-to-determine-whether-a-string-represents-a-numeric-value.md)|Pokazuje, jak bezpiecznie analizować ciąg, aby sprawdzić, czy ma prawidłową wartość liczbową.|  
|[Interpolacja ciągów](../../language-reference/tokens/interpolated.md)|W tym artykule opisano funkcję interpolacji ciągów, która zapewnia wygodną składnię do formatowania ciągów.|
|[Podstawowe operacje na ciągach](../../../standard/base-types/basic-string-operations.md)|Zawiera łącza do <xref:System.String?displayProperty=nameWithType> tematów, które używają i <xref:System.Text.StringBuilder?displayProperty=nameWithType> metody do wykonywania podstawowych operacji ciągu.|  
|[Analiza składniowa ciągów](../../../standard/base-types/parsing-strings.md)|W tym artykule opisano sposób konwertowania reprezentacji ciągów typów podstawowych .NET na wystąpienia odpowiednich typów.|  
|[Analizowanie ciągów daty i godziny w .NET](../../../standard/base-types/parsing-datetime.md)|Pokazuje, jak przekonwertować ciąg, taki jak "24.01.2008" na <xref:System.DateTime?displayProperty=nameWithType> obiekt.|  
|[Porównywanie ciągów](../../../standard/base-types/comparing.md)|Zawiera informacje dotyczące sposobu porównywania ciągów i zawiera przykłady w języku C# i Visual Basic.|  
|[Używanie klasy StringBuilder](../../../standard/base-types/stringbuilder.md)|Opisuje sposób tworzenia i modyfikowania <xref:System.Text.StringBuilder> dynamicznych obiektów ciągu przy użyciu klasy.|  
|[LINQ i ciągi](../concepts/linq/linq-and-strings.md)|Zawiera informacje dotyczące sposobu wykonywania różnych operacji ciągu przy użyciu kwerend LINQ.|  
|[Przewodnik programowania języka C#](../index.md)|Zawiera łącza do tematów, które wyjaśniają konstrukcje programowania w języku C#.|  
