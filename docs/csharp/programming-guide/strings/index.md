---
title: Ciągi (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: 9b108a1613e01016c541d088612303c6aaa13629
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strings-c-programming-guide"></a>Ciągi (Przewodnik programowania w języku C#)
Ciąg jest obiektem typu <xref:System.String> którego wartość jest tekstem. Wewnętrznie, tekst jest przechowywana jako sekwencyjnych kolekcji tylko do odczytu z <xref:System.Char> obiektów. Brak nie przerywa null znak na końcu C# ciąg. w związku z tym ciągu języka C# może zawierać dowolną liczbę osadzonych znaki null ('\0'). <xref:System.String.Length%2A> Właściwości ciągu reprezentuje liczbę `Char` obiekty nie zawiera, nie liczbę znaków Unicode. Aby uzyskać dostęp do poszczególnych punktów kodowych Unicode w ciągu, użyj <xref:System.Globalization.StringInfo> obiektu.  
  
## <a name="string-vs-systemstring"></a>Ciąg wersji programu vs. System.String  
 W języku C# `string` — słowo kluczowe jest aliasem <xref:System.String>. W związku z tym `String` i `string` są równoważne, a można użyć niezależnie od konwencji nazewnictwa preferowane. `String` Klasa udostępnia wiele metod bezpiecznego tworzenia, modyfikowania i porównywanie ciągów. Ponadto w języku C# overloads niektórych operatorów, aby uprościć typowe operacje na ciągach. Aby uzyskać więcej informacji na temat słowo kluczowe, zobacz [ciąg](../../../csharp/language-reference/keywords/string.md). Aby uzyskać więcej informacji o typie i jego metod, zobacz <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Deklarowanie i Inicjowanie ciągów  
 Można zadeklarować i zainicjować ciągów na różne sposoby, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 Należy pamiętać, że nie należy używać [nowe](../../../csharp/language-reference/keywords/new-operator.md) operatora do utworzenia obiektu ciąg, z wyjątkiem podczas inicjowania ciągu z tablicy znaków.  
  
 Inicjuje ciąg z <xref:System.String.Empty> stałą wartość, aby utworzyć nową <xref:System.String> obiektu, w których ciąg jest o zerowej długości. Reprezentacja ciągu literału ciągu o zerowej długości jest "". Przez inicjowanie ciągów <xref:System.String.Empty> wartość zamiast [null](../../../csharp/language-reference/keywords/null.md), można zmniejszyć ryzyko <xref:System.NullReferenceException> wystąpienia. Użyj statycznych <xref:System.String.IsNullOrEmpty%28System.String%29> metody Sprawdź wartość ciągu, przed podjęciem próby dostępu do niego.  
  
## <a name="immutability-of-string-objects"></a>Immutability obiektów w postaci ciągów  
 Ciąg obiekty są *niezmienialnych*: nie można zmienić po utworzeniu. Wszystkie <xref:System.String> metody i operatory C#, które wydają się zmodyfikować ciąg faktycznie zwracają wyniki w nowym obiekcie string. W poniższym przykładzie gdy zawartość `s1` i `s2` są połączone do jednego ciągu, dwa ciągi oryginalnego są zostały zmodyfikowane. `+=` Operator tworzy nowy ciąg, który zawiera łączne zawartość. Ten nowy obiekt jest przypisany do zmiennej `s1`i oryginalny obiekt, który został przypisany do `s1` wydane dla wyrzucanie elementów bezużytecznych, ponieważ nie inne zmienna przechowuje odwołanie do niej.  
  
 [!code-csharp[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 Ciąg "Modyfikowanie" jest rzeczywiście ciąg Tworzenie nowego, należy zachować ostrożność, po utworzeniu odwołania do ciągów. Jeśli utworzenie odwołania do ciągu, a następnie "Modyfikuj" oryginalnego ciągu, odwołanie będzie wskaż oryginalny obiekt zamiast nowego obiektu, który został utworzony, gdy ciąg został zmodyfikowany. Poniższy kod ilustruje tego zachowania:  
  
 [!code-csharp[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 Aby uzyskać więcej informacji dotyczących sposobu tworzenia nowych ciągów, które są oparte na zmiany, takie jak wyszukiwanie i zamienianie operacji w oryginalnym ciągu, zobacz [porady: modyfikowanie zawartości ciągu](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Literały ciągu regularne i dosłownego wyrażenia  
 Używaj literałów ciągów regularne, gdy należy osadzić znaki specjalne podane w języku C#, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 Użyj ciągi verbatim dla wygody i zwiększenia czytelności, gdy tekst ciąg zawiera znaki ukośnik odwrotny, na przykład w ścieżkach plików. Ponieważ ciągi verbatim Zachowaj znaki nowego wiersza jako część ciągu tekstowego, mogą być używane zainicjować ciągi wielowierszowe. Aby osadzić znak cudzysłowu w ciągu dosłownego wyrażenia, należy użyć podwójnego cudzysłowu. W poniższym przykładzie przedstawiono niektóre typowe zastosowania ciągi verbatim:  
  
 [!code-csharp[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## <a name="string-escape-sequences"></a>Sekwencje unikowe ciągu  
  
|Sekwencja specjalna|Nazwa znaku|Kodowanie Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|pojedynczy cudzysłów|0x0027|  
|\\"|podwójnego cudzysłowu|0x0022|  
|\\\\ |ukośnik odwrotny|0x005C|  
|\0|Null|0x0000|  
|\a|Alert|0x0007|  
|\b|Backspace|0x0008|  
|\f|Wysuw strony|0x000C|  
|\n|Nowy wiersz|0x000A|  
|\r|Powrót karetki|0x000D|  
|\t|Tabulator poziomy|0x0009|  
|\U|Sekwencja ucieczki kodu Unicode znaki dwuskładnikowe.|\Unnnnnnnn|  
|\u|Sekwencja ucieczki kodu Unicode|\u0041 = "A"|  
|\v|Tabulator pionowy|0x000B|  
|\x|Podobnie jak "\u" z wyjątkiem o zmiennej długości sekwencja ucieczki kodu Unicode.|\x0041 = "A"|  
  
> [!NOTE]
>  W czasie kompilacji ciągi verbatim są konwertowane na zwykłe ciągi zawierające te same sekwencji unikowych. W związku z tym Jeśli przeglądasz ciągu dosłownego wyrażenia w oknie wyrażeń kontrolnych debugera, zobaczysz znaki specjalne, które zostały dodane przez kompilator nie dosłownego wyrażenia wersji w kodzie źródłowym. Na przykład ciągu dosłownego wyrażenia @"C:\files.txt" będą wyświetlane w oknie wyrażeń kontrolnych jako "C:\\\files.txt".  
  
## <a name="format-strings"></a>Ciągi formatujące  
 Ciąg formatu to ciąg, którego zawartość można określić dynamicznie w czasie wykonywania. Ciąg formatu jest tworzone przy użyciu statycznych <xref:System.String.Format%2A> — metoda i osadzanie symbole zastępcze w nawiasach klamrowych, które zostaną zastąpione przez inne wartości w czasie wykonywania. W poniższym przykładzie użyto ciąg formatu, aby zapisać wynik każdej iteracji pętli:  
  
 [!code-csharp[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 Jednego przeciążenia <xref:System.Console.WriteLine%2A> metoda przyjmuje jako parametr ciągu formatu. W związku z tym można osadzić tylko literał bez jawnego wywołania do metody ciągu formatu. Jednak jeśli używasz <xref:System.Diagnostics.Trace.WriteLine%2A> metodę w celu wyświetlenia danych wyjściowych debugowania w programie Visual Studio **dane wyjściowe** okna, musisz jawnie wywołać <xref:System.String.Format%2A> — metoda ponieważ <xref:System.Diagnostics.Trace.WriteLine%2A> akceptuje tylko ciąg znaków, a nie w ciągu formatu. Aby uzyskać więcej informacji na temat ciągi formatów, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).  
  
## <a name="substrings"></a>Podciągów  
 Ciąg jest sekwencja znaków, który jest zawarty w ciągu. Użyj <xref:System.String.Substring%2A> metodę w celu utworzenia nowego ciągu z części oryginalnego ciągu. Jedno lub więcej wystąpień podciągu można wyszukiwać za pomocą <xref:System.String.IndexOf%2A> metody. Użyj <xref:System.String.Replace%2A> metody należy zastąpić wszystkie wystąpienia wskazany podciąg nowe parametry. Podobnie jak <xref:System.String.Substring%2A> metody <xref:System.String.Replace%2A> faktycznie zwraca nowy ciąg i nie modyfikować oryginalnego ciągu. Aby uzyskać więcej informacji, zobacz [porady: wyszukiwanie ciągów](../../how-to/search-strings.md) i [porady: modyfikowanie zawartości ciągu](../../how-to/modify-string-contents.md).  
  
 [!code-csharp[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## <a name="accessing-individual-characters"></a>Uzyskiwanie dostępu do poszczególnych znaków  
 Tablicy notacji o wartości indeksu służy do uzyskania dostępu tylko do odczytu do poszczególnych znaków, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 Jeśli <xref:System.String> metod nie udostępniają funkcje, które muszą być konieczne zmodyfikowanie znaki w ciągu, można użyć <xref:System.Text.StringBuilder> obiekt do zmodyfikowania poszczególnych znaków "w miejscu", a następnie utwórz nowe parametry do przechowywania wyników za pomocą <xref:System.Text.StringBuilder> metody. W poniższym przykładzie założono, należy zmodyfikować oryginalny ciąg w określony sposób i następnie zapisać wyniki do użytku w przyszłości:  
  
 [!code-csharp[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## <a name="null-strings-and-empty-strings"></a>Ciągów o wartości null i puste ciągi  
 Ciąg pusty jest wystąpieniem <xref:System.String?displayProperty=nameWithType> obiekt zawierający znaki zero. Puste ciągi są często używane w różnych scenariuszach programowania do reprezentowania puste pole. Można wywoływać metod w pustych ciągów, ponieważ są one prawidłowe <xref:System.String?displayProperty=nameWithType> obiektów. Puste ciągi są inicjowane w następujący sposób:  
  
```  
string s = String.Empty;  
```  
  
 Z kolei pusty ciąg nie odwołuje się do wystąpienia <xref:System.String?displayProperty=nameWithType> obiekt i próba wywołania metody na pusty ciąg przyczyny <xref:System.NullReferenceException>. Jednak można użyć ciągów o wartości null w operacji porównania i łączenia z innymi ciągami. Poniższe przykłady przedstawiają w niektórych przypadkach, w których odwołania na pusty ciąg, a nie powoduje wyjątków:  
  
 [!code-csharp[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Używanie StringBuilder ciąg szybkie tworzenie  
 Operacje na ciągach w programie .NET są stopniu zoptymalizowany i w większości przypadków nie mieć znaczący wpływ na wydajność. Jednak w niektórych scenariuszach, takich jak pętle ścisłej, które wykonują wiele setek lub tysięcy razy, operacje na ciągach może wpłynąć na wydajność. <xref:System.Text.StringBuilder> Klasy utworzenie buforu ciągu, który zapewnia lepszą wydajność, jeśli program wykonuje wiele działań na ciągach. <xref:System.Text.StringBuilder> Ciąg umożliwia również przypisać coś znaki, wbudowane ciągu nie obsługuje typu danych. Ten kod, na przykład zmiany zawartości ciągu bez tworzenia nowego ciągu:  
  
 [!code-csharp[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 W tym przykładzie <xref:System.Text.StringBuilder> obiektu służy do tworzenia ciągu z zestawu typy liczbowe:  
  
 [!code-csharp[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## <a name="strings-extension-methods-and-linq"></a>Ciągi, metod rozszerzeń i LINQ  
 Ponieważ <xref:System.String> typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, można użyć metody rozszerzenia zdefiniowane w <xref:System.Linq.Enumerable> klasy na ciągach. Aby uniknąć bałaganu visual, te metody są wykluczone z technologii IntelliSense dla <xref:System.String> typu, ale są jednak dostępne. Można również użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia na ciągi zapytań. Aby uzyskać więcej informacji, zobacz [LINQ i ciągi](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Instrukcje: modyfikowanie zawartości ciągu](../../how-to/modify-string-contents.md)|Ilustracja technik Przekształcanie ciągów i zmodyfikowania zawartości ciągów.|  
|[Instrukcje: porównywanie ciągów](../../how-to/compare-strings.md)|Pokazuje, jak wykonać porządkowej i kultury porównań określonych ciągów.|  
|[Instrukcje: łączenie wielu ciągów](../../how-to/concatenate-multiple-strings.md)|Przedstawia różne sposoby dołączenia wielu ciągów w jeden.|
|[Porady: analizowanie ciągów za pomocą String.Split ](../../how-to/parse-strings-using-split.md)|Zawiera przykłady kodu, które przedstawiają sposób użycia `String.Split` metodę, aby przeanalizować parametry.|  
|[Porady: wyszukiwanie ciągów](../../how-to/search-strings.md)|Wyjaśniono, jak użyć funkcji wyszukiwania dla określonego tekstu lub wzorce w ciągach.|  
|[Instrukcje: określanie, czy ciąg reprezentuje wartość liczbową](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Pokazuje, jak można bezpiecznie przeanalizować ciągu czy ma prawidłową wartość liczbową.|  
|[Interpolacja ciągów](../../language-reference/tokens/interpolated.md)|Zawiera opis funkcji interpolacji ciągu, która umożliwia wygodne składni formatowanie ciągów.|
|[Podstawowe operacje na ciągach](../../../../docs/standard/base-types/basic-string-operations.md)|Zawiera łącza do tematów, które używają <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> metody wykonywać podstawowe operacje na ciągach.|  
|[Analizowanie ciągów](../../../standard/base-types/parsing-strings.md)|Opisuje sposób konwertowania ciągu reprezentacje typów podstawowych .NET do wystąpień odpowiednie typy.|  
|[Analizowanie ciągów daty i godziny w .NET](../../../standard/base-types/parsing-datetime.md)|Pokazuje, jak można przekonwertować ciągu, takich jak "2008-01-24" do <xref:System.DateTime?displayProperty=nameWithType> obiektu.|  
|[Porównywanie ciągów](../../../../docs/standard/base-types/comparing.md)|Zawiera informacje na temat sposobu porównywania ciągów oraz przykłady w języku C# i Visual Basic.|  
|[Używanie klasy StringBuilder](../../../standard/base-types/stringbuilder.md)|Opisuje sposób tworzenia i modyfikowania obiektów ciąg dynamiczny za pomocą <xref:System.Text.StringBuilder> klasy.|  
|[LINQ i ciągi](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|Zawiera informacje dotyczące sposobu wykonywania różnych operacji na ciągach przy użyciu zapytań LINQ.|  
|[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)|Zawiera łącza do tematów dotyczących konstrukcji programowania w języku C#.|  
