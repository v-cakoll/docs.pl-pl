---
title: Ciągi (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: a06a5144e91901417906f071efd8e19c10cf2cba
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170655"
---
# <a name="strings-c-programming-guide"></a>Ciągi (Przewodnik programowania w języku C#)
Ciąg jest obiektem typu <xref:System.String> którego wartość jest wartością tekstową. Wewnętrznie, tekst jest przechowywany jako sekwencyjną kolekcją tylko do odczytu z <xref:System.Char> obiektów. Brak nie znaku zakończenia o wartości null na końcu ciągu języka C#; w związku z tym ciąg języka C# może zawierać dowolną liczbę osadzone znaki null ('\0'). <xref:System.String.Length%2A> Właściwość ciągu reprezentuje liczbę `Char` obiektów zawiera, nie liczbę znaków Unicode. Aby uzyskać dostęp do poszczególnych punkty kodowe Unicode w ciągu, należy użyć <xref:System.Globalization.StringInfo> obiektu.  
  
## <a name="string-vs-systemstring"></a>Ciąg programu vs. System.String  
 W języku C# `string` — słowo kluczowe jest aliasem <xref:System.String>. W związku z tym `String` i `string` są równoważne, a można użyć jednego z tych konwencji nazewnictwa użytkownik sobie tego życzy. `String` Klasa udostępnia wiele metod tworzenia bezpiecznego, manipulowanie i porównywanie ciągów. Ponadto w języku C# przeciążenia niektóre operatory upraszczające typowe operacje na ciągach. Aby uzyskać więcej informacji na temat słowa kluczowego, zobacz [ciąg](../../../csharp/language-reference/keywords/string.md). Aby uzyskać więcej informacji o typie i jego metod, zobacz <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Deklarowanie i Inicjowanie ciągów  
 Można zadeklarować i zainicjować ciągi na różne sposoby, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 Należy zauważyć, że nie używasz [nowe](../../../csharp/language-reference/keywords/new-operator.md) operatora do utworzenia obiektu ciąg, z wyjątkiem sytuacji, gdy inicjowanie ciągu z tablicy znaków.  
  
 Inicjuje ciąg z użyciem <xref:System.String.Empty> stałą wartość, aby utworzyć nowy <xref:System.String> obiektu, którego parametry są o zerowej długości. Literał ciągu reprezentującego ciągiem o zerowej długości jest "". Przez inicjowanie ciągów za pomocą <xref:System.String.Empty> wartości zamiast [null](../../../csharp/language-reference/keywords/null.md), można zmniejszyć prawdopodobieństwo <xref:System.NullReferenceException> występuje. Używa się statycznej <xref:System.String.IsNullOrEmpty%28System.String%29> metodę, aby sprawdzić wartość ciągu, zanim spróbujesz uzyskać do niego dostęp.  
  
## <a name="immutability-of-string-objects"></a>Niezmienność obiektów w postaci ciągów  
 Obiektów w postaci ciągów są *niezmienne*: nie można zmienić po ich utworzeniu. Wszystkie <xref:System.String> metody i operatory C#, które pojawiają się zmodyfikować ciągu rzeczywistości zwracają wyniki w nowym obiekcie ciągu. W poniższym przykładzie gdy zawartość `s1` i `s2` są łączone w celu utworzenia pojedynczego ciągu, niezmodyfikowanego są dwa ciągi oryginalnej. `+=` Operatora, tworzy nowy ciąg, który zawiera połączone zawartość. Nowy obiekt jest przypisany do zmiennej `s1`, a oryginalny obiekt, który został przypisany do `s1` wydane do wyrzucania elementów bezużytecznych, ponieważ nie inne zmienna zawiera odwołanie do niej.  
  
 [!code-csharp[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 Ponieważ ciąg "modyfikacji" jest faktycznie nowe tworzenia ciągu, należy zachować ostrożność podczas tworzenia odwołania do ciągów. Jeśli utworzenie odwołania do ciągu, a następnie "Modyfikuj" oryginalny ciąg odwołania będzie nadal wskaż oryginalnego obiektu zamiast nowy obiekt, który został utworzony podczas modyfikacji ciągu. Poniższy kod ilustruje ten problem:  
  
 [!code-csharp[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 Aby uzyskać więcej informacji na temat tworzenia nowych ciągów, które są oparte na modyfikacje, takich jak wyszukiwanie i zamienianie operacji w oryginalnym ciągu, zobacz [porady: modyfikowanie zawartości ciągu](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Literały ciągów znaków zwykłych i Verbatim  
 Używaj literałów ciągów regularne, gdy należy osadzić znaki ucieczki dostarczana przez C#, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 Na użytek ciągi verbatim zwiększenie wygody działania i zwiększenia czytelności, gdy ciąg tekstu zawiera ukośnik odwrotny znaków, na przykład w ścieżkach plików. Ponieważ ciągi verbatim Zachowaj znaki nowego wiersza, jako część ciąg tekstu, ich może służyć do zainicjowania ciągi wielowierszowe. Aby osadzić znak cudzysłowu wewnątrz ciąg verbatim, należy użyć podwójnego cudzysłowu. Jedne z typowych zastosowań ciągi verbatim można znaleźć w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## <a name="string-escape-sequences"></a>Sekwencje ucieczki w ciągu  
  
|Sekwencja unikowa|Nazwa znaków|Kodowanie Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|pojedynczy cudzysłów|0x0027|  
|\\"|podwójny cudzysłów|0x0022|  
|\\\\ |Ukośnik odwrotny|0x005C|  
|\0|Null|0x0000|  
|\a|Zgłoś alert|0x0007|  
|\b|Backspace|0x0008|  
|\f|Wysuw strony|0x000C|  
|\n|Nowy wiersz|0x000A|  
|\r|Powrót karetki|0x000D|  
|\t|tabulator poziomy|0x0009|  
|\U|Sekwencja unikowa Unicode znaki dwuskładnikowe.|\Unnnnnnnn|  
|\u|Sekwencja unikowa Unicode|\u0041 = "A"|  
|\v|tabulator pionowy|0x000B|  
|\x|Sekwencja unikowa Unicode jest podobny do "\u" z wyjątkiem o zmiennej długości.|\x0041 lub \x41 = "A"|  
  
> [!NOTE]
>  W czasie kompilacji ciągi verbatim są konwertowane na zwykłe ciągi przy użyciu tych samych sekwencje ucieczki. W związku z tym jeśli ciąg verbatim można wyświetlić w oknie czujki debugera, zobaczysz znaki ucieczki, które zostały dodane przez kompilator nie verbatim wersji z kodu źródłowego. Na przykład ciąg verbatim @"C:\files.txt" będą wyświetlane w oknie czujki jako "C:\\\files.txt".  
  
## <a name="format-strings"></a>Ciągi formatujące  
 Ciąg formatu to ciąg, w których zawartość może być określany dynamicznie w czasie wykonywania. Utwórz ciąg formatu przy użyciu statycznej <xref:System.String.Format%2A> metody i osadzanie symbole zastępcze w nawiasach klamrowych, które zostaną zastąpione przez inne wartości w czasie wykonywania. W poniższym przykładzie użyto ciągu formatu służący do wypełniania wyjściowego wynik każdej iteracji pętli:  
  
 [!code-csharp[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 Jednego przeciążenia <xref:System.Console.WriteLine%2A> metoda przyjmuje ciąg formatu jako parametr. W związku z tym można po prostu osadzić ciąg formatu literał bez jawnego wywołania do metody. Jednak jeśli używasz <xref:System.Diagnostics.Trace.WriteLine%2A> metodę w celu wyświetlenia danych wyjściowych debugowania w programie Visual Studio **dane wyjściowe** okna, trzeba jawnie wywołać <xref:System.String.Format%2A> metody ponieważ <xref:System.Diagnostics.Trace.WriteLine%2A> akceptuje tylko ciąg, a nie w ciągu formatu. Aby uzyskać więcej informacji na temat ciągów formatujących, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).  
  
## <a name="substrings"></a>Podciągów  
 Podciąg jest dowolną sekwencję znaków, który znajduje się w ciągu. Użyj <xref:System.String.Substring%2A> metodę, aby utworzyć nowy ciąg z części oryginalny ciąg. Jedno lub więcej wystąpień podciągu można wyszukiwać za pomocą <xref:System.String.IndexOf%2A> metody. Użyj <xref:System.String.Replace%2A> metodę, aby zastąpić wszystkie wystąpienia określony podciąg nowy ciąg. Podobnie jak <xref:System.String.Substring%2A> metody <xref:System.String.Replace%2A> rzeczywistości zwraca nowy ciąg, a nie zmodyfikuje oryginalny ciąg. Aby uzyskać więcej informacji, zobacz [porady: wyszukiwanie ciągów](../../how-to/search-strings.md) i [porady: modyfikowanie zawartości ciągu](../../how-to/modify-string-contents.md).  
  
 [!code-csharp[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## <a name="accessing-individual-characters"></a>Uzyskiwanie dostępu do poszczególnych znaków  
 Za pomocą notacji tablicy i wartości indeksu można uzyskać dostęp tylko do odczytu do pojedynczych znaków, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 Jeśli <xref:System.String> metody nie udostępniają funkcje, które musi mieć, aby zmodyfikować pojedynczych znaków w ciągu, można użyć <xref:System.Text.StringBuilder> obiekt do zmodyfikowania poszczególne znaki "w miejscu", a następnie utwórz nowy ciąg do przechowywania wyników przy użyciu <xref:System.Text.StringBuilder> metody. W poniższym przykładzie przyjmijmy, że należy zmodyfikować oryginalny ciąg w określony sposób, a następnie zapisać wyniki do użycia w przyszłości:  
  
 [!code-csharp[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## <a name="null-strings-and-empty-strings"></a>Ciągi zerowe i puste ciągi  
 Pusty ciąg jest wystąpieniem <xref:System.String?displayProperty=nameWithType> obiekt, który zawiera zero znaków. Puste ciągi są często używane w różnych scenariuszach programowania do reprezentowania pole tekstowe puste. Można wywoływać metody dla pustych ciągów, ponieważ są one prawidłowe <xref:System.String?displayProperty=nameWithType> obiektów. Puste ciągi są inicjowane w następujący sposób:  
  
```  
string s = String.Empty;  
```  
  
 Z drugiej strony, pusty ciąg nie odwołuje się do wystąpienia <xref:System.String?displayProperty=nameWithType> obiekt i wszystkie próby wywołania metody wobec ciągiem o wartości null powoduje, że <xref:System.NullReferenceException>. Jednak można użyć ciągów o wartości null w operacji porównywania i łączenia z innymi ciągami. W poniższych przykładach pokazano niektóre przypadki, w których jest odwołanie do pusty ciąg, a nie powoduje zgłoszenie wyjątku:  
  
 [!code-csharp[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Używanie StringBuilder do tworzenia szybkich ciągu  
 Operacje na ciągach w programie .NET wysoce zoptymalizowane i w większości przypadków nie znacznie wpłynąć na wydajność. Jednak w niektórych scenariuszach, takich jak ścisłej pętli, które są wykonywane wiele setki lub tysiące razy, operacje na ciągach może wpłynąć na wydajność. <xref:System.Text.StringBuilder> Klasy tworzy buforu ciągu, który oferuje lepszą wydajność, jeśli program wykonuje wiele działań na ciągach. <xref:System.Text.StringBuilder> Ciągu umożliwia także ponowne przypisywanie poszczególnych znaków coś wbudowanych ciągu nie obsługuje typu danych. Ten kod, na przykład zmiany zawartości ciągu bez tworzenia nowego ciągu:  
  
 [!code-csharp[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 W tym przykładzie <xref:System.Text.StringBuilder> obiekt jest używany do tworzenia ciągu z zestawu typów liczbowych:  
  
 [!code-csharp[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## <a name="strings-extension-methods-and-linq"></a>Ciągi i metod rozszerzeń LINQ  
 Ponieważ <xref:System.String> typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, można użyć metody rozszerzenia zdefiniowane w <xref:System.Linq.Enumerable> klasy na ciągi. Aby uniknąć zaśmiecania visual, te metody są wykluczane z technologii IntelliSense dla <xref:System.String> typu, ale są jednak dostępne. Można również użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach dla ciągów zapytań. Aby uzyskać więcej informacji, zobacz [LINQ i ciągi](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Instrukcje: modyfikowanie zawartości ciągu](../../how-to/modify-string-contents.md)|Ilustruje techniki Przekształcanie ciągów i modyfikowania zawartości ciągów.|  
|[Instrukcje: porównywanie ciągów](../../how-to/compare-strings.md)|Pokazuje, jak przeprowadzić porządkowe i kultury określonej porównania ciągów.|  
|[Instrukcje: łączenie wielu ciągów](../../how-to/concatenate-multiple-strings.md)|Ilustruje różne sposoby, aby dołączyć wielu ciągów w jeden.|
|[Porady: analizowanie ciągów za pomocą funkcji String.Split ](../../how-to/parse-strings-using-split.md)|Zawiera przykłady kodu, które ilustrują sposób korzystania `String.Split` metodę, aby przeanalizować ciągi.|  
|[Porady: wyszukiwanie ciągów](../../how-to/search-strings.md)|Opis sposobu użycia wyszukać określony tekst lub wzorców w ciągach.|  
|[Instrukcje: określanie, czy ciąg reprezentuje wartość liczbową](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Pokazuje, jak bezpiecznie przeanalizować składni ciągu, aby zobaczyć, czy ma prawidłową wartość liczbową.|  
|[Interpolacja ciągów](../../language-reference/tokens/interpolated.md)|Zawiera opis funkcji interpolacji ciągu, która udostępnia wygodne Składnia na ciągi formatu.|
|[Podstawowe operacje na ciągach](../../../../docs/standard/base-types/basic-string-operations.md)|Zawiera łącza do tematów, które używają <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> metody, aby wykonywać podstawowe operacje na ciągach.|  
|[Analizowanie ciągów](../../../standard/base-types/parsing-strings.md)|W tym artykule opisano sposób konwertowania ciągów reprezentujących podstawowych typów .NET do wystąpień odpowiednie typy.|  
|[Analizowanie ciągów daty i godziny na platformie .NET](../../../standard/base-types/parsing-datetime.md)|Pokazuje, jak przekonwertować ciąg, taki jak "01/24/2008" Aby <xref:System.DateTime?displayProperty=nameWithType> obiektu.|  
|[Porównywanie ciągów](../../../../docs/standard/base-types/comparing.md)|Zawiera informacje na temat sposobu porównywania ciągów i zawiera przykłady w języku C# i Visual Basic.|  
|[Używanie klasy StringBuilder](../../../standard/base-types/stringbuilder.md)|W tym artykule opisano sposób tworzenia i modyfikowania obiektów dynamicznych parametrów przy użyciu <xref:System.Text.StringBuilder> klasy.|  
|[LINQ i ciągi](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|Zawiera informacje dotyczące sposobu wykonywania różnych operacji na ciągach przy użyciu zapytań LINQ.|  
|[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)|Zawiera łącza do tematów, które opisują konstrukcje programowania w języku C#.|  
