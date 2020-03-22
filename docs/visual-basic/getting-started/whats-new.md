---
title: Co nowego w programie Visual Basic
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: 3ab468f6c68429a3a5cb8706152288afae520df3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187141"
---
# <a name="whats-new-for-visual-basic"></a>Co nowego w programie Visual Basic

W tym temacie wymieniono nazwy kluczowych funkcji dla każdej wersji programu Visual Basic wraz ze szczegółowymi opisami nowych i ulepszonych funkcji w najnowszych wersjach języka.

## <a name="current-version"></a>Bieżąca wersja

Visual Basic 16.0 / Visual Studio 2019 w wersji 16.0\
Aby uzyskać nowe funkcje, zobacz [Visual Basic 16.0](#visual-basic-160).

## <a name="previous-versions"></a>Poprzednie wersje

Visual Basic 15.8 / Visual Studio 2017 w wersji 15.8\
Aby uzyskać nowe funkcje, zobacz [Visual Basic 15.8](#visual-basic-158).

Visual Basic 15.5 / Visual Studio 2017 w wersji 15.5\
Aby uzyskać nowe funkcje, zobacz [Visual Basic 15.5](#visual-basic-155).

Visual Basic 15.3 / Visual Studio 2017 w wersji 15.3\
Aby uzyskać nowe funkcje, zobacz [Visual Basic 15.3](#visual-basic-153).

Visual Basic 2017 / Visual Studio 2017\
Aby uzyskać nowe funkcje, zobacz [Visual Basic 2017](#visual-basic-2017).

Visual Basic / Visual Studio 2015\
Aby uzyskać nowe funkcje, zobacz [Visual Basic 14](#visual-basic-14).

Visual Basic / Visual Studio 2013\
Podglądy technologii platformy kompilatora .NET ("Roslyn")

Visual Basic / Visual Studio 2012\
`Async`i `await` słowa kluczowe, iteratory, atrybuty informacji o rozmówcy

Visual Basic, Visual Studio 2010\
Automatycznie implementowane właściwości, inicjatory kolekcji, kontynuacja wiersza niejawnego, dynamiczne, ogólne odchylenie co/contra, globalny dostęp do przestrzeni nazw

Visual Basic / Visual Studio 2008\
Zintegrowane zapytanie językowe (LINQ), literały XML, wnioskowanie o typach lokalnych, inicjatory obiektów, typy anonimowe, metody rozszerzenia, wnioskowanie o typie lokalnym, `var` wyrażenia lambda, `if` operator, metody częściowe, typy wartości nullable

Visual Basic / Visual Studio 2005\
Typy `My` typów i pomocników (dostęp do aplikacji, komputera, systemu plików, sieci)

Visual Basic / Visual Studio .NET 2003\
Operatory zmiany bitowej, deklaracja zmiennej pętli

Visual Basic / Visual Studio .NET 2002\
Pierwsze wydanie programu Visual Basic .NET

## <a name="visual-basic-160"></a>Visual Basic 16.0

Program Visual Basic 16.0 koncentruje się na dostarczaniu większej liczby funkcji środowiska wykonawczego języka Visual Basic (microsoft.visualbasic.dll) do platformy .NET Core i jest pierwszą wersją programu Visual Basic skoncentrowaną na programie .NET Core. Wiele części środowiska wykonawczego języka Visual Basic zależy od wersji WinForms, które zostaną dodane w nowszej wersji programu Visual Basic.

**Komentarze dozwolone w większej liczbie miejsc w zestawieniach**

W języku Visual Basic 15.8 i wcześniejszych wersjach komentarze są dozwolone tylko w pustych wierszach, na końcu instrukcji lub w określonych miejscach w instrukcji, w których dozwolona jest kontynuacja wiersza niejawnego. Począwszy od języka Visual Basic 16.0, komentarze są również dozwolone po jawne kontynuacje wiersza i w instrukcji w wierszu, począwszy od spacji, po której następuje podkreślenie.

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

## <a name="visual-basic-158"></a>Visual Basic 15.8

**Zoptymalizowana konwersja zmiennoprzecinka do liczby całkowitej**

W poprzednich wersjach języka Visual Basic konwersja wartości [Double](../language-reference/data-types/double-data-type.md) i [Single](../language-reference/data-types/single-data-type.md) na liczby całkowite oferowała stosunkowo niską wydajność. Visual Basic 15.8 znacznie zwiększa wydajność konwersji zmiennoprzecinkowych do liczb całkowitych po przeznaczeniu wartości zwróconej za pomocą jednej z następujących metod do jednej z [wewnętrznych funkcji konwersji całkowitej Visual Basic](../language-reference/functions/type-conversion-functions.md) (CByte, CShort, CInt, CLng, CSByte, CUShort, CUInt, CULng) lub gdy wartość zwrócona przez którąkolwiek z następujących metod jest niejawnie rzutowany na integralny [typ,](../language-reference/statements/option-strict-statement.md) gdy opcja Strict jest ustawiona na: `Off`

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Ta optymalizacja umożliwia szybsze uruchamianie kodu — nawet dwa razy szybciej dla kodu, który wykonuje dużą liczbę konwersji do typów liczb całkowitych. Poniższy przykład ilustruje kilka prostych wywołań metody, których dotyczy ta optymalizacja:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

Należy zauważyć, że to obcina, a nie zaokrągla wartości zmiennoprzecinkowych.

## <a name="visual-basic-155"></a>Visual Basic 15.5

[Argumenty nazwane inne niż końcowe](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

W języku Visual Basic 15.3 i wcześniejszych wersjach, gdy wywołanie metody zawierało argumenty zarówno według pozycji, jak i nazwy, argumenty pozycyjne musiały poprzedzać nazwane argumenty. Począwszy od języka Visual Basic 15.5, argumenty pozycyjne i nazwane mogą być wyświetlane w dowolnej kolejności, o ile wszystkie argumenty do ostatniego argumentu pozycyjnego znajdują się we właściwej pozycji. Jest to szczególnie przydatne, gdy nazwane argumenty są używane do kodu bardziej czytelny.

Na przykład następujące wywołanie metody ma dwa argumenty pozycyjne między argumentem nazwany. Nazwany argument wyjaśnia, że wartość 19 reprezentuje wiek.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected`modyfikator dostępu do członków](../language-reference/modifiers/private-protected.md)

Ta nowa kombinacja słów kluczowych definiuje element członkowski, który jest dostępny dla wszystkich elementów członkowskich w jego klasy zawierającej, jak również przez typy pochodzące z klasy zawierającej, ale tylko wtedy, gdy znajdują się one również w zestawie zawierającym. Ponieważ struktury nie mogą `Private Protected` być dziedziczone, mogą być stosowane tylko do członków klasy.

**Wiodący separator sześciokątny/binarny/ósemkowy**

W programie Visual Basic 2017`_`dodano obsługę znaku podkreślenia ( ) jako separatora cyfr. Począwszy od języka Visual Basic 15.5, można użyć znaku podkreślenia jako interełownika między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. W poniższym przykładzie użyto separatora cyfr wiodących do zdefiniowania 3 271 948 384 jako liczby szesnastkowej:

```vb
Dim number As Integer = &H_C305_F860
```

Aby użyć znaku podkreślenia jako separatora wiodącego, należy dodać\*następujący element do pliku projektu języka Visual Basic ( .vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**Wnioskowanie o nazwie krotki**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Po przypisaniu wartości elementów krotki ze zmiennych visual basic wnioskuje nazwę elementów krotki z odpowiednich nazw zmiennych; nie trzeba jawnie nazwać elementu krotki. W poniższym przykładzie użyto wnioskowania do utworzenia krotki z trzema nazwanymi elementami, `state`, `stateName`i `capital`.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Dodatkowe przełączniki kompilatora**

Kompilator wiersza polecenia języka Visual Basic obsługuje teraz opcje kompilatora [**-refout**](../reference/command-line-compiler/refout-compiler-option.md) i [**-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) do kontrolowania danych wyjściowych zestawów referencyjnych. **-refout** definiuje katalog wyjściowy zestawu odwołań i **-refonly** określa, że tylko zestaw odniesienia ma być wyprowadzany przez kompilację.

## <a name="visual-basic-2017"></a>Program Visual Basic 2017

[**Krotek**](../programming-guide/language-features/data-types/tuples.md)

Krotek są odciążona struktura danych, która najczęściej jest używana do zwracania wielu wartości z wywołania pojedynczej metody. Zwykle, aby zwrócić wiele wartości z metody, należy wykonać jedną z następujących czynności:

- Zdefiniuj `Class` typ `Structure`niestandardowy (a lub a ). Jest to rozwiązanie wagi ciężkiej.

- Zdefiniuj jeden lub więcej `ByRef` parametrów, oprócz zwracania wartości z metody.

Obsługa krotek w języku Visual Basic umożliwia szybkie zdefiniowanie krotki, opcjonalnie przypisać nazwy semantyczne do jego wartości i szybko pobrać jego wartości. Poniższy przykład otacza wywołanie <xref:System.Int32.TryParse%2A> metody i zwraca krotki.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Następnie można wywołać metodę i obsłużyć zwróconą kroszkę z kodem, podobnie jak poniżej.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**Literały binarne i separatory cyfr**

Literał binarny można zdefiniować `&B` za `&b`pomocą prefiksu lub pliku . Ponadto można użyć znaku podkreślenia, jako separatora cyfry, `_`aby zwiększyć czytelność. W poniższym przykładzie użyto `Byte` obu operacji do przypisania wartości i wyświetlenia jej jako liczby dziesiętnej, szesnastkowej i binarnej.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Aby uzyskać więcej informacji, zobacz sekcję "Przydziały dosłowne" typów danych [Bajt](../language-reference/data-types/byte-data-type.md#literal-assignments), [Liczba całkowita](../language-reference/data-types/integer-data-type.md#literal-assignments), [Długa](../language-reference/data-types/long-data-type.md#literal-assignments), [Krótka, Bajt,](../language-reference/data-types/sbyte-data-type.md#literal-assignments) [UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments)i [UShort.](../language-reference/data-types/ushort-data-type.md#literal-assignments) [Short](../language-reference/data-types/short-data-type.md#literal-assignments)

[**Obsługa wartości zwracania odwołania c#**](../programming-guide/language-features/procedures/ref-return-values.md)

Począwszy od języka C# 7.0, C# obsługuje odwołania wartości zwracane. Oznacza to, że gdy wywołanie metoda odbiera wartość zwróconą przez odwołanie, można zmienić wartość odwołania. Visual Basic nie pozwala na tworzenie metod z odwołania zwracane wartości, ale to pozwala na korzystanie i modyfikowanie wartości zwracane odwołania.

Na przykład następująca `Sentence` klasa napisana w `FindNext` języku C# zawiera metodę, która znajduje następny wyraz w zdaniu, który zaczyna się od określonego podciągu. Ciąg jest zwracany jako odwołanie wartości `Boolean` zwracanej, a zmienna przekazywana przez odwołanie do metody wskazuje, czy wyszukiwanie zakończyło się pomyślnie. Oznacza to, że oprócz odczytu zwracana wartość, obiektu wywołującego można również `Sentence` zmodyfikować go i tej modyfikacji jest odzwierciedlone w klasie.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

W najprostszej formie można zmodyfikować słowo znalezione w zdaniu za pomocą kodu, takiego jak poniżej. Należy zauważyć, że nie są przypisywanie wartości do metody, ale raczej do wyrażenia, które zwraca metoda, która jest odwołanie wartości zwracanej.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Problem z tym kodem jest jednak, że jeśli dopasowanie nie zostanie znaleziony, metoda zwraca pierwsze słowo. Ponieważ w przykładzie nie bada `Boolean` wartość argumentu, aby ustalić, czy dopasowanie zostanie znalezione, modyfikuje pierwszy wyraz, jeśli nie ma dopasowania. Poniższy przykład koryguje to, zastępując pierwszy wyraz z siebie, jeśli nie ma dopasowania.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Lepszym rozwiązaniem jest użycie metody pomocnika, do której wartość zwracana odwołanie jest przekazywana przez odwołanie. Metoda pomocnika można następnie zmodyfikować argument przekazany do niego przez odwołanie. Poniższy przykład to robi.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Aby uzyskać więcej informacji, zobacz [Odwołanie do wartości zwracane](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[NazwaOf](../language-reference/operators/nameof.md)

Można uzyskać niekwalifikowaną nazwę ciągu typu lub elementu członkowskiego do użycia w komunikacie o błędzie bez twardego kodowania ciągu.  Dzięki temu kod zachować poprawne podczas refaktoryzacji.  Ta funkcja jest również przydatna do podłączania łącza MVC kontrolera widoku modelu i wypalania zdarzeń zmienionych właściwości.

[Interpolacja ciągów](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

Do konstruowania ciągów można użyć wyrażeń interpolacji ciągów.  Interpolowane wyrażenie ciągu wygląda jak ciąg szablonu zawierający wyrażenia.  Interpolowany ciąg jest łatwiejszy do zrozumienia w odniesieniu do argumentów niż [formatowanie złożone](../../standard/base-types/composite-formatting.md).

[Dostęp do elementów członkowskich warunkowych z wartością null i indeksowanie](../language-reference/operators/null-conditional-operators.md)

Przed wykonaniem operacji dostępu elementu członkowskiego (`?.`) lub index (`?[]`) można przetestować wartość null w bardzo lekki sposób składniowy.  Te operatory ułatwiają pisanie mniej kodu do obsługi kontroli null, szczególnie w przypadku malejąco do struktur danych.  Jeśli lewy argument lub odwołanie do obiektu ma wartość null, operacje zwracają wartość null.

[Literały ciągów wielowierszowych](../../visual-basic/programming-guide/language-features/strings/string-basics.md)

Literały ciągów mogą zawierać sekwencje nowego linii.  Nie potrzebujesz już starej pracy wokół korzystania z`<xml><![CDATA[...text with newlines...]]></xml>.Value`

**Komentarze**

Można umieścić komentarze po niejawnych kontynuacji wiersza, wewnątrz wyrażeń inicjatora i wśród terminów wyrażenia LINQ.

**Inteligentniejsza, w pełni kwalifikowana rozdzielczość nazw**

Biorąc pod `Threading.Thread.Sleep(1000)`uwagę kod, takich jak Visual Basic używane do wyszukiwania obszaru nazw "Wątki", odkryć, że był niejednoznaczny między System.Threading i System.Windows.Threading, a następnie zgłosić błąd.  Visual Basic uwzględnia teraz oba możliwe przestrzenie nazw razem.  Jeśli zostanie wyświetlona lista ukończenia, edytor programu Visual Studio wyświetla listę członków z obu typów na liście uzupełniania.

**Literały daty na początku roku**

Możesz mieć dosłowy daty w formacie yyyy-mm-dd, `#2015-03-17 16:10 PM#`.

**Właściwości interfejsu readonly**

Można zaimplementować tylko do odczytu właściwości interfejsu przy użyciu readwrite właściwości. Interfejs gwarantuje minimalne funkcje i nie zatrzymuje implementującej klasy z zezwalania na właściwość, która ma być ustawiona.

[TypeOf \<expr> IsNot \<typ>](../../visual-basic/language-reference/operators/typeof-operator.md)

Aby uzyskać więcej czytelności kodu, `TypeOf` można `IsNot`teraz używać z .

[> identyfikator ostrzeżenia \<#Disable i>identyfikatora ostrzeżenia \<#Enable](../../visual-basic/language-reference/directives/index.md)

Można wyłączyć i włączyć określone ostrzeżenia dla regionów w pliku źródłowym.

**Ulepszenia komentarza do doc XML**

Podczas pisania komentarzy doc, można uzyskać inteligentny edytor i budować `crefs` obsługę sprawdzania poprawności nazw parametrów, właściwej obsługi (ogólne, operatory, itp.), kolorowanie i refaktoryzacji.

[Definicje modułów częściowych i interfejsów](../../visual-basic/language-reference/modifiers/partial.md)

Oprócz klas i struktur można zadeklarować częściowe moduły i interfejsy.

[#Region dyrektyw wewnątrz organów metod](../../visual-basic/language-reference/directives/region-directive.md)

Można umieścić #Region... #End ograniczniki regionu w dowolnym miejscu w pliku, wewnątrz funkcji, a nawet obejmujące między organami funkcji.

[Definicje zastępowań są niejawnie przeciążeniami](../../visual-basic/language-reference/modifiers/overrides.md)

Jeśli dodasz `Overrides` modyfikator do definicji, kompilator niejawnie dodaje, `Overloads` dzięki czemu można wpisać mniej kodu w typowych przypadkach.

**CObj dozwolone w argumentach atrybutów**

Kompilator używany do podania błędu, który CObj (...) nie był stałą, gdy był używany w konstrukcjach atrybutów.

**Deklarowanie i spożywanie niejednoznacznych metod z różnych interfejsów**

Wcześniej następujący kod dał błędy, które uniemożliwiały `IMock` deklarowanie `GetDetails` lub wywoływanie (jeśli zostały one zadeklarowane w języku C#):

```vb
Interface ICustomer
  Sub GetDetails(x As Integer)
End Interface

Interface ITime
  Sub GetDetails(x As String)
End Interface

Interface IMock : Inherits ICustomer, ITime
  Overloads Sub GetDetails(x As Char)
End Interface

Interface IMock2 : Inherits ICustomer, ITime
End Interface
```

Teraz kompilator użyje normalnych reguł rozpoznawania `GetDetails` przeciążenia, aby wybrać najbardziej odpowiednie do wywołania i można zadeklarować relacje interfejsu w języku Visual Basic, takie jak te pokazane w przykładzie.

## <a name="see-also"></a>Zobacz też

- [Co nowego w programie Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Co nowego w programie Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019)
